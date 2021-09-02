# Downloading Rocky Linux

This guide will cover the downloading and verification of installation media
from the Rocky Linux website.

You can download the official installation media sets from the Rocky Linux
website, at [rockylinux.org/download](https://rockylinux.org/download).

## Definitions

On the download page, there are two main options you will need to choose from
in order to download the correct image for your system. These are the
_Image Type_ and the _Architecture_.

### Image Types

Rocky Linux ships boot media images in three forms, of which you will need to
choose a single type to use.

1. The _boot_ media contains just enough for the system to boot, but not enough
   packages to install from -- so it assumes you are able to install from some
   other remote network media (locally or externally, for example using a
   mirror).

2. The _minimal_ media contains enough for the system to boot, as well as
   install from, but includes only the _Minimal Install_ package set, which is
   enough to get a new Rocky Linux host set up, but will likely require a
   remote network install media in order to expand upon the installed package
   set.

3. The _DVD_ media contains every package publicly available in the core Rocky
   Linux repositories (_BaseOS_, _AppStream_, _PowerTools_) at the time the
   image was created, and can be used to install any available installation
   targets.


### Architecture

Most modern systems use a 64-bit architecture, commonly abbreviated as `x64` or
`x86_64`. Older systems may still use 32-bit, abbreviated as `x86`.

You will need to determine whether your processor (CPU) is a _32-bit_ or
_64-bit_ model, and download the appropriate installation media.

- In the event that your processor is 64-bit, you will need the `x86_64` image.
- In the event that your processor is 32-bit, you will need the `x84` image.


## Verifying your installation media

Once you have downloaded the correct media for your system, you should verify
its integrity by getting the _Checksum_ file from the Downloads page and
checking your media's hash against it.

This ensures that the media you have downloaded is 100% official and has not
been tampered with, by ensuring that the hash provided by the media's offical
distributor matches that of the downloaded media, therefore verifying that no
third party has modified it. It also ensures that the image downloaded is not
corrupt, as if it is corrupt its hash will not match.

!!! Note
    If you download media from the official Rocky Linux website and its
    checksum does _not_ match, you should inform the RESF by email at
    [security@rockylinux.org](mailto:security@rockylinux.org).

You can use the `sha256sum` utility to do this.

```shell
$ sha256sum \
    -C /path/to/CHECKSUM \ # the checksum file you downloaded from the website
    --ignore-missing \
    /path/to/Rocky-8.4-<arch>-<variant>.iso # the path to the install media
```

If successful, you should receive this as output:

```
Rocky-8.4-<arch>-<variant>.iso: OK
```
