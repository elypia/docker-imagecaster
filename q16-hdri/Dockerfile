# Build all files for deployment.
FROM alpine:3.11.3 AS build

# The location to download and extract ImageCaster from.
ARG LOCATION="https://gitlab.com/Elypia/imagecaster/-/jobs/473625857/artifacts/download"

# Environment variables set to ensure consistency in names.
ENV IMAGECASTER_ARCHIVE="imagecaster.zip"

# We'll move builds from here to the next image.
WORKDIR /home/dev/

# Setup and Build ImageCaster
RUN echo "Downloading and extracting ImageCaster locally" && \
    wget --output-document ${IMAGECASTER_ARCHIVE} ${LOCATION} && \
    unzip ${IMAGECASTER_ARCHIVE} && \
    echo "Delete zip archive of ImageCaster before continuing" && \
    rm ${IMAGECASTER_ARCHIVE}

# Start building our final image.
FROM mcr.microsoft.com/dotnet/core/runtime:3.1.2-bionic

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

COPY --from=build /home/dev/imagecaster/* /usr/local/bin/
