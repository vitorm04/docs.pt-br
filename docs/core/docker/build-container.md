---
title: 'Tutorial: Colocar em contêiner um aplicativo com o Docker'
description: Neste tutorial, você aprenderá como contêiner um aplicativo .NET Core com o Docker.
ms.date: 01/09/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 8be12792e4a9e8511dba87e657f700cc4ec97a16
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2020
ms.locfileid: "79546569"
---
# <a name="tutorial-containerize-a-net-core-app"></a><span data-ttu-id="3913d-103">Tutorial: Containerize um aplicativo .NET Core</span><span class="sxs-lookup"><span data-stu-id="3913d-103">Tutorial: Containerize a .NET Core app</span></span>

<span data-ttu-id="3913d-104">Este tutorial ensina como criar uma imagem do Docker que contenha seu aplicativo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3913d-104">This tutorial teaches you how to build a Docker image that contains your .NET Core application.</span></span> <span data-ttu-id="3913d-105">A imagem pode ser usada para criar contêineres para seu ambiente de desenvolvimento local, nuvem privada ou nuvem pública.</span><span class="sxs-lookup"><span data-stu-id="3913d-105">The image can be used to create containers for your local development environment, private cloud, or public cloud.</span></span>

<span data-ttu-id="3913d-106">Você aprenderá a:</span><span class="sxs-lookup"><span data-stu-id="3913d-106">You'll learn to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="3913d-107">Criar e publicar um aplicativo .NET Core simples</span><span class="sxs-lookup"><span data-stu-id="3913d-107">Create and publish a simple .NET Core app</span></span>
> - <span data-ttu-id="3913d-108">Criar e configurar um Dockerfile para .NET Core</span><span class="sxs-lookup"><span data-stu-id="3913d-108">Create and configure a Dockerfile for .NET Core</span></span>
> - <span data-ttu-id="3913d-109">Compilar uma imagem do docker</span><span class="sxs-lookup"><span data-stu-id="3913d-109">Build a Docker image</span></span>
> - <span data-ttu-id="3913d-110">Criar e executar um contêiner do Docker</span><span class="sxs-lookup"><span data-stu-id="3913d-110">Create and run a Docker container</span></span>

<span data-ttu-id="3913d-111">Você aprenderá as tarefas de build e implantação de contêiner do Docker para um aplicativo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3913d-111">You'll understand the Docker container build and deploy tasks for a .NET Core application.</span></span> <span data-ttu-id="3913d-112">A *plataforma Docker* usa o *Mecanismo do Docker* para criar e empacotar aplicativos como *imagens do Docker* com agilidade.</span><span class="sxs-lookup"><span data-stu-id="3913d-112">The *Docker platform* uses the *Docker engine* to quickly build and package apps as *Docker images*.</span></span> <span data-ttu-id="3913d-113">Essas imagens são gravadas no formato *Dockerfile* para serem implantadas e executadas em um contêiner em camadas.</span><span class="sxs-lookup"><span data-stu-id="3913d-113">These images are written in the *Dockerfile* format to be deployed and run in a layered container.</span></span>

> [!WARNING]
> <span data-ttu-id="3913d-114">**Este tutorial não é para ASP.NET aplicativos Core.**</span><span class="sxs-lookup"><span data-stu-id="3913d-114">**This tutorial isn't for ASP.NET Core apps.**</span></span> <span data-ttu-id="3913d-115">Se você estiver usando ASP.NET Core, leia o [Learn how to containerize a ASP.NET tutorial do aplicativo Core.](/aspnet/core/host-and-deploy/docker/building-net-docker-images)</span><span class="sxs-lookup"><span data-stu-id="3913d-115">If you're using ASP.NET Core, read the [Learn how to containerize an ASP.NET Core application](/aspnet/core/host-and-deploy/docker/building-net-docker-images) tutorial.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3913d-116">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="3913d-116">Prerequisites</span></span>

<span data-ttu-id="3913d-117">Instale os seguintes pré-requisitos:</span><span class="sxs-lookup"><span data-stu-id="3913d-117">Install the following prerequisites:</span></span>

- <span data-ttu-id="3913d-118">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="3913d-118">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download)</span></span>\
<span data-ttu-id="3913d-119">Se você tiver o .NET Core instalado, use o comando `dotnet --info` para determinar qual SDK está usando.</span><span class="sxs-lookup"><span data-stu-id="3913d-119">If you have .NET Core installed, use the `dotnet --info` command to determine which SDK you're using.</span></span>

- [<span data-ttu-id="3913d-120">Docker Community Edition</span><span class="sxs-lookup"><span data-stu-id="3913d-120">Docker Community Edition</span></span>](https://www.docker.com/products/docker-desktop)

- <span data-ttu-id="3913d-121">Uma pasta de trabalho temporária para o *Dockerfile* e o aplicativo de exemplo do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3913d-121">A temporary working folder for the *Dockerfile* and .NET Core example app.</span></span> <span data-ttu-id="3913d-122">Neste tutorial, o nome *docker-working* é usado como pasta de trabalho.</span><span class="sxs-lookup"><span data-stu-id="3913d-122">In this tutorial, the name *docker-working* is used as the working folder.</span></span>

## <a name="create-net-core-app"></a><span data-ttu-id="3913d-123">Criar aplicativo .NET Core</span><span class="sxs-lookup"><span data-stu-id="3913d-123">Create .NET Core app</span></span>

<span data-ttu-id="3913d-124">Você precisa de um aplicativo .NET Core que o contêiner do Docker irá executar.</span><span class="sxs-lookup"><span data-stu-id="3913d-124">You need a .NET Core app that the Docker container will run.</span></span> <span data-ttu-id="3913d-125">Abra seu terminal, crie uma pasta de trabalho se você ainda não fez isso e entre nela.</span><span class="sxs-lookup"><span data-stu-id="3913d-125">Open your terminal, create a working folder if you haven't already, and enter it.</span></span> <span data-ttu-id="3913d-126">Na pasta de trabalho, execute o seguinte comando para criar um novo projeto em um subdiretório chamado *app*:</span><span class="sxs-lookup"><span data-stu-id="3913d-126">In the working folder, run the following command to create a new project in a subdirectory named *app*:</span></span>

```dotnetcli
dotnet new console -o app -n myapp
```

<span data-ttu-id="3913d-127">A árvore de pastas terá aparência semelhante à seguinte:</span><span class="sxs-lookup"><span data-stu-id="3913d-127">Your folder tree will look like the following:</span></span>

```
docker-working
│
└───app
    │   myapp.csproj
    │   Program.cs
    │
    └───obj
            myapp.csproj.nuget.cache
            myapp.csproj.nuget.dgspec.json
            myapp.csproj.nuget.g.props
            myapp.csproj.nuget.g.targets
            project.assets.json
```

<span data-ttu-id="3913d-128">O comando `dotnet new` cria uma pasta chamada *app* e gera um aplicativo "Olá, Mundo".</span><span class="sxs-lookup"><span data-stu-id="3913d-128">The `dotnet new` command creates a new folder named *app* and generates a "Hello World" app.</span></span> <span data-ttu-id="3913d-129">Entre na pasta *app* e execute o comando `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="3913d-129">Enter the *app* folder and run the command `dotnet run`.</span></span> <span data-ttu-id="3913d-130">Você verá a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="3913d-130">You'll see the following output:</span></span>

```console
> dotnet run
Hello World!
```

<span data-ttu-id="3913d-131">O modelo padrão cria um aplicativo que imprime no terminal e, em seguida, sai.</span><span class="sxs-lookup"><span data-stu-id="3913d-131">The default template creates an app that prints to the terminal and then exits.</span></span> <span data-ttu-id="3913d-132">Neste tutorial, você usará um aplicativo que faz um loop indefinidamente.</span><span class="sxs-lookup"><span data-stu-id="3913d-132">For this tutorial, you'll use an app that loops indefinitely.</span></span> <span data-ttu-id="3913d-133">Abra o arquivo *Program.cs* em um editor de texto.</span><span class="sxs-lookup"><span data-stu-id="3913d-133">Open the *Program.cs* file in a text editor.</span></span> <span data-ttu-id="3913d-134">Ele deve se parecer com o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="3913d-134">It should currently look like the following code:</span></span>

```csharp
using System;

namespace myapp
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

<span data-ttu-id="3913d-135">Substitua o arquivo pelo seguinte código que conta os números a cada segundo:</span><span class="sxs-lookup"><span data-stu-id="3913d-135">Replace the file with the following code that counts numbers every second:</span></span>

```csharp
using System;

namespace myapp
{
    class Program
    {
        static void Main(string[] args)
        {
            var counter = 0;
            var max = args.Length != 0 ? Convert.ToInt32(args[0]) : -1;
            while (max == -1 || counter < max)
            {
                counter++;
                Console.WriteLine($"Counter: {counter}");
                System.Threading.Tasks.Task.Delay(1000).Wait();
            }
        }
    }
}
```

<span data-ttu-id="3913d-136">Salve o arquivo e teste o programa novamente com `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="3913d-136">Save the file and test the program again with `dotnet run`.</span></span> <span data-ttu-id="3913d-137">Lembre-se de que esse aplicativo é executado indefinidamente.</span><span class="sxs-lookup"><span data-stu-id="3913d-137">Remember that this app runs indefinitely.</span></span> <span data-ttu-id="3913d-138">Use o comando cancelar <kbd>CTRL</kbd>+<kbd>C</kbd> para pará-lo.</span><span class="sxs-lookup"><span data-stu-id="3913d-138">Use the cancel command <kbd>CTRL</kbd>+<kbd>C</kbd> to stop it.</span></span> <span data-ttu-id="3913d-139">Você verá a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="3913d-139">You'll see the following output:</span></span>

```console
> dotnet run
Counter: 1
Counter: 2
Counter: 3
Counter: 4
^C
```

<span data-ttu-id="3913d-140">Se você passar um número na linha de comando para o aplicativo, ele apenas contará até tal valor e, em seguida, sairá.</span><span class="sxs-lookup"><span data-stu-id="3913d-140">If you pass a number on the command line to the app, it will only count up to that amount and then exit.</span></span> <span data-ttu-id="3913d-141">Experimente com `dotnet run -- 5` para contar até cinco.</span><span class="sxs-lookup"><span data-stu-id="3913d-141">Try it with `dotnet run -- 5` to count to five.</span></span>

> [!NOTE]
> <span data-ttu-id="3913d-142">Quaisquer parâmetros após `--` não são passados para o comando `dotnet run` e, em vez disso, são passados para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3913d-142">Any parameters after `--` are not passed to the `dotnet run` command and instead are passed to your application.</span></span>

## <a name="publish-net-core-app"></a><span data-ttu-id="3913d-143">Publicar um aplicativo .NET Core</span><span class="sxs-lookup"><span data-stu-id="3913d-143">Publish .NET Core app</span></span>

<span data-ttu-id="3913d-144">Antes de adicionar seu aplicativo .NET Core à imagem do Docker, publique-o.</span><span class="sxs-lookup"><span data-stu-id="3913d-144">Before you add your .NET Core app to the Docker image, publish it.</span></span> <span data-ttu-id="3913d-145">Você deseja assegurar que o contêiner execute a versão publicada do aplicativo quando ele for iniciado.</span><span class="sxs-lookup"><span data-stu-id="3913d-145">You want to make sure that the container runs the published version of the app when it's started.</span></span>

<span data-ttu-id="3913d-146">Da pasta de trabalho, entre na pasta *app* com o código-fonte de exemplo e execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="3913d-146">From the working folder, enter the *app* folder with the example source code and run the following command:</span></span>

```dotnetcli
dotnet publish -c Release
```

<span data-ttu-id="3913d-147">Esse comando compila seu aplicativo para a pasta *publish*.</span><span class="sxs-lookup"><span data-stu-id="3913d-147">This command compiles your app to the *publish* folder.</span></span> <span data-ttu-id="3913d-148">O caminho para a pasta *publish* da pasta de trabalho deve ser `.\app\bin\Release\netcoreapp3.1\publish\`</span><span class="sxs-lookup"><span data-stu-id="3913d-148">The path to the *publish* folder from the working folder should be `.\app\bin\Release\netcoreapp3.1\publish\`</span></span>

<span data-ttu-id="3913d-149">A partir da pasta do *aplicativo,* obtenha uma lista de diretórios da pasta de publicação para verificar se o arquivo *myapp.dll* foi criado.</span><span class="sxs-lookup"><span data-stu-id="3913d-149">From the *app* folder, get a directory listing of the publish folder to verify that the *myapp.dll* file was created.</span></span>

```console
> dir bin\Release\netcoreapp3.1\publish

    Directory:  C:\docker-working\app\bin\Release\netcoreapp3.1\publish

01/09/2020  11:41 AM    <DIR>          .
01/09/2020  11:41 AM    <DIR>          ..
01/09/2020  11:41 AM               407 myapp.deps.json
01/09/2020  12:15 PM             4,608 myapp.dll
01/09/2020  12:15 PM           169,984 myapp.exe
01/09/2020  12:15 PM               736 myapp.pdb
01/09/2020  11:41 AM               154 myapp.runtimeconfig.json
```

<span data-ttu-id="3913d-150">Se você estiver usando Linux ou `ls` macOS, use o comando para obter uma listagem de diretório e verifique se o arquivo *myapp.dll* foi criado.</span><span class="sxs-lookup"><span data-stu-id="3913d-150">If you're using Linux or macOS, use the `ls` command to get a directory listing and verify that the *myapp.dll* file was created.</span></span>

```bash
me@DESKTOP:/docker-working/app$ ls bin/Release/netcoreapp3.1/publish
myapp.deps.json  myapp.dll  myapp.pdb  myapp.runtimeconfig.json
```

## <a name="create-the-dockerfile"></a><span data-ttu-id="3913d-151">Criar o Dockerfile</span><span class="sxs-lookup"><span data-stu-id="3913d-151">Create the Dockerfile</span></span>

<span data-ttu-id="3913d-152">O arquivo *Dockerfile* é usado pelo comando `docker build` para criar uma imagem de contêiner.</span><span class="sxs-lookup"><span data-stu-id="3913d-152">The *Dockerfile* file is used by the `docker build` command to create a container image.</span></span> <span data-ttu-id="3913d-153">Este arquivo é um arquivo de texto chamado *Dockerfile* que não tem uma extensão.</span><span class="sxs-lookup"><span data-stu-id="3913d-153">This file is a text file named *Dockerfile* that doesn't have an extension.</span></span>

<span data-ttu-id="3913d-154">No terminal, navegue em um diretório acima até a pasta de trabalho criada no início.</span><span class="sxs-lookup"><span data-stu-id="3913d-154">In your terminal, navigate up a directory to the working folder you created at the start.</span></span> <span data-ttu-id="3913d-155">Crie um arquivo chamado *Dockerfile* em sua pasta de trabalho e abra-o em um editor de texto.</span><span class="sxs-lookup"><span data-stu-id="3913d-155">Create a file named *Dockerfile* in your working folder and open it in a text editor.</span></span> <span data-ttu-id="3913d-156">Dependendo do tipo de aplicação que você vai contêiner, você escolherá o tempo de execução do ASP.NET Core ou o tempo de execução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3913d-156">Depending on the type of application you're going to containerize, you'll choose either the ASP.NET Core runtime or the .NET Core runtime.</span></span> <span data-ttu-id="3913d-157">Na dúvida, escolha o tempo de execução ASP.NET Core, que inclui o tempo de execução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3913d-157">When in doubt, choose the ASP.NET Core runtime, which includes the .NET Core runtime.</span></span> <span data-ttu-id="3913d-158">Este tutorial usará a imagem de tempo de execução ASP.NET Core, mas o aplicativo criado nas seções anteriores é um aplicativo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3913d-158">This tutorial will use the ASP.NET Core runtime image, but the application created in the previous sections is an .NET Core application.</span></span>

- <span data-ttu-id="3913d-159">tempo de execução do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="3913d-159">ASP.NET Core runtime</span></span>

  ```dockerfile
  FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
  ```

- <span data-ttu-id="3913d-160">runtime do .NET Core</span><span class="sxs-lookup"><span data-stu-id="3913d-160">.NET Core runtime</span></span>

  ```dockerfile
  FROM mcr.microsoft.com/dotnet/core/runtime:3.1
  ```

<span data-ttu-id="3913d-161">O `FROM` comando diz ao Docker para puxar para baixo a imagem marcada **3.1** do repositório especificado.</span><span class="sxs-lookup"><span data-stu-id="3913d-161">The `FROM` command tells Docker to pull down the image tagged **3.1** from the specified repository.</span></span> <span data-ttu-id="3913d-162">Certifique-se de puxar a versão de tempo de execução que corresponde ao tempo de execução visado pelo seu SDK.</span><span class="sxs-lookup"><span data-stu-id="3913d-162">Make sure that you pull the runtime version that matches the runtime targeted by your SDK.</span></span> <span data-ttu-id="3913d-163">Por exemplo, o aplicativo criado na seção anterior usou o SDK .NET Core 3.1 e a imagem base referida no *Arquivo Docker* é marcada com **3.1**.</span><span class="sxs-lookup"><span data-stu-id="3913d-163">For example, the app created in the previous section used the .NET Core 3.1 SDK and the base image referred to in the *Dockerfile* is tagged with **3.1**.</span></span>

<span data-ttu-id="3913d-164">Salve o arquivo *Dockerfile*.</span><span class="sxs-lookup"><span data-stu-id="3913d-164">Save the *Dockerfile* file.</span></span> <span data-ttu-id="3913d-165">A estrutura de diretório da pasta de trabalho deve ser semelhante à mostrada a seguir.</span><span class="sxs-lookup"><span data-stu-id="3913d-165">The directory structure of the working folder should look like the following.</span></span> <span data-ttu-id="3913d-166">Algumas das pastas e arquivos de nível mais profundo foram eliminados para economizar espaço no artigo:</span><span class="sxs-lookup"><span data-stu-id="3913d-166">Some of the deeper-level files and folders have been cut to save space in the article:</span></span>

```
docker-working
│   Dockerfile
│
└───app
    │   myapp.csproj
    │   Program.cs
    │
    ├───bin
    │   └───Release
    │       └───netcoreapp3.1
    │           └───publish
    │                   myapp.deps.json
    │                   myapp.exe
    │                   myapp.dll
    │                   myapp.pdb
    │                   myapp.runtimeconfig.json
    │
    └───obj
```

<span data-ttu-id="3913d-167">Do terminal, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="3913d-167">From your terminal, run the following command:</span></span>

```console
docker build -t myimage -f Dockerfile .
```

<span data-ttu-id="3913d-168">O Docker processará cada linha no *Dockerfile*.</span><span class="sxs-lookup"><span data-stu-id="3913d-168">Docker will process each line in the *Dockerfile*.</span></span> <span data-ttu-id="3913d-169">O `.` no comando `docker build` instrui o Docker a usar a pasta atual para encontrar um *Dockerfile*.</span><span class="sxs-lookup"><span data-stu-id="3913d-169">The `.` in the `docker build` command tells Docker to use the current folder to find a *Dockerfile*.</span></span> <span data-ttu-id="3913d-170">Esse comando constrói a imagem e cria um repositório local chamado **myimage** que aponta para essa imagem.</span><span class="sxs-lookup"><span data-stu-id="3913d-170">This command builds the image and creates a local repository named **myimage** that points to that image.</span></span> <span data-ttu-id="3913d-171">Após a conclusão desse comando, execute `docker images` para ver uma lista de imagens instaladas:</span><span class="sxs-lookup"><span data-stu-id="3913d-171">After this command finishes, run `docker images` to see a list of images installed:</span></span>

```console
> docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
myimage                                 latest              38db0eb8f648        4 weeks ago         346MB
mcr.microsoft.com/dotnet/core/aspnet    3.1                 38db0eb8f648        4 weeks ago         346MB
```

<span data-ttu-id="3913d-172">Observe que as duas imagens compartilham o mesmo valor de **ID DA IMAGEM**.</span><span class="sxs-lookup"><span data-stu-id="3913d-172">Notice that the two images share the same **IMAGE ID** value.</span></span> <span data-ttu-id="3913d-173">O valor é o mesmo entre as duas imagens porque o único comando no *Dockerfile* era basear a nova imagem em uma imagem existente.</span><span class="sxs-lookup"><span data-stu-id="3913d-173">The value is the same between both images because the only command in the *Dockerfile* was to base the new image on an existing image.</span></span> <span data-ttu-id="3913d-174">Vamos adicionar dois comandos ao *Dockerfile*.</span><span class="sxs-lookup"><span data-stu-id="3913d-174">Let's add two commands to the *Dockerfile*.</span></span> <span data-ttu-id="3913d-175">Cada comando cria uma nova camada de imagem com o comando final representando a imagem para a que a entrada do repositório **myimage** aponta.</span><span class="sxs-lookup"><span data-stu-id="3913d-175">Each command creates a new image layer with the final command representing the image the **myimage** repository entry points to.</span></span>

```dockerfile
COPY app/bin/Release/netcoreapp3.1/publish/ app/

ENTRYPOINT ["dotnet", "app/myapp.dll"]
```

<span data-ttu-id="3913d-176">O comando `COPY` informa ao Docker para copiar a pasta especificada em seu computador para uma pasta no contêiner.</span><span class="sxs-lookup"><span data-stu-id="3913d-176">The `COPY` command tells Docker to copy the specified folder on your computer to a folder in the container.</span></span> <span data-ttu-id="3913d-177">Nesse exemplo, a pasta *publish* é copiada para uma pasta chamada *app* no contêiner.</span><span class="sxs-lookup"><span data-stu-id="3913d-177">In this example, the *publish* folder is copied to a folder named *app* in the container.</span></span>

<span data-ttu-id="3913d-178">O comando seguinte, `ENTRYPOINT`, informa ao Docker para configurar o contêiner para ser executado como um executável.</span><span class="sxs-lookup"><span data-stu-id="3913d-178">The next command, `ENTRYPOINT`, tells Docker to configure the container to run as an executable.</span></span> <span data-ttu-id="3913d-179">Quando o contêiner é iniciado, o comando `ENTRYPOINT` é executado.</span><span class="sxs-lookup"><span data-stu-id="3913d-179">When the container starts, the `ENTRYPOINT` command runs.</span></span> <span data-ttu-id="3913d-180">Quando esse comando terminar, o contêiner será interrompido automaticamente.</span><span class="sxs-lookup"><span data-stu-id="3913d-180">When this command ends, the container will automatically stop.</span></span>

<span data-ttu-id="3913d-181">No seu terminal, execute `docker build -t myimage -f Dockerfile .` e, quando o comando terminar, execute `docker images`.</span><span class="sxs-lookup"><span data-stu-id="3913d-181">From your terminal, run `docker build -t myimage -f Dockerfile .` and when that command finishes, run `docker images`.</span></span>

```console
> docker build -t myimage -f Dockerfile .
Sending build context to Docker daemon  1.624MB
Step 1/3 : FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
 ---> 38db0eb8f648
Step 2/3 : COPY app/bin/Release/netcoreapp3.1/publish/ app/
 ---> 37873673e468
Step 3/3 : ENTRYPOINT ["dotnet", "app/myapp.dll"]
 ---> Running in d8deb7b3aa9e
Removing intermediate container d8deb7b3aa9e
 ---> 0d602ca35c1d
Successfully built 0d602ca35c1d
Successfully tagged myimage:latest

> docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
myimage                                 latest              0d602ca35c1d        4 seconds ago       346MB
mcr.microsoft.com/dotnet/core/aspnet    3.1                 38db0eb8f648        4 weeks ago         346MB
```

<span data-ttu-id="3913d-182">Cada comando no *Dockerfile* gerou uma camada e criou uma **ID DA IMAGEM**.</span><span class="sxs-lookup"><span data-stu-id="3913d-182">Each command in the *Dockerfile* generated a layer and created an **IMAGE ID**.</span></span> <span data-ttu-id="3913d-183">A **ID DA IMAGEM** final (a sua será diferente) é **ddcc6646461b** e, a seguir, você criará um contêiner baseado nessa imagem.</span><span class="sxs-lookup"><span data-stu-id="3913d-183">The final **IMAGE ID** (yours will be different) is **ddcc6646461b** and next you'll create a container based on this image.</span></span>

## <a name="create-a-container"></a><span data-ttu-id="3913d-184">Criar um contêiner</span><span class="sxs-lookup"><span data-stu-id="3913d-184">Create a container</span></span>

<span data-ttu-id="3913d-185">Agora que você tem uma imagem que contém o seu aplicativo, você pode criar um contêiner.</span><span class="sxs-lookup"><span data-stu-id="3913d-185">Now that you have an image that contains your app, you can create a container.</span></span> <span data-ttu-id="3913d-186">Você pode criar um contêiner de duas maneiras.</span><span class="sxs-lookup"><span data-stu-id="3913d-186">You can create a container in two ways.</span></span> <span data-ttu-id="3913d-187">Primeiro, criar um novo contêiner que foi interrompido.</span><span class="sxs-lookup"><span data-stu-id="3913d-187">First, create a new container that is stopped.</span></span>

```console
> docker create myimage
ceda87b219a4e55e9ad5d833ee1a7ea4da21b5ea7ce5a7d08f3051152e784944
```

<span data-ttu-id="3913d-188">O comando `docker create` acima criará um contêiner baseado na imagem **myimage**.</span><span class="sxs-lookup"><span data-stu-id="3913d-188">The `docker create` command from above will create a container based on the **myimage** image.</span></span> <span data-ttu-id="3913d-189">A saída desse comando mostra a **ID DO CONTÊINER** (a sua será diferente) do contêiner criado.</span><span class="sxs-lookup"><span data-stu-id="3913d-189">The output of that command shows you the **CONTAINER ID** (yours will be different) of the created container.</span></span> <span data-ttu-id="3913d-190">Para ver uma lista de *todos* os contêineres, use o comando `docker ps -a`:</span><span class="sxs-lookup"><span data-stu-id="3913d-190">To see a list of *all* containers, use the `docker ps -a` command:</span></span>

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS        PORTS   NAMES
ceda87b219a4        myimage             "dotnet app/myapp.dll"   4 seconds ago       Created               gallant_lehmann
```

### <a name="manage-the-container"></a><span data-ttu-id="3913d-191">Gerenciar o contêiner</span><span class="sxs-lookup"><span data-stu-id="3913d-191">Manage the container</span></span>

<span data-ttu-id="3913d-192">Cada contêiner é atribuído a um nome aleatório que você pode usar para se referir a essa instância de contêiner.</span><span class="sxs-lookup"><span data-stu-id="3913d-192">Each container is assigned a random name that you can use to refer to that container instance.</span></span> <span data-ttu-id="3913d-193">Por exemplo, o contêiner que foi criado escolheu automaticamente o nome **gallant_lehmann** (o seu será diferente) e esse nome pode ser usado para iniciar o contêiner.</span><span class="sxs-lookup"><span data-stu-id="3913d-193">For example, the container that was created automatically chose the name **gallant_lehmann** (yours will be different) and that name can be used to start the container.</span></span> <span data-ttu-id="3913d-194">Você substitui o nome automático por um específico usando o parâmetro `docker create --name`.</span><span class="sxs-lookup"><span data-stu-id="3913d-194">You override the automatic name with a specific one by using the `docker create --name` parameter.</span></span>

<span data-ttu-id="3913d-195">O exemplo a seguir usa o comando `docker start` para iniciar o contêiner e, em seguida, usa o comando `docker ps` para mostrar apenas os contêineres em execução:</span><span class="sxs-lookup"><span data-stu-id="3913d-195">The following example uses the `docker start` command to start the container, and then uses the `docker ps` command to only show containers that are running:</span></span>

```console
> docker start gallant_lehmann
gallant_lehmann

> docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS         PORTS   NAMES
ceda87b219a4        myimage             "dotnet app/myapp.dll"   7 minutes ago       Up 8 seconds           gallant_lehmann
```

<span data-ttu-id="3913d-196">Da mesma forma, o comando `docker stop` interromperá o contêiner.</span><span class="sxs-lookup"><span data-stu-id="3913d-196">Similarly, the `docker stop` command will stop the container.</span></span> <span data-ttu-id="3913d-197">O exemplo a `docker stop` seguir usa o comando para `docker ps` parar o contêiner e, em seguida, usa o comando para mostrar que nenhum contêiner está sendo executado:</span><span class="sxs-lookup"><span data-stu-id="3913d-197">The following example uses the `docker stop` command to stop the container, and then uses the `docker ps` command to show that no containers are running:</span></span>

```console
> docker stop gallant_lehmann
gallant_lehmann

> docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS     PORTS   NAMES
```

### <a name="connect-to-a-container"></a><span data-ttu-id="3913d-198">Conectar-se a um contêiner</span><span class="sxs-lookup"><span data-stu-id="3913d-198">Connect to a container</span></span>

<span data-ttu-id="3913d-199">Depois que um contêiner estiver em execução, você poderá se conectar a ele para ver a saída.</span><span class="sxs-lookup"><span data-stu-id="3913d-199">After a container is running, you can connect to it to see the output.</span></span> <span data-ttu-id="3913d-200">Use os comandos `docker start` e `docker attach` para iniciar o contêiner e inspecionar o fluxo de saída.</span><span class="sxs-lookup"><span data-stu-id="3913d-200">Use the `docker start` and `docker attach` commands to start the container and peek at the output stream.</span></span> <span data-ttu-id="3913d-201">Neste exemplo, a tecla <kbd>CTRL + C</kbd> é usada para se separar do recipiente em execução.</span><span class="sxs-lookup"><span data-stu-id="3913d-201">In this example, the <kbd>CTRL + C</kbd> keystroke is used to detach from the running container.</span></span> <span data-ttu-id="3913d-202">Esta tecla pode realmente terminar o processo no recipiente, o que irá parar o recipiente.</span><span class="sxs-lookup"><span data-stu-id="3913d-202">This keystroke may actually end the process in the container, which will stop the container.</span></span> <span data-ttu-id="3913d-203">O parâmetro `--sig-proxy=false` garante que <kbd>Ctrl+C</kbd> não interrompa o processo no contêiner.</span><span class="sxs-lookup"><span data-stu-id="3913d-203">The `--sig-proxy=false` parameter ensures that <kbd>CTRL + C</kbd> won't stop the process in the container.</span></span>

<span data-ttu-id="3913d-204">Depois de desanexar do contêiner, reanexe para verificar se ele ainda está em execução e contando.</span><span class="sxs-lookup"><span data-stu-id="3913d-204">After you detach from the container, reattach to verify that it's still running and counting.</span></span>

```console
> docker start gallant_lehmann
gallant_lehmann

> docker attach --sig-proxy=false gallant_lehmann
Counter: 7
Counter: 8
Counter: 9
^C

> docker attach --sig-proxy=false gallant_lehmann
Counter: 17
Counter: 18
Counter: 19
^C
```

### <a name="delete-a-container"></a><span data-ttu-id="3913d-205">Excluir um contêiner</span><span class="sxs-lookup"><span data-stu-id="3913d-205">Delete a container</span></span>

<span data-ttu-id="3913d-206">Para os fins desse artigo, você não quer contêineres sem função alguma.</span><span class="sxs-lookup"><span data-stu-id="3913d-206">For the purposes of this article you don't want containers just hanging around doing nothing.</span></span> <span data-ttu-id="3913d-207">Exclua o contêiner que você criou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="3913d-207">Delete the container you previously created.</span></span> <span data-ttu-id="3913d-208">Se o contêiner estiver em execução, interrompa-o.</span><span class="sxs-lookup"><span data-stu-id="3913d-208">If the container is running, stop it.</span></span>

```console
> docker stop gallant_lehmann
```

<span data-ttu-id="3913d-209">O exemplo a seguir lista todos os contêineres.</span><span class="sxs-lookup"><span data-stu-id="3913d-209">The following example lists all containers.</span></span> <span data-ttu-id="3913d-210">Em seguida, ele usa o comando `docker rm` para excluir o contêiner e, em seguida, verifica uma segunda vez para verificar qualquer contêiner em execução.</span><span class="sxs-lookup"><span data-stu-id="3913d-210">It then uses the `docker rm` command to delete the container, and then checks a second time for any running containers.</span></span>

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS     PORTS   NAMES
ceda87b219a4        myimage             "dotnet app/myapp.dll"   19 minutes ago      Exited             gallant_lehmann

> docker rm gallant_lehmann
gallant_lehmann

> docker ps -a
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS     PORTS    NAMES
```

### <a name="single-run"></a><span data-ttu-id="3913d-211">Execução única</span><span class="sxs-lookup"><span data-stu-id="3913d-211">Single run</span></span>

<span data-ttu-id="3913d-212">O Docker fornece o comando `docker run` para criar e executar o contêiner como um único comando.</span><span class="sxs-lookup"><span data-stu-id="3913d-212">Docker provides the `docker run` command to create and run the container as a single command.</span></span> <span data-ttu-id="3913d-213">Este comando elimina a necessidade de executar `docker create` e, em seguida, `docker start`.</span><span class="sxs-lookup"><span data-stu-id="3913d-213">This command eliminates the need to run `docker create` and then `docker start`.</span></span> <span data-ttu-id="3913d-214">Você também pode definir esse comando para excluir automaticamente o contêiner quando o contêiner for interrompido.</span><span class="sxs-lookup"><span data-stu-id="3913d-214">You can also set this command to automatically delete the container when the container stops.</span></span> <span data-ttu-id="3913d-215">Por exemplo, use `docker run -it --rm` para fazer duas coisas: primeiro, use automaticamente o terminal atual para se conectar ao contêiner e, quando o contêiner terminar, remova-o:</span><span class="sxs-lookup"><span data-stu-id="3913d-215">For example, use `docker run -it --rm` to do two things, first, automatically use the current terminal to connect to the container, and then when the container finishes, remove it:</span></span>

```console
> docker run -it --rm myimage
Counter: 1
Counter: 2
Counter: 3
Counter: 4
Counter: 5
^C
```

<span data-ttu-id="3913d-216">Com `docker run -it`, o comando <kbd>Ctrl+C</kbd> interromperá o processo em execução no contêiner, que, por sua vez, interrompe o contêiner.</span><span class="sxs-lookup"><span data-stu-id="3913d-216">With `docker run -it`, the <kbd>CTRL + C</kbd> command will stop process that is running in the container, which in turn, stops the container.</span></span> <span data-ttu-id="3913d-217">Como o parâmetro `--rm` foi fornecido, o contêiner é automaticamente excluído quando o processo é interrompido.</span><span class="sxs-lookup"><span data-stu-id="3913d-217">Since the `--rm` parameter was provided, the container is automatically deleted when the process is stopped.</span></span> <span data-ttu-id="3913d-218">Verifique se ele não existe:</span><span class="sxs-lookup"><span data-stu-id="3913d-218">Verify that it doesn't exist:</span></span>

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS    PORTS   NAMES
```

### <a name="change-the-entrypoint"></a><span data-ttu-id="3913d-219">Alterar o ENTRYPOINT</span><span class="sxs-lookup"><span data-stu-id="3913d-219">Change the ENTRYPOINT</span></span>

<span data-ttu-id="3913d-220">O comando `docker run` também permite modificar o comando `ENTRYPOINT` do *Dockerfile* e executar outra coisa, mas apenas para esse contêiner.</span><span class="sxs-lookup"><span data-stu-id="3913d-220">The `docker run` command also lets you modify the `ENTRYPOINT` command from the *Dockerfile* and run something else, but only for that container.</span></span> <span data-ttu-id="3913d-221">Por exemplo, use o seguinte comando para executar `bash` ou `cmd.exe`.</span><span class="sxs-lookup"><span data-stu-id="3913d-221">For example, use the following command to run `bash` or `cmd.exe`.</span></span> <span data-ttu-id="3913d-222">Edite o comando conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="3913d-222">Edit the command as necessary.</span></span>

#### <a name="windows"></a><span data-ttu-id="3913d-223">Windows</span><span class="sxs-lookup"><span data-stu-id="3913d-223">Windows</span></span>

<span data-ttu-id="3913d-224">Neste exemplo, `ENTRYPOINT` é alterado para `cmd.exe`.</span><span class="sxs-lookup"><span data-stu-id="3913d-224">In this example, `ENTRYPOINT` is changed to `cmd.exe`.</span></span> <span data-ttu-id="3913d-225"><kbd>CtRL</kbd>+<kbd>C</kbd> é pressionado para terminar o processo e parar o recipiente.</span><span class="sxs-lookup"><span data-stu-id="3913d-225"><kbd>CTRL</kbd>+<kbd>C</kbd> is pressed to end the process and stop the container.</span></span>

```console
> docker run -it --rm --entrypoint "cmd.exe" myimage

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

#### <a name="linux"></a><span data-ttu-id="3913d-226">Linux</span><span class="sxs-lookup"><span data-stu-id="3913d-226">Linux</span></span>

<span data-ttu-id="3913d-227">Neste exemplo, `ENTRYPOINT` é alterado para `bash`.</span><span class="sxs-lookup"><span data-stu-id="3913d-227">In this example, `ENTRYPOINT` is changed to `bash`.</span></span> <span data-ttu-id="3913d-228">O comando `quit` é executado, o que encerra o processo e interrompe o contêiner.</span><span class="sxs-lookup"><span data-stu-id="3913d-228">The `quit` command is run which ends the process and stop the container.</span></span>

```bash
root@user:~# docker run -it --rm --entrypoint "bash" myimage
root@8515e897c893:/# ls app
myapp.deps.json  myapp.dll  myapp.pdb  myapp.runtimeconfig.json
root@8515e897c893:/# exit
exit
```

## <a name="essential-commands"></a><span data-ttu-id="3913d-229">Comandos essenciais</span><span class="sxs-lookup"><span data-stu-id="3913d-229">Essential commands</span></span>

<span data-ttu-id="3913d-230">O Docker tem muitos comandos diferentes que englobam o que você deseja fazer com o contêiner e as imagens.</span><span class="sxs-lookup"><span data-stu-id="3913d-230">Docker has many different commands that cover what you want to do with your container and images.</span></span> <span data-ttu-id="3913d-231">Esses comandos do Docker são essenciais para gerenciar seus contêineres:</span><span class="sxs-lookup"><span data-stu-id="3913d-231">These Docker commands are essential to managing your containers:</span></span>

- [<span data-ttu-id="3913d-232">docker build</span><span class="sxs-lookup"><span data-stu-id="3913d-232">docker build</span></span>](https://docs.docker.com/engine/reference/commandline/build/)
- [<span data-ttu-id="3913d-233">docker run</span><span class="sxs-lookup"><span data-stu-id="3913d-233">docker run</span></span>](https://docs.docker.com/engine/reference/commandline/run/)
- [<span data-ttu-id="3913d-234">docker ps</span><span class="sxs-lookup"><span data-stu-id="3913d-234">docker ps</span></span>](https://docs.docker.com/engine/reference/commandline/ps/)
- [<span data-ttu-id="3913d-235">docker stop</span><span class="sxs-lookup"><span data-stu-id="3913d-235">docker stop</span></span>](https://docs.docker.com/engine/reference/commandline/stop/)
- [<span data-ttu-id="3913d-236">docker rm</span><span class="sxs-lookup"><span data-stu-id="3913d-236">docker rm</span></span>](https://docs.docker.com/engine/reference/commandline/rm/)
- [<span data-ttu-id="3913d-237">docker rmi</span><span class="sxs-lookup"><span data-stu-id="3913d-237">docker rmi</span></span>](https://docs.docker.com/engine/reference/commandline/rmi/)
- [<span data-ttu-id="3913d-238">imagem docker</span><span class="sxs-lookup"><span data-stu-id="3913d-238">docker image</span></span>](https://docs.docker.com/engine/reference/commandline/image/)

## <a name="clean-up-resources"></a><span data-ttu-id="3913d-239">Limpar recursos</span><span class="sxs-lookup"><span data-stu-id="3913d-239">Clean up resources</span></span>

<span data-ttu-id="3913d-240">Durante este tutorial, você criou contêineres e imagens.</span><span class="sxs-lookup"><span data-stu-id="3913d-240">During this tutorial, you created containers and images.</span></span> <span data-ttu-id="3913d-241">Se quiser, exclua esses recursos.</span><span class="sxs-lookup"><span data-stu-id="3913d-241">If you want, delete these resources.</span></span> <span data-ttu-id="3913d-242">Use os seguintes comandos para:</span><span class="sxs-lookup"><span data-stu-id="3913d-242">Use the following commands to</span></span>

01. <span data-ttu-id="3913d-243">Listar todos os contêineres</span><span class="sxs-lookup"><span data-stu-id="3913d-243">List all containers</span></span>

    ```console
    > docker ps -a
    ```

02. <span data-ttu-id="3913d-244">Interromper os contêineres em execução.</span><span class="sxs-lookup"><span data-stu-id="3913d-244">Stop containers that are running.</span></span> <span data-ttu-id="3913d-245">`CONTAINER_NAME` representa o nome atribuído automaticamente ao contêiner.</span><span class="sxs-lookup"><span data-stu-id="3913d-245">The `CONTAINER_NAME` represents the name automatically assigned to the container.</span></span>

    ```console
    > docker stop CONTAINER_NAME
    ```

03. <span data-ttu-id="3913d-246">Excluir o contêiner</span><span class="sxs-lookup"><span data-stu-id="3913d-246">Delete the container</span></span>

    ```console
    > docker rm CONTAINER_NAME
    ```

<span data-ttu-id="3913d-247">Em seguida, exclua todas as imagens que você não deseja mais em seu computador.</span><span class="sxs-lookup"><span data-stu-id="3913d-247">Next, delete any images that you no longer want on your machine.</span></span> <span data-ttu-id="3913d-248">Exclua a imagem criada pelo seu *Dockerfile* e exclua a imagem do .NET Core na qual o *Dockerfile* teve base.</span><span class="sxs-lookup"><span data-stu-id="3913d-248">Delete the image created by your *Dockerfile* and then delete the .NET Core image the *Dockerfile* was based on.</span></span> <span data-ttu-id="3913d-249">Você pode usar a **ID DA IMAGEM** ou a cadeia de caracteres formatada **REPOSITÓRIO:TAG**.</span><span class="sxs-lookup"><span data-stu-id="3913d-249">You can use the **IMAGE ID** or the **REPOSITORY:TAG** formatted string.</span></span>

```console
docker rmi myimage:latest
docker rmi mcr.microsoft.com/dotnet/core/aspnet:3.1
```

<span data-ttu-id="3913d-250">Use o comando `docker images` para ver uma lista de imagens instaladas.</span><span class="sxs-lookup"><span data-stu-id="3913d-250">Use the `docker images` command to see a list of images installed.</span></span>

> [!NOTE]
> <span data-ttu-id="3913d-251">Arquivos de imagem podem ser grandes.</span><span class="sxs-lookup"><span data-stu-id="3913d-251">Image files can be large.</span></span> <span data-ttu-id="3913d-252">Normalmente, você removeria contêineres temporários criados durante o teste e o desenvolvimento de seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3913d-252">Typically, you would remove temporary containers you created while testing and developing your app.</span></span> <span data-ttu-id="3913d-253">Em geral, mantenha as imagens de base com o runtime instalado se você planeja construir outras imagens com base nesse runtime.</span><span class="sxs-lookup"><span data-stu-id="3913d-253">You usually keep the base images with the runtime installed if you plan on building other images based on that runtime.</span></span>

## <a name="next-steps"></a><span data-ttu-id="3913d-254">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="3913d-254">Next steps</span></span>

- [<span data-ttu-id="3913d-255">Aprenda a colocar em contêiner um aplicativo ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="3913d-255">Learn how to containerize an ASP.NET Core application.</span></span>](/aspnet/core/host-and-deploy/docker/building-net-docker-images)
- [<span data-ttu-id="3913d-256">Experimentar o Tutorial de Microsserviço do ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="3913d-256">Try the ASP.NET Core Microservice Tutorial.</span></span>](https://dotnet.microsoft.com/learn/web/aspnet-microservice-tutorial/intro)
- [<span data-ttu-id="3913d-257">Revisar os serviços do Azure que oferecem suporte a contêineres.</span><span class="sxs-lookup"><span data-stu-id="3913d-257">Review the Azure services that support containers.</span></span>](https://azure.microsoft.com/overview/containers/)
- [<span data-ttu-id="3913d-258">Ler mais sobre os comandos do Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="3913d-258">Read about Dockerfile commands.</span></span>](https://docs.docker.com/engine/reference/builder/)
- [<span data-ttu-id="3913d-259">Explore as Ferramentas de Contêiner para Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3913d-259">Explore the Container Tools for Visual Studio</span></span>](/visualstudio/containers/overview)
