FROM alpine:3.4

# Install nginx and tooling we need
RUN apk update && \
    apk add nginx curl unzip && \
    rm -rf /var/cache/apk/*

# Use consul-template to re-write our Nginx virtualhost config
RUN curl -Lo /tmp/consul_template_0.15.0_linux_amd64.zip https://releases.hashicorp.com/consul-template/0.15.0/consul-template_0.15.0_linux_amd64.zip && \
    unzip /tmp/consul_template_0.15.0_linux_amd64.zip && \
    mv consul-template /bin

# Install ContainerPilot
ENV CONTAINERPILOT_VERSION dev-not-for-release
COPY containerpilot /bin/containerpilot

COPY containerpilot.json5 /etc/containerpilot.json5
ENV CONTAINERPILOT=/etc/containerpilot.json5

COPY reload-nginx.sh /bin/
COPY index.html /usr/share/nginx/html/
COPY style.css /usr/share/nginx/html/
COPY nginx.conf /etc/nginx/nginx.conf
COPY nginx.conf.ctmpl /etc/containerpilot/


EXPOSE 80
CMD ["/bin/containerpilot"]
#, "nginx"]
