FROM mhart/alpine-node:latest

RUN apk update && \
    apk add curl

# Install ContainerPilot
ENV CONTAINERPILOT_VERSION dev-not-for-release
COPY containerpilot /bin/containerpilot

# COPY ContainerPilot configuration
COPY containerpilot.json5 /etc/containerpilot.json5
ENV CONTAINERPILOT=/etc/containerpilot.json5


# Install our application
COPY index.js /opt/hello/

EXPOSE 3001
CMD ["/bin/containerpilot"]
