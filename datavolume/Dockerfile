# This is a base for a persistant data container

FROM stackbrew/busybox:latest
LABEL author="Randy Hall <randy.hall@open-source.guru>"
# Create data directory
RUN mkdir -p /var/lib/mysql

# Create volume 
VOLUME ["/var/lib/mysql"]
