FROM alpine:latest

MAINTAINER fudali113@gmail.com

RUN wget https://storage.googleapis.com/kubernetes-release/release/v1.10.3/bin/linux/amd64/kubectl && \
    chmod +x ./kubectl && \
    mv ./kubectl /usr/local/bin/kubectl
    
RUN wget https://github.com/argoproj/argo/releases/download/v2.1.1/argo-linux-amd64 && \
    chmod +x ./argo-linux-amd64 && \
    mv ./argo-linux-amd64 /usr/local/bin/argo
    
CMD [ "sh" ]
