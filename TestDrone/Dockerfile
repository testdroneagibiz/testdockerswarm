FROM microsoft/dotnet:2.1-sdk-alpine AS build
WORKDIR /app

COPY *.csproj ./
RUN dotnet restore

COPY . ./
RUN dotnet publish -c Release -o out

FROM microsoft/dotnet:2.1.5-aspnetcore-runtime-alpine3.7
WORKDIR /app
COPY --from=build /app/out .
ENTRYPOINT ["dotnet", "TestDrone.dll"]

