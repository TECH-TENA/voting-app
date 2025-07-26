# Dockerfile for worker service (.NET Core)
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build

WORKDIR /src
COPY worker/*.csproj ./ 
RUN dotnet restore

COPY worker/. .
RUN dotnet publish -c Release -o /app/publish

FROM mcr.microsoft.com/dotnet/aspnet:8.0
WORKDIR /app
COPY --from=build /app/publish .

ENTRYPOINT ["dotnet", "Worker.dll"]
