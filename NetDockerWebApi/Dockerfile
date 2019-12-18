FROM mcr.microsoft.com/dotnet/core/sdk:2.2 AS build-env
WORKDIR /app
COPY *.csproj ./
RUN dotnet restore
COPY . ./
RUN dotnet publish -c Release -o output
# Runtime image
FROM mcr.microsoft.com/dotnet/core/aspnet:2.1
WORKDIR /app
COPY --from=build-env /app/output .
ENTRYPOINT ["dotnet", "NetDockerWebApi.dll"]
























##FROM microsoft/dotnet:2.1-aspnetcore-runtime AS base
##WORKDIR /app
##EXPOSE 80
##EXPOSE 443
##
##FROM microsoft/dotnet:2.1-sdk AS build
##WORKDIR /src
##COPY ["NetDockerWebApi/NetDockerWebApi.csproj", "NetDockerWebApi/"]
##RUN dotnet restore "NetDockerWebApi/NetDockerWebApi.csproj"
##COPY . .
##WORKDIR "/src/NetDockerWebApi"
##RUN dotnet build "NetDockerWebApi.csproj" -c Release -o /app
##
##FROM build AS publish
##RUN dotnet publish "NetDockerWebApi.csproj" -c Release -o /app
##
##FROM base AS final
##WORKDIR /app
##COPY --from=publish /app .
##ENTRYPOINT ["dotnet", "NetDockerWebApi.dll"]