FROM alpine:latest

MAINTAINER fudali113@gmail.com

RUN wget https://storage.googleapis.com/kubernetes-release/release/v1.10.3/bin/linux/amd64/kubectl && \
    chmod +x ./kubectl && \
    mv ./kubectl /usr/local/bin/kubectl
  
RUN curl -sSL -o /usr/local/bin/argo https://github.com/argoproj/argo/releases/download/v2.1.1/argo-linux-amd64 && \
    chmod +x /usr/local/bin/argo
    
CMD [ "sh" ]
