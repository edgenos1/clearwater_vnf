FROM aahad91/cw-base
MAINTAINER aahad91

RUN apt-get update && DEBIAN_FRONTEND=noninteractive apt-get install -y --force-yes bono
RUN sed -e 's/\(echo 0 > \/proc\/sys\/kernel\/yama\/ptrace_scope\)/# \0/g' -i /etc/init.d/bono

RUN apt-get update && DEBIAN_FRONTEND=noninteractive apt-get install -y --force-yes restund
RUN sed -e 's/\(echo 0 > \/proc\/sys\/kernel\/yama\/ptrace_scope\)/# \0/g' -i /etc/init.d/restund

COPY bono.supervisord.conf /etc/supervisor/conf.d/bono.conf
COPY restund.supervisord.conf /etc/supervisor/conf.d/restund.conf
COPY clearwater-group.supervisord.conf /etc/supervisor/conf.d/clearwater-group.conf

RUN cp /etc/clearwater/socket-factory.supervisord.conf /etc/supervisor/conf.d/

EXPOSE 3478 3478/udp 5058 5060 5060/udp 5062
