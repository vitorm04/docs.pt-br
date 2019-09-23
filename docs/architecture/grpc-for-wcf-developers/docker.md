---
title: Docker-gRPC para desenvolvedores do WCF
description: Criando imagens do Docker para aplicativos ASP.NET Core gRPC
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 6e9d4956077286d133d09ab8e681ba5e82ab1aa4
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184473"
---
# <a name="docker"></a>Docker

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Esta seção abordará a criação de imagens do Docker para aplicativos ASP.NET Core gRPC, pronta para execução no Docker, kubernetes ou outros ambientes de contêiner. O aplicativo de exemplo usado, com um ASP.NET Core aplicativo Web MVC e um serviço gRPC, está disponível no repositório [RendleLabs/gRPC-for-WCF-Developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) no github.

## <a name="microsoft-base-images-for-aspnet-core-applications"></a>Imagens base da Microsoft para aplicativos ASP.NET Core

A Microsoft fornece uma variedade de imagens básicas para a criação e a execução de aplicativos .NET Core. Para criar uma imagem ASP.NET Core 3,0, são usadas duas imagens base: uma imagem do SDK para criar e publicar o aplicativo e uma imagem de tempo de execução para implantação.

| Image | Descrição |
| ----- | ----------- |
| [mcr.microsoft.com/dotnet/core/sdk](https://hub.docker.com/_/microsoft-dotnet-core-sdk/) | Para a criação de `docker build`aplicativos com o. Não deve ser usado na produção. |
| [mcr.microsoft.com/dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) | Contém as dependências de tempo de execução e ASP.NET Core. Para produção. |

Para cada imagem, há quatro variantes com base em diferentes distribuições do Linux, diferenciadas por marcas.

| Marca (s) de imagem | Linux | Observações |
| --------- | ----- | ----- |
| 3,0-Buster, 3,0 | Debian 10 | A imagem padrão se nenhuma variante do sistema operacional for especificada. |
| 3,0 – Alpine Ski | Alpine 3,9 | As imagens da Alpine base são muito menores do que Debian ou Ubuntu. |
| 3,0-disco | Ubuntu 19, 4 | |
| 3,0-Bionic | Ubuntu 18.04 | |

A imagem da Alpine base é cerca de 100 MB, em comparação com 200 MB para as imagens Debian e Ubuntu, mas alguns pacotes de software ou bibliotecas podem não estar disponíveis no gerenciamento de pacotes da Alpine Ski. Se você não tiver certeza de qual imagem usar, é melhor usar o Debian padrão, a menos que tenha uma necessidade atraente de utilizar um distribuição diferente.

> [!IMPORTANT]
> Certifique-se de usar a mesma variante do Linux para a compilação e o tempo de execução. Os aplicativos criados e publicados em uma variante podem não funcionar em outro.

## <a name="create-a-docker-image"></a>Criar uma imagem do Docker

Uma imagem do Docker é definida por um *Dockerfile*, um arquivo de texto que contém todos os comandos necessários para criar o aplicativo e instalar as dependências necessárias para compilar ou executar o aplicativo. O exemplo a seguir mostra a Dockerfile mais simples para um aplicativo ASP.NET Core 3,0:

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

O Dockerfile tem duas partes: a primeira usa a `sdk` imagem base para compilar e publicar o aplicativo; a segunda cria uma imagem de tempo de `aspnet` execução a partir da base. Isso ocorre porque a `sdk` imagem é cerca de 900 MB em comparação com cerca de 200 MB para a imagem de tempo de execução, e a maior parte do seu conteúdo é desnecessária no tempo de execução.

### <a name="the-build-steps"></a>As etapas de compilação

| Etapa | Descrição |
| ---- | ----------- |
| `FROM ...` | Declara a imagem base e atribui o alias (consulte `builder` a próxima seção para obter uma explicação). |
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

As imagens base da Microsoft para o Docker `ASPNETCORE_URLS` definem a `http://+:80`variável de ambiente como, o que significa que o Kestrel será executado sem https nessa porta. Se você estiver usando HTTPS com um certificado personalizado (conforme descrito na [seção anterior](self-hosted.md)), você deve substituir isso definindo a variável de ambiente **na parte de criação da imagem de tempo de execução** de seu Dockerfile.

```dockerfile
# Runtime image creation
FROM mcr.microsoft.com/dotnet/core/aspnet:3.0

ENV ASPNETCORE_URLS=https://+:443
```

### <a name="the-dockerignore-file"></a>O arquivo. dockerignore

Assim como `.gitignore` os arquivos que excluem determinados arquivos e diretórios do controle do `.dockerignore` código-fonte, o arquivo pode ser usado para excluir arquivos e diretórios de serem copiados para a imagem durante a compilação. Isso não apenas poupa tempo de cópia, mas também pode evitar alguns erros confusos que surgem de ter ( `obj` particularmente) o diretório do seu PC copiado para a imagem. Você deve adicionar pelo menos entradas para `bin` e `obj` ao seu `.dockerignore` arquivo.

```console
bin/
obj/
```

## <a name="build-the-image"></a>Criar a imagem

Para uma solução com um único aplicativo e, portanto, um único Dockerfile, é mais simples colocar o Dockerfile no diretório base; ou seja, o mesmo diretório que o `.sln` arquivo. Nesse caso, para criar a imagem, use o seguinte `docker build` comando do diretório que contém o Dockerfile.

```console
docker build --tag stockdata .
```

O `--tag` sinalizador com `-t`nome confuso (que pode ser reduzido) especifica o nome completo da imagem, *incluindo* a marca real, se especificado. O `.` no final especifica o *contexto* no qual a compilação será executada; o diretório de trabalho atual para os `COPY` comandos no Dockerfile.

Se você tiver vários aplicativos em uma única solução, poderá manter o Dockerfile de cada aplicativo em sua própria pasta, ao lado do `.csproj` arquivo, mas você ainda deverá executar o `docker build` comando do diretório base para garantir que a solução e todos os projetos são copiados para a imagem. Você pode especificar um Dockerfile abaixo do diretório atual usando o `--file` sinalizador ( `-f`ou).

```console
docker build --tag stockdata --file src/StockData/Dockerfile .
```

## <a name="run-the-image-in-a-container-on-your-machine"></a>Executar a imagem em um contêiner em seu computador

Para executar a imagem em sua instância local do Docker, use `docker run` o comando.

```console
docker run -ti -p 5000:80 stockdata
```

O `-ti` sinalizador conecta o terminal atual ao terminal do contêiner e é executado no modo interativo. A `-p 5000:80` porta de publicação (links) 80 no contêiner para a porta 80 na interface de rede do localhost.

## <a name="push-the-image-to-a-registry"></a>Enviar a imagem por push a um registro

Depois de verificar que a imagem funciona, você precisa enviá-la por push para um registro do Docker para disponibilizá-la em outros sistemas. As redes internas precisarão provisionar um registro do Docker. Isso pode ser tão simples quanto executar a [própria `registry` imagem do Docker](https://docs.docker.com/registry/deploying/) (certo, o registro do Docker é executado em um contêiner do Docker), mas há várias soluções mais abrangentes disponíveis. Para o compartilhamento externo e o uso de nuvem, há vários registros gerenciados disponíveis, como o [registro de contêiner do Azure](https://docs.microsoft.com/azure/container-registry/) ou o [Hub do Docker](https://docs.docker.com/docker-hub/repos/).

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
>[Próximo](kubernetes.md)
