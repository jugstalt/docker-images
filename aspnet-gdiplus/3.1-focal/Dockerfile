FROM mcr.microsoft.com/dotnet/aspnet:3.1-focal

# install libgdiplus  (gdiplus.dll)
RUN apt-get update
RUN apt-get install -y libgdiplus lsof
#RUN apt-get install -y libc6-dev

# link gdiplus.dd
RUN ln -s /usr/lib/libgdiplus.so.0.0.0 /usr/lib/gdiplus.dll