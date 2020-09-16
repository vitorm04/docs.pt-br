---
title: 'Tutorial: Colocar em contêiner um aplicativo com o Docker'
description: Neste tutorial, você aprenderá a colocar em contêiner um aplicativo .NET Core com o Docker.
ms.date: 04/27/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: b6775c760ef3f5bf1c9519430b038f149c9cf30f
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538495"
---
# <a name="tutorial-containerize-a-net-core-app"></a><span data-ttu-id="c8e12-103">Tutorial: colocar um aplicativo .NET Core em contêineres</span><span class="sxs-lookup"><span data-stu-id="c8e12-103">Tutorial: Containerize a .NET Core app</span></span>

<span data-ttu-id="c8e12-104">Neste tutorial, você aprenderá a colocar em contêiner um aplicativo .NET Core com o Docker.</span><span class="sxs-lookup"><span data-stu-id="c8e12-104">In this tutorial, you'll learn how to containerize a .NET Core application with Docker.</span></span> <span data-ttu-id="c8e12-105">Os contêineres têm muitos recursos e benefícios, como uma infraestrutura imutável, fornecendo uma arquitetura portátil e habilitando a escalabilidade.</span><span class="sxs-lookup"><span data-stu-id="c8e12-105">Containers have many features and benefits, such as being an immutable infrastructure, providing a portable architecture, and enabling scalability.</span></span> <span data-ttu-id="c8e12-106">A imagem pode ser usada para criar contêineres para seu ambiente de desenvolvimento local, nuvem privada ou nuvem pública.</span><span class="sxs-lookup"><span data-stu-id="c8e12-106">The image can be used to create containers for your local development environment, private cloud, or public cloud.</span></span>

<span data-ttu-id="c8e12-107">Neste tutorial, você:</span><span class="sxs-lookup"><span data-stu-id="c8e12-107">In this tutorial, you:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="c8e12-108">Criar e publicar um aplicativo .NET Core simples</span><span class="sxs-lookup"><span data-stu-id="c8e12-108">Create and publish a simple .NET Core app</span></span>
> - <span data-ttu-id="c8e12-109">Criar e configurar um Dockerfile para .NET Core</span><span class="sxs-lookup"><span data-stu-id="c8e12-109">Create and configure a Dockerfile for .NET Core</span></span>
> - <span data-ttu-id="c8e12-110">Compilar uma imagem do docker</span><span class="sxs-lookup"><span data-stu-id="c8e12-110">Build a Docker image</span></span>
> - <span data-ttu-id="c8e12-111">Criar e executar um contêiner do Docker</span><span class="sxs-lookup"><span data-stu-id="c8e12-111">Create and run a Docker container</span></span>

<span data-ttu-id="c8e12-112">Você aprenderá as tarefas de build e implantação de contêiner do Docker para um aplicativo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c8e12-112">You'll understand the Docker container build and deploy tasks for a .NET Core application.</span></span> <span data-ttu-id="c8e12-113">A *plataforma Docker* usa o *Mecanismo do Docker* para criar e empacotar aplicativos como *imagens do Docker* com agilidade.</span><span class="sxs-lookup"><span data-stu-id="c8e12-113">The *Docker platform* uses the *Docker engine* to quickly build and package apps as *Docker images*.</span></span> <span data-ttu-id="c8e12-114">Essas imagens são gravadas no formato *Dockerfile* para serem implantadas e executadas em um contêiner em camadas.</span><span class="sxs-lookup"><span data-stu-id="c8e12-114">These images are written in the *Dockerfile* format to be deployed and run in a layered container.</span></span>

> [!NOTE]
> <span data-ttu-id="c8e12-115">Este tutorial **não é** para aplicativos ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="c8e12-115">This tutorial **is not** for ASP.NET Core apps.</span></span> <span data-ttu-id="c8e12-116">Se você estiver usando ASP.NET Core, consulte o tutorial [saiba como colocar um aplicativo em contêineres de ASP.NET Core](/aspnet/core/host-and-deploy/docker/building-net-docker-images) .</span><span class="sxs-lookup"><span data-stu-id="c8e12-116">If you're using ASP.NET Core, see the [Learn how to containerize an ASP.NET Core application](/aspnet/core/host-and-deploy/docker/building-net-docker-images) tutorial.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c8e12-117">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="c8e12-117">Prerequisites</span></span>

<span data-ttu-id="c8e12-118">Instale os seguintes pré-requisitos:</span><span class="sxs-lookup"><span data-stu-id="c8e12-118">Install the following prerequisites:</span></span>

- <span data-ttu-id="c8e12-119">[SDK do .NET Core 3,1](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="c8e12-119">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download)</span></span>\
<span data-ttu-id="c8e12-120">Se você tiver o .NET Core instalado, use o comando `dotnet --info` para determinar qual SDK está usando.</span><span class="sxs-lookup"><span data-stu-id="c8e12-120">If you have .NET Core installed, use the `dotnet --info` command to determine which SDK you're using.</span></span>
- [<span data-ttu-id="c8e12-121">Docking Community Edition</span><span class="sxs-lookup"><span data-stu-id="c8e12-121">Docker Community Edition</span></span>](https://www.docker.com/products/docker-desktop)
- <span data-ttu-id="c8e12-122">Uma pasta de trabalho temporária para o *Dockerfile* e o aplicativo de exemplo do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c8e12-122">A temporary working folder for the *Dockerfile* and .NET Core example app.</span></span> <span data-ttu-id="c8e12-123">Neste tutorial, o nome *Docker – Working* é usado como a pasta de trabalho.</span><span class="sxs-lookup"><span data-stu-id="c8e12-123">In this tutorial, the name *docker-working* is used as the working folder.</span></span>

## <a name="create-net-core-app"></a><span data-ttu-id="c8e12-124">Criar aplicativo .NET Core</span><span class="sxs-lookup"><span data-stu-id="c8e12-124">Create .NET Core app</span></span>

<span data-ttu-id="c8e12-125">Você precisa de um aplicativo .NET Core que o contêiner do Docker irá executar.</span><span class="sxs-lookup"><span data-stu-id="c8e12-125">You need a .NET Core app that the Docker container will run.</span></span> <span data-ttu-id="c8e12-126">Abra seu terminal, crie uma pasta de trabalho se você ainda não fez isso e entre nela.</span><span class="sxs-lookup"><span data-stu-id="c8e12-126">Open your terminal, create a working folder if you haven't already, and enter it.</span></span> <span data-ttu-id="c8e12-127">Na pasta de trabalho, execute o seguinte comando para criar um novo projeto em um subdiretório chamado *app*:</span><span class="sxs-lookup"><span data-stu-id="c8e12-127">In the working folder, run the following command to create a new project in a subdirectory named *app*:</span></span>

```dotnetcli
dotnet new console -o App -n NetCore.Docker
```

<span data-ttu-id="c8e12-128">A árvore de pastas terá aparência semelhante à seguinte:</span><span class="sxs-lookup"><span data-stu-id="c8e12-128">Your folder tree will look like the following:</span></span>

```
docker-working
    └──App
        ├──NetCore.Docker.csproj
        ├──Program.cs
        └──obj
            ├──NetCore.Docker.csproj.nuget.dgspec.json
            ├──NetCore.Docker.csproj.nuget.g.props
            ├──NetCore.Docker.csproj.nuget.g.targets
            ├──project.assets.json
            └──project.nuget.cache
```

<span data-ttu-id="c8e12-129">O `dotnet new` comando cria uma nova pasta chamada *app* e gera um aplicativo de console "Olá, mundo".</span><span class="sxs-lookup"><span data-stu-id="c8e12-129">The `dotnet new` command creates a new folder named *App* and generates a "Hello World" console application.</span></span> <span data-ttu-id="c8e12-130">Altere os diretórios e navegue até a pasta do *aplicativo* de sua sessão de terminal.</span><span class="sxs-lookup"><span data-stu-id="c8e12-130">Change directories and navigate into the *App* folder, from your terminal session.</span></span> <span data-ttu-id="c8e12-131">Use o `dotnet run` comando para iniciar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c8e12-131">Use the `dotnet run` command to start the app.</span></span> <span data-ttu-id="c8e12-132">O aplicativo será executado e imprimirá `Hello World!` abaixo do comando:</span><span class="sxs-lookup"><span data-stu-id="c8e12-132">The application will run, and print `Hello World!` below the command:</span></span>

```dotnetcli
dotnet run
Hello World!
```

<span data-ttu-id="c8e12-133">O modelo padrão cria um aplicativo que é impresso no terminal e, em seguida, termina imediatamente.</span><span class="sxs-lookup"><span data-stu-id="c8e12-133">The default template creates an app that prints to the terminal and then immediately terminates.</span></span> <span data-ttu-id="c8e12-134">Neste tutorial, você usará um aplicativo que faz um loop indefinidamente.</span><span class="sxs-lookup"><span data-stu-id="c8e12-134">For this tutorial, you'll use an app that loops indefinitely.</span></span> <span data-ttu-id="c8e12-135">Abra o arquivo *Program.cs* em um editor de texto.</span><span class="sxs-lookup"><span data-stu-id="c8e12-135">Open the *Program.cs* file in a text editor.</span></span>

> [!TIP]
> <span data-ttu-id="c8e12-136">Se você estiver usando Visual Studio Code, na sessão de terminal anterior, digite o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="c8e12-136">If you're using Visual Studio Code, from the previous terminal session type the following command:</span></span>
>
> ```console
> code .
> ```
>
> <span data-ttu-id="c8e12-137">Isso abrirá a pasta do *aplicativo* que contém o projeto no Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="c8e12-137">This will open the *App* folder that contains the project in Visual Studio Code.</span></span>

<span data-ttu-id="c8e12-138">O *Program.cs* deve ser semelhante ao seguinte código C#:</span><span class="sxs-lookup"><span data-stu-id="c8e12-138">The *Program.cs* should look like the following C# code:</span></span>

```csharp
using System;

namespace NetCore.Docker
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

<span data-ttu-id="c8e12-139">Substitua o arquivo pelo seguinte código que conta os números a cada segundo:</span><span class="sxs-lookup"><span data-stu-id="c8e12-139">Replace the file with the following code that counts numbers every second:</span></span>

```csharp
using System;
using System.Threading.Tasks;

namespace NetCore.Docker
{
    class Program
    {
        static async Task Main(string[] args)
        {
            var counter = 0;
            var max = args.Length != 0 ? Convert.ToInt32(args[0]) : -1;
            while (max == -1 || counter < max)
            {
                Console.WriteLine($"Counter: {++counter}");
                await Task.Delay(1000);
            }
        }
    }
}
```

<span data-ttu-id="c8e12-140">Salve o arquivo e teste o programa novamente com `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="c8e12-140">Save the file and test the program again with `dotnet run`.</span></span> <span data-ttu-id="c8e12-141">Lembre-se de que esse aplicativo é executado indefinidamente.</span><span class="sxs-lookup"><span data-stu-id="c8e12-141">Remember that this app runs indefinitely.</span></span> <span data-ttu-id="c8e12-142">Use o comando Cancel <kbd>Ctrl + C</kbd> para interrompê-lo.</span><span class="sxs-lookup"><span data-stu-id="c8e12-142">Use the cancel command <kbd>Ctrl+C</kbd> to stop it.</span></span> <span data-ttu-id="c8e12-143">Veja a seguir um exemplo de saída:</span><span class="sxs-lookup"><span data-stu-id="c8e12-143">The following is an example output:</span></span>

```dotnetcli
dotnet run
Counter: 1
Counter: 2
Counter: 3
Counter: 4
^C
```

<span data-ttu-id="c8e12-144">Se você passar um número na linha de comando para o aplicativo, ele apenas contará até tal valor e, em seguida, sairá.</span><span class="sxs-lookup"><span data-stu-id="c8e12-144">If you pass a number on the command line to the app, it will only count up to that amount and then exit.</span></span> <span data-ttu-id="c8e12-145">Experimente com `dotnet run -- 5` para contar até cinco.</span><span class="sxs-lookup"><span data-stu-id="c8e12-145">Try it with `dotnet run -- 5` to count to five.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c8e12-146">Quaisquer parâmetros após `--` não são passados para o comando `dotnet run` e, em vez disso, são passados para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c8e12-146">Any parameters after `--` are not passed to the `dotnet run` command and instead are passed to your application.</span></span>

## <a name="publish-net-core-app"></a><span data-ttu-id="c8e12-147">Publicar um aplicativo .NET Core</span><span class="sxs-lookup"><span data-stu-id="c8e12-147">Publish .NET Core app</span></span>

<span data-ttu-id="c8e12-148">Antes de adicionar o aplicativo .NET Core à imagem do Docker, primeiro ele deve ser publicado.</span><span class="sxs-lookup"><span data-stu-id="c8e12-148">Before adding the .NET Core app to the Docker image, first it must be published.</span></span> <span data-ttu-id="c8e12-149">É melhor fazer com que o contêiner execute a versão publicada do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c8e12-149">It is best to have the container run the published version of the app.</span></span> <span data-ttu-id="c8e12-150">Para publicar o aplicativo, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="c8e12-150">To publish the app, run the following command:</span></span>

```dotnetcli
dotnet publish -c Release
```

<span data-ttu-id="c8e12-151">Esse comando compila seu aplicativo para a pasta *publish*.</span><span class="sxs-lookup"><span data-stu-id="c8e12-151">This command compiles your app to the *publish* folder.</span></span> <span data-ttu-id="c8e12-152">O caminho para a pasta *publish* da pasta de trabalho deve ser `.\App\bin\Release\netcoreapp3.1\publish\`</span><span class="sxs-lookup"><span data-stu-id="c8e12-152">The path to the *publish* folder from the working folder should be `.\App\bin\Release\netcoreapp3.1\publish\`</span></span>

#### <a name="windows"></a>[<span data-ttu-id="c8e12-153">Windows</span><span class="sxs-lookup"><span data-stu-id="c8e12-153">Windows</span></span>](#tab/windows)

<span data-ttu-id="c8e12-154">Na pasta do *aplicativo* , obtenha uma listagem de diretório da pasta de publicação para verificar se o arquivo de *NetCore.Docker.dll* foi criado.</span><span class="sxs-lookup"><span data-stu-id="c8e12-154">From the *App* folder, get a directory listing of the publish folder to verify that the *NetCore.Docker.dll* file was created.</span></span>

```powershell
dir .\bin\Release\netcoreapp3.1\publish\

    Directory: C:\Users\dapine\App\bin\Release\netcoreapp3.1\publish

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        4/27/2020   8:27 AM            434 NetCore.Docker.deps.json
-a----        4/27/2020   8:27 AM           6144 NetCore.Docker.dll
-a----        4/27/2020   8:27 AM         171520 NetCore.Docker.exe
-a----        4/27/2020   8:27 AM            860 NetCore.Docker.pdb
-a----        4/27/2020   8:27 AM            154 NetCore.Docker.runtimeconfig.json
```

#### <a name="linux"></a>[<span data-ttu-id="c8e12-155">Linux</span><span class="sxs-lookup"><span data-stu-id="c8e12-155">Linux</span></span>](#tab/linux)

<span data-ttu-id="c8e12-156">Use o `ls` comando para obter uma listagem de diretório e verificar se o arquivo de *NetCore.Docker.dll* foi criado.</span><span class="sxs-lookup"><span data-stu-id="c8e12-156">Use the `ls` command to get a directory listing and verify that the *NetCore.Docker.dll* file was created.</span></span>

```bash
me@DESKTOP:/docker-working/app$ ls bin/Release/netcoreapp3.1/publish
NetCore.Docker.deps.json  NetCore.Docker.dll  NetCore.Docker.pdb  NetCore.Docker.runtimeconfig.json
```

---

## <a name="create-the-dockerfile"></a><span data-ttu-id="c8e12-157">Criar o Dockerfile</span><span class="sxs-lookup"><span data-stu-id="c8e12-157">Create the Dockerfile</span></span>

<span data-ttu-id="c8e12-158">O arquivo *Dockerfile* é usado pelo comando `docker build` para criar uma imagem de contêiner.</span><span class="sxs-lookup"><span data-stu-id="c8e12-158">The *Dockerfile* file is used by the `docker build` command to create a container image.</span></span> <span data-ttu-id="c8e12-159">Esse arquivo é um arquivo de texto chamado *Dockerfile* que não tem uma extensão.</span><span class="sxs-lookup"><span data-stu-id="c8e12-159">This file is a text file named *Dockerfile* that doesn't have an extension.</span></span>

<span data-ttu-id="c8e12-160">Crie um arquivo chamado *Dockerfile* no diretório que contém o *. csproj* e abra-o em um editor de texto.</span><span class="sxs-lookup"><span data-stu-id="c8e12-160">Create a file named *Dockerfile* in directory containing the *.csproj* and open it in a text editor.</span></span> <span data-ttu-id="c8e12-161">Este tutorial usará a imagem do ASP.NET Core Runtime (que contém a imagem do tempo de execução do .NET Core) e corresponde ao aplicativo de console do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c8e12-161">This tutorial will use the ASP.NET Core runtime image (which contains the .NET Core runtime image) and corresponds with the .NET Core console application.</span></span>

```dockerfile
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
```

> [!NOTE]
> <span data-ttu-id="c8e12-162">A imagem de tempo de execução ASP.NET Core é usada intencionalmente aqui, embora a `mcr.microsoft.com/dotnet/core/runtime:3.1` imagem possa ter sido usada.</span><span class="sxs-lookup"><span data-stu-id="c8e12-162">The ASP.NET Core runtime image is used intentionally here, although the `mcr.microsoft.com/dotnet/core/runtime:3.1` image could have been used.</span></span>

<span data-ttu-id="c8e12-163">A `FROM` palavra-chave requer um nome de imagem de contêiner do Docker totalmente qualificado.</span><span class="sxs-lookup"><span data-stu-id="c8e12-163">The `FROM` keyword requires a fully qualified Docker container image name.</span></span> <span data-ttu-id="c8e12-164">O registro de contêiner da Microsoft (MCR, mcr.microsoft.com) é uma agregação do Hub do Docker, que hospeda contêineres publicamente acessíveis.</span><span class="sxs-lookup"><span data-stu-id="c8e12-164">The Microsoft Container Registry (MCR, mcr.microsoft.com) is a syndicate of Docker Hub - which hosts publicly accessible containers.</span></span> <span data-ttu-id="c8e12-165">O `dotnet/core` segmento é o repositório de contêiner, onde o `aspnet` segmento é o nome da imagem de contêiner.</span><span class="sxs-lookup"><span data-stu-id="c8e12-165">The `dotnet/core` segment is the container repository, where as the `aspnet` segment is the container image name.</span></span> <span data-ttu-id="c8e12-166">A imagem é marcada com `3.1` , que é usada para controle de versão.</span><span class="sxs-lookup"><span data-stu-id="c8e12-166">The image is tagged with `3.1`, which is used for versioning.</span></span> <span data-ttu-id="c8e12-167">Portanto, `mcr.microsoft.com/dotnet/core/aspnet:3.1` é o tempo de execução do .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="c8e12-167">Thus, `mcr.microsoft.com/dotnet/core/aspnet:3.1` is the .NET Core 3.1 runtime.</span></span> <span data-ttu-id="c8e12-168">Certifique-se de extrair a versão de tempo de execução que corresponde ao tempo de execução direcionado pelo seu SDK.</span><span class="sxs-lookup"><span data-stu-id="c8e12-168">Make sure that you pull the runtime version that matches the runtime targeted by your SDK.</span></span> <span data-ttu-id="c8e12-169">Por exemplo, o aplicativo criado na seção anterior usava o SDK do .NET Core 3,1 e a imagem base mencionada no *Dockerfile* é marcada com **3,1**.</span><span class="sxs-lookup"><span data-stu-id="c8e12-169">For example, the app created in the previous section used the .NET Core 3.1 SDK and the base image referred to in the *Dockerfile* is tagged with **3.1**.</span></span>

<span data-ttu-id="c8e12-170">Salve o arquivo *Dockerfile*.</span><span class="sxs-lookup"><span data-stu-id="c8e12-170">Save the *Dockerfile* file.</span></span> <span data-ttu-id="c8e12-171">A estrutura de diretório da pasta de trabalho deve ser semelhante à mostrada a seguir.</span><span class="sxs-lookup"><span data-stu-id="c8e12-171">The directory structure of the working folder should look like the following.</span></span> <span data-ttu-id="c8e12-172">Alguns arquivos e pastas de nível mais profundo foram omitidos para economizar espaço no artigo:</span><span class="sxs-lookup"><span data-stu-id="c8e12-172">Some of the deeper-level files and folders have been omitted to save space in the article:</span></span>

```
docker-working
    └──App
        ├──Dockerfile
        ├──NetCore.Docker.csproj
        ├──Program.cs
        ├──bin
        │   └──Release
        │       └──netcoreapp3.1
        │           └──publish
        │               ├──NetCore.Docker.deps.json
        │               ├──NetCore.Docker.exe
        │               ├──NetCore.Docker.dll
        │               ├──NetCore.Docker.pdb
        │               └──NetCore.Docker.runtimeconfig.json
        └──obj
            └──...
```

<span data-ttu-id="c8e12-173">Do terminal, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="c8e12-173">From your terminal, run the following command:</span></span>

```console
docker build -t counter-image -f Dockerfile .
```

<span data-ttu-id="c8e12-174">O Docker processará cada linha no *Dockerfile*.</span><span class="sxs-lookup"><span data-stu-id="c8e12-174">Docker will process each line in the *Dockerfile*.</span></span> <span data-ttu-id="c8e12-175">O `.` no comando `docker build` instrui o Docker a usar a pasta atual para encontrar um *Dockerfile*.</span><span class="sxs-lookup"><span data-stu-id="c8e12-175">The `.` in the `docker build` command tells Docker to use the current folder to find a *Dockerfile*.</span></span> <span data-ttu-id="c8e12-176">Esse comando cria a imagem e cria um repositório local chamado **Counter-Image** que aponta para essa imagem.</span><span class="sxs-lookup"><span data-stu-id="c8e12-176">This command builds the image and creates a local repository named **counter-image** that points to that image.</span></span> <span data-ttu-id="c8e12-177">Após a conclusão desse comando, execute `docker images` para ver uma lista de imagens instaladas:</span><span class="sxs-lookup"><span data-stu-id="c8e12-177">After this command finishes, run `docker images` to see a list of images installed:</span></span>

```console
docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
counter-image                           latest              e6780479db63        4 days ago          190MB
mcr.microsoft.com/dotnet/core/aspnet    3.1                 e6780479db63        4 days ago          190MB
```

<span data-ttu-id="c8e12-178">Observe que as duas imagens compartilham o mesmo valor de **ID DA IMAGEM**.</span><span class="sxs-lookup"><span data-stu-id="c8e12-178">Notice that the two images share the same **IMAGE ID** value.</span></span> <span data-ttu-id="c8e12-179">O valor é o mesmo entre as duas imagens porque o único comando no *Dockerfile* era basear a nova imagem em uma imagem existente.</span><span class="sxs-lookup"><span data-stu-id="c8e12-179">The value is the same between both images because the only command in the *Dockerfile* was to base the new image on an existing image.</span></span> <span data-ttu-id="c8e12-180">Vamos adicionar três comandos ao *Dockerfile*.</span><span class="sxs-lookup"><span data-stu-id="c8e12-180">Let's add three commands to the *Dockerfile*.</span></span> <span data-ttu-id="c8e12-181">Cada comando cria uma nova camada de imagem com o comando final que representa os pontos de entrada do repositório de **imagem de contador** para.</span><span class="sxs-lookup"><span data-stu-id="c8e12-181">Each command creates a new image layer with the final command representing the **counter-image** repository entry points to.</span></span>

```dockerfile
COPY bin/Release/netcoreapp3.1/publish/ App/
WORKDIR /App
ENTRYPOINT ["dotnet", "NetCore.Docker.dll"]
```

<span data-ttu-id="c8e12-182">O comando `COPY` informa ao Docker para copiar a pasta especificada em seu computador para uma pasta no contêiner.</span><span class="sxs-lookup"><span data-stu-id="c8e12-182">The `COPY` command tells Docker to copy the specified folder on your computer to a folder in the container.</span></span> <span data-ttu-id="c8e12-183">Neste exemplo, a pasta de *publicação* é copiada para uma pasta chamada *aplicativo* no contêiner.</span><span class="sxs-lookup"><span data-stu-id="c8e12-183">In this example, the *publish* folder is copied to a folder named *App* in the container.</span></span>

<span data-ttu-id="c8e12-184">O `WORKDIR` comando altera o **diretório atual** dentro do contêiner para o *aplicativo*.</span><span class="sxs-lookup"><span data-stu-id="c8e12-184">The `WORKDIR` command changes the **current directory** inside of the container to *App*.</span></span>

<span data-ttu-id="c8e12-185">O comando seguinte, `ENTRYPOINT`, informa ao Docker para configurar o contêiner para ser executado como um executável.</span><span class="sxs-lookup"><span data-stu-id="c8e12-185">The next command, `ENTRYPOINT`, tells Docker to configure the container to run as an executable.</span></span> <span data-ttu-id="c8e12-186">Quando o contêiner é iniciado, o comando `ENTRYPOINT` é executado.</span><span class="sxs-lookup"><span data-stu-id="c8e12-186">When the container starts, the `ENTRYPOINT` command runs.</span></span> <span data-ttu-id="c8e12-187">Quando esse comando terminar, o contêiner será interrompido automaticamente.</span><span class="sxs-lookup"><span data-stu-id="c8e12-187">When this command ends, the container will automatically stop.</span></span>

<span data-ttu-id="c8e12-188">No seu terminal, execute `docker build -t counter-image -f Dockerfile .` e, quando o comando terminar, execute `docker images`.</span><span class="sxs-lookup"><span data-stu-id="c8e12-188">From your terminal, run `docker build -t counter-image -f Dockerfile .` and when that command finishes, run `docker images`.</span></span>

```console
docker build -t counter-image -f Dockerfile .
Sending build context to Docker daemon  1.117MB
Step 1/4 : FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
 ---> e6780479db63
Step 2/4 : COPY bin/Release/netcoreapp3.1/publish/ App/
 ---> d1732740eed2
Step 3/4 : WORKDIR /App
 ---> Running in b1701a42f3ff
Removing intermediate container b1701a42f3ff
 ---> 919aab5b95e3
Step 4/4 : ENTRYPOINT ["dotnet", "NetCore.Docker.dll"]
 ---> Running in c12aebd26ced
Removing intermediate container c12aebd26ced
 ---> cd11c3df9b19
Successfully built cd11c3df9b19
Successfully tagged counter-image:latest

docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
counter-image                           latest              cd11c3df9b19        41 seconds ago      190MB
mcr.microsoft.com/dotnet/core/aspnet    3.1                 e6780479db63        4 days ago          190MB
```

<span data-ttu-id="c8e12-189">Cada comando no *Dockerfile* gerou uma camada e criou uma **ID DA IMAGEM**.</span><span class="sxs-lookup"><span data-stu-id="c8e12-189">Each command in the *Dockerfile* generated a layer and created an **IMAGE ID**.</span></span> <span data-ttu-id="c8e12-190">A **ID da imagem** final (a sua será diferente) é **cd11c3df9b19** e, em seguida, você criará um contêiner com base nessa imagem.</span><span class="sxs-lookup"><span data-stu-id="c8e12-190">The final **IMAGE ID** (yours will be different) is **cd11c3df9b19** and next you'll create a container based on this image.</span></span>

## <a name="create-a-container"></a><span data-ttu-id="c8e12-191">Criar um contêiner</span><span class="sxs-lookup"><span data-stu-id="c8e12-191">Create a container</span></span>

<span data-ttu-id="c8e12-192">Agora que você tem uma imagem que contém o seu aplicativo, você pode criar um contêiner.</span><span class="sxs-lookup"><span data-stu-id="c8e12-192">Now that you have an image that contains your app, you can create a container.</span></span> <span data-ttu-id="c8e12-193">Você pode criar um contêiner de duas maneiras.</span><span class="sxs-lookup"><span data-stu-id="c8e12-193">You can create a container in two ways.</span></span> <span data-ttu-id="c8e12-194">Primeiro, criar um novo contêiner que foi interrompido.</span><span class="sxs-lookup"><span data-stu-id="c8e12-194">First, create a new container that is stopped.</span></span>

```console
docker create --name core-counter counter-image
0f281cb3af994fba5d962cc7d482828484ea14ead6bfe386a35e5088c0058851
```

<span data-ttu-id="c8e12-195">O `docker create` comando acima criará um contêiner com base na imagem do **contador-imagem** .</span><span class="sxs-lookup"><span data-stu-id="c8e12-195">The `docker create` command from above will create a container based on the **counter-image** image.</span></span> <span data-ttu-id="c8e12-196">A saída desse comando mostra a **ID DO CONTÊINER** (a sua será diferente) do contêiner criado.</span><span class="sxs-lookup"><span data-stu-id="c8e12-196">The output of that command shows you the **CONTAINER ID** (yours will be different) of the created container.</span></span> <span data-ttu-id="c8e12-197">Para ver uma lista de *todos* os contêineres, use o comando `docker ps -a`:</span><span class="sxs-lookup"><span data-stu-id="c8e12-197">To see a list of *all* containers, use the `docker ps -a` command:</span></span>

```console
docker ps -a
CONTAINER ID    IMAGE            COMMAND                   CREATED           STATUS     PORTS    NAMES
0f281cb3af99    counter-image    "dotnet NetCore.Dock…"    40 seconds ago    Created             core-counter
```

### <a name="manage-the-container"></a><span data-ttu-id="c8e12-198">Gerenciar o contêiner</span><span class="sxs-lookup"><span data-stu-id="c8e12-198">Manage the container</span></span>

<span data-ttu-id="c8e12-199">O contêiner foi criado com um nome específico `core-counter` , esse nome é usado para gerenciar o contêiner.</span><span class="sxs-lookup"><span data-stu-id="c8e12-199">The container was created with a specific name `core-counter`, this name is used to manage the container.</span></span> <span data-ttu-id="c8e12-200">O exemplo a seguir usa o comando `docker start` para iniciar o contêiner e, em seguida, usa o comando `docker ps` para mostrar apenas os contêineres em execução:</span><span class="sxs-lookup"><span data-stu-id="c8e12-200">The following example uses the `docker start` command to start the container, and then uses the `docker ps` command to only show containers that are running:</span></span>

```console
docker start core-counter
core-counter

docker ps
CONTAINER ID    IMAGE            COMMAND                   CREATED          STATUS          PORTS    NAMES
2f6424a7ddce    counter-image    "dotnet NetCore.Dock…"    2 minutes ago    Up 11 seconds            core-counter
```

<span data-ttu-id="c8e12-201">Da mesma forma, o comando `docker stop` interromperá o contêiner.</span><span class="sxs-lookup"><span data-stu-id="c8e12-201">Similarly, the `docker stop` command will stop the container.</span></span> <span data-ttu-id="c8e12-202">O exemplo a seguir usa o `docker stop` comando para parar o contêiner e, em seguida, usa o `docker ps` comando para mostrar que nenhum contêiner está em execução:</span><span class="sxs-lookup"><span data-stu-id="c8e12-202">The following example uses the `docker stop` command to stop the container, and then uses the `docker ps` command to show that no containers are running:</span></span>

```console
docker stop core-counter
core-counter

docker ps
CONTAINER ID    IMAGE    COMMAND    CREATED    STATUS    PORTS    NAMES
```

### <a name="connect-to-a-container"></a><span data-ttu-id="c8e12-203">Conectar-se a um contêiner</span><span class="sxs-lookup"><span data-stu-id="c8e12-203">Connect to a container</span></span>

<span data-ttu-id="c8e12-204">Depois que um contêiner estiver em execução, você poderá se conectar a ele para ver a saída.</span><span class="sxs-lookup"><span data-stu-id="c8e12-204">After a container is running, you can connect to it to see the output.</span></span> <span data-ttu-id="c8e12-205">Use os comandos `docker start` e `docker attach` para iniciar o contêiner e inspecionar o fluxo de saída.</span><span class="sxs-lookup"><span data-stu-id="c8e12-205">Use the `docker start` and `docker attach` commands to start the container and peek at the output stream.</span></span> <span data-ttu-id="c8e12-206">Neste exemplo, a tecla <kbd>Ctrl + C</kbd> é usada para desanexar do contêiner em execução.</span><span class="sxs-lookup"><span data-stu-id="c8e12-206">In this example, the <kbd>Ctrl+C</kbd> keystroke is used to detach from the running container.</span></span> <span data-ttu-id="c8e12-207">Esse pressionamento de teclas encerrará o processo no contêiner, a menos que especificado de outra forma, o que interromperia o contêiner.</span><span class="sxs-lookup"><span data-stu-id="c8e12-207">This keystroke will end the process in the container unless otherwise specified, which would stop the container.</span></span> <span data-ttu-id="c8e12-208">O `--sig-proxy=false` parâmetro garante que <kbd>Ctrl + C</kbd> não pare o processo no contêiner.</span><span class="sxs-lookup"><span data-stu-id="c8e12-208">The `--sig-proxy=false` parameter ensures that <kbd>Ctrl+C</kbd> will not stop the process in the container.</span></span>

<span data-ttu-id="c8e12-209">Depois de desanexar do contêiner, reanexe para verificar se ele ainda está em execução e contando.</span><span class="sxs-lookup"><span data-stu-id="c8e12-209">After you detach from the container, reattach to verify that it's still running and counting.</span></span>

```console
docker start core-counter
core-counter

docker attach --sig-proxy=false core-counter
Counter: 7
Counter: 8
Counter: 9
^C

docker attach --sig-proxy=false core-counter
Counter: 17
Counter: 18
Counter: 19
^C
```

### <a name="delete-a-container"></a><span data-ttu-id="c8e12-210">Excluir um contêiner</span><span class="sxs-lookup"><span data-stu-id="c8e12-210">Delete a container</span></span>

<span data-ttu-id="c8e12-211">Para os fins desse artigo, você não quer contêineres sem função alguma.</span><span class="sxs-lookup"><span data-stu-id="c8e12-211">For the purposes of this article you don't want containers just hanging around doing nothing.</span></span> <span data-ttu-id="c8e12-212">Exclua o contêiner que você criou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="c8e12-212">Delete the container you previously created.</span></span> <span data-ttu-id="c8e12-213">Se o contêiner estiver em execução, interrompa-o.</span><span class="sxs-lookup"><span data-stu-id="c8e12-213">If the container is running, stop it.</span></span>

```console
docker stop core-counter
```

<span data-ttu-id="c8e12-214">O exemplo a seguir lista todos os contêineres.</span><span class="sxs-lookup"><span data-stu-id="c8e12-214">The following example lists all containers.</span></span> <span data-ttu-id="c8e12-215">Em seguida, ele usa o comando `docker rm` para excluir o contêiner e, em seguida, verifica uma segunda vez para verificar qualquer contêiner em execução.</span><span class="sxs-lookup"><span data-stu-id="c8e12-215">It then uses the `docker rm` command to delete the container, and then checks a second time for any running containers.</span></span>

```console
docker ps -a
CONTAINER ID    IMAGE            COMMAND                   CREATED          STATUS                        PORTS    NAMES
2f6424a7ddce    counter-image    "dotnet NetCore.Dock…"    7 minutes ago    Exited (143) 20 seconds ago            core-counter

docker rm core-counter
core-counter

docker ps -a
CONTAINER ID    IMAGE    COMMAND    CREATED    STATUS    PORTS    NAMES
```

### <a name="single-run"></a><span data-ttu-id="c8e12-216">Execução única</span><span class="sxs-lookup"><span data-stu-id="c8e12-216">Single run</span></span>

<span data-ttu-id="c8e12-217">O Docker fornece o comando `docker run` para criar e executar o contêiner como um único comando.</span><span class="sxs-lookup"><span data-stu-id="c8e12-217">Docker provides the `docker run` command to create and run the container as a single command.</span></span> <span data-ttu-id="c8e12-218">Este comando elimina a necessidade de executar `docker create` e, em seguida, `docker start`.</span><span class="sxs-lookup"><span data-stu-id="c8e12-218">This command eliminates the need to run `docker create` and then `docker start`.</span></span> <span data-ttu-id="c8e12-219">Você também pode definir esse comando para excluir automaticamente o contêiner quando o contêiner for interrompido.</span><span class="sxs-lookup"><span data-stu-id="c8e12-219">You can also set this command to automatically delete the container when the container stops.</span></span> <span data-ttu-id="c8e12-220">Por exemplo, use `docker run -it --rm` para fazer duas coisas: primeiro, use automaticamente o terminal atual para se conectar ao contêiner e, quando o contêiner terminar, remova-o:</span><span class="sxs-lookup"><span data-stu-id="c8e12-220">For example, use `docker run -it --rm` to do two things, first, automatically use the current terminal to connect to the container, and then when the container finishes, remove it:</span></span>

```console
docker run -it --rm counter-image
Counter: 1
Counter: 2
Counter: 3
Counter: 4
Counter: 5
^C
```

<span data-ttu-id="c8e12-221">O contêiner também passa parâmetros para a execução do aplicativo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c8e12-221">The container also passes parameters into the execution of the .NET Core app.</span></span> <span data-ttu-id="c8e12-222">Para instruir o aplicativo .NET Core a contar apenas a 3 passagens 3.</span><span class="sxs-lookup"><span data-stu-id="c8e12-222">To instruct the .NET Core app to count only to 3 pass in 3.</span></span>

```console
docker run -it --rm counter-image 3
Counter: 1
Counter: 2
Counter: 3
```

<span data-ttu-id="c8e12-223">Com `docker run -it` o, o comando <kbd>Ctrl + C</kbd> interromperá o processo que está sendo executado no contêiner, o que, por sua vez, interromperá o contêiner.</span><span class="sxs-lookup"><span data-stu-id="c8e12-223">With `docker run -it`, the <kbd>Ctrl+C</kbd> command will stop process that is running in the container, which in turn, stops the container.</span></span> <span data-ttu-id="c8e12-224">Como o parâmetro `--rm` foi fornecido, o contêiner é automaticamente excluído quando o processo é interrompido.</span><span class="sxs-lookup"><span data-stu-id="c8e12-224">Since the `--rm` parameter was provided, the container is automatically deleted when the process is stopped.</span></span> <span data-ttu-id="c8e12-225">Verifique se ele não existe:</span><span class="sxs-lookup"><span data-stu-id="c8e12-225">Verify that it doesn't exist:</span></span>

```console
docker ps -a
CONTAINER ID    IMAGE    COMMAND    CREATED    STATUS    PORTS    NAMES
```

### <a name="change-the-entrypoint"></a><span data-ttu-id="c8e12-226">Alterar o ENTRYPOINT</span><span class="sxs-lookup"><span data-stu-id="c8e12-226">Change the ENTRYPOINT</span></span>

<span data-ttu-id="c8e12-227">O comando `docker run` também permite modificar o comando `ENTRYPOINT` do *Dockerfile* e executar outra coisa, mas apenas para esse contêiner.</span><span class="sxs-lookup"><span data-stu-id="c8e12-227">The `docker run` command also lets you modify the `ENTRYPOINT` command from the *Dockerfile* and run something else, but only for that container.</span></span> <span data-ttu-id="c8e12-228">Por exemplo, use o seguinte comando para executar `bash` ou `cmd.exe`.</span><span class="sxs-lookup"><span data-stu-id="c8e12-228">For example, use the following command to run `bash` or `cmd.exe`.</span></span> <span data-ttu-id="c8e12-229">Edite o comando conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="c8e12-229">Edit the command as necessary.</span></span>

#### <a name="windows"></a>[<span data-ttu-id="c8e12-230">Windows</span><span class="sxs-lookup"><span data-stu-id="c8e12-230">Windows</span></span>](#tab/windows)

<span data-ttu-id="c8e12-231">Neste exemplo, `ENTRYPOINT` é alterado para `cmd.exe`.</span><span class="sxs-lookup"><span data-stu-id="c8e12-231">In this example, `ENTRYPOINT` is changed to `cmd.exe`.</span></span> <span data-ttu-id="c8e12-232"><kbd>Ctrl + C</kbd> é pressionado para encerrar o processo e parar o contêiner.</span><span class="sxs-lookup"><span data-stu-id="c8e12-232"><kbd>Ctrl+C</kbd> is pressed to end the process and stop the container.</span></span>

```console
docker run -it --rm --entrypoint "cmd.exe" counter-image

Microsoft Windows [Version 10.0.17763.379]
(c) 2018 Microsoft Corporation. All rights reserved.

C:\>dir
 Volume in drive C has no label.
 Volume Serial Number is 3005-1E84

 Directory of C:\

04/09/2019  08:46 AM    <DIR>          app
03/07/2019  10:25 AM             5,510 License.txt
04/02/2019  01:35 PM    <DIR>          Program Files
04/09/2019  01:06 PM    <DIR>          Users
04/02/2019  01:35 PM    <DIR>          Windows
               1 File(s)          5,510 bytes
               4 Dir(s)  21,246,517,248 bytes free

C:\>^C
```

#### <a name="linux"></a>[<span data-ttu-id="c8e12-233">Linux</span><span class="sxs-lookup"><span data-stu-id="c8e12-233">Linux</span></span>](#tab/linux)

<span data-ttu-id="c8e12-234">Neste exemplo, `ENTRYPOINT` é alterado para `bash`.</span><span class="sxs-lookup"><span data-stu-id="c8e12-234">In this example, `ENTRYPOINT` is changed to `bash`.</span></span> <span data-ttu-id="c8e12-235">O comando `exit` é executado, o que encerra o processo e interrompe o contêiner.</span><span class="sxs-lookup"><span data-stu-id="c8e12-235">The `exit` command is run which ends the process and stop the container.</span></span>

```bash
docker run -it --rm --entrypoint "bash" counter-image
root@b735b9799abf:/App# ls
NetCore.Docker.deps.json  NetCore.Docker.dll  NetCore.Docker.exe  NetCore.Docker.pdb  NetCore.Docker.runtimeconfig.json
root@b735b9799abf:/App# dotnet NetCore.Docker.dll 3
Counter: 1
Counter: 2
Counter: 3
root@b735b9799abf:/App# exit
exit
```

---

## <a name="essential-commands"></a><span data-ttu-id="c8e12-236">Comandos essenciais</span><span class="sxs-lookup"><span data-stu-id="c8e12-236">Essential commands</span></span>

<span data-ttu-id="c8e12-237">O Docker tem muitos comandos diferentes que criam, gerenciam e interagem com contêineres e imagens.</span><span class="sxs-lookup"><span data-stu-id="c8e12-237">Docker has many different commands that create, manage, and interact with containers and images.</span></span> <span data-ttu-id="c8e12-238">Esses comandos do Docker são essenciais para gerenciar seus contêineres:</span><span class="sxs-lookup"><span data-stu-id="c8e12-238">These Docker commands are essential to managing your containers:</span></span>

- [<span data-ttu-id="c8e12-239">docker build</span><span class="sxs-lookup"><span data-stu-id="c8e12-239">docker build</span></span>](https://docs.docker.com/engine/reference/commandline/build/)
- [<span data-ttu-id="c8e12-240">docker run</span><span class="sxs-lookup"><span data-stu-id="c8e12-240">docker run</span></span>](https://docs.docker.com/engine/reference/commandline/run/)
- [<span data-ttu-id="c8e12-241">docker ps</span><span class="sxs-lookup"><span data-stu-id="c8e12-241">docker ps</span></span>](https://docs.docker.com/engine/reference/commandline/ps/)
- [<span data-ttu-id="c8e12-242">docker stop</span><span class="sxs-lookup"><span data-stu-id="c8e12-242">docker stop</span></span>](https://docs.docker.com/engine/reference/commandline/stop/)
- [<span data-ttu-id="c8e12-243">docker rm</span><span class="sxs-lookup"><span data-stu-id="c8e12-243">docker rm</span></span>](https://docs.docker.com/engine/reference/commandline/rm/)
- [<span data-ttu-id="c8e12-244">docker rmi</span><span class="sxs-lookup"><span data-stu-id="c8e12-244">docker rmi</span></span>](https://docs.docker.com/engine/reference/commandline/rmi/)
- [<span data-ttu-id="c8e12-245">imagem do Docker</span><span class="sxs-lookup"><span data-stu-id="c8e12-245">docker image</span></span>](https://docs.docker.com/engine/reference/commandline/image/)

## <a name="clean-up-resources"></a><span data-ttu-id="c8e12-246">Limpar os recursos</span><span class="sxs-lookup"><span data-stu-id="c8e12-246">Clean up resources</span></span>

<span data-ttu-id="c8e12-247">Durante este tutorial, você criou contêineres e imagens.</span><span class="sxs-lookup"><span data-stu-id="c8e12-247">During this tutorial, you created containers and images.</span></span> <span data-ttu-id="c8e12-248">Se quiser, exclua esses recursos.</span><span class="sxs-lookup"><span data-stu-id="c8e12-248">If you want, delete these resources.</span></span> <span data-ttu-id="c8e12-249">Use os seguintes comandos para:</span><span class="sxs-lookup"><span data-stu-id="c8e12-249">Use the following commands to</span></span>

01. <span data-ttu-id="c8e12-250">Listar todos os contêineres</span><span class="sxs-lookup"><span data-stu-id="c8e12-250">List all containers</span></span>

    ```console
    docker ps -a
    ```

02. <span data-ttu-id="c8e12-251">Interrompa os contêineres que estão sendo executados por seu nome.</span><span class="sxs-lookup"><span data-stu-id="c8e12-251">Stop containers that are running by their name.</span></span>

    ```console
    docker stop counter-image
    ```

03. <span data-ttu-id="c8e12-252">Excluir o contêiner</span><span class="sxs-lookup"><span data-stu-id="c8e12-252">Delete the container</span></span>

    ```console
    docker rm counter-image
    ```

<span data-ttu-id="c8e12-253">Em seguida, exclua todas as imagens que você não deseja mais em seu computador.</span><span class="sxs-lookup"><span data-stu-id="c8e12-253">Next, delete any images that you no longer want on your machine.</span></span> <span data-ttu-id="c8e12-254">Exclua a imagem criada pelo seu *Dockerfile* e exclua a imagem do .NET Core na qual o *Dockerfile* teve base.</span><span class="sxs-lookup"><span data-stu-id="c8e12-254">Delete the image created by your *Dockerfile* and then delete the .NET Core image the *Dockerfile* was based on.</span></span> <span data-ttu-id="c8e12-255">Você pode usar a **ID DA IMAGEM** ou a cadeia de caracteres formatada **REPOSITÓRIO:TAG**.</span><span class="sxs-lookup"><span data-stu-id="c8e12-255">You can use the **IMAGE ID** or the **REPOSITORY:TAG** formatted string.</span></span>

```console
docker rmi counter-image:latest
docker rmi mcr.microsoft.com/dotnet/core/aspnet:3.1
```

<span data-ttu-id="c8e12-256">Use o comando `docker images` para ver uma lista de imagens instaladas.</span><span class="sxs-lookup"><span data-stu-id="c8e12-256">Use the `docker images` command to see a list of images installed.</span></span>

> [!TIP]
> <span data-ttu-id="c8e12-257">Arquivos de imagem podem ser grandes.</span><span class="sxs-lookup"><span data-stu-id="c8e12-257">Image files can be large.</span></span> <span data-ttu-id="c8e12-258">Normalmente, você removeria contêineres temporários criados durante o teste e o desenvolvimento de seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c8e12-258">Typically, you would remove temporary containers you created while testing and developing your app.</span></span> <span data-ttu-id="c8e12-259">Em geral, mantenha as imagens de base com o runtime instalado se você planeja construir outras imagens com base nesse runtime.</span><span class="sxs-lookup"><span data-stu-id="c8e12-259">You usually keep the base images with the runtime installed if you plan on building other images based on that runtime.</span></span>

## <a name="next-steps"></a><span data-ttu-id="c8e12-260">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="c8e12-260">Next steps</span></span>

- [<span data-ttu-id="c8e12-261">Aprenda a colocar em contêiner um aplicativo ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="c8e12-261">Learn how to containerize an ASP.NET Core application.</span></span>](/aspnet/core/host-and-deploy/docker/building-net-docker-images)
- [<span data-ttu-id="c8e12-262">Experimentar o Tutorial de Microsserviço do ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="c8e12-262">Try the ASP.NET Core Microservice Tutorial.</span></span>](https://dotnet.microsoft.com/learn/web/aspnet-microservice-tutorial/intro)
- [<span data-ttu-id="c8e12-263">Revisar os serviços do Azure que oferecem suporte a contêineres.</span><span class="sxs-lookup"><span data-stu-id="c8e12-263">Review the Azure services that support containers.</span></span>](https://azure.microsoft.com/overview/containers/)
- [<span data-ttu-id="c8e12-264">Ler mais sobre os comandos do Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="c8e12-264">Read about Dockerfile commands.</span></span>](https://docs.docker.com/engine/reference/builder/)
- [<span data-ttu-id="c8e12-265">Explore as Ferramentas de Contêiner para Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c8e12-265">Explore the Container Tools for Visual Studio</span></span>](/visualstudio/containers/overview)
