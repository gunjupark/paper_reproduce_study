FROM pytorch/pytorch:1.11.0-cuda11.3-cudnn8-devel

ENV DEBIAN_FRONTEND=noninteractive

RUN mkdir /secure

### For Certificate #####
RUN apt-get install -y ca-certificates

COPY ./tmp.crt /secure 

RUN cp /secure/tmp.crt /usr/local/share/ca-certificates/ && \
    update-ca-certificates && \
    apt-key adv --keyserver keyserver.ubuntu.com --recv-keys <MY_PUBKEY>

########################3

RUN apt-get update  && \
    apt-get install -y git vim libgtk2.0-dev && \
    rm -rf /var/cache/apk/*

RUN pip --no-cache-dir install Cython

COPY 1_DETR/requirements.txt /workspace

RUN pip --no-cache-dir install -r /workspace/requirements.txt
