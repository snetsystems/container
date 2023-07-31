FROM debian:bullseye-slim

ARG VERSION=1.4.5
ARG COMMIT=3c27290
ARG ARCH=amd64

# I already downloaded the package here because the download speed has been extremely slow at my office.
# You can comment and then can download via curl of RUN sentence on your container running.
COPY cloudhub_${VERSION}.${COMMIT}_${ARCH}.deb /cloudhub_${VERSION}.${COMMIT}_${ARCH}.deb

RUN apt-get update && apt-get install -y curl --no-install-recommends && \
    rm -rf /var/lib/apt/lists/* && \
	#curl -SLO "https://github.com/snetsystems/cloudhub/releases/download/${VERSION}/cloudhub_${VERSION}.${COMMIT}_amd64.deb" && \
    dpkg -i cloudhub_${VERSION}.${COMMIT}_${ARCH}.deb && \
    rm -f cloudhub_${VERSION}.${COMMIT}_${ARCH}.deb* && \
    apt-get purge -y --auto-remove $buildDeps

COPY LICENSE /usr/share/cloudhub/LICENSE
COPY agpl-3.0.md /usr/share/cloudhub/agpl-3.0.md

EXPOSE 8888

VOLUME /var/lib/cloudhub

COPY entrypoint.sh /entrypoint.sh
ENTRYPOINT ["/entrypoint.sh"]
CMD ["cloudhub"]
