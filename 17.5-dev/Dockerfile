# This is a Dockerfile to build a erlang runtime image.
FROM dasudian/docker-erlang:17.5
MAINTAINER Mengz You <mengz.you@outlook.com>

# Working dir and volume
RUN mkdir /src/
VOLUME /src/
WORKDIR /src/

# Start erlang console
CMD ["erl"]
