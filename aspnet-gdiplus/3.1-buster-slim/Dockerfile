FROM mcr.microsoft.com/dotnet/aspnet:3.1-buster-slim

# libgdiplus (gdiplus.dll)
RUN apt-get update
RUN apt-get -y install libgif-dev autoconf libtool automake build-essential gettext libglib2.0-dev libcairo2-dev libtiff-dev libexif-dev
RUN apt-get -y install git

RUN git clone https://github.com/mono/libgdiplus.git
WORKDIR /libgdiplus
RUN ./autogen.sh
RUN make 
RUN make check
RUN make install

RUN ln -s /usr/local/lib/libgdiplus.so /usr/lib/libgdiplus.so
RUN ln -s /usr/local/lib/libgdiplus.so.0.0.0 /usr/lib/gdiplus.dll