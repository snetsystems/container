FROM buildpack-deps:bullseye-curl

RUN DEBIAN_FRONTEND=noninteractive apt-get update && \
    DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends iputils-ping snmp procps lm-sensors libcap2-bin && \
    rm -rf /var/lib/apt/lists/*

ARG VERSION=1.23.4-snet-2
RUN ARCH= && dpkgArch="$(dpkg --print-architecture)" && \
    case "${dpkgArch##*-}" in \
      amd64) ARCH='amd64';; \
      arm64) ARCH='arm64';; \
      *)     echo "Unsupported architecture: ${dpkgArch}"; exit 1;; \
    esac && \
    wget -nv https://github.com/snetsystems/telegraf/releases/download/v${VERSION}/telegraf_${VERSION}-1_${ARCH}.deb && \
    dpkg -i telegraf_${VERSION}-1_${ARCH}.deb && \
    rm -f telegraf_${VERSION}-1_${ARCH}.deb

EXPOSE 8125/udp 8092/udp 8094

COPY entrypoint.sh /entrypoint.sh
ENTRYPOINT ["/entrypoint.sh"]
CMD ["telegraf"]
