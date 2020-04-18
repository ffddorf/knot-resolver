FROM debian:10

ENV container docker
ENV LC_ALL C
ENV DEBIAN_FRONTEND noninteractive
VOLUME [ "/sys/fs/cgroup" ]
CMD ["/sbin/init"]

RUN apt-get update && apt-get install -y \
    apt-transport-https \
    ca-certificates \
    gnupg2 \
    python3 \
    sudo \
    systemd \
    systemd-sysv

RUN rm -f /lib/systemd/system/multi-user.target.wants/* \
    /etc/systemd/system/*.wants/* \
    /lib/systemd/system/local-fs.target.wants/* \
    /lib/systemd/system/sockets.target.wants/*udev* \
    /lib/systemd/system/sockets.target.wants/*initctl* \
    /lib/systemd/system/sysinit.target.wants/systemd-tmpfiles-setup* \
    /lib/systemd/system/systemd-update-utmp*
