#
# THIS FILE IS AUTOGENERATED; SEE "contrib/builder/deb/ppc64le/generate.sh"!
#

FROM ppc64le/ubuntu:trusty

RUN apt-get update && apt-get install -y apparmor bash-completion btrfs-tools build-essential curl ca-certificates debhelper dh-apparmor dh-systemd git libapparmor-dev libdevmapper-dev libltdl-dev libsqlite3-dev pkg-config golang-1.6 libsystemd-journal-dev --no-install-recommends && rm -rf /var/lib/apt/lists/*

ENV GO_VERSION 1.7.1
ENV GO_DOWNLOAD_URL https://golang.org/dl/go${GO_VERSION}.src.tar.gz
ENV GOROOT_BOOTSTRAP /usr/lib/go-1.6

RUN curl -fsSL "$GO_DOWNLOAD_URL" -o golang.tar.gz \
	&& tar -C /usr/local -xzf golang.tar.gz \
	&& rm golang.tar.gz \
	&& cd /usr/local/go/src && ./make.bash 2>&1 \
	&& apt-get purge -y golang-1.6 && apt-get autoremove -y

ENV PATH $PATH:/usr/local/go/bin

ENV AUTO_GOPATH 1

ENV DOCKER_BUILDTAGS apparmor pkcs11 selinux
ENV RUNC_BUILDTAGS apparmor selinux
