[German - Deutsch](README_de.md)

# Docker Images

In this repository I publish some of my Docker Base images (e.g. for AspNet Core)

## Motivation

The standard Docker repositories for AspNet Cor are not always sufficient. Often additional Linux libraries are necessary for everything to work as on the Windows development environment.

An example of the GDI+ library (libgdiplus). This must be additionally installed in the image when the image is created.
But some images do not install the latest version of *libgdiplus*.

For example, a problem occurs with `DrawImage(...)` if the source image has alpha channel values. Transparency
is not included in older version of the library!

### Solution:
One possible solution is to use an image based on Ubuntu (mcr.microsoft.com/dotnet/aspnet:3.1-focal). A current version of *libgidplus* appears to be loaded here.

Debian Based Images (mcr.microsoft.com/dotnet/aspnet:3.1-buster-slim) installs an older version of the library where this problem still exists. In this case, when creating the image, the current version of the library must be cloned from GitHub and then compiled with the image. With this image the Alpha channel is also used in the `DrawImage(...)` interpreted correctly.

### Note:
Since one focus of my work is geographical information systems, a proj4 or GDAL is often installed for the images. These installations can be omitted if only a current *libgdiplus* version should be used. 