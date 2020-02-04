# Build all files for deployment.
FROM mcr.microsoft.com/dotnet/core/sdk:3.1.101-alpine3.10 AS build

# The tag in the ImageCaster repository to checkout.
ARG TAG="0.2.1"

# We'll move builds from here to the next image.
WORKDIR /home/dev/

# Setup and Build ImageCaster
RUN echo "Installing git, cloning ImageCaster, and checking out ${TAG}" && \
    apk add git && \
    git clone https://gitlab.com/Elypia/imagecaster.git . && \
    git checkout -b build ${TAG} && \
    cd src/ImageCaster/ && \
    echo "Build release version of ImageCaster for Docker environment" && \
    dotnet publish --configuration Release-Q16-HDRI --runtime linux-x64 --self-contained false

# Start building our final image.
FROM mcr.microsoft.com/dotnet/core/runtime:3.1.1-bionic

LABEL maintainer="seth@elypia.org"

# Add imagecaster user, and install a generic open font.
RUN echo "Adding imagecaster system group and user" && \
    groupadd --system --gid 1000 imagecaster && \
    useradd --system --create-home --gid imagecaster --uid 1000 --shell /bin/bash imagecaster && \
    echo "Install generic open font and clear apt cache" && \
    apt-get update && \
    apt-get install -y ttf-dejavu && \
    rm --recursive --force /var/lib/apt/lists/*

USER imagecaster

WORKDIR /home/imagecaster

COPY --from=build /home/dev/src/ImageCaster/bin/Release-Q*/netcoreapp3.1/linux-x64/publish/* /usr/local/bin/
