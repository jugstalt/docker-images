FROM mcr.microsoft.com/dotnet/aspnet:5.0-focal

# install libgdiplus
RUN apt-get update
RUN apt-get install -y libgdiplus lsof
RUN apt-get install -y libc6-dev

# install proj4
RUN apt-get install -y proj-bin

# install gdal
#RUN apt-get update
#RUN apt-get -y install gdal-bin

# link gdiplus.dd
RUN ln -s /usr/lib/libgdiplus.so.0.0.0 /usr/lib/gdiplus.dll
# link proj.dll
RUN ln -s /usr/lib/x86_64-linux-gnu/libproj.so.15.3.1 /usr/lib/proj.dll