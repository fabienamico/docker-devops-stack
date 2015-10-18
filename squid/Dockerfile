FROM debian:jessie
RUN apt-get -q update && apt-get -qy install python squid3
RUN sed -i "s/^#acl localnet/acl localnet/" /etc/squid3/squid.conf
RUN sed -i "s/^#http_access allow localnet/http_access allow localnet/" /etc/squid3/squid.conf
# https://github.com/jmtd/squid-in-a-can/commit/693877e2523cb298e7827711f1541ef516b100aa
# RUN mv /etc/squid3/squid.conf /etc/squid3/squid.conf.in
RUN mkdir -p /var/cache/squid3
RUN chown -R proxy:proxy /var/cache/squid3
ADD deploy_squid.py /tmp/deploy_squid.py
RUN ["chmod", "+x", "/tmp/deploy_squid.py"]
CMD /tmp/deploy_squid.py
