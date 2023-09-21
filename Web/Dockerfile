#See https://aka.ms/customizecontainer to learn how to customize your debug container and how Visual Studio uses this Dockerfile to build your images for faster debugging.

FROM mcr.microsoft.com/dotnet/core/sdk:3.0 AS build-env
WORKDIR /src
#EXPOSE 80
#EXPOSE 443

COPY . .
WORKDIR /src/Web
RUN dotnet restore
RUN dotnet publish -c Release -o out

FROM mcr.microsoft.com/dotnet/core/aspnet:3.0
WORKDIR /app
COPY --from=build-env /src/Web/out ./

ENTRYPOINT ["dotnet", "Web.dll"]