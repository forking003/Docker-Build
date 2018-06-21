FROM alpine
MAINTAINER lx0758 lx0758@qq.com

RUN \
sed -i 's/dl-cdn.alpinelinux.org/mirrors.aliyun.com/g' /etc/apk/repositories && \
echo 'http://mirrors.aliyun.com/alpine/v3.7/releases'>>/etc/apk/repositories && \
echo 'http://mirrors.aliyun.com/alpine/edge/main'>>/etc/apk/repositories && \
echo 'http://mirrors.aliyun.com/alpine/edge/testing'>>/etc/apk/repositories && \
echo 'http://mirrors.aliyun.com/alpine/edge/releases'>>/etc/apk/repositories && \
echo 'http://mirrors.aliyun.com/alpine/edge/community'>>/etc/apk/repositories && \
apk add --no-cache bash bash-completion lrzsz curl && \
echo "alias sz='lsz'">>~/.bashrc && \
echo "alias rz='lrz'">>~/.bashrc && \
echo "alias ll='ls -l --color=auto --full-time'">>~/.bashrc && \
source ~/.bashrc

RUN \
apk add --no-cache nginx && \
mkdir /run/nginx && \
sed -i 's/return 404;/root \/var\/lib\/nginx\/html;\n                index index.html index.htm;/g' /etc/nginx/conf.d/default.conf

EXPOSE 80
EXPOSE 443

ENTRYPOINT ["/usr/sbin/nginx", "-g", "daemon off;"]