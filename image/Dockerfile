FROM python:3.7.5-buster
MAINTAINER Ilya <ilya.kazakevich@jetbrains.com>
# Based on Phusion

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
RUN echo en_US.UTF-8 ru_RU.UTF-8 | dpkg-reconfigure locales
RUN locale-gen
RUN apt-get update \
    && apt-get install -y gettext nginx curl postgresql-client-11



RUN curl https://bootstrap.pypa.io/get-pip.py | python
CMD ["/sbin/my_init"]
