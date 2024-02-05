# Build Stage
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /app
COPY ./DockerTest.Api.csproj ./
RUN dotnet restore
COPY . .
RUN dotnet publish ./DockerTest.Api.csproj -c release -o build
# Runtime Stage
FROM mcr.microsoft.com/dotnet/aspnet:8.0 AS base
WORKDIR /app
COPY --from=build /app ./
ENTRYPOINT [ "dotnet", ".build/DockerTest.Api.dll" ]