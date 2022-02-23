# docker build --tag thomasyue/happifyml:HappifyML-pytorch-1.8-cuda11-cudnn8 -f Dockerfile.azure .
# docker push thomasyue/happifyml:HappifyML-pytorch-1.8-cuda11-cudnn8
FROM mcr.microsoft.com/azureml/openmpi4.1.0-cuda11.1-cudnn8-ubuntu18.04
LABEL maintainer="Happify AI Team (Thomas Yue, thomas@happify.com)"

ENV CONDA_ENV_PATH /azureml-envs/pytorch-1.8

# Create conda environment
RUN conda create -p $CONDA_ENV_PATH \
    python=3.8 \
    pip=20.2.4 \
    pytorch=1.8.1 \
    torchvision=0.9.1 \
    cudatoolkit=11.1.1 \
    nvidia-apex=0.1.0 \
    -c anaconda -c pytorch -c conda-forge

# Prepend path to conda environment
ENV PATH $CONDA_ENV_PATH/bin:$PATH

# research template packages
RUN HOROVOD_WITH_PYTORCH=1 \
    pip install 'pytorch-lightning==1.3.5' \ 
                'torchmetrics==0.4.0' \ 
                'deepspeed==0.5.6' \ 
                'hydra-core==1.1.0' \ 
                'hydra-colorlog==1.1.0' \ 
                'hydra-optuna-sweeper==1.1.0' \ 
                'wandb>=0.10.30' \ 
                'transformers==4.12.3' \ 
                'datasets==1.16.1' \ 
                'accelerate==0.3.0' \ 
                'seqeval==1.2.2' \ 
                'pre-commit' \ 
                'black' \ 
                'isort' \ 
                'flake8' \ 
                'rich' \ 
                'scikit-learn>=0.24.2' \ 
                'seaborn>=0.11.1' \ 
                'pandas>=1.2.4' \ 
                'spacy==3.1.0' \ 
                'azureml-core==1.38.0' \
                'azureml-defaults==1.38.0' \
                'azureml-mlflow==1.38.0' \
                'azureml-telemetry==1.38.0' \
                'horovod[pytorch]==0.21.3' \
                'onnxruntime-gpu>=1.7,<1.10'

# This is needed for mpi to locate libpython
ENV LD_LIBRARY_PATH $CONDA_ENV_PATH/lib:$LD_LIBRARY_PATH

SHELL ["/bin/bash", "-c"]