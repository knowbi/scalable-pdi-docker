# Provisioning image

FROM	pdi:latest

MAINTAINER Yannick Mols

RUN	useradd -ms /bin/bash pentaho
RUN	chown -R pentaho /opt/*
WORKDIR	/home/pentaho

# add ssh key
COPY	build/ssh/* /home/pentaho/.ssh/
RUN	chown -R pentaho /home/pentaho/

USER	pentaho
RUN     eval "$(ssh-agent -s)" && ssh-add ~/.ssh/id_rsa

# add kettle.properties
COPY	build/properties/kettle.properties .kettle/

# add plugins, drivers, jdbc.properties
WORKDIR	/opt/data-integration
COPY	build/plugins/* plugins/
COPY	build/drivers/* lib/
COPY	build/properties/jdbc.properties simple-jndi/

# add entrypoint
COPY	build/entry/script.sh .
USER	root
RUN	chmod +x script.sh
USER	pentaho

# create mount directory

ENTRYPOINT ["/bin/bash"]
