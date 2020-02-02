# ImageCaster for Docker [![matrix-members]][matrix] [![discord-members]][discord] [![docker-shield]][docker] [![donate-shield]][elypia-donate]
## Docker Images
There are 3 deployments of ImageCaster, each corresponding to builds of
ImageMagick: Q16-HDRI, Q16, and Q8. By not specifying which you'll use
Q16-HDRI by default which should be good for most use cases, but using
Q16, or Q8 can yield substantially quickly build times if your
requirements allow it.

* [`x.y.z-q16-hdri`, `x.y-q16-hdri`, `x-q16-hdri`, `latest-q16-hdri`, `q16-hdri`, `x.y.z`, `x.y`, `x`, `latest`][q16-hdri]
* [`x.y.z-q16`, `x.y-q16`, `x-q16`, `q16`][q16]
* [`x.y.z-q8`, `x.y-q8`, `x-q8`, `q8`][q8]

## About ImageCaster
ImageCaster is a small CLI application that can be used to manage
exporting images. It's primary use case is for CI/CD where a
repository that has a set of images as a source and programmatically
produces images as a result of a build.

## Open-Source
This project is open-source under the [GNU General Public License]!  
While not legal advice, you can find a [TL;DR] that sums up what
you're allowed and not allowed to do along with any requirements if you
want to use or derive work from this source code!  

**All non-code files including videos, models, audio, bitmaps, vectors, and 
animations such as GIFs, are not under the aforementioned license; all rights
are reserved by Elypia CIC.** 

[q16-hdri]: https://gitlab.com/Elypia/docker-imagecaster/blob/master/q16-hdri/Dockerfile "Dockerfile for Q16-HDRI Builds"
[q16]: https://gitlab.com/Elypia/docker-imagecaster/blob/master/q16/Dockerfile "Dockerfile for Q16 Builds"
[q8]: https://gitlab.com/Elypia/docker-imagecaster/blob/master/q8/Dockerfile "Dockerfile for Q8 Builds"

[matrix]: https://matrix.to/#/+elypia:matrix.org "Matrix Invite"
[discord]: https://discordapp.com/invite/hprGMaM "Discord Invite"
[docker]: https://hub.docker.com/r/elypia/imagecaster "ImageCaster on Docker"
[elypia-donate]: https://elypia.org/donate "Donate to Elypia"
[GNU General Public License]: https://www.gnu.org/licenses/gpl-3.0.en.html "GPL"
[TL;DR]: https://tldrlegal.com/license/gnu-general-public-license-v3-(gpl-3) "TL;DR of GPL"

[matrix-members]: https://img.shields.io/matrix/elypia-general:matrix.org?logo=matrix "Matrix Shield"
[discord-members]: https://discordapp.com/api/guilds/184657525990359041/widget.png "Discord Shield"
[docker-shield]: https://img.shields.io/docker/pulls/elypia/imagecaster?logo=docker "Docker Shield"
[donate-shield]: https://img.shields.io/badge/Elypia-Donate-blueviolet "Donate Shield"
