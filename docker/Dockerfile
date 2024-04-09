FROM nvidia/cuda:12.3.0-devel-ubuntu22.04
# replace CUDA version to your CUDA version.
# You can check your CUDA version with below.
# nvcc -V

RUN apt-get update
RUN apt-get install -y python3
RUN apt-get -y install python3-pip git
RUN pip install python-multipart

RUN pip3 install torch torchvision torchaudio
# replace CUDA version to your CUDA version.

RUN mkdir workspace
WORKDIR /workspace

RUN pip3 install fastapi uvicorn[standard] fsspec[http]==2023.5.0
RUN git clone https://github.com/sairin94/nougat.git
WORKDIR /workspace/nougat

RUN python3 setup.py install
RUN pip3 install --no-cache-dir --upgrade numpy

EXPOSE 8503

CMD ["uvicorn", "app:app", "--host", "0.0.0.0", "--port", "8503"]
# Run this using 'docker run -it -d -p <YOUR PORT>:8503 --gpus all <IMAGE NAME>

