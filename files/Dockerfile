FROM python:3.6.0-alpine
ENV CONSUL_TEMPLATE_VERSION=0.19.5
ENV TOKEN=myroot
ENV PORT=8081
RUN apk update
RUN apk add curl
RUN apk add jq
ADD https://releases.hashicorp.com/consul-template/${CONSUL_TEMPLATE_VERSION}/consul-template_${CONSUL_TEMPLATE_VERSION}_linux_amd64.tgz .
RUN tar -C /usr/local/bin -xzvf consul-template_${CONSUL_TEMPLATE_VERSION}_linux_amd64.tgz
RUN chmod 0755 /usr/local/bin/*
COPY config.yml.tpl /src/config.yml.tpl
COPY ./public_html/ /src
COPY ./public_html/commands.sh /tmp/commands.sh
RUN ["chmod", "+x", "/tmp/commands.sh"]
ENTRYPOINT ["/tmp/commands.sh"]
WORKDIR /src
