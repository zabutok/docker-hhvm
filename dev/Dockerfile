# brunoric/docker-hhvm:dev
FROM brunoric/hhvm:base
MAINTAINER brunoric <brunoric@gmail.com>

ENV HHVM_VERSION master
ENV CORE_NUMBER 2

# Building HHVM
WORKDIR /hhvm-repo
RUN git submodule update --init --recursive
RUN cmake -DMYSQL_UNIX_SOCK_ADDR=/var/run/mysqld/mysqld.sock .
RUN make -j ${CORE_NUMBER}
RUN make install

# Removing the pulled repository
WORKDIR /
RUN rm -rf hhvm-repo

# Exposing HHVM-FastCGI port
EXPOSE 9000

# Default command
CMD ["/scripts/start.sh"]
