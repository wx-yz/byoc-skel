FROM mcr.microsoft.com/dotnet/sdk:7.0-jammy AS build

ARG USERNAME=user123
ARG USER_UID=1000
ARG USER_GID=$USER_UID

RUN groupadd --gid $USER_GID $USERNAME \
    && useradd --uid $USER_UID --gid $USER_GID -m $USERNAME

USER $USERNAME

WORKDIR /source
COPY *.csproj .
RUN dotnet restore -r linux-x64 

COPY . .
RUN dotnet publish -c Release -o todoapi 

FROM mcr.microsoft.com/dotnet/aspnet:7.0-jammy-amd64
WORKDIR /todoapi
COPY --from=build /source/todoapi .
ENTRYPOINT ["dotnet", "TodoApi.dll"]

