---
title: Docker-gRPC para desenvolvedores do WCF
description: Criando imagens do Docker para aplicativos ASP.NET Core gRPC
ms.date: 09/02/2019
ms.openlocfilehash: 379750edfa1a9fc282e43ffa83e5695425f31a26
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91152709"
---
# <a name="create-docker-images"></a>Criar imagens do Docker

Esta seção aborda a criação de imagens do Docker para ASP.NET Core aplicativos gRPC, prontos para execução no Docker, kubernetes ou outros ambientes de contêiner. O aplicativo de exemplo usado, com um ASP.NET Core aplicativo Web MVC e um serviço gRPC, está disponível no repositório [dotnet-Architecture/gRPC-for-WCF-Developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) no github.

## <a name="microsoft-base-images-for-aspnet-core-applications"></a>Imagens base da Microsoft para aplicativos ASP.NET Core

A Microsoft fornece uma variedade de imagens básicas para a criação e a execução de aplicativos .NET Core. Para criar uma imagem ASP.NET Core 3,0, você usa duas imagens base:

- Uma imagem do SDK para compilar e publicar o aplicativo.
- Uma imagem de tempo de execução para implantação.

| Imagem | Descrição |
| ----- | ----------- |
| [mcr.microsoft.com/dotnet/core/sdk](https://hub.docker.com/_/microsoft-dotnet-core-sdk/) | Para a criação de aplicativos com o `docker build` . Não deve ser usado na produção. |
| [mcr.microsoft.com/dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) | Contém as dependências de tempo de execução e ASP.NET Core. Para produção. |

Para cada imagem, há quatro variantes com base em diferentes distribuições do Linux, diferenciadas por marcas.

| Marca (s) de imagem | Linux | Observações |
| --------- | ----- | ----- |
| 3,0-Buster, 3,0 | Debian 10 | A imagem padrão se nenhuma variante do sistema operacional for especificada. |
| 3,0 – Alpine Ski | Alpine 3,9 | As imagens da Alpine base são muito menores do que Debian ou Ubuntu. |
| 3,0-disco | Ubuntu 19.04 | |
| 3,0-Bionic | Ubuntu 18.04 | |

A imagem do Alpine base é de cerca de 100 MB, em comparação com 200 MB para as imagens Debian e Ubuntu. Alguns pacotes de software ou bibliotecas podem não estar disponíveis no gerenciamento de pacotes da Alpine Ski. Se você não tiver certeza de qual imagem usar, provavelmente deverá escolher o Debian padrão.

> [!IMPORTANT]
> Certifique-se de usar a mesma variante do Linux para a compilação e o tempo de execução. Os aplicativos criados e publicados em uma variante podem não funcionar em outro.

## <a name="create-a-docker-image"></a>Criar uma imagem do Docker

Uma imagem do Docker é definida por um *Dockerfile*. Esse é um arquivo de texto que contém todos os comandos necessários para compilar o aplicativo e instalar quaisquer dependências necessárias para compilar ou executar o aplicativo. O exemplo a seguir mostra a Dockerfile mais simples para um aplicativo ASP.NET Core 3,0:

```dockerfile
# Application build steps
FROM mcr.microsoft.com/dotnet/core/sdk:3.0 as builder

WORKDIR /src

COPY . .

RUN dotnet restore

RUN dotnet publish -c Release -o /published src/StockData/StockData.csproj

# Runtime image creation
FROM mcr.microsoft.com/dotnet/core/aspnet:3.0

# Uncomment the line below if running with HTTPS
# ENV ASPNETCORE_URLS=https://+:443

WORKDIR /app

COPY --from=builder /published .

ENTRYPOINT [ "dotnet", "StockData.dll" ]
```

O Dockerfile tem duas partes: a primeira usa a `sdk` imagem base para compilar e publicar o aplicativo; a segunda cria uma imagem de tempo de execução a partir da `aspnet` base. Isso ocorre porque a `sdk` imagem está em cerca de 900 MB, em comparação com cerca de 200 MB para a imagem de tempo de execução, e a maior parte de seu conteúdo é desnecessária no tempo de execução.

### <a name="the-build-steps"></a>As etapas de compilação

| Etapa | Descrição |
| ---- | ----------- |
| `FROM ...` | Declara a imagem base e atribui o `builder` alias. |
| `WORKDIR /src` | Cria o `/src` diretório e o define como o diretório de trabalho atual. |
| `COPY . .` | Copia tudo abaixo do diretório atual no host para o diretório atual na imagem. |
| `RUN dotnet restore` | Restaura todos os pacotes externos (ASP.NET Core estrutura 3,0 é pré-instalada com o SDK). |
| `RUN dotnet publish ...` | Compila e publica uma compilação de versão. Observe que o `--runtime` sinalizador não é necessário. |

### <a name="the-runtime-image-steps"></a>As etapas da imagem de tempo de execução

| Etapa | Descrição |
| ---- | ----------- |
| `FROM ...` | Declara uma nova imagem de base. |
| `WORKDIR /app` | Cria o `/app` diretório e o define como o diretório de trabalho atual. |
| `COPY --from=builder ...` | Copia o aplicativo publicado da imagem anterior, usando o `builder` alias da primeira `FROM` linha. |
| `ENTRYPOINT [ ... ]` | Define o comando a ser executado quando o contêiner é iniciado. O `dotnet` comando na imagem de tempo de execução só pode executar arquivos dll. |

### <a name="https-in-docker"></a>HTTPS no Docker

As imagens base da Microsoft para o Docker definem a `ASPNETCORE_URLS` variável de ambiente como `http://+:80` , o que significa que Kestrel é executado sem https nessa porta. Se você estiver usando HTTPS com um certificado personalizado (conforme descrito em [aplicativos gRPC hospedados internamente](self-hosted.md)), você deverá substituir isso. Defina a variável de ambiente na parte de criação da imagem de tempo de execução de seu Dockerfile.

```dockerfile
# Runtime image creation
FROM mcr.microsoft.com/dotnet/core/aspnet:3.0

ENV ASPNETCORE_URLS=https://+:443
```

### <a name="the-dockerignore-file"></a>O arquivo. dockerignore

Assim como `.gitignore` os arquivos que excluem determinados arquivos e diretórios do controle do código-fonte, o `.dockerignore` arquivo pode ser usado para excluir arquivos e diretórios de serem copiados para a imagem durante a compilação. Isso não apenas poupa tempo de cópia, mas também pode evitar alguns erros que surgem de ter o `obj` diretório do seu PC copiado para a imagem. No mínimo, você deve adicionar entradas para `bin` e `obj` ao seu `.dockerignore` arquivo.

```console
bin/
obj/
```

## <a name="build-the-image"></a>Criar a imagem

Para uma solução com um único aplicativo e, portanto, um único Dockerfile, é mais simples colocar o Dockerfile no diretório base. Em outras palavras, coloque-o no mesmo diretório que o `.sln` arquivo. Nesse caso, para criar a imagem, use o seguinte `docker build` comando do diretório que contém o Dockerfile.

```console
docker build --tag stockdata .
```

O `--tag` sinalizador com nome confuso (que pode ser reduzido `-t` ) especifica o nome completo da imagem, incluindo a marca real, se especificado. O `.` no final especifica o contexto no qual a compilação será executada; o diretório de trabalho atual para os `COPY` comandos no Dockerfile.

Se você tiver vários aplicativos em uma única solução, poderá manter o Dockerfile de cada aplicativo em sua própria pasta, ao lado do `.csproj` arquivo. Você ainda deve executar o `docker build` comando do diretório base para garantir que a solução e todos os projetos sejam copiados para a imagem. Você pode especificar um Dockerfile abaixo do diretório atual usando o `--file` sinalizador (ou `-f` ).

```console
docker build --tag stockdata --file src/StockData/Dockerfile .
```

## <a name="run-the-image-in-a-container-on-your-machine"></a>Executar a imagem em um contêiner em seu computador

Para executar a imagem em sua instância local do Docker, use o `docker run` comando.

```console
docker run -ti -p 5000:80 stockdata
```

O `-ti` sinalizador conecta o terminal atual ao terminal do contêiner e é executado no modo interativo. A `-p 5000:80` porta de publicação (links) 80 no contêiner para a porta 5000 na interface de rede do localhost.

## <a name="push-the-image-to-a-registry"></a>Efetue o push da imagem para um Registro

Depois de verificar se a imagem funciona, envie-a por push para um registro do Docker para disponibilizá-la em outros sistemas. As redes internas precisarão provisionar um registro do Docker. Isso pode ser tão simples quanto executar a [própria `registry` imagem do Docker](https://docs.docker.com/registry/deploying/) (o registro do Docker é executado em um contêiner do Docker), mas há várias soluções mais abrangentes disponíveis. Para o compartilhamento externo e o uso de nuvem, há vários registros gerenciados disponíveis, como o [registro de contêiner do Azure](/azure/container-registry/) ou o [Hub do Docker](https://docs.docker.com/docker-hub/repos/).

Para enviar por push para o Hub do Docker, Prefixe o nome da imagem com o nome do usuário ou da organização.

```console
docker tag stockdata myorg/stockdata
docker push myorg/stockdata
```

Para enviar por push para um registro privado, Prefixe o nome da imagem com o nome do host do registro e o nome da organização.

```console
docker tag stockdata internal-registry:5000/myorg/stockdata
docker push internal-registry:5000/myorg/stockdata
```

Depois que a imagem estiver em um registro, você poderá implantá-la em hosts do Docker individuais ou em um mecanismo de orquestração de contêiner, como kubernetes.

>[!div class="step-by-step"]
>[Anterior](self-hosted.md) 
> [Avançar](kubernetes.md)
