FROM mcr.microsoft.com/dotnet/core/aspnet:3.1-buster-slim AS base
WORKDIR /app
EXPOSE 80

FROM mcr.microsoft.com/dotnet/core/sdk:3.1-buster AS build
WORKDIR /src
COPY ["MyWeb/MyWeb.csproj", "MyWeb/"]
RUN dotnet restore "MyWeb/MyWeb.csproj"
COPY . .
WORKDIR "/src/MyWeb"
RUN dotnet build "MyWeb.csproj" -c Release -o /app

FROM build AS publish
RUN dotnet publish "MyWeb.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "MyWeb.dll"]