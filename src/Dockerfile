FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
COPY . ./src
WORKDIR /src
RUN dotnet restore
RUN dotnet publish -c Release -o /published
FROM mcr.microsoft.com/dotnet/aspnet:8.0
RUN adduser --disabled-password --no-create-home  --shell /bin/bash dot
USER dot
WORKDIR /dot
COPY --from=build /published .
EXPOSE 5000
CMD ["dotnet","dotnet-demoapp.dll"]
