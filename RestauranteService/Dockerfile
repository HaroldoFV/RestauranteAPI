FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build
WORKDIR /app
COPY *.csproj ./
RUN dotnet restore
COPY . ./
RUN dotnet publish -c Release -o out

FROM mcr.microsoft.com/dotnet/aspnet:6.0
WORKDIR /app
COPY --from=build /app/out .
ENTRYPOINT ["dotnet", "RestauranteService.dll"] 


#utilizando multi-stage build em nossas imagens a fim de reduzir o tamanho do entregável final.
#docker build -t restauranteservice:1.1 . 