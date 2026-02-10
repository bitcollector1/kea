FROM debian:latest

RUN apt update && apt install curl gnupg apt-transport-https -y
RUN curl -1sLf 'https://dl.cloudsmith.io/public/isc/kea-3-0/setup.deb.sh'| bash
RUN apt update && apt install isc-kea -y
RUN apt update && apt install isc-kea-pgsql -y
RUN apt update && apt install isc-kea-admin -y

EXPOSE 67/udp
EXPOSE 67/tcp
EXPOSE 8000/tcp

# Bug in Debian/Docker instance preventing raw sockets unless root
USER root:root

CMD ["/usr/sbin/kea-dhcp4", "-c", "/etc/kea/kea-dhcp4.conf"]
