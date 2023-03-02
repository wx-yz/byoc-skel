FROM mcr.microsoft.com/dotnet/sdk:7.0-jammy AS build

WORKDIR /source
COPY *.csproj .
RUN dotnet restore -r linux-x64 

COPY . .
RUN dotnet publish -c Release -o todoapi 

FROM mcr.microsoft.com/dotnet/aspnet:7.0-jammy-amd64
WORKDIR /todoapi
COPY --from=build /source/todoapi .

# ARG USERNAME=appuser
# ARG USER_UID=10001

# RUN useradd -u $USER_UID $USERNAME

USER 10001

ENTRYPOINT ["dotnet", "TodoApi.dll"]

