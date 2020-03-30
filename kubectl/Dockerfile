FROM alpine:3.7

MAINTAINER fudali113@gmail.com

RUN mkdir ~/.kube && \
    echo -e "apiVersion: v1 \n\
clusters:   \n\
- cluster:  \n\
{{if .k8sCAD}}\
    certificate-authority-data: {{.k8sCAD}} \n\
{{else}}\
    insecure-skip-tls-verify: true \n\
{{end}}\
    server: {{.k8sServer}}  \n\
  name: k8s \n\
contexts:   \n\
- context:  \n\
    cluster: k8s    \n\
    user: kubernetes-admin  \n\
  name: kubernetes-admin@kubernetes \n\
current-context: kubernetes-admin@kubernetes    \n\
kind: Config    \n\
preferences: {} \n\
users:  \n\
- name: kubernetes-admin    \n\
  user: \n\
    client-certificate-data: {{.k8sCCD}}    \n\
    client-key-data: {{.k8sCKD}}      \n\
{{if .token}}\
    token: {{.token}} \n\
{{end}}\
    " > ~/config.tpl && \
    cat ~/config.tpl > /config.tpl
    
#更新Alpine的软件源为国内（清华大学）的站点，因为从默认官源拉取实在太慢了。。。
RUN echo "https://mirror.tuna.tsinghua.edu.cn/alpine/v3.4/main/" > /etc/apk/repositories

RUN apk update \
        && apk upgrade \
        && apk add --no-cache bash \
        bash-doc \
        bash-completion \
        && rm -rf /var/cache/apk/* \
        && /bin/bash

RUN wget https://storage.googleapis.com/kubernetes-release/release/v1.14.8/bin/linux/amd64/kubectl && \
    chmod +x ./kubectl && \
    mv ./kubectl /usr/local/bin/kubectl

RUN wget https://github.com/fudali113/go-tpl-replacer/releases/download/0.1.1/go-tpl-replacer-0.1.1-linux && \
    chmod +x ./go-tpl-replacer-0.1.1-linux && \
    mv ./go-tpl-replacer-0.1.1-linux /usr/local/bin/go-tpl-replacer
    
RUN wget https://github.com/fudali113/k8s-images/releases/download/v0.1.2/kubedog-linux-amd64-v0.3.4 && \
    chmod +x ./kubedog-linux-amd64-v0.3.4 && \
    mv ./kubedog-linux-amd64-v0.3.4 /usr/local/bin/kubedog

CMD [ "/bin/bash" ]
