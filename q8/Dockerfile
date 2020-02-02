# Build all files for deployment.
FROM mcr.microsoft.com/dotnet/core/sdk:3.1.101-alpine3.10 AS build

# The tag in the ImageCaster repository to checkout.
ARG TAG="0.1.9"

# We'll move builds from here to the next image.
WORKDIR /home/dev/

# Setup and Build ImageCaster
RUN apk add git && \
    git clone https://gitlab.com/Elypia/imagecaster.git . && \
    git checkout -b build ${TAG} && \
    cd src/ImageCaster/ && \
    dotnet publish -c Release-Q8 -r linux-x64 --self-contained false

# Start building our final image.
FROM mcr.microsoft.com/dotnet/core/runtime:3.1.1-bionic

LABEL maintainer="seth@elypia.org"

# Add imagecaster user, and install a generic open font.
RUN useradd -ms /bin/bash imagecaster && \
    apt-get update && \
    apt-get install -y ttf-dejavu && \
    rm -rf /var/lib/apt/lists/*

USER imagecaster

WORKDIR /home/imagecaster

COPY --from=build /home/dev/src/ImageCaster/bin/Release-Q*/netcoreapp3.1/linux-x64/publish/* /usr/local/bin/
