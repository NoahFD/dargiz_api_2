FROM mcr.microsoft.com/dotnet/sdk:5.0 AS build-env
WORKDIR /app

# Copy csproj and restore as distinct layers
COPY ./WebApplication_4/*.csproj ./WebApplication_4/
RUN dotnet restore ./WebApplication_4/WebApplication_4.csproj

# Copy everything else and build
COPY . ./
RUN dotnet publish -c Release -o out ./WebApplication_4/WebApplication_4.csproj

# Build runtime image
FROM mcr.microsoft.com/dotnet/aspnet:5.0
WORKDIR /app
COPY --from=build-env /app/out .
ENTRYPOINT ["dotnet", "WebApplication_4.dll"]
