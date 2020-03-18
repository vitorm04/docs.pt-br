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
# <a name="create-docker-images"></a><span data-ttu-id="0fa43-103">Criar imagens do Docker</span><span class="sxs-lookup"><span data-stu-id="0fa43-103">Create Docker images</span></span>

<span data-ttu-id="0fa43-104">Esta seção abrange a criação de imagens Docker para ASP.NET aplicativos core gRPC, prontos para serem executados em Docker, Kubernetes ou outros ambientes de contêineres.</span><span class="sxs-lookup"><span data-stu-id="0fa43-104">This section covers the creation of Docker images for ASP.NET Core gRPC applications, ready to run in Docker, Kubernetes, or other container environments.</span></span> <span data-ttu-id="0fa43-105">O aplicativo de exemplo utilizado, com um aplicativo web Core MVC ASP.NET e um serviço gRPC, está disponível no repositório [dotnet-architecture/grpc-for-wcf-developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) no GitHub.</span><span class="sxs-lookup"><span data-stu-id="0fa43-105">The sample application used, with an ASP.NET Core MVC web app and a gRPC service, is available on the [dotnet-architecture/grpc-for-wcf-developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) repository on GitHub.</span></span>

## <a name="microsoft-base-images-for-aspnet-core-applications"></a><span data-ttu-id="0fa43-106">Imagens básicas da Microsoft para aplicativos ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="0fa43-106">Microsoft base images for ASP.NET Core applications</span></span>

<span data-ttu-id="0fa43-107">A Microsoft fornece uma série de imagens básicas para construir e executar aplicativos .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0fa43-107">Microsoft provides a range of base images for building and running .NET Core applications.</span></span> <span data-ttu-id="0fa43-108">Para criar uma imagem ASP.NET Core 3.0, você usa duas imagens base:</span><span class="sxs-lookup"><span data-stu-id="0fa43-108">To create an ASP.NET Core 3.0 image, you use two base images:</span></span>

- <span data-ttu-id="0fa43-109">Uma imagem SDK para construir e publicar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0fa43-109">An SDK image to build and publish the application.</span></span>
- <span data-ttu-id="0fa43-110">Uma imagem em tempo de execução para implantação.</span><span class="sxs-lookup"><span data-stu-id="0fa43-110">A runtime image for deployment.</span></span>

| <span data-ttu-id="0fa43-111">Imagem</span><span class="sxs-lookup"><span data-stu-id="0fa43-111">Image</span></span> | <span data-ttu-id="0fa43-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="0fa43-112">Description</span></span> |
| ----- | ----------- |
| [<span data-ttu-id="0fa43-113">mcr.microsoft.com/dotnet/core/sdk</span><span class="sxs-lookup"><span data-stu-id="0fa43-113">mcr.microsoft.com/dotnet/core/sdk</span></span>](https://hub.docker.com/_/microsoft-dotnet-core-sdk/) | <span data-ttu-id="0fa43-114">Para construir aplicações `docker build`com .</span><span class="sxs-lookup"><span data-stu-id="0fa43-114">For building applications with `docker build`.</span></span> <span data-ttu-id="0fa43-115">Não deve ser usado na produção.</span><span class="sxs-lookup"><span data-stu-id="0fa43-115">Not to be used in production.</span></span> |
| [<span data-ttu-id="0fa43-116">mcr.microsoft.com/dotnet/core/aspnet</span><span class="sxs-lookup"><span data-stu-id="0fa43-116">mcr.microsoft.com/dotnet/core/aspnet</span></span>](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) | <span data-ttu-id="0fa43-117">Contém o tempo de execução e ASP.NET dependências do Core.</span><span class="sxs-lookup"><span data-stu-id="0fa43-117">Contains the runtime and ASP.NET Core dependencies.</span></span> <span data-ttu-id="0fa43-118">Para produção.</span><span class="sxs-lookup"><span data-stu-id="0fa43-118">For production.</span></span> |

<span data-ttu-id="0fa43-119">Para cada imagem, há quatro variantes baseadas em diferentes distribuições Linux, distinguidas por tags.</span><span class="sxs-lookup"><span data-stu-id="0fa43-119">For each image, there are four variants based on different Linux distributions, distinguished by tags.</span></span>

| <span data-ttu-id="0fa43-120">Tag(s) de imagem</span><span class="sxs-lookup"><span data-stu-id="0fa43-120">Image tag(s)</span></span> | <span data-ttu-id="0fa43-121">Linux</span><span class="sxs-lookup"><span data-stu-id="0fa43-121">Linux</span></span> | <span data-ttu-id="0fa43-122">Observações</span><span class="sxs-lookup"><span data-stu-id="0fa43-122">Notes</span></span> |
| --------- | ----- | ----- |
| <span data-ttu-id="0fa43-123">3.0-buster, 3.0</span><span class="sxs-lookup"><span data-stu-id="0fa43-123">3.0-buster, 3.0</span></span> | <span data-ttu-id="0fa43-124">Debian 10</span><span class="sxs-lookup"><span data-stu-id="0fa43-124">Debian 10</span></span> | <span data-ttu-id="0fa43-125">A imagem padrão se nenhuma variante do Sistema Operacional for especificada.</span><span class="sxs-lookup"><span data-stu-id="0fa43-125">The default image if no OS variant is specified.</span></span> |
| <span data-ttu-id="0fa43-126">3.0-alpino</span><span class="sxs-lookup"><span data-stu-id="0fa43-126">3.0-alpine</span></span> | <span data-ttu-id="0fa43-127">Alpino 3.9</span><span class="sxs-lookup"><span data-stu-id="0fa43-127">Alpine 3.9</span></span> | <span data-ttu-id="0fa43-128">As imagens base alpinas são muito menores do que as do Debian ou do Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="0fa43-128">Alpine base images are much smaller than Debian or Ubuntu ones.</span></span> |
| <span data-ttu-id="0fa43-129">3.0-disco</span><span class="sxs-lookup"><span data-stu-id="0fa43-129">3.0-disco</span></span> | <span data-ttu-id="0fa43-130">Ubuntu 19.04</span><span class="sxs-lookup"><span data-stu-id="0fa43-130">Ubuntu 19.04</span></span> | |
| <span data-ttu-id="0fa43-131">3.0-biônico</span><span class="sxs-lookup"><span data-stu-id="0fa43-131">3.0-bionic</span></span> | <span data-ttu-id="0fa43-132">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="0fa43-132">Ubuntu 18.04</span></span> | |

<span data-ttu-id="0fa43-133">A imagem base alpina é de cerca de 100 MB, em comparação com 200 MB para as imagens Debian e Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="0fa43-133">The Alpine base image is around 100 MB, compared to 200 MB for the Debian and Ubuntu images.</span></span> <span data-ttu-id="0fa43-134">Alguns pacotes de software ou bibliotecas podem não estar disponíveis no gerenciamento de pacotes da Alpine.</span><span class="sxs-lookup"><span data-stu-id="0fa43-134">Some software packages or libraries might not be available in Alpine's package management.</span></span> <span data-ttu-id="0fa43-135">Se você não tem certeza de qual imagem usar, provavelmente deve escolher o Debian padrão.</span><span class="sxs-lookup"><span data-stu-id="0fa43-135">If you're not sure which image to use, you should probably choose the default Debian.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0fa43-136">Certifique-se de usar a mesma variante do Linux para a compilação e o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="0fa43-136">Make sure you use the same variant of Linux for the build and the runtime.</span></span> <span data-ttu-id="0fa43-137">Aplicativos construídos e publicados em uma variante podem não funcionar em outra.</span><span class="sxs-lookup"><span data-stu-id="0fa43-137">Applications built and published on one variant might not work on another.</span></span>

## <a name="create-a-docker-image"></a><span data-ttu-id="0fa43-138">Criar uma imagem do Docker</span><span class="sxs-lookup"><span data-stu-id="0fa43-138">Create a Docker image</span></span>

<span data-ttu-id="0fa43-139">Uma imagem do Docker é definida por um *arquivo Docker*.</span><span class="sxs-lookup"><span data-stu-id="0fa43-139">A Docker image is defined by a *Dockerfile*.</span></span> <span data-ttu-id="0fa43-140">Este é um arquivo de texto que contém todos os comandos necessários para construir o aplicativo e instalar quaisquer dependências necessárias para a construção ou execução do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0fa43-140">This is a text file that contains all the commands needed to build the application and install any dependencies that are required for either building or running the application.</span></span> <span data-ttu-id="0fa43-141">O exemplo a seguir mostra o arquivo Docker mais simples para um aplicativo ASP.NET Core 3.0:</span><span class="sxs-lookup"><span data-stu-id="0fa43-141">The following example shows the simplest Dockerfile for an ASP.NET Core 3.0 application:</span></span>

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

<span data-ttu-id="0fa43-142">O Arquivo Docker tem duas partes: a primeira usa a `sdk` imagem base para construir e publicar o aplicativo; o segundo cria uma imagem `aspnet` de tempo de execução a partir da base.</span><span class="sxs-lookup"><span data-stu-id="0fa43-142">The Dockerfile has two parts: the first uses the `sdk` base image to build and publish the application; the second creates a runtime image from the `aspnet` base.</span></span> <span data-ttu-id="0fa43-143">Isso porque `sdk` a imagem é de cerca de 900 MB, em comparação com cerca de 200 MB para a imagem em tempo de execução, e a maioria de seu conteúdo é desnecessária em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="0fa43-143">This is because the `sdk` image is around 900 MB, compared to around 200 MB for the runtime image, and most of its contents are unnecessary at runtime.</span></span>

### <a name="the-build-steps"></a><span data-ttu-id="0fa43-144">As etapas de construção</span><span class="sxs-lookup"><span data-stu-id="0fa43-144">The build steps</span></span>

| <span data-ttu-id="0fa43-145">Etapa</span><span class="sxs-lookup"><span data-stu-id="0fa43-145">Step</span></span> | <span data-ttu-id="0fa43-146">Descrição</span><span class="sxs-lookup"><span data-stu-id="0fa43-146">Description</span></span> |
| ---- | ----------- |
| `FROM ...` | <span data-ttu-id="0fa43-147">Declara a imagem base e `builder` atribui o alias.</span><span class="sxs-lookup"><span data-stu-id="0fa43-147">Declares the base image and assigns the `builder` alias.</span></span> |
| `WORKDIR /src` | <span data-ttu-id="0fa43-148">Cria `/src` o diretório e define-o como o diretório de trabalho atual.</span><span class="sxs-lookup"><span data-stu-id="0fa43-148">Creates the `/src` directory and sets it as the current working directory.</span></span> |
| `COPY . .` | <span data-ttu-id="0fa43-149">Copia tudo abaixo do diretório atual sobre o host para o diretório atual na imagem.</span><span class="sxs-lookup"><span data-stu-id="0fa43-149">Copies everything below the current directory on the host into the current directory on the image.</span></span> |
| `RUN dotnet restore` | <span data-ttu-id="0fa43-150">Restaura quaisquer pacotes externos (ASP.NET framework Core 3.0 está pré-instalado com o SDK).</span><span class="sxs-lookup"><span data-stu-id="0fa43-150">Restores any external packages (ASP.NET Core 3.0 framework is pre-installed with the SDK).</span></span> |
| `RUN dotnet publish ...` | <span data-ttu-id="0fa43-151">Constrói e publica uma compilação de lançamento.</span><span class="sxs-lookup"><span data-stu-id="0fa43-151">Builds and publishes a Release build.</span></span> <span data-ttu-id="0fa43-152">Note que `--runtime` a bandeira não é necessária.</span><span class="sxs-lookup"><span data-stu-id="0fa43-152">Note that the `--runtime` flag isn't required.</span></span> |

### <a name="the-runtime-image-steps"></a><span data-ttu-id="0fa43-153">As etapas de imagem em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="0fa43-153">The runtime image steps</span></span>

| <span data-ttu-id="0fa43-154">Etapa</span><span class="sxs-lookup"><span data-stu-id="0fa43-154">Step</span></span> | <span data-ttu-id="0fa43-155">Descrição</span><span class="sxs-lookup"><span data-stu-id="0fa43-155">Description</span></span> |
| ---- | ----------- |
| `FROM ...` | <span data-ttu-id="0fa43-156">Declara uma nova imagem base.</span><span class="sxs-lookup"><span data-stu-id="0fa43-156">Declares a new base image.</span></span> |
| `WORKDIR /app` | <span data-ttu-id="0fa43-157">Cria `/app` o diretório e define-o como o diretório de trabalho atual.</span><span class="sxs-lookup"><span data-stu-id="0fa43-157">Creates the `/app` directory and sets it as the current working directory.</span></span> |
| `COPY --from=builder ...` | <span data-ttu-id="0fa43-158">Copia o aplicativo publicado da imagem `builder` anterior, usando `FROM` o alias da primeira linha.</span><span class="sxs-lookup"><span data-stu-id="0fa43-158">Copies the published application from the previous image, by using the `builder` alias from the first `FROM` line.</span></span> |
| `ENTRYPOINT [ ... ]` | <span data-ttu-id="0fa43-159">Define o comando para ser executado quando o contêiner começar.</span><span class="sxs-lookup"><span data-stu-id="0fa43-159">Sets the command to run when the container starts.</span></span> <span data-ttu-id="0fa43-160">O `dotnet` comando na imagem de tempo de execução só pode executar arquivos DLL.</span><span class="sxs-lookup"><span data-stu-id="0fa43-160">The `dotnet` command in the runtime image can only run DLL files.</span></span> |

### <a name="https-in-docker"></a><span data-ttu-id="0fa43-161">HTTPS em Docker</span><span class="sxs-lookup"><span data-stu-id="0fa43-161">HTTPS in Docker</span></span>

<span data-ttu-id="0fa43-162">As imagens base `ASPNETCORE_URLS` da Microsoft `http://+:80`para docker definem a variável ambiente para , o que significa que o Kestrel é executado sem HTTPS nessa porta.</span><span class="sxs-lookup"><span data-stu-id="0fa43-162">Microsoft base images for Docker set the `ASPNETCORE_URLS` environment variable to `http://+:80`, meaning that Kestrel runs without HTTPS on that port.</span></span> <span data-ttu-id="0fa43-163">Se você estiver usando HTTPS com um certificado personalizado (como descrito em [aplicativos gRPC auto-hospedados),](self-hosted.md)você deve substituí-lo.</span><span class="sxs-lookup"><span data-stu-id="0fa43-163">If you're using HTTPS with a custom certificate (as described in [Self-hosted gRPC applications](self-hosted.md)), you should override this.</span></span> <span data-ttu-id="0fa43-164">Defina a variável de ambiente na parte de criação de imagem em tempo de execução do seu Arquivo Docker.</span><span class="sxs-lookup"><span data-stu-id="0fa43-164">Set the environment variable in the runtime image creation part of your Dockerfile.</span></span>

```dockerfile
# Runtime image creation
FROM mcr.microsoft.com/dotnet/core/aspnet:3.0

ENV ASPNETCORE_URLS=https://+:443
```

### <a name="the-dockerignore-file"></a><span data-ttu-id="0fa43-165">O arquivo .dockerignore</span><span class="sxs-lookup"><span data-stu-id="0fa43-165">The .dockerignore file</span></span>

<span data-ttu-id="0fa43-166">Assim `.gitignore` como arquivos que excluem certos arquivos `.dockerignore` e diretórios do controle de origem, o arquivo pode ser usado para excluir arquivos e diretórios de serem copiados para a imagem durante a compilação.</span><span class="sxs-lookup"><span data-stu-id="0fa43-166">Much like `.gitignore` files that exclude certain files and directories from source control, the `.dockerignore` file can be used to exclude files and directories from being copied to the image during build.</span></span> <span data-ttu-id="0fa43-167">Isso não só economiza tempo de cópia, mas também pode `obj` evitar alguns erros que surgem de ter o diretório do seu PC copiado para a imagem.</span><span class="sxs-lookup"><span data-stu-id="0fa43-167">This not only saves time copying, but can also avoid some errors that arise from having the `obj` directory from your PC copied into the image.</span></span> <span data-ttu-id="0fa43-168">No mínimo, você deve adicionar `bin` `obj` entradas `.dockerignore` para e para o seu arquivo.</span><span class="sxs-lookup"><span data-stu-id="0fa43-168">At a minimum, you should add entries for `bin` and `obj` to your `.dockerignore` file.</span></span>

```console
bin/
obj/
```

## <a name="build-the-image"></a><span data-ttu-id="0fa43-169">Criar a imagem</span><span class="sxs-lookup"><span data-stu-id="0fa43-169">Build the image</span></span>

<span data-ttu-id="0fa43-170">Para uma solução com um único aplicativo e, portanto, um único arquivo Docker, é mais simples colocar o Arquivo Docker no diretório base.</span><span class="sxs-lookup"><span data-stu-id="0fa43-170">For a solution with a single application, and thus a single Dockerfile, it's simplest to put the Dockerfile in the base directory.</span></span> <span data-ttu-id="0fa43-171">Em outras palavras, coloque-o no `.sln` mesmo diretório que o arquivo.</span><span class="sxs-lookup"><span data-stu-id="0fa43-171">In other words, put it in the same directory as the `.sln` file.</span></span> <span data-ttu-id="0fa43-172">Nesse caso, para construir a imagem, use o seguinte `docker build` comando do diretório que contém o arquivo Docker.</span><span class="sxs-lookup"><span data-stu-id="0fa43-172">In that case, to build the image, use the following `docker build` command from the directory containing the Dockerfile.</span></span>

```console
docker build --tag stockdata .
```

<span data-ttu-id="0fa43-173">O `--tag` sinalizador chamado confusamente (que `-t`pode ser encurtado para ) especifica o nome completo da imagem, incluindo a tag real, se especificado.</span><span class="sxs-lookup"><span data-stu-id="0fa43-173">The confusingly named `--tag` flag (which can be shortened to `-t`) specifies the whole name of the image, including the actual tag if specified.</span></span> <span data-ttu-id="0fa43-174">O `.` final especifica o contexto em que a compilação será executada; o diretório de trabalho `COPY` atual para os comandos no arquivo Docker.</span><span class="sxs-lookup"><span data-stu-id="0fa43-174">The `.` at the end specifies the context in which the build will be run; the current working directory for the `COPY` commands in the Dockerfile.</span></span>

<span data-ttu-id="0fa43-175">Se você tiver vários aplicativos dentro de uma única solução, você pode manter `.csproj` o Arquivo Docker para cada aplicativo em sua própria pasta, ao lado do arquivo.</span><span class="sxs-lookup"><span data-stu-id="0fa43-175">If you have multiple applications within a single solution, you can keep the Dockerfile for each application in its own folder, beside the `.csproj` file.</span></span> <span data-ttu-id="0fa43-176">Você ainda deve `docker build` executar o comando do diretório base para garantir que a solução e todos os projetos sejam copiados para a imagem.</span><span class="sxs-lookup"><span data-stu-id="0fa43-176">You should still run the `docker build` command from the base directory to ensure that the solution and all the projects are copied into the image.</span></span> <span data-ttu-id="0fa43-177">Você pode especificar um arquivo Docker abaixo `--file` do `-f`diretório atual usando o sinalizador (ou )</span><span class="sxs-lookup"><span data-stu-id="0fa43-177">You can specify a Dockerfile below the current directory by using the `--file` (or `-f`) flag.</span></span>

```console
docker build --tag stockdata --file src/StockData/Dockerfile .
```

## <a name="run-the-image-in-a-container-on-your-machine"></a><span data-ttu-id="0fa43-178">Execute a imagem em um recipiente em sua máquina</span><span class="sxs-lookup"><span data-stu-id="0fa43-178">Run the image in a container on your machine</span></span>

<span data-ttu-id="0fa43-179">Para executar a imagem na instância `docker run` local do Docker, use o comando.</span><span class="sxs-lookup"><span data-stu-id="0fa43-179">To run the image in your local Docker instance, use the `docker run` command.</span></span>

```console
docker run -ti -p 5000:80 stockdata
```

<span data-ttu-id="0fa43-180">O `-ti` sinalizador conecta seu terminal atual ao terminal do contêiner e é executado no modo interativo.</span><span class="sxs-lookup"><span data-stu-id="0fa43-180">The `-ti` flag connects your current terminal to the container's terminal, and runs in interactive mode.</span></span> <span data-ttu-id="0fa43-181">A `-p 5000:80` porta publica (links) 80 no contêiner para porta 5000 na interface de rede localhost.</span><span class="sxs-lookup"><span data-stu-id="0fa43-181">The `-p 5000:80` publishes (links) port 80 on the container to port 5000 on the localhost network interface.</span></span>

## <a name="push-the-image-to-a-registry"></a><span data-ttu-id="0fa43-182">Efetue o push da imagem para um Registro</span><span class="sxs-lookup"><span data-stu-id="0fa43-182">Push the image to a registry</span></span>

<span data-ttu-id="0fa43-183">Depois de verificar se a imagem funciona, empurre-a para um registro do Docker para disponibilizá-la em outros sistemas.</span><span class="sxs-lookup"><span data-stu-id="0fa43-183">After you've verified that the image works, push it to a Docker registry to make it available on other systems.</span></span> <span data-ttu-id="0fa43-184">As redes internas precisarão prover um registro Docker.</span><span class="sxs-lookup"><span data-stu-id="0fa43-184">Internal networks will need to provision a Docker registry.</span></span> <span data-ttu-id="0fa43-185">Isso pode ser tão simples quanto executar a [própria `registry` imagem do Docker](https://docs.docker.com/registry/deploying/) (o registro Docker é executado em um contêiner Docker), mas existem várias soluções mais abrangentes disponíveis.</span><span class="sxs-lookup"><span data-stu-id="0fa43-185">This can be as simple as running [Docker's own `registry` image](https://docs.docker.com/registry/deploying/) (the Docker registry runs in a Docker container), but there are various more comprehensive solutions available.</span></span> <span data-ttu-id="0fa43-186">Para compartilhamento externo e uso em nuvem, existem vários registros gerenciados disponíveis, como [o Azure Container Registry](https://docs.microsoft.com/azure/container-registry/) ou o Docker [Hub](https://docs.docker.com/docker-hub/repos/).</span><span class="sxs-lookup"><span data-stu-id="0fa43-186">For external sharing and cloud use, there are various managed registries available, such as [Azure Container Registry](https://docs.microsoft.com/azure/container-registry/) or [Docker Hub](https://docs.docker.com/docker-hub/repos/).</span></span>

<span data-ttu-id="0fa43-187">Para empurrar para o Docker Hub, prefixe o nome da imagem com o nome do usuário ou da organização.</span><span class="sxs-lookup"><span data-stu-id="0fa43-187">To push to Docker Hub, prefix the image name with your user or organization name.</span></span>

```console
docker tag stockdata myorg/stockdata
docker push myorg/stockdata
```

<span data-ttu-id="0fa43-188">Para empurrar para um registro privado, prefixe o nome da imagem com o nome do host do registro e o nome da organização.</span><span class="sxs-lookup"><span data-stu-id="0fa43-188">To push to a private registry, prefix the image name with the registry host name and the organization name.</span></span>

```console
docker tag stockdata internal-registry:5000/myorg/stockdata
docker push internal-registry:5000/myorg/stockdata
```

<span data-ttu-id="0fa43-189">Depois que a imagem estiver em um registro, você pode implantá-la em hosts Docker individuais ou em um mecanismo de orquestração de contêineres como kubernetes.</span><span class="sxs-lookup"><span data-stu-id="0fa43-189">After the image is in a registry, you can deploy it to individual Docker hosts, or to a container orchestration engine like Kubernetes.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="0fa43-190">[Próximo](self-hosted.md)
>[anterior](kubernetes.md)</span><span class="sxs-lookup"><span data-stu-id="0fa43-190">[Previous](self-hosted.md)
[Next](kubernetes.md)</span></span>
