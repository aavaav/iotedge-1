FROM debian:9-slim

# package installation needs to exec as root
RUN apt-get update && apt-get install -y \
  libssl1.0.2 \
  ca-certificates \
  && rm -rf /var/lib/apt/lists/*

# run everything else as system user
RUN useradd -ms /bin/bash edgeletuser
USER edgeletuser

WORKDIR /app
ADD ./docker/linux/amd64/libiothsm.so* /app/
ADD ./docker/linux/amd64/iotedged /app

ENV LD_LIBRARY_PATH /app

CMD ["/app/iotedged"]
