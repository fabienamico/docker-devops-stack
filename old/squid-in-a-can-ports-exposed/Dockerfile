FROM jpetazzo/squid-in-a-can:latest

# https://github.com/jmtd/squid-in-a-can/commit/693877e2523cb298e7827711f1541ef516b100aa
RUN mv /etc/squid3/squid.conf /etc/squid3/squid.conf.in

ADD deploy_squid.py /tmp/deploy_squid.py

EXPOSE 3128
EXPOSE 3129
