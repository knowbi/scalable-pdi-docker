# PDI base image

FROM    ubuntu:16.04

MAINTAINER Yannick Mols

RUN     apt-get update && \
        DEBIAN_FRONTEND=noninteractive \
        apt-get -y install --no-install-recommends openjdk-8-jre-headless && \
        apt-get -y install --no-install-recommends unzip && \
	apt-get -y install --no-install-recommends git && \
	apt-get -y install --no-install-recommends ssh && \
        apt-get clean && \
        rm -rf /var/lib/apt/lists && \
        apt-get purge -y --auto-remove

WORKDIR /opt/
COPY data-integration ./data-integration

ENTRYPOINT ["/bin/bash"]
