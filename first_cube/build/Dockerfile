FROM ubuntu:18.04
MAINTAINER MLPerf MLBox Working Group

# Remove all stopped containers: docker rm $(docker ps -a -q)
# Remove containers like none:none: docker rmi $(docker images | grep none | awk '{print $3}')

WORKDIR /workspace

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
            software-properties-common \
            python3-dev \
            curl && \
    rm -rf /var/lib/apt/lists/*

RUN curl -fSsL -O https://bootstrap.pypa.io/get-pip.py && \
    python3 get-pip.py && \
    rm get-pip.py

COPY requirements.txt /requirements.txt
RUN pip3 install --no-cache-dir -r /requirements.txt

COPY mlc_algo_efficiency_mnist_jax.py /workspace/mlc_algo_efficiency_mnist_jax.py

# defult parameter to ENTRYPOINT 
# CMD  ["10"]

ENTRYPOINT ["python3", "/workspace/mlc_algo_efficiency_mnist_jax.py"]
