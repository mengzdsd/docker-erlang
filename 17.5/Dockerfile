# This is a Dockerfile to build a erlang runtime image.
FROM dasudian/docker-buildpack:ubuntu-14.04
MAINTAINER Mengz You <mengz.you@outlook.com>

# Environments
ENV ERLANG_VERSION 17.5
ENV ERLANG_SRC_URL http://www.erlang.org/download/otp_src_17.5.tar.gz
ENV ERLANG_SRC_FILE otp_src_17.5.tar.gz
ENV ERLANG_SRC_DIR otp_src_17.5/

# Update and install build tool packages
RUN apt-get update \
  && apt-get install -y --no-install-recommends libncurses5-dev openssl libssl-dev fop xsltproc unixodbc-dev systemtap-sdt-dev \
  && apt-get clean \
  && rm -rf /var/lib/apt/lists/*

# Add erlang source codes
ADD $ERLANG_SRC_URL /

RUN tar -C /usr/src -xzf "$ERLANG_SRC_FILE" \
  && cd "/usr/src/$ERLANG_SRC_DIR" \
  && ./configure --enable-smp-support --enable-kernel-poll --enable-sctp --enable-native-libs --enable-vm-probes --enable-shared-zlib --enable-m64-build --with-dynamic-trace=dtrace \
  && make \
  && make install \
  && cd / && rm -rf "/$ERLANG_SRC_FILE" "/usr/src/$ERLANG_SRC_DIR"
