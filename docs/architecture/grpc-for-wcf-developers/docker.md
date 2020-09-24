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
# <a name="create-docker-images"></a><span data-ttu-id="c98f0-103">Criar imagens do Docker</span><span class="sxs-lookup"><span data-stu-id="c98f0-103">Create Docker images</span></span>

<span data-ttu-id="c98f0-104">Esta seção aborda a criação de imagens do Docker para ASP.NET Core aplicativos gRPC, prontos para execução no Docker, kubernetes ou outros ambientes de contêiner.</span><span class="sxs-lookup"><span data-stu-id="c98f0-104">This section covers the creation of Docker images for ASP.NET Core gRPC applications, ready to run in Docker, Kubernetes, or other container environments.</span></span> <span data-ttu-id="c98f0-105">O aplicativo de exemplo usado, com um ASP.NET Core aplicativo Web MVC e um serviço gRPC, está disponível no repositório [dotnet-Architecture/gRPC-for-WCF-Developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) no github.</span><span class="sxs-lookup"><span data-stu-id="c98f0-105">The sample application used, with an ASP.NET Core MVC web app and a gRPC service, is available on the [dotnet-architecture/grpc-for-wcf-developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) repository on GitHub.</span></span>

## <a name="microsoft-base-images-for-aspnet-core-applications"></a><span data-ttu-id="c98f0-106">Imagens base da Microsoft para aplicativos ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c98f0-106">Microsoft base images for ASP.NET Core applications</span></span>

<span data-ttu-id="c98f0-107">A Microsoft fornece uma variedade de imagens básicas para a criação e a execução de aplicativos .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c98f0-107">Microsoft provides a range of base images for building and running .NET Core applications.</span></span> <span data-ttu-id="c98f0-108">Para criar uma imagem ASP.NET Core 3,0, você usa duas imagens base:</span><span class="sxs-lookup"><span data-stu-id="c98f0-108">To create an ASP.NET Core 3.0 image, you use two base images:</span></span>

- <span data-ttu-id="c98f0-109">Uma imagem do SDK para compilar e publicar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c98f0-109">An SDK image to build and publish the application.</span></span>
- <span data-ttu-id="c98f0-110">Uma imagem de tempo de execução para implantação.</span><span class="sxs-lookup"><span data-stu-id="c98f0-110">A runtime image for deployment.</span></span>

| <span data-ttu-id="c98f0-111">Imagem</span><span class="sxs-lookup"><span data-stu-id="c98f0-111">Image</span></span> | <span data-ttu-id="c98f0-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="c98f0-112">Description</span></span> |
| ----- | ----------- |
| [<span data-ttu-id="c98f0-113">mcr.microsoft.com/dotnet/core/sdk</span><span class="sxs-lookup"><span data-stu-id="c98f0-113">mcr.microsoft.com/dotnet/core/sdk</span></span>](https://hub.docker.com/_/microsoft-dotnet-core-sdk/) | <span data-ttu-id="c98f0-114">Para a criação de aplicativos com o `docker build` .</span><span class="sxs-lookup"><span data-stu-id="c98f0-114">For building applications with `docker build`.</span></span> <span data-ttu-id="c98f0-115">Não deve ser usado na produção.</span><span class="sxs-lookup"><span data-stu-id="c98f0-115">Not to be used in production.</span></span> |
| [<span data-ttu-id="c98f0-116">mcr.microsoft.com/dotnet/core/aspnet</span><span class="sxs-lookup"><span data-stu-id="c98f0-116">mcr.microsoft.com/dotnet/core/aspnet</span></span>](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) | <span data-ttu-id="c98f0-117">Contém as dependências de tempo de execução e ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="c98f0-117">Contains the runtime and ASP.NET Core dependencies.</span></span> <span data-ttu-id="c98f0-118">Para produção.</span><span class="sxs-lookup"><span data-stu-id="c98f0-118">For production.</span></span> |

<span data-ttu-id="c98f0-119">Para cada imagem, há quatro variantes com base em diferentes distribuições do Linux, diferenciadas por marcas.</span><span class="sxs-lookup"><span data-stu-id="c98f0-119">For each image, there are four variants based on different Linux distributions, distinguished by tags.</span></span>

| <span data-ttu-id="c98f0-120">Marca (s) de imagem</span><span class="sxs-lookup"><span data-stu-id="c98f0-120">Image tag(s)</span></span> | <span data-ttu-id="c98f0-121">Linux</span><span class="sxs-lookup"><span data-stu-id="c98f0-121">Linux</span></span> | <span data-ttu-id="c98f0-122">Observações</span><span class="sxs-lookup"><span data-stu-id="c98f0-122">Notes</span></span> |
| --------- | ----- | ----- |
| <span data-ttu-id="c98f0-123">3,0-Buster, 3,0</span><span class="sxs-lookup"><span data-stu-id="c98f0-123">3.0-buster, 3.0</span></span> | <span data-ttu-id="c98f0-124">Debian 10</span><span class="sxs-lookup"><span data-stu-id="c98f0-124">Debian 10</span></span> | <span data-ttu-id="c98f0-125">A imagem padrão se nenhuma variante do sistema operacional for especificada.</span><span class="sxs-lookup"><span data-stu-id="c98f0-125">The default image if no OS variant is specified.</span></span> |
| <span data-ttu-id="c98f0-126">3,0 – Alpine Ski</span><span class="sxs-lookup"><span data-stu-id="c98f0-126">3.0-alpine</span></span> | <span data-ttu-id="c98f0-127">Alpine 3,9</span><span class="sxs-lookup"><span data-stu-id="c98f0-127">Alpine 3.9</span></span> | <span data-ttu-id="c98f0-128">As imagens da Alpine base são muito menores do que Debian ou Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="c98f0-128">Alpine base images are much smaller than Debian or Ubuntu ones.</span></span> |
| <span data-ttu-id="c98f0-129">3,0-disco</span><span class="sxs-lookup"><span data-stu-id="c98f0-129">3.0-disco</span></span> | <span data-ttu-id="c98f0-130">Ubuntu 19.04</span><span class="sxs-lookup"><span data-stu-id="c98f0-130">Ubuntu 19.04</span></span> | |
| <span data-ttu-id="c98f0-131">3,0-Bionic</span><span class="sxs-lookup"><span data-stu-id="c98f0-131">3.0-bionic</span></span> | <span data-ttu-id="c98f0-132">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="c98f0-132">Ubuntu 18.04</span></span> | |

<span data-ttu-id="c98f0-133">A imagem do Alpine base é de cerca de 100 MB, em comparação com 200 MB para as imagens Debian e Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="c98f0-133">The Alpine base image is around 100 MB, compared to 200 MB for the Debian and Ubuntu images.</span></span> <span data-ttu-id="c98f0-134">Alguns pacotes de software ou bibliotecas podem não estar disponíveis no gerenciamento de pacotes da Alpine Ski.</span><span class="sxs-lookup"><span data-stu-id="c98f0-134">Some software packages or libraries might not be available in Alpine's package management.</span></span> <span data-ttu-id="c98f0-135">Se você não tiver certeza de qual imagem usar, provavelmente deverá escolher o Debian padrão.</span><span class="sxs-lookup"><span data-stu-id="c98f0-135">If you're not sure which image to use, you should probably choose the default Debian.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c98f0-136">Certifique-se de usar a mesma variante do Linux para a compilação e o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="c98f0-136">Make sure you use the same variant of Linux for the build and the runtime.</span></span> <span data-ttu-id="c98f0-137">Os aplicativos criados e publicados em uma variante podem não funcionar em outro.</span><span class="sxs-lookup"><span data-stu-id="c98f0-137">Applications built and published on one variant might not work on another.</span></span>

## <a name="create-a-docker-image"></a><span data-ttu-id="c98f0-138">Criar uma imagem do Docker</span><span class="sxs-lookup"><span data-stu-id="c98f0-138">Create a Docker image</span></span>

<span data-ttu-id="c98f0-139">Uma imagem do Docker é definida por um *Dockerfile*.</span><span class="sxs-lookup"><span data-stu-id="c98f0-139">A Docker image is defined by a *Dockerfile*.</span></span> <span data-ttu-id="c98f0-140">Esse é um arquivo de texto que contém todos os comandos necessários para compilar o aplicativo e instalar quaisquer dependências necessárias para compilar ou executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c98f0-140">This is a text file that contains all the commands needed to build the application and install any dependencies that are required for either building or running the application.</span></span> <span data-ttu-id="c98f0-141">O exemplo a seguir mostra a Dockerfile mais simples para um aplicativo ASP.NET Core 3,0:</span><span class="sxs-lookup"><span data-stu-id="c98f0-141">The following example shows the simplest Dockerfile for an ASP.NET Core 3.0 application:</span></span>

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

<span data-ttu-id="c98f0-142">O Dockerfile tem duas partes: a primeira usa a `sdk` imagem base para compilar e publicar o aplicativo; a segunda cria uma imagem de tempo de execução a partir da `aspnet` base.</span><span class="sxs-lookup"><span data-stu-id="c98f0-142">The Dockerfile has two parts: the first uses the `sdk` base image to build and publish the application; the second creates a runtime image from the `aspnet` base.</span></span> <span data-ttu-id="c98f0-143">Isso ocorre porque a `sdk` imagem está em cerca de 900 MB, em comparação com cerca de 200 MB para a imagem de tempo de execução, e a maior parte de seu conteúdo é desnecessária no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="c98f0-143">This is because the `sdk` image is around 900 MB, compared to around 200 MB for the runtime image, and most of its contents are unnecessary at runtime.</span></span>

### <a name="the-build-steps"></a><span data-ttu-id="c98f0-144">As etapas de compilação</span><span class="sxs-lookup"><span data-stu-id="c98f0-144">The build steps</span></span>

| <span data-ttu-id="c98f0-145">Etapa</span><span class="sxs-lookup"><span data-stu-id="c98f0-145">Step</span></span> | <span data-ttu-id="c98f0-146">Descrição</span><span class="sxs-lookup"><span data-stu-id="c98f0-146">Description</span></span> |
| ---- | ----------- |
| `FROM ...` | <span data-ttu-id="c98f0-147">Declara a imagem base e atribui o `builder` alias.</span><span class="sxs-lookup"><span data-stu-id="c98f0-147">Declares the base image and assigns the `builder` alias.</span></span> |
| `WORKDIR /src` | <span data-ttu-id="c98f0-148">Cria o `/src` diretório e o define como o diretório de trabalho atual.</span><span class="sxs-lookup"><span data-stu-id="c98f0-148">Creates the `/src` directory and sets it as the current working directory.</span></span> |
| `COPY . .` | <span data-ttu-id="c98f0-149">Copia tudo abaixo do diretório atual no host para o diretório atual na imagem.</span><span class="sxs-lookup"><span data-stu-id="c98f0-149">Copies everything below the current directory on the host into the current directory on the image.</span></span> |
| `RUN dotnet restore` | <span data-ttu-id="c98f0-150">Restaura todos os pacotes externos (ASP.NET Core estrutura 3,0 é pré-instalada com o SDK).</span><span class="sxs-lookup"><span data-stu-id="c98f0-150">Restores any external packages (ASP.NET Core 3.0 framework is pre-installed with the SDK).</span></span> |
| `RUN dotnet publish ...` | <span data-ttu-id="c98f0-151">Compila e publica uma compilação de versão.</span><span class="sxs-lookup"><span data-stu-id="c98f0-151">Builds and publishes a Release build.</span></span> <span data-ttu-id="c98f0-152">Observe que o `--runtime` sinalizador não é necessário.</span><span class="sxs-lookup"><span data-stu-id="c98f0-152">Note that the `--runtime` flag isn't required.</span></span> |

### <a name="the-runtime-image-steps"></a><span data-ttu-id="c98f0-153">As etapas da imagem de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="c98f0-153">The runtime image steps</span></span>

| <span data-ttu-id="c98f0-154">Etapa</span><span class="sxs-lookup"><span data-stu-id="c98f0-154">Step</span></span> | <span data-ttu-id="c98f0-155">Descrição</span><span class="sxs-lookup"><span data-stu-id="c98f0-155">Description</span></span> |
| ---- | ----------- |
| `FROM ...` | <span data-ttu-id="c98f0-156">Declara uma nova imagem de base.</span><span class="sxs-lookup"><span data-stu-id="c98f0-156">Declares a new base image.</span></span> |
| `WORKDIR /app` | <span data-ttu-id="c98f0-157">Cria o `/app` diretório e o define como o diretório de trabalho atual.</span><span class="sxs-lookup"><span data-stu-id="c98f0-157">Creates the `/app` directory and sets it as the current working directory.</span></span> |
| `COPY --from=builder ...` | <span data-ttu-id="c98f0-158">Copia o aplicativo publicado da imagem anterior, usando o `builder` alias da primeira `FROM` linha.</span><span class="sxs-lookup"><span data-stu-id="c98f0-158">Copies the published application from the previous image, by using the `builder` alias from the first `FROM` line.</span></span> |
| `ENTRYPOINT [ ... ]` | <span data-ttu-id="c98f0-159">Define o comando a ser executado quando o contêiner é iniciado.</span><span class="sxs-lookup"><span data-stu-id="c98f0-159">Sets the command to run when the container starts.</span></span> <span data-ttu-id="c98f0-160">O `dotnet` comando na imagem de tempo de execução só pode executar arquivos dll.</span><span class="sxs-lookup"><span data-stu-id="c98f0-160">The `dotnet` command in the runtime image can only run DLL files.</span></span> |

### <a name="https-in-docker"></a><span data-ttu-id="c98f0-161">HTTPS no Docker</span><span class="sxs-lookup"><span data-stu-id="c98f0-161">HTTPS in Docker</span></span>

<span data-ttu-id="c98f0-162">As imagens base da Microsoft para o Docker definem a `ASPNETCORE_URLS` variável de ambiente como `http://+:80` , o que significa que Kestrel é executado sem https nessa porta.</span><span class="sxs-lookup"><span data-stu-id="c98f0-162">Microsoft base images for Docker set the `ASPNETCORE_URLS` environment variable to `http://+:80`, meaning that Kestrel runs without HTTPS on that port.</span></span> <span data-ttu-id="c98f0-163">Se você estiver usando HTTPS com um certificado personalizado (conforme descrito em [aplicativos gRPC hospedados internamente](self-hosted.md)), você deverá substituir isso.</span><span class="sxs-lookup"><span data-stu-id="c98f0-163">If you're using HTTPS with a custom certificate (as described in [Self-hosted gRPC applications](self-hosted.md)), you should override this.</span></span> <span data-ttu-id="c98f0-164">Defina a variável de ambiente na parte de criação da imagem de tempo de execução de seu Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="c98f0-164">Set the environment variable in the runtime image creation part of your Dockerfile.</span></span>

```dockerfile
# Runtime image creation
FROM mcr.microsoft.com/dotnet/core/aspnet:3.0

ENV ASPNETCORE_URLS=https://+:443
```

### <a name="the-dockerignore-file"></a><span data-ttu-id="c98f0-165">O arquivo. dockerignore</span><span class="sxs-lookup"><span data-stu-id="c98f0-165">The .dockerignore file</span></span>

<span data-ttu-id="c98f0-166">Assim como `.gitignore` os arquivos que excluem determinados arquivos e diretórios do controle do código-fonte, o `.dockerignore` arquivo pode ser usado para excluir arquivos e diretórios de serem copiados para a imagem durante a compilação.</span><span class="sxs-lookup"><span data-stu-id="c98f0-166">Much like `.gitignore` files that exclude certain files and directories from source control, the `.dockerignore` file can be used to exclude files and directories from being copied to the image during build.</span></span> <span data-ttu-id="c98f0-167">Isso não apenas poupa tempo de cópia, mas também pode evitar alguns erros que surgem de ter o `obj` diretório do seu PC copiado para a imagem.</span><span class="sxs-lookup"><span data-stu-id="c98f0-167">This not only saves time copying, but can also avoid some errors that arise from having the `obj` directory from your PC copied into the image.</span></span> <span data-ttu-id="c98f0-168">No mínimo, você deve adicionar entradas para `bin` e `obj` ao seu `.dockerignore` arquivo.</span><span class="sxs-lookup"><span data-stu-id="c98f0-168">At a minimum, you should add entries for `bin` and `obj` to your `.dockerignore` file.</span></span>

```console
bin/
obj/
```

## <a name="build-the-image"></a><span data-ttu-id="c98f0-169">Criar a imagem</span><span class="sxs-lookup"><span data-stu-id="c98f0-169">Build the image</span></span>

<span data-ttu-id="c98f0-170">Para uma solução com um único aplicativo e, portanto, um único Dockerfile, é mais simples colocar o Dockerfile no diretório base.</span><span class="sxs-lookup"><span data-stu-id="c98f0-170">For a solution with a single application, and thus a single Dockerfile, it's simplest to put the Dockerfile in the base directory.</span></span> <span data-ttu-id="c98f0-171">Em outras palavras, coloque-o no mesmo diretório que o `.sln` arquivo.</span><span class="sxs-lookup"><span data-stu-id="c98f0-171">In other words, put it in the same directory as the `.sln` file.</span></span> <span data-ttu-id="c98f0-172">Nesse caso, para criar a imagem, use o seguinte `docker build` comando do diretório que contém o Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="c98f0-172">In that case, to build the image, use the following `docker build` command from the directory containing the Dockerfile.</span></span>

```console
docker build --tag stockdata .
```

<span data-ttu-id="c98f0-173">O `--tag` sinalizador com nome confuso (que pode ser reduzido `-t` ) especifica o nome completo da imagem, incluindo a marca real, se especificado.</span><span class="sxs-lookup"><span data-stu-id="c98f0-173">The confusingly named `--tag` flag (which can be shortened to `-t`) specifies the whole name of the image, including the actual tag if specified.</span></span> <span data-ttu-id="c98f0-174">O `.` no final especifica o contexto no qual a compilação será executada; o diretório de trabalho atual para os `COPY` comandos no Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="c98f0-174">The `.` at the end specifies the context in which the build will be run; the current working directory for the `COPY` commands in the Dockerfile.</span></span>

<span data-ttu-id="c98f0-175">Se você tiver vários aplicativos em uma única solução, poderá manter o Dockerfile de cada aplicativo em sua própria pasta, ao lado do `.csproj` arquivo.</span><span class="sxs-lookup"><span data-stu-id="c98f0-175">If you have multiple applications within a single solution, you can keep the Dockerfile for each application in its own folder, beside the `.csproj` file.</span></span> <span data-ttu-id="c98f0-176">Você ainda deve executar o `docker build` comando do diretório base para garantir que a solução e todos os projetos sejam copiados para a imagem.</span><span class="sxs-lookup"><span data-stu-id="c98f0-176">You should still run the `docker build` command from the base directory to ensure that the solution and all the projects are copied into the image.</span></span> <span data-ttu-id="c98f0-177">Você pode especificar um Dockerfile abaixo do diretório atual usando o `--file` sinalizador (ou `-f` ).</span><span class="sxs-lookup"><span data-stu-id="c98f0-177">You can specify a Dockerfile below the current directory by using the `--file` (or `-f`) flag.</span></span>

```console
docker build --tag stockdata --file src/StockData/Dockerfile .
```

## <a name="run-the-image-in-a-container-on-your-machine"></a><span data-ttu-id="c98f0-178">Executar a imagem em um contêiner em seu computador</span><span class="sxs-lookup"><span data-stu-id="c98f0-178">Run the image in a container on your machine</span></span>

<span data-ttu-id="c98f0-179">Para executar a imagem em sua instância local do Docker, use o `docker run` comando.</span><span class="sxs-lookup"><span data-stu-id="c98f0-179">To run the image in your local Docker instance, use the `docker run` command.</span></span>

```console
docker run -ti -p 5000:80 stockdata
```

<span data-ttu-id="c98f0-180">O `-ti` sinalizador conecta o terminal atual ao terminal do contêiner e é executado no modo interativo.</span><span class="sxs-lookup"><span data-stu-id="c98f0-180">The `-ti` flag connects your current terminal to the container's terminal, and runs in interactive mode.</span></span> <span data-ttu-id="c98f0-181">A `-p 5000:80` porta de publicação (links) 80 no contêiner para a porta 5000 na interface de rede do localhost.</span><span class="sxs-lookup"><span data-stu-id="c98f0-181">The `-p 5000:80` publishes (links) port 80 on the container to port 5000 on the localhost network interface.</span></span>

## <a name="push-the-image-to-a-registry"></a><span data-ttu-id="c98f0-182">Efetue o push da imagem para um Registro</span><span class="sxs-lookup"><span data-stu-id="c98f0-182">Push the image to a registry</span></span>

<span data-ttu-id="c98f0-183">Depois de verificar se a imagem funciona, envie-a por push para um registro do Docker para disponibilizá-la em outros sistemas.</span><span class="sxs-lookup"><span data-stu-id="c98f0-183">After you've verified that the image works, push it to a Docker registry to make it available on other systems.</span></span> <span data-ttu-id="c98f0-184">As redes internas precisarão provisionar um registro do Docker.</span><span class="sxs-lookup"><span data-stu-id="c98f0-184">Internal networks will need to provision a Docker registry.</span></span> <span data-ttu-id="c98f0-185">Isso pode ser tão simples quanto executar a [própria `registry` imagem do Docker](https://docs.docker.com/registry/deploying/) (o registro do Docker é executado em um contêiner do Docker), mas há várias soluções mais abrangentes disponíveis.</span><span class="sxs-lookup"><span data-stu-id="c98f0-185">This can be as simple as running [Docker's own `registry` image](https://docs.docker.com/registry/deploying/) (the Docker registry runs in a Docker container), but there are various more comprehensive solutions available.</span></span> <span data-ttu-id="c98f0-186">Para o compartilhamento externo e o uso de nuvem, há vários registros gerenciados disponíveis, como o [registro de contêiner do Azure](/azure/container-registry/) ou o [Hub do Docker](https://docs.docker.com/docker-hub/repos/).</span><span class="sxs-lookup"><span data-stu-id="c98f0-186">For external sharing and cloud use, there are various managed registries available, such as [Azure Container Registry](/azure/container-registry/) or [Docker Hub](https://docs.docker.com/docker-hub/repos/).</span></span>

<span data-ttu-id="c98f0-187">Para enviar por push para o Hub do Docker, Prefixe o nome da imagem com o nome do usuário ou da organização.</span><span class="sxs-lookup"><span data-stu-id="c98f0-187">To push to Docker Hub, prefix the image name with your user or organization name.</span></span>

```console
docker tag stockdata myorg/stockdata
docker push myorg/stockdata
```

<span data-ttu-id="c98f0-188">Para enviar por push para um registro privado, Prefixe o nome da imagem com o nome do host do registro e o nome da organização.</span><span class="sxs-lookup"><span data-stu-id="c98f0-188">To push to a private registry, prefix the image name with the registry host name and the organization name.</span></span>

```console
docker tag stockdata internal-registry:5000/myorg/stockdata
docker push internal-registry:5000/myorg/stockdata
```

<span data-ttu-id="c98f0-189">Depois que a imagem estiver em um registro, você poderá implantá-la em hosts do Docker individuais ou em um mecanismo de orquestração de contêiner, como kubernetes.</span><span class="sxs-lookup"><span data-stu-id="c98f0-189">After the image is in a registry, you can deploy it to individual Docker hosts, or to a container orchestration engine like Kubernetes.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="c98f0-190">[Anterior](self-hosted.md) 
> [Avançar](kubernetes.md)</span><span class="sxs-lookup"><span data-stu-id="c98f0-190">[Previous](self-hosted.md)
[Next](kubernetes.md)</span></span>
