---
title: Docker - gRPC para Desenvolvedores WCF
description: Criando imagens Docker para ASP.NET aplicativos core gRPC
ms.date: 09/02/2019
ms.openlocfilehash: e67c43f9486fbfe9a5d3e84e3b74770eb621f604
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148108"
---
# <a name="create-docker-images"></a>Criar imagens do Docker

Esta seção abrange a criação de imagens Docker para ASP.NET aplicativos core gRPC, prontos para serem executados em Docker, Kubernetes ou outros ambientes de contêineres. O aplicativo de exemplo utilizado, com um aplicativo web Core MVC ASP.NET e um serviço gRPC, está disponível no repositório [dotnet-architecture/grpc-for-wcf-developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) no GitHub.

## <a name="microsoft-base-images-for-aspnet-core-applications"></a>Imagens básicas da Microsoft para aplicativos ASP.NET Core

A Microsoft fornece uma série de imagens básicas para construir e executar aplicativos .NET Core. Para criar uma imagem ASP.NET Core 3.0, você usa duas imagens base:

- Uma imagem SDK para construir e publicar o aplicativo.
- Uma imagem em tempo de execução para implantação.

| Imagem | Descrição |
| ----- | ----------- |
| [mcr.microsoft.com/dotnet/core/sdk](https://hub.docker.com/_/microsoft-dotnet-core-sdk/) | Para construir aplicações `docker build`com . Não deve ser usado na produção. |
| [mcr.microsoft.com/dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) | Contém o tempo de execução e ASP.NET dependências do Core. Para produção. |

Para cada imagem, há quatro variantes baseadas em diferentes distribuições Linux, distinguidas por tags.

| Tag(s) de imagem | Linux | Observações |
| --------- | ----- | ----- |
| 3.0-buster, 3.0 | Debian 10 | A imagem padrão se nenhuma variante do Sistema Operacional for especificada. |
| 3.0-alpino | Alpino 3.9 | As imagens base alpinas são muito menores do que as do Debian ou do Ubuntu. |
| 3.0-disco | Ubuntu 19.04 | |
| 3.0-biônico | Ubuntu 18.04 | |

A imagem base alpina é de cerca de 100 MB, em comparação com 200 MB para as imagens Debian e Ubuntu. Alguns pacotes de software ou bibliotecas podem não estar disponíveis no gerenciamento de pacotes da Alpine. Se você não tem certeza de qual imagem usar, provavelmente deve escolher o Debian padrão.

> [!IMPORTANT]
> Certifique-se de usar a mesma variante do Linux para a compilação e o tempo de execução. Aplicativos construídos e publicados em uma variante podem não funcionar em outra.

## <a name="create-a-docker-image"></a>Criar uma imagem do Docker

Uma imagem do Docker é definida por um *arquivo Docker*. Este é um arquivo de texto que contém todos os comandos necessários para construir o aplicativo e instalar quaisquer dependências necessárias para a construção ou execução do aplicativo. O exemplo a seguir mostra o arquivo Docker mais simples para um aplicativo ASP.NET Core 3.0:

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

O Arquivo Docker tem duas partes: a primeira usa a `sdk` imagem base para construir e publicar o aplicativo; o segundo cria uma imagem `aspnet` de tempo de execução a partir da base. Isso porque `sdk` a imagem é de cerca de 900 MB, em comparação com cerca de 200 MB para a imagem em tempo de execução, e a maioria de seu conteúdo é desnecessária em tempo de execução.

### <a name="the-build-steps"></a>As etapas de construção

| Etapa | Descrição |
| ---- | ----------- |
| `FROM ...` | Declara a imagem base e `builder` atribui o alias. |
| `WORKDIR /src` | Cria `/src` o diretório e define-o como o diretório de trabalho atual. |
| `COPY . .` | Copia tudo abaixo do diretório atual sobre o host para o diretório atual na imagem. |
| `RUN dotnet restore` | Restaura quaisquer pacotes externos (ASP.NET framework Core 3.0 está pré-instalado com o SDK). |
| `RUN dotnet publish ...` | Constrói e publica uma compilação de lançamento. Note que `--runtime` a bandeira não é necessária. |

### <a name="the-runtime-image-steps"></a>As etapas de imagem em tempo de execução

| Etapa | Descrição |
| ---- | ----------- |
| `FROM ...` | Declara uma nova imagem base. |
| `WORKDIR /app` | Cria `/app` o diretório e define-o como o diretório de trabalho atual. |
| `COPY --from=builder ...` | Copia o aplicativo publicado da imagem `builder` anterior, usando `FROM` o alias da primeira linha. |
| `ENTRYPOINT [ ... ]` | Define o comando para ser executado quando o contêiner começar. O `dotnet` comando na imagem de tempo de execução só pode executar arquivos DLL. |

### <a name="https-in-docker"></a>HTTPS em Docker

As imagens base `ASPNETCORE_URLS` da Microsoft `http://+:80`para docker definem a variável ambiente para , o que significa que o Kestrel é executado sem HTTPS nessa porta. Se você estiver usando HTTPS com um certificado personalizado (como descrito em [aplicativos gRPC auto-hospedados),](self-hosted.md)você deve substituí-lo. Defina a variável de ambiente na parte de criação de imagem em tempo de execução do seu Arquivo Docker.

```dockerfile
# Runtime image creation
FROM mcr.microsoft.com/dotnet/core/aspnet:3.0

ENV ASPNETCORE_URLS=https://+:443
```

### <a name="the-dockerignore-file"></a>O arquivo .dockerignore

Assim `.gitignore` como arquivos que excluem certos arquivos `.dockerignore` e diretórios do controle de origem, o arquivo pode ser usado para excluir arquivos e diretórios de serem copiados para a imagem durante a compilação. Isso não só economiza tempo de cópia, mas também pode `obj` evitar alguns erros que surgem de ter o diretório do seu PC copiado para a imagem. No mínimo, você deve adicionar `bin` `obj` entradas `.dockerignore` para e para o seu arquivo.

```console
bin/
obj/
```

## <a name="build-the-image"></a>Criar a imagem

Para uma solução com um único aplicativo e, portanto, um único arquivo Docker, é mais simples colocar o Arquivo Docker no diretório base. Em outras palavras, coloque-o no `.sln` mesmo diretório que o arquivo. Nesse caso, para construir a imagem, use o seguinte `docker build` comando do diretório que contém o arquivo Docker.

```console
docker build --tag stockdata .
```

O `--tag` sinalizador chamado confusamente (que `-t`pode ser encurtado para ) especifica o nome completo da imagem, incluindo a tag real, se especificado. O `.` final especifica o contexto em que a compilação será executada; o diretório de trabalho `COPY` atual para os comandos no arquivo Docker.

Se você tiver vários aplicativos dentro de uma única solução, você pode manter `.csproj` o Arquivo Docker para cada aplicativo em sua própria pasta, ao lado do arquivo. Você ainda deve `docker build` executar o comando do diretório base para garantir que a solução e todos os projetos sejam copiados para a imagem. Você pode especificar um arquivo Docker abaixo `--file` do `-f`diretório atual usando o sinalizador (ou )

```console
docker build --tag stockdata --file src/StockData/Dockerfile .
```

## <a name="run-the-image-in-a-container-on-your-machine"></a>Execute a imagem em um recipiente em sua máquina

Para executar a imagem na instância `docker run` local do Docker, use o comando.

```console
docker run -ti -p 5000:80 stockdata
```

O `-ti` sinalizador conecta seu terminal atual ao terminal do contêiner e é executado no modo interativo. A `-p 5000:80` porta publica (links) 80 no contêiner para porta 5000 na interface de rede localhost.

## <a name="push-the-image-to-a-registry"></a>Efetue o push da imagem para um Registro

Depois de verificar se a imagem funciona, empurre-a para um registro do Docker para disponibilizá-la em outros sistemas. As redes internas precisarão prover um registro Docker. Isso pode ser tão simples quanto executar a [própria `registry` imagem do Docker](https://docs.docker.com/registry/deploying/) (o registro Docker é executado em um contêiner Docker), mas existem várias soluções mais abrangentes disponíveis. Para compartilhamento externo e uso em nuvem, existem vários registros gerenciados disponíveis, como [o Azure Container Registry](https://docs.microsoft.com/azure/container-registry/) ou o Docker [Hub](https://docs.docker.com/docker-hub/repos/).

Para empurrar para o Docker Hub, prefixe o nome da imagem com o nome do usuário ou da organização.

```console
docker tag stockdata myorg/stockdata
docker push myorg/stockdata
```

Para empurrar para um registro privado, prefixe o nome da imagem com o nome do host do registro e o nome da organização.

```console
docker tag stockdata internal-registry:5000/myorg/stockdata
docker push internal-registry:5000/myorg/stockdata
```

Depois que a imagem estiver em um registro, você pode implantá-la em hosts Docker individuais ou em um mecanismo de orquestração de contêineres como kubernetes.

>[!div class="step-by-step"]
>[Próximo](self-hosted.md)
>[anterior](kubernetes.md)
