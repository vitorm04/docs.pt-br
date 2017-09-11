---
title: Criando imagens do Docker do .NET Core
description: "Noções básicas de imagens do Docker e do .NET Core"
keywords: .NET, .NET Core, Docker
author: spboyer
ms.author: shboyer
ms.date: 08/29/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-docker
ms.devlang: dotnet
ms.assetid: 03c28597-7e73-46d6-a9c3-f9cb55642739
ms.translationtype: HT
ms.sourcegitcommit: 9dc52f3a8c74c1aa575a83cb3bbd579b93fae9ae
ms.openlocfilehash: 0e679ffc22f52de5e2ce8194942efbb2f5299ee4
ms.contentlocale: pt-br
ms.lasthandoff: 09/06/2017

---

#<a name="building-docker-images-for-net-core-applications"></a><span data-ttu-id="2525b-104">Criando imagens do Docker para .NET Core Applications</span><span class="sxs-lookup"><span data-stu-id="2525b-104">Building Docker Images for .NET Core Applications</span></span>

 
> [!IMPORTANT]
> <span data-ttu-id="2525b-105">Estamos em processo de atualização do .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="2525b-105">We are in the process of updating for .NET Core 2.0.</span></span> <span data-ttu-id="2525b-106">As instruções a seguir estão desatualizadas.</span><span class="sxs-lookup"><span data-stu-id="2525b-106">The instructions below are out of date.</span></span> <span data-ttu-id="2525b-107">Pedimos sinceras desculpas pelo inconveniente!</span><span class="sxs-lookup"><span data-stu-id="2525b-107">We sincerely apologize for any inconvenience!</span></span>

<span data-ttu-id="2525b-108">Para entender como usar o .NET Core e o Docker juntos, precisamos primeiro conhecer as diferentes imagens do Docker que são oferecidas e quando é o caso de uso ideal para usá-las.</span><span class="sxs-lookup"><span data-stu-id="2525b-108">In order to get an understanding of how to use .NET Core and Docker together, we must first get to know the different Docker images that are offered and when is the right use case for them.</span></span> <span data-ttu-id="2525b-109">Percorreremos aqui as variações oferecidas, compilaremos uma API Web do ASP.NET Core, usaremos as ferramentas do Yeoman Docker para criar um contêiner depurável e veremos como o Visual Studio Code pode ajudar no processo.</span><span class="sxs-lookup"><span data-stu-id="2525b-109">Here we will walk through the variations offered, build an ASP.NET Core Web API, use the Yeoman Docker tools to create a debuggable container as well as peek at how Visual Studio Code can assist in the process.</span></span> 

## <a name="docker-image-optimizations"></a><span data-ttu-id="2525b-110">Otimizações de imagem de Docker</span><span class="sxs-lookup"><span data-stu-id="2525b-110">Docker Image Optimizations</span></span>

<span data-ttu-id="2525b-111">Ao criar imagens do Docker para desenvolvedores, nos concentramos em três cenários principais:</span><span class="sxs-lookup"><span data-stu-id="2525b-111">When building Docker images for developers, we focused on three main scenarios:</span></span>

- <span data-ttu-id="2525b-112">Imagens usadas para desenvolver aplicativos .NET Core</span><span class="sxs-lookup"><span data-stu-id="2525b-112">Images used to develop .NET Core apps</span></span>
- <span data-ttu-id="2525b-113">Imagens usadas para compilar aplicativos .NET Core</span><span class="sxs-lookup"><span data-stu-id="2525b-113">Images used to build .NET Core apps</span></span>
- <span data-ttu-id="2525b-114">Imagens usadas para executar aplicativos .NET Core</span><span class="sxs-lookup"><span data-stu-id="2525b-114">Images used to run .NET Core apps</span></span>

<span data-ttu-id="2525b-115">Por que três imagens?</span><span class="sxs-lookup"><span data-stu-id="2525b-115">Why three images?</span></span>
<span data-ttu-id="2525b-116">Ao desenvolver, compilar e executar aplicativos em contêineres, temos prioridades diferentes.</span><span class="sxs-lookup"><span data-stu-id="2525b-116">When developing, building and running containerized applications, we have different priorities.</span></span>
- <span data-ttu-id="2525b-117">**Desenvolvimento:** quanto tempo você leva para iterar alterações e a capacidade de depurá-las.</span><span class="sxs-lookup"><span data-stu-id="2525b-117">**Development:**  How fast can you iterate changes, and the ability to debug the changes.</span></span> <span data-ttu-id="2525b-118">O tamanho da imagem não é tão importante, pois você pode fazer alterações em seu código e observá-las rapidamente.</span><span class="sxs-lookup"><span data-stu-id="2525b-118">The size of the image isn't as important, rather can you make changes to your code and see them quickly.</span></span> <span data-ttu-id="2525b-119">Algumas das nossas ferramentas, como o [yo docker](https://aka.ms/yodocker) para uso no Visual Studio Code, utilizam essa imagem durante o tempo de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="2525b-119">Some of our tools, like [yo docker](https://aka.ms/yodocker) for use in Visual Studio Code use this image during development time.</span></span> 
- <span data-ttu-id="2525b-120">**Compilação:** o que é necessário para compilar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2525b-120">**Build:** What's needed to compile your app.</span></span> <span data-ttu-id="2525b-121">Isso inclui o compilador e as outras dependências para otimizar os binários.</span><span class="sxs-lookup"><span data-stu-id="2525b-121">This includes the compiler and any other dependencies to optimize the binaries.</span></span> <span data-ttu-id="2525b-122">Essa imagem não é aquela que você implanta, mas sim uma imagem que você usa para compilar o conteúdo incluído em uma imagem de produção.</span><span class="sxs-lookup"><span data-stu-id="2525b-122">This image isn't the image you deploy, rather it's an image you use to build the content you place into a production image.</span></span> <span data-ttu-id="2525b-123">Essa imagem deve ser usada na integração contínua ou no ambiente de build.</span><span class="sxs-lookup"><span data-stu-id="2525b-123">This image would be used in your continuous integration, or build environment.</span></span> <span data-ttu-id="2525b-124">Por exemplo, em vez de instalar todas as dependências diretamente em um agente de build, este criaria instâncias de uma imagem para compilar o aplicativo com todas as dependências necessárias para compilar o aplicativo contido na imagem.</span><span class="sxs-lookup"><span data-stu-id="2525b-124">For instance, rather than installing all the dependencies directly on a build agent, the build agent would instance a build image to compile the application with all the dependencies required to build the app contained within the image.</span></span> <span data-ttu-id="2525b-125">O agente de build precisa saber apenas como executar essa imagem do Docker.</span><span class="sxs-lookup"><span data-stu-id="2525b-125">Your build agent only needs to know how to run this Docker image.</span></span> 
- <span data-ttu-id="2525b-126">**Produção:** em quanto tempo você pode implantar e iniciar sua imagem.</span><span class="sxs-lookup"><span data-stu-id="2525b-126">**Production:** How fast you can deploy and start your image.</span></span> <span data-ttu-id="2525b-127">Essa imagem é pequena, por isso ela pode trafegar rapidamente pela rede do seu Registro do Docker para os hosts do Docker.</span><span class="sxs-lookup"><span data-stu-id="2525b-127">This image is small so it can quickly travel across the network from your Docker Registry to your Docker hosts.</span></span> <span data-ttu-id="2525b-128">O conteúdo está pronto para ser executado e habilitar o tempo mais rápido possível da execução do Docker até o processamento de resultados.</span><span class="sxs-lookup"><span data-stu-id="2525b-128">The contents are ready to run enabling the fastest time from Docker run to processing results.</span></span> <span data-ttu-id="2525b-129">A compilação dinâmica do código não é necessária no modelo de Docker imutável.</span><span class="sxs-lookup"><span data-stu-id="2525b-129">In the immutable Docker model, there's no need for dynamic compilation of code.</span></span> <span data-ttu-id="2525b-130">O conteúdo colocado nesta imagem ficaria limitado aos binários e conteúdos necessários para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2525b-130">The content you place in this image would be limited to the binaries and content needed to run the application.</span></span> <span data-ttu-id="2525b-131">Por exemplo, a saída publicada usa `dotnet publish`, que contém os binários compilados, imagens, arquivos e arquivos.js e .css.</span><span class="sxs-lookup"><span data-stu-id="2525b-131">For example, the published output using `dotnet publish` which contains the compiled binaries, images, .js and .css files.</span></span> <span data-ttu-id="2525b-132">Com o passar do tempo, você verá imagens que contém pacotes pré-compilados com JIT.</span><span class="sxs-lookup"><span data-stu-id="2525b-132">Over time, you'll see images that contain pre-jitted packages.</span></span>  

<span data-ttu-id="2525b-133">Embora haja várias versões da imagem do .NET Core, todas elas compartilham uma ou mais camadas.</span><span class="sxs-lookup"><span data-stu-id="2525b-133">Though there are multiple versions of the .NET Core image, they all share one or more layers.</span></span> <span data-ttu-id="2525b-134">A quantidade de espaço em disco necessário para armazenar ou para o delta obter o Registro é muito menor do que no todo, pois todas as imagens compartilham a mesma camada base e potencialmente outras.</span><span class="sxs-lookup"><span data-stu-id="2525b-134">The amount of disk space needed to store or the delta to pull from your registry is much smaller than the whole because all of the images share the same base layer and potentially others.</span></span>  

## <a name="docker-image-variations"></a><span data-ttu-id="2525b-135">Variações de imagem do Docker</span><span class="sxs-lookup"><span data-stu-id="2525b-135">Docker image variations</span></span>

<span data-ttu-id="2525b-136">Para atingir os objetivos descritos acima, fornecemos variantes de imagem em [microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/).</span><span class="sxs-lookup"><span data-stu-id="2525b-136">To achieve the goals above, we provide image variants under [microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/).</span></span>

- <span data-ttu-id="2525b-137">`microsoft/dotnet:<version>-sdk`: isto é, **microsoft/dotnet:1.0.0-preview2-sdk**, essa imagem contém o SDK do .NET Core que inclui o .NET Core e a CLI (Ferramentas de Linha de Comando).</span><span class="sxs-lookup"><span data-stu-id="2525b-137">`microsoft/dotnet:<version>-sdk` : that is **microsoft/dotnet:1.0.0-preview2-sdk**, this image contains the .NET Core SDK which includes the .NET Core and Command Line Tools (CLI).</span></span> <span data-ttu-id="2525b-138">Essa imagem é mapeada para o **cenário de desenvolvimento**.</span><span class="sxs-lookup"><span data-stu-id="2525b-138">This image maps to the **development scenario**.</span></span> <span data-ttu-id="2525b-139">Ela seria usada para o desenvolvimento, depuração e teste de unidade local.</span><span class="sxs-lookup"><span data-stu-id="2525b-139">You would use this image for local development, debugging and unit testing.</span></span> <span data-ttu-id="2525b-140">Por exemplo, todo o desenvolvimento realizado antes de inserir o código.</span><span class="sxs-lookup"><span data-stu-id="2525b-140">For example, all the development you do, before you check in your code.</span></span> <span data-ttu-id="2525b-141">Essa imagem também pode ser usada para cenários **de build**.</span><span class="sxs-lookup"><span data-stu-id="2525b-141">This image can also be used for your **build** scenarios.</span></span>

- <span data-ttu-id="2525b-142">`microsoft/dotnet:<version>-core`: isto é, **microsoft/dotnet:1.0.0-core**, a imagem que executa [aplicativos .NET Core portáteis](../deploying/index.md) e é otimizada para executar seu aplicativo em **produção**.</span><span class="sxs-lookup"><span data-stu-id="2525b-142">`microsoft/dotnet:<version>-core` : that is **microsoft/dotnet:1.0.0-core**, image which runs [portable .NET Core applications](../deploying/index.md) and it is optimized for running your application in **production**.</span></span> <span data-ttu-id="2525b-143">Ela não contém o SDK e tem por objetivo levar a saída otimizada do `dotnet publish`.</span><span class="sxs-lookup"><span data-stu-id="2525b-143">It does not contain the SDK, and is meant to take the optimized output of `dotnet publish`.</span></span> <span data-ttu-id="2525b-144">O tempo de execução portátil é adequado para cenários de contêiner Docker, pois a execução de vários contêineres tira vantagem das camas de imagem compartilhadas.</span><span class="sxs-lookup"><span data-stu-id="2525b-144">The portable runtime is well suited for Docker container scenarios as running multiple containers benefit from shared image layers.</span></span>  

## <a name="alternative-images"></a><span data-ttu-id="2525b-145">Imagens alternativas</span><span class="sxs-lookup"><span data-stu-id="2525b-145">Alternative images</span></span>

<span data-ttu-id="2525b-146">Além dos cenários otimizados de desenvolvimento, build e produção, fornecemos imagens adicionais:</span><span class="sxs-lookup"><span data-stu-id="2525b-146">In addition to the optimized scenarios of development, build and production, we provide additional images:</span></span>

- <span data-ttu-id="2525b-147">`microsoft/dotnet:<version>-onbuild`: isto é, **microsoft/dotnet:1.0.0-preview2-onbuild**, contém gatilhos [ONBUILD](https://docs.docker.com/engine/reference/builder/#/onbuild).</span><span class="sxs-lookup"><span data-stu-id="2525b-147">`microsoft/dotnet:<version>-onbuild` : that is **microsoft/dotnet:1.0.0-preview2-onbuild**, contains [ONBUILD](https://docs.docker.com/engine/reference/builder/#/onbuild) triggers.</span></span> <span data-ttu-id="2525b-148">O build realizará a [COPY](https://docs.docker.com/engine/reference/builder/#/copy) do seu aplicativo, executará `dotnet restore` e criará uma instrução [ENTRYPOINT](https://docs.docker.com/engine/reference/builder/#/entrypoint) `dotnet run` para executar o aplicativo quando a imagem do Docker for executada.</span><span class="sxs-lookup"><span data-stu-id="2525b-148">The build will [COPY](https://docs.docker.com/engine/reference/builder/#/copy) your application, run `dotnet restore` and create an [ENTRYPOINT](https://docs.docker.com/engine/reference/builder/#/entrypoint) `dotnet run` instruction to run the application when the Docker image is run.</span></span> <span data-ttu-id="2525b-149">Embora não seja uma imagem otimizada para produção, ela pode ser útil para alguns simplesmente para copiar seu código-fonte em uma imagem e executá-lo.</span><span class="sxs-lookup"><span data-stu-id="2525b-149">While not an optimized image for production, some may find it useful to simply copy their source code into an image and run it.</span></span> 

- <span data-ttu-id="2525b-150">`microsoft/dotnet:<version>-core-deps`: isto é, **microsoft/dotnet:1.0.0-core-deps**, use essa imagem se você desejar executar os aplicativos autocontidos.</span><span class="sxs-lookup"><span data-stu-id="2525b-150">`microsoft/dotnet:<version>-core-deps` : that is **microsoft/dotnet:1.0.0-core-deps**, if you wish to run self-contained applications use this image.</span></span> <span data-ttu-id="2525b-151">Ela contém o sistema operacional com todas as dependências nativas exigidas pelo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2525b-151">It contains the operating system with all of the native dependencies needed by .NET Core.</span></span> <span data-ttu-id="2525b-152">Essa imagem também pode ser usada como uma imagem-base para suas próprias compilações CoreFX ou CoreCLR personalizadas.</span><span class="sxs-lookup"><span data-stu-id="2525b-152">This image can also be used as a base image for your own custom CoreFX or CoreCLR builds.</span></span> <span data-ttu-id="2525b-153">Enquanto a variante **onbuild** é otimizada para simplesmente colocar seu código em uma imagem e executá-lo, essa imagem é otimizada para ter apenas as dependências do sistema operacional necessárias para executar aplicativos .NET Core com o tempo de execução .NET empacotado com o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2525b-153">While the **onbuild** variant is optimized to simply place your code in an image and run it, this image is optimized to have only the operating system dependencies required to run .NET Core apps that have the .NET runtime packaged with the application.</span></span> <span data-ttu-id="2525b-154">Essa imagem geralmente não é otimizada para executar vários contêineres .NET Core no mesmo host, visto que cada imagem traz o tempo de execução do .NET Core dentro do aplicativo e as camadas de imagem não trazem qualquer benefício.</span><span class="sxs-lookup"><span data-stu-id="2525b-154">This image isn't generally optimized for running multiple .NET Core containers on the same host, as each image carries the .NET Core runtime within the application, and you will not benefit from image layering.</span></span>   

<span data-ttu-id="2525b-155">Versões mais recentes de cada variante:</span><span class="sxs-lookup"><span data-stu-id="2525b-155">Latest versions of each variant:</span></span>

- <span data-ttu-id="2525b-156">`microsoft/dotnet` ou `microsoft/dotnet:latest` (inclui o SDK)</span><span class="sxs-lookup"><span data-stu-id="2525b-156">`microsoft/dotnet` or `microsoft/dotnet:latest` (includes SDK)</span></span>
- `microsoft/dotnet:onbuild`
- `microsoft/dotnet:core`
- `microsoft/dotnet:core-deps`

<span data-ttu-id="2525b-157">Veja aqui uma lista das imagens após um `docker pull <imagename>` em um computador de desenvolvimento para mostrar os diversos tamanhos.</span><span class="sxs-lookup"><span data-stu-id="2525b-157">Here is a list of the images after a `docker pull <imagename>` on a development machine to show the various sizes.</span></span> <span data-ttu-id="2525b-158">Observe que a variante de desenvolvimento/compilação, `microsoft/dotnet:1.0.0-preview2-sdk`, é maior, pois contém o SDK para desenvolver e compilar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2525b-158">Notice, the development/build variant, `microsoft/dotnet:1.0.0-preview2-sdk` is larger as it contains the SDK to develop and build your application.</span></span> <span data-ttu-id="2525b-159">A variante de produção, `microsoft/dotnet:core`, é menor, pois contém apenas o tempo de execução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2525b-159">The production variant, `microsoft/dotnet:core` is smaller, as it only contains the .NET Core runtime.</span></span> <span data-ttu-id="2525b-160">A imagem mínima capaz de ser usada no Linux, `core-deps`, é muito menor, mas seu aplicativo precisará trazer uma cópia particular do tempo de execução .NET consigo.</span><span class="sxs-lookup"><span data-stu-id="2525b-160">The minimal image capable of being used on Linux, `core-deps`, is quite smaller, however your application will need to copy a private copy of the .NET runtime with it.</span></span> <span data-ttu-id="2525b-161">Como os contêineres já são barreiras de isolamento particular, você perderá essa otimização ao executar vários dotnet baseados em contêineres.</span><span class="sxs-lookup"><span data-stu-id="2525b-161">Since containers are already private isolation barriers, you will lose that optimization when running multiple dotnet based containers.</span></span> 

```
REPOSITORY          TAG                     IMAGE ID            SIZE
microsoft/dotnet    1.0.0-preview2-onbuild  19b6a6c4b1db        540.4 MB
microsoft/dotnet    onbuild                 19b6a6c4b1db        540.4 MB
microsoft/dotnet    1.0.0-preview2-sdk      a92c3d9ad0e7        540.4 MB
microsoft/dotnet    core                    5224a9f2a2aa        253.2 MB
microsoft/dotnet    1.0.0-core-deps         c981a2eebe0e        166.2 MB
microsoft/dotnet    core-deps               c981a2eebe0e        166.2 MB
microsoft/dotnet    latest                  03c10abbd08a        540.4 MB
microsoft/dotnet    1.0.0-core              b8da4a1fd280        253.2 MB
```

## <a name="prerequisites"></a><span data-ttu-id="2525b-162">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="2525b-162">Prerequisites</span></span>

<span data-ttu-id="2525b-163">Para compilar e executar, você precisará de alguns itens instalados:</span><span class="sxs-lookup"><span data-stu-id="2525b-163">To build and run, you'll need a few things installed:</span></span>

- [<span data-ttu-id="2525b-164">.NET Core</span><span class="sxs-lookup"><span data-stu-id="2525b-164">.NET Core</span></span>](http://dot.net)
- <span data-ttu-id="2525b-165">[Docker](https://www.docker.com/products/docker) para executar seus contêineres Docker localmente</span><span class="sxs-lookup"><span data-stu-id="2525b-165">[Docker](https://www.docker.com/products/docker) to run your Docker containers locally</span></span>
- [<span data-ttu-id="2525b-166">Node.js</span><span class="sxs-lookup"><span data-stu-id="2525b-166">Node.js</span></span>](https://nodejs.org/)
- <span data-ttu-id="2525b-167">[Gerador Yeoman para ASP.NET](https://github.com/omnisharp/generator-aspnet) para criar o aplicativo da API Web</span><span class="sxs-lookup"><span data-stu-id="2525b-167">[Yeoman generator for ASP.NET](https://github.com/omnisharp/generator-aspnet) for creating the Web API application</span></span>
- <span data-ttu-id="2525b-168">[Gerador Yeoman para Docker](http://aka.ms/yodocker) da Microsoft</span><span class="sxs-lookup"><span data-stu-id="2525b-168">[Yeoman generator for Docker](http://aka.ms/yodocker) from Microsoft</span></span>

<span data-ttu-id="2525b-169">Instale os geradores Yeoman para ASP.NET Core e Docker usando npm</span><span class="sxs-lookup"><span data-stu-id="2525b-169">Install the Yeoman generators for ASP.NET Core and Docker using npm</span></span> 

```
npm install -g yo generator-aspnet generator-docker
```

> [!NOTE]
> <span data-ttu-id="2525b-170">Este exemplo usará o [Visual Studio Code](http://code.visualstudio.com) como editor.</span><span class="sxs-lookup"><span data-stu-id="2525b-170">This sample will be using [Visual Studio Code](http://code.visualstudio.com) for the editor.</span></span>

## <a name="creating-the-web-api-application"></a><span data-ttu-id="2525b-171">Criando o aplicativo da API Web</span><span class="sxs-lookup"><span data-stu-id="2525b-171">Creating the Web API application</span></span>

<span data-ttu-id="2525b-172">Para um ponto de referência, antes de colocarmos o aplicativo em contêineres, primeiro devemos executá-lo localmente.</span><span class="sxs-lookup"><span data-stu-id="2525b-172">For a reference point, before we containerize the application, first run the application locally.</span></span> 

<span data-ttu-id="2525b-173">O aplicativo concluído está localizado no [repositório dotnet/docs no GitHub](https://github.com/dotnet/docs/tree/master/samples/core/docker/building-net-docker-images).</span><span class="sxs-lookup"><span data-stu-id="2525b-173">The finished application is located in the [dotnet/docs repository on GitHub](https://github.com/dotnet/docs/tree/master/samples/core/docker/building-net-docker-images).</span></span> <span data-ttu-id="2525b-174">Para obter instruções de download, consulte [Exemplos e tutoriais](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="2525b-174">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

<span data-ttu-id="2525b-175">Crie um diretório para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2525b-175">Create a directory for your application.</span></span>

<span data-ttu-id="2525b-176">Abra um comando ou sessão de terminal nesse diretório e use o gerador Yeoman do ASP.NET digitando o seguinte:</span><span class="sxs-lookup"><span data-stu-id="2525b-176">Open a command or terminal session in that directory and use the ASP.NET Yeoman generator by typing the following:</span></span>
```
yo aspnet
```

<span data-ttu-id="2525b-177">Selecione **Aplicativo da API Web** e digite **api** para o nome do aplicativo e pressione Enter.</span><span class="sxs-lookup"><span data-stu-id="2525b-177">Select **Web API Application** and type **api** for the name of the app and tap enter.</span></span>  <span data-ttu-id="2525b-178">Depois que o aplicativo é esboçado, mude para o diretório `/api` e restaure as dependências NuGet usando `dotnet restore`.</span><span class="sxs-lookup"><span data-stu-id="2525b-178">Once the application is scaffolded, change to the `/api` directory and restore the NuGet dependencies using `dotnet restore`.</span></span>

```
cd api
dotnet restore
```

<span data-ttu-id="2525b-179">Teste o aplicativo usando `dotnet run` e navegando até **http://localhost:5000/api/values**</span><span class="sxs-lookup"><span data-stu-id="2525b-179">Test the application using `dotnet run` and browsing to **http://localhost:5000/api/values**</span></span>

```javascript
[
    "value1",
    "value2"
]
```

<span data-ttu-id="2525b-180">Use `Ctrl+C` para interromper o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2525b-180">Use `Ctrl+C` to stop the application.</span></span>

## <a name="adding-docker-support"></a><span data-ttu-id="2525b-181">Adicionando suporte ao Docker</span><span class="sxs-lookup"><span data-stu-id="2525b-181">Adding Docker support</span></span>

<span data-ttu-id="2525b-182">A adição de suporte ao Docker para o projeto é realizada usando o gerador Yeoman da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="2525b-182">Adding Docker support to the project is achieved using the Yeoman generator from Microsoft.</span></span> <span data-ttu-id="2525b-183">No momento, ele dá suporte a projetos do .NET Core, Node.js e Go criando um Dockerfile e scripts que ajudam a criar e executar projetos dentro de contêineres.</span><span class="sxs-lookup"><span data-stu-id="2525b-183">It currently supports .NET Core, Node.js and Go projects by creating a Dockerfile and scripts that help build and run projects inside containers.</span></span> <span data-ttu-id="2525b-184">Arquivos específicos do Visual Studio Code também são adicionados (launch.json, tasks.json) para depuração do editor e suporte à paleta de comandos.</span><span class="sxs-lookup"><span data-stu-id="2525b-184">Visual Studio Code specific files are also added (launch.json, tasks.json) for editor debugging and command palette support.</span></span>

```console
$ yo docker

     _-----_     ╭──────────────────────────╮
    |       |    │   Welcome to the Docker  │
    |--(o)--|    │        generator!        │
   `---------´   │     Let's add Docker     │
    ( _´U`_ )    │  container magic to your │
    /___A___\   /│           app!           │
     |  ~  |     ╰──────────────────────────╯
   __'.___.'__
 ´   `  |° ´ Y `

? What language is your project using? (Use arrow keys)
❯ .NET Core
  Golang
  Node.js
```

- <span data-ttu-id="2525b-185">Selecione `.NET Core` como o tipo de projeto</span><span class="sxs-lookup"><span data-stu-id="2525b-185">Select `.NET Core` as the project type</span></span>
- <span data-ttu-id="2525b-186">`rtm` para a versão do .NET Core</span><span class="sxs-lookup"><span data-stu-id="2525b-186">`rtm` for the version of .NET Core</span></span>
- <span data-ttu-id="2525b-187">`Y` o projeto usa um servidor Web</span><span class="sxs-lookup"><span data-stu-id="2525b-187">`Y` the project uses a web server</span></span>
- <span data-ttu-id="2525b-188">`5000` é a porta que o aplicativo da API Web está escutando em (http://localhost:5000)</span><span class="sxs-lookup"><span data-stu-id="2525b-188">`5000` is the port the Web API application is listening on (http://localhost:5000)</span></span>
- <span data-ttu-id="2525b-189">`api` para o nome da imagem</span><span class="sxs-lookup"><span data-stu-id="2525b-189">`api` for the image name</span></span>
- <span data-ttu-id="2525b-190">`api` para o nome do serviço</span><span class="sxs-lookup"><span data-stu-id="2525b-190">`api` for the service name</span></span>
- <span data-ttu-id="2525b-191">`api` para o projeto de composição</span><span class="sxs-lookup"><span data-stu-id="2525b-191">`api` for the compose project</span></span> 
- <span data-ttu-id="2525b-192">`Y` para substituir o Dockerfile atual</span><span class="sxs-lookup"><span data-stu-id="2525b-192">`Y` to overwrite the current Dockerfile</span></span>

<span data-ttu-id="2525b-193">Quando o gerador estiver concluído, os seguintes arquivos são adicionados ao projeto</span><span class="sxs-lookup"><span data-stu-id="2525b-193">When the generator is complete, the following files are added to the project</span></span>

- <span data-ttu-id="2525b-194">.vscode/launch.json</span><span class="sxs-lookup"><span data-stu-id="2525b-194">.vscode/launch.json</span></span>
- <span data-ttu-id="2525b-195">Dockerfile.debug</span><span class="sxs-lookup"><span data-stu-id="2525b-195">Dockerfile.debug</span></span>
- <span data-ttu-id="2525b-196">Dockerfile</span><span class="sxs-lookup"><span data-stu-id="2525b-196">Dockerfile</span></span>
- <span data-ttu-id="2525b-197">docker-compose.debug.yml</span><span class="sxs-lookup"><span data-stu-id="2525b-197">docker-compose.debug.yml</span></span>
- <span data-ttu-id="2525b-198">docker-compose.yml</span><span class="sxs-lookup"><span data-stu-id="2525b-198">docker-compose.yml</span></span>
- <span data-ttu-id="2525b-199">dockerTask.ps1</span><span class="sxs-lookup"><span data-stu-id="2525b-199">dockerTask.ps1</span></span>
- <span data-ttu-id="2525b-200">dockerTask.sh</span><span class="sxs-lookup"><span data-stu-id="2525b-200">dockerTask.sh</span></span>
- <span data-ttu-id="2525b-201">.vscode/tasks.json</span><span class="sxs-lookup"><span data-stu-id="2525b-201">.vscode/tasks.json</span></span>

<span data-ttu-id="2525b-202">O gerador cria dois Dockerfiles.</span><span class="sxs-lookup"><span data-stu-id="2525b-202">The generator creates two Dockerfiles.</span></span>

<span data-ttu-id="2525b-203">**Dockerfile.Debug** – Este arquivo se baseia na imagem **microsoft/dotnet:1.0.0-preview2-sdk**, a qual podemos observar na lista de variantes que inclui o SDK, a CLI e o .NET Core, e será a imagem usada para desenvolvimento e depuração (F5).</span><span class="sxs-lookup"><span data-stu-id="2525b-203">**Dockerfile.debug** - this file is based on the **microsoft/dotnet:1.0.0-preview2-sdk** image which if you note from the list of image variants, includes the SDK, CLI and .NET Core and will be the image used for development and debugging (F5).</span></span> <span data-ttu-id="2525b-204">Incluir todos esses componentes gera uma imagem maior com um tamanho de aproximadamente 540 MB.</span><span class="sxs-lookup"><span data-stu-id="2525b-204">Including all of these components produces a larger image with a size roughly of 540MB.</span></span>

<span data-ttu-id="2525b-205">**Dockerfile** – Essa é a imagem de lançamento baseada em **microsoft/dotnet:1.0.0-core** e deve ser usada para produção.</span><span class="sxs-lookup"><span data-stu-id="2525b-205">**Dockerfile** - this image is the release image based on **microsoft/dotnet:1.0.0-core** and should be used for production.</span></span> <span data-ttu-id="2525b-206">Essa imagem compilada tem aproximadamente 253 MB.</span><span class="sxs-lookup"><span data-stu-id="2525b-206">This image when built is approximately 253 MB.</span></span>

### <a name="creating-the-docker-images"></a><span data-ttu-id="2525b-207">Criar as imagens do Docker</span><span class="sxs-lookup"><span data-stu-id="2525b-207">Creating the Docker images</span></span>
<span data-ttu-id="2525b-208">Usando o script `dockerTask.sh` ou `dockerTask.ps1`, podemos criar ou compor a imagem e o contêiner para o aplicativo **api** para um ambiente específico.</span><span class="sxs-lookup"><span data-stu-id="2525b-208">Using the `dockerTask.sh` or `dockerTask.ps1` script, we can build or compose the image and container for the **api** application for a specific environment.</span></span> <span data-ttu-id="2525b-209">Crie a imagem de **depuração** executando o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="2525b-209">Build the **debug** image by running the following command.</span></span>

```bash
./dockerTask.sh build debug
```

<span data-ttu-id="2525b-210">A imagem compilará o aplicativo ASP.NET, executará `dotnet restore`, adicionará o depurador à imagem, definirá um `ENTRYPOINT` e, por fim, copiará o aplicativo para a imagem.</span><span class="sxs-lookup"><span data-stu-id="2525b-210">The image will build the ASP.NET application, run `dotnet restore`, add the debugger to the image, set an `ENTRYPOINT` and finally copy the app to the image.</span></span> <span data-ttu-id="2525b-211">O resultado é uma imagem do Docker chamada *api* com um `TAG` de *depuração*.</span><span class="sxs-lookup"><span data-stu-id="2525b-211">The result is a Docker image named *api* with a `TAG` of *debug*.</span></span>  <span data-ttu-id="2525b-212">Veja as imagens no computador usando `docker images`.</span><span class="sxs-lookup"><span data-stu-id="2525b-212">See the images on the machine using `docker images`.</span></span>

```bash
docker images

REPOSITORY          TAG                  IMAGE ID            CREATED             SIZE
api                 debug                70e89fbc5dbe        a few seconds ago   779.8 MB
```

<span data-ttu-id="2525b-213">Outra maneira de gerar a imagem e executar o aplicativo dentro do contêiner Docker é abrir o aplicativo no Visual Studio Code e usar as ferramentas de depuração.</span><span class="sxs-lookup"><span data-stu-id="2525b-213">Another way to generate the image and run the application within the Docker container is to open the application in Visual Studio Code and use the debugging tools.</span></span> 

<span data-ttu-id="2525b-214">Escolha o ícone de depuração na Barra de Visões, no lado esquerdo do Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="2525b-214">Select the debugging icon in the View Bar on the left side of Visual Studio Code.</span></span>

![ícone de depuração vscode](./media/building-net-docker-images/debugging_debugicon.png)

<span data-ttu-id="2525b-216">Em seguida, toque no ícone de reprodução ou F5 para gerar a imagem e iniciar o aplicativo dentro do contêiner.</span><span class="sxs-lookup"><span data-stu-id="2525b-216">Then tap the play icon or F5 to generate the image and start the application within the container.</span></span> <span data-ttu-id="2525b-217">A API Web será iniciada usando seu navegador da Web padrão em http://localhost:5000.</span><span class="sxs-lookup"><span data-stu-id="2525b-217">The Web API will be launched using your default web browser at http://localhost:5000.</span></span>

![Depuração de Ferramentas do VSCode Docker](./media/building-net-docker-images/docker-tools-vscode-f5.png)

<span data-ttu-id="2525b-219">Você pode definir pontos de interrupção em seu aplicativo, percorrê-los, etc., como se o aplicativo fosse executado localmente em seu computador de desenvolvimento em vez de dentro do contêiner.</span><span class="sxs-lookup"><span data-stu-id="2525b-219">You may set break points in your application, step through, etc. just as if the application was running locally on your development machine as opposed to inside the container.</span></span> <span data-ttu-id="2525b-220">A vantagem da depuração dentro do contêiner é que essa é a mesma imagem que seria implantada em um ambiente de produção.</span><span class="sxs-lookup"><span data-stu-id="2525b-220">The benefit to debugging within the container is this is the same image that would be deployed to a production environment.</span></span>

<span data-ttu-id="2525b-221">Criar a imagem de lançamento ou de produção requer simplesmente executar o comando do terminal passando o nome do ambiente do `release`.</span><span class="sxs-lookup"><span data-stu-id="2525b-221">Creating the release or production image requires simply running the command from the terminal passing the `release` environment name.</span></span>

```bash
./dockerTask build release
```

<span data-ttu-id="2525b-222">O comando cria a imagem com base na menor imagem de base **microsoft / dotnet:core**, [EXPÕE](https://docs.docker.com/engine/reference/builder/#/expose) a porta 5000, define o [PONTO DE ENTRADA](https://docs.docker.com/engine/reference/builder/#/entrypoint) para `dotnet api.dll` e o copia para o diretório `/app`.</span><span class="sxs-lookup"><span data-stu-id="2525b-222">The command creates the image based on the smaller **microsoft/dotnet:core** base image, [EXPOSE](https://docs.docker.com/engine/reference/builder/#/expose) port 5000, sets the [ENTRYPOINT](https://docs.docker.com/engine/reference/builder/#/entrypoint) for `dotnet api.dll` and copies it to the `/app` directory.</span></span> <span data-ttu-id="2525b-223">Não há nenhum depurador, o SDK ou `dotnet restore`, resultando em uma imagem muito menor.</span><span class="sxs-lookup"><span data-stu-id="2525b-223">There is no debugger, SDK or `dotnet restore` resulting in a much smaller image.</span></span> <span data-ttu-id="2525b-224">A imagem é denominada **api** com um `TAG` de **mais recente**.</span><span class="sxs-lookup"><span data-stu-id="2525b-224">The image is named **api** with a `TAG` of **latest**.</span></span>

```
REPOSITORY          TAG                  IMAGE ID            CREATED             SIZE
api                 debug                70e89fbc5dbe        1 hour ago        779.8 MB
api                 latest               ef17184c8de6        1 hour ago        260.7 MB
```

## <a name="summary"></a><span data-ttu-id="2525b-225">Resumo</span><span class="sxs-lookup"><span data-stu-id="2525b-225">Summary</span></span>

<span data-ttu-id="2525b-226">Usando o gerador de Docker para adicionar os arquivos necessários ao aplicativo da API Web simplificou o processo de criar as versões de desenvolvimento e produção das imagens.</span><span class="sxs-lookup"><span data-stu-id="2525b-226">Using the Docker generator to add the necessary files to our Web API application made the process simple to create the development and production versions of the images.</span></span>  <span data-ttu-id="2525b-227">As ferramentas são plataforma cruzada, fornecendo também um script do PowerShell para obter os mesmos resultados no Windows, enquanto a integração do Visual Studio Code fornece um passo a passo de depuração do aplicativo dentro do contêiner.</span><span class="sxs-lookup"><span data-stu-id="2525b-227">The tooling is cross platform by also providing a PowerShell script to accomplish the same results on Windows and Visual Studio Code integration providing step through debugging of the application within the container.</span></span> <span data-ttu-id="2525b-228">Compreendendo as variantes de imagem e os cenários de destino, você pode otimizar seu processo de desenvolvimento de loop interno, obtendo imagens otimizadas para implantações de produção.</span><span class="sxs-lookup"><span data-stu-id="2525b-228">By understanding the image variants and the target scenarios, you can optimize your inner-loop development process, while achieving optimized images for production deployments.</span></span>  



