FROM python:3.6
MAINTAINER Phusion <info@phusion.nl>

COPY . /bd_build

RUN /bd_build/prepare.sh && \
	/bd_build/system_services.sh && \
	/bd_build/utilities.sh && \
	/bd_build/cleanup.sh

ENV DEBIAN_FRONTEND="teletype" \
    LANG="en_US.UTF-8" \
    LANGUAGE="en_US:en" \
    LC_ALL="en_US.UTF-8"


# Generate locale
RUN echo en_US.UTF-8 | dpkg-reconfigure locales

CMD ["/sbin/my_init"]
