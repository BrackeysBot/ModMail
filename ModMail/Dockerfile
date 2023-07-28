FROM mcr.microsoft.com/dotnet/runtime:7.0 AS base
WORKDIR /app

FROM mcr.microsoft.com/dotnet/sdk:7.0 AS build
WORKDIR /src
COPY ["ModMail/ModMail.csproj", "ModMail/"]
RUN dotnet restore "ModMail/ModMail.csproj"
COPY . .
WORKDIR "/src/ModMail"
RUN dotnet build "ModMail.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "ModMail.csproj" -c Release -o /app/publish /p:UseAppHost=false

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "ModMail.dll"]
