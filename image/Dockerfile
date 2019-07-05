FROM python:3.6.8-stretch
MAINTAINER Phusion <info@phusion.nl>

ARG QEMU_ARCH
ADD x86_64_qemu-${QEMU_ARCH}-static.tar.gz /usr/bin

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

CMD ["/sbin/my_init"]
