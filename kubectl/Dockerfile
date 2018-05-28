FROM alpine:3.7

MAINTAINER fudali113@gmail.com

RUN wget https://storage.googleapis.com/kubernetes-release/release/v1.10.3/bin/linux/amd64/kubectl && \
    chmod +x ./kubectl && \
    mv ./kubectl /usr/local/bin/kubectl

RUN wget https://github.com/fudali113/k8s-images/releases/download/0.1/go-tpl-replacer-0.1-linux && \
    chmod +x ./go-tpl-replacer-0.1-linux && \
    mv ./go-tpl-replacer-0.1-linux /usr/local/bin/go-tpl-replacer

ENTRYPOINT [ "sh" ]

