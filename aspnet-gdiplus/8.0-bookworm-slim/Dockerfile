FROM mcr.microsoft.com/dotnet/aspnet:8.0-bookworm-slim AS compile
RUN apt-get update
RUN apt-get -y install libgif-dev autoconf libtool automake build-essential gettext libglib2.0-dev libcairo2-dev libtiff-dev libexif-dev
RUN apt-get -y install git

RUN git clone https://github.com/mono/libgdiplus.git
WORKDIR /libgdiplus
RUN ./autogen.sh
RUN make 
# RUN make check
RUN make install

FROM mcr.microsoft.com/dotnet/aspnet:8.0-bookworm-slim AS final

# install libgdiplus  (gdiplus.dll)
RUN apt-get update
RUN apt-get install -y libgdiplus lsof
#RUN apt-get install -y libc6-dev

# copy latest build from compile => this also uses alpha channel on gr.DrawImage etc...
WORKDIR /usr/lib
COPY --from=compile /usr/local/lib/libgdiplus.so.0.0.0 .

RUN ln -s /usr/lib/libgdiplus.so.0.0.0 /usr/lib/gdiplus.dll




