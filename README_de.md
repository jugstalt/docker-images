# Docker Images

In diesem Repository veröffentliche ich einige meiner Docker Basis Images (zB für AspNet Core)

## Motivation

Die Standard Docker Repositories für AspNet Cor sind nicht immer ausreichend. Oft sind zusätzliche Linux Bibliotheken notwendig damit alles wie auf der Windows Entwicklungsumgebung funktioniert.

Ein Beispiel die die GDI+ Bibliothek (libgdiplus). Diese muss in das Image beim Erstellen des Images zusätzlich installiert werden.
Dabei installieren einige Images nicht die aktuellste Version von *libgdiplus*.
Ein Problem tritt beispielsweise bei `DrawImage(...)` auf, wenn das Quellbild Alpha Kanal Werte aufweißt. Die Transparenz
wird bei älteren Version der Bibliothek nicht berücksichtigt! 

Lösung:
Ein mögliche Lösing ist es, ein auf Ubuntu basierendes Image zu verwenden (mcr.microsoft.com/dotnet/aspnet:3.1-focal). Hier scheint eine aktuelle Version von *libgidplus* geladen zu werden.

Bei Debian basieren Images (mcr.microsoft.com/dotnet/aspnet:3.1-buster-slim) wird eine ältere Version der Bibliothek installiert, bei der dieses Problem noch besteht. Hier muss beim Erstellen des Images die aktuelle Version von GitHub geklont in compiliert werden. Mit diesem Image wird auch der Alpha Kanal beim `DrawImage(...)` richtig interpretiert.

Hinweis:
Da sich ein Schwerpunkt meiner Arbeit um geographische Informationssystem dreht, wird ein den Images auch oft Proj4 oder GDAL installiert. Diese Installationen können weggelassen werden, wenn nur eine aktuelle *libgdiplus* Version verwendet werden sollte. 

