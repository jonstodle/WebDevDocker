FROM microsoft/dotnet:2.1-sdk AS build

WORKDIR /source

COPY WebDevDocker.csproj .

RUN dotnet restore

COPY index.html .

COPY . .

RUN dotnet publish -c Release -o /output


FROM microsoft/dotnet:2.1-aspnetcore-runtime

WORKDIR /app

COPY --from=build /output .

EXPOSE 80

CMD ["dotnet", "WebDevDocker.dll"]