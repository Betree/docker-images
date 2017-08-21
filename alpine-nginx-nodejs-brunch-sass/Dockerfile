# ---- Build stage ----
FROM smebberson/alpine-nginx-nodejs:4.4.0 as builder
MAINTAINER Benjamin Piouffle <benjamin.piouffle@gmail.com>

ENV LIBSASS_VERSION=3.4 SASSC_VERSION=3.4
WORKDIR /build

# Install build tools
RUN apk --update add git build-base libstdc++ make g++ python curl
# Update certificates to deal with git SSL error (generate a warning - you can ignore it)
RUN mkdir -p /etc/ssl/certs  && update-ca-certificates
# Clone libsass + sassc and run make
RUN git clone https://github.com/sass/libsass && cd libsass && git checkout $LIBSASS_VERSION && \
    git clone https://github.com/sass/sassc && cd sassc && git checkout $SASSC_VERSION && \
    make

# ---- Actual image, without build tools ----

FROM smebberson/alpine-nginx-nodejs:4.4.0
MAINTAINER Benjamin Piouffle <benjamin.piouffle@gmail.com>

# Copy SASS binary
COPY --from=builder /build/libsass/sassc/bin/sassc /usr/bin/sassc

# Install brunch + sass node packages
RUN npm install -g brunch node-sass