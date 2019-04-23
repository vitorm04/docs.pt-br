---
title: 'Tutorial: Colocar em contêiner um aplicativo com o Docker'
description: Neste tutorial, você aprenderá como colocar em contêiner um aplicativo .NET Core com o Docker.
ms.date: 04/10/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: fcbac0e0d17d2481d42e715a7f2790586e31d085
ms.sourcegitcommit: 8080271c246b57f4fb68c28369634bff46843424
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2019
ms.locfileid: "59553830"
---
# <a name="tutorial-containerize-a-net-core-app"></a><span data-ttu-id="88272-103">Tutorial: Colocar em contêiner um aplicativo .NET Core</span><span class="sxs-lookup"><span data-stu-id="88272-103">Tutorial: Containerize a .NET Core app</span></span>

<span data-ttu-id="88272-104">Este tutorial ensina como criar uma imagem do Docker que contenha seu aplicativo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="88272-104">This tutorial teaches you how to build a Docker image that contains your .NET Core application.</span></span> <span data-ttu-id="88272-105">A imagem pode ser usada para criar contêineres para seu ambiente de desenvolvimento local, nuvem privada ou nuvem pública.</span><span class="sxs-lookup"><span data-stu-id="88272-105">The image can be used to create containers for your local development environment, private cloud, or public cloud.</span></span>

<span data-ttu-id="88272-106">Você aprenderá a:</span><span class="sxs-lookup"><span data-stu-id="88272-106">You'll learn to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="88272-107">Criar e publicar um aplicativo .NET Core simples</span><span class="sxs-lookup"><span data-stu-id="88272-107">Create and publish a simple .NET Core app</span></span>
> * <span data-ttu-id="88272-108">Criar e configurar um Dockerfile para .NET Core</span><span class="sxs-lookup"><span data-stu-id="88272-108">Create and configure a Dockerfile for .NET Core</span></span>
> * <span data-ttu-id="88272-109">Criar uma imagem do Docker</span><span class="sxs-lookup"><span data-stu-id="88272-109">Build a Docker image</span></span>
> * <span data-ttu-id="88272-110">Criar e executar um contêiner do Docker</span><span class="sxs-lookup"><span data-stu-id="88272-110">Create and run a Docker container</span></span>

<span data-ttu-id="88272-111">Você aprenderá as tarefas de build e implantação de contêiner do Docker para um aplicativo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="88272-111">You'll understand the Docker container build and deploy tasks for a .NET Core application.</span></span> <span data-ttu-id="88272-112">A *plataforma Docker* usa o *Mecanismo do Docker* para criar e empacotar aplicativos como *imagens do Docker* com agilidade.</span><span class="sxs-lookup"><span data-stu-id="88272-112">The *Docker platform* uses the *Docker engine* to quickly build and package apps as *Docker images*.</span></span> <span data-ttu-id="88272-113">Essas imagens são gravadas no formato *Dockerfile* para serem implantadas e executadas em um contêiner em camadas.</span><span class="sxs-lookup"><span data-stu-id="88272-113">These images are written in the *Dockerfile* format to be deployed and run in a layered container.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="88272-114">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="88272-114">Prerequisites</span></span>

<span data-ttu-id="88272-115">Instale os seguintes pré-requisitos:</span><span class="sxs-lookup"><span data-stu-id="88272-115">Install the following prerequisites:</span></span>

- <span data-ttu-id="88272-116">[SDK do .NET Core 2.2](https://dotnet.microsoft.com/download)\\</span><span class="sxs-lookup"><span data-stu-id="88272-116">[.NET Core 2.2 SDK](https://dotnet.microsoft.com/download)\\</span></span>
<span data-ttu-id="88272-117">Se você tiver o .NET Core instalado, use o comando `dotnet --info` para determinar qual SDK está usando.</span><span class="sxs-lookup"><span data-stu-id="88272-117">If you have .NET Core installed, use the `dotnet --info` command to determine which SDK you're using.</span></span>

- [<span data-ttu-id="88272-118">Docker Community Edition</span><span class="sxs-lookup"><span data-stu-id="88272-118">Docker Community Edition</span></span>](https://www.docker.com/products/docker-desktop)

- <span data-ttu-id="88272-119">Um diretório de trabalho temporário para o *Dockerfile* e o aplicativo de exemplo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="88272-119">A temporary working directory for the *Dockerfile* and .NET Core example app.</span></span>

### <a name="use-sdk-version-22"></a><span data-ttu-id="88272-120">Use a versão 2.2 do SDK</span><span class="sxs-lookup"><span data-stu-id="88272-120">Use SDK version 2.2</span></span>

<span data-ttu-id="88272-121">Se você estiver usando um SDK mais recente, como o 3.0, certifique-se de que seu aplicativo seja forçado a usar o SDK 2.2.</span><span class="sxs-lookup"><span data-stu-id="88272-121">If you're using an SDK that is newer, like 3.0, make sure that your app is forced to use the 2.2 SDK.</span></span> <span data-ttu-id="88272-122">Crie um arquivo chamado `global.json` no seu diretório de trabalho e cole o seguinte código json:</span><span class="sxs-lookup"><span data-stu-id="88272-122">Create a file named `global.json` in your working directory and paste in the following json code:</span></span>

```json
{
  "sdk": {
    "version": "2.2.100"
  }
}
```

<span data-ttu-id="88272-123">Salve esse arquivo.</span><span class="sxs-lookup"><span data-stu-id="88272-123">Save this file.</span></span> <span data-ttu-id="88272-124">A presença do arquivo forçará o .NET Core a usar a versão 2.2 para qualquer comando `dotnet` chamado deste diretório e abaixo.</span><span class="sxs-lookup"><span data-stu-id="88272-124">The presence of file will force .NET Core to use version 2.2 for any `dotnet` command called from this directory and below.</span></span>

## <a name="create-net-core-app"></a><span data-ttu-id="88272-125">Criar um aplicativo .NET Core</span><span class="sxs-lookup"><span data-stu-id="88272-125">Create .NET Core app</span></span>

<span data-ttu-id="88272-126">Você precisa de um aplicativo .NET Core que o contêiner do Docker irá executar.</span><span class="sxs-lookup"><span data-stu-id="88272-126">You need a .NET Core app that the Docker container will run.</span></span> <span data-ttu-id="88272-127">Abra seu terminal, crie um diretório de trabalho e insira-o.</span><span class="sxs-lookup"><span data-stu-id="88272-127">Open your terminal, create a working directory, and enter it.</span></span> <span data-ttu-id="88272-128">No diretório de trabalho, execute o seguinte comando para criar um novo projeto em um subdiretório denominado app:</span><span class="sxs-lookup"><span data-stu-id="88272-128">In the working directory, run the following command to create a new project in a subdirectory named app:</span></span>

```console
dotnet new console -o app -n myapp
```

<span data-ttu-id="88272-129">Esse comando cria um novo diretório chamado *app* e gera um aplicativo "Olá, Mundo".</span><span class="sxs-lookup"><span data-stu-id="88272-129">That command creates a new directory named *app* and generates a "Hello World" app.</span></span> <span data-ttu-id="88272-130">Você pode testar esse aplicativo para ver o que ele faz.</span><span class="sxs-lookup"><span data-stu-id="88272-130">You can test this app to see what it does.</span></span> <span data-ttu-id="88272-131">Insira o diretório *app* e execute o comando `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="88272-131">Enter the *app* directory and execute the command `dotnet run`.</span></span> <span data-ttu-id="88272-132">Você verá a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="88272-132">You'll see the following output:</span></span>

```console
> dotnet run
Hello World!
```

<span data-ttu-id="88272-133">O modelo padrão cria um aplicativo que imprime no terminal e, em seguida, sai.</span><span class="sxs-lookup"><span data-stu-id="88272-133">The default template creates an app that prints to the terminal and then exits.</span></span> <span data-ttu-id="88272-134">Neste tutorial, você usará um aplicativo que faz um loop indefinidamente.</span><span class="sxs-lookup"><span data-stu-id="88272-134">For this tutorial, you'll use an app that loops indefinitely.</span></span> <span data-ttu-id="88272-135">Abra o arquivo **Program.cs** em um editor de texto.</span><span class="sxs-lookup"><span data-stu-id="88272-135">Open the **Program.cs** file in a text editor.</span></span> <span data-ttu-id="88272-136">Ele deve se parecer com o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="88272-136">It should currently look like the following code:</span></span>

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

<span data-ttu-id="88272-137">Substitua o arquivo pelo seguinte código que conta os números a cada segundo:</span><span class="sxs-lookup"><span data-stu-id="88272-137">Replace the file with the following code that counts numbers every second:</span></span>

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
            while(max == -1 || counter < max)
            {
                counter++;
                Console.WriteLine($"Counter: {counter}");
                System.Threading.Tasks.Task.Delay(1000).Wait();
            }
        }
    }
}
```

<span data-ttu-id="88272-138">Salve o arquivo e teste o programa novamente com `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="88272-138">Save the file and test the program again with `dotnet run`.</span></span> <span data-ttu-id="88272-139">Lembre-se de que esse aplicativo é executado indefinidamente.</span><span class="sxs-lookup"><span data-stu-id="88272-139">Remember that this app runs indefinitely.</span></span> <span data-ttu-id="88272-140">Use o comando de cancelamento <kbd>Ctrl+C</kbd> para interrompê-lo.</span><span class="sxs-lookup"><span data-stu-id="88272-140">Use the cancel command <kbd>CTRL + C</kbd> to stop it.</span></span> <span data-ttu-id="88272-141">Você verá a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="88272-141">You'll see the following output:</span></span>

```console
> dotnet run
Counter: 1
Counter: 2
Counter: 3
Counter: 4
^C
```

<span data-ttu-id="88272-142">Se você passar um número na linha de comando para o aplicativo, ele apenas contará até tal valor e, em seguida, sairá.</span><span class="sxs-lookup"><span data-stu-id="88272-142">If you pass a number on the command line to the app, it will only count up to that amount and then exit.</span></span> <span data-ttu-id="88272-143">Experimente com `dotnet run -- 5` para contar até cinco.</span><span class="sxs-lookup"><span data-stu-id="88272-143">Try it with `dotnet run -- 5` to count to five.</span></span>

> [!NOTE]
> <span data-ttu-id="88272-144">Quaisquer parâmetros após `--` são passados para o seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="88272-144">Any parameters after `--` are passed to your application.</span></span>

## <a name="publish-net-core-app"></a><span data-ttu-id="88272-145">Publicar um aplicativo .NET Core</span><span class="sxs-lookup"><span data-stu-id="88272-145">Publish .NET Core app</span></span>

<span data-ttu-id="88272-146">Antes de adicionar seu aplicativo .NET Core à imagem do Docker, publique-o.</span><span class="sxs-lookup"><span data-stu-id="88272-146">Before you add your .NET Core app to the Docker image, publish it.</span></span> <span data-ttu-id="88272-147">O contêiner executará a versão publicada do aplicativo quando for iniciado.</span><span class="sxs-lookup"><span data-stu-id="88272-147">The container will execute the published version of the app when it's started.</span></span>

<span data-ttu-id="88272-148">No diretório de trabalho, insira o diretório **app** com o código-fonte do exemplo e execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="88272-148">From the working directory, enter the **app** directory with the example source code and run the following command:</span></span>

```console
dotnet publish -c Release
```

<span data-ttu-id="88272-149">Esse comando compila seu aplicativo para a pasta **publish** na pasta de saída do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="88272-149">This command compiles your app to the **publish** folder in the output folder of your app.</span></span> <span data-ttu-id="88272-150">O caminho para a pasta **publish** do diretório de trabalho deve ser `.\app\bin\Release\netcoreapp2.2\publish\`</span><span class="sxs-lookup"><span data-stu-id="88272-150">The path to the **publish** folder from the working directory should be `.\app\bin\Release\netcoreapp2.2\publish\`</span></span>

<span data-ttu-id="88272-151">Obtenha uma listagem de diretórios da pasta de publicação para verificar se o **myapp.dll** foi criado.</span><span class="sxs-lookup"><span data-stu-id="88272-151">Get a directory listing of the publish folder to verify that the **myapp.dll** was created.</span></span> <span data-ttu-id="88272-152">No diretório **app**, execute um dos seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="88272-152">From the **app** directory, run one of the following commands:</span></span>

```console
> dir bin\Release\netcoreapp2.2\publish
 Directory of C:\path-to-working-dir\app\bin\Release\netcoreapp2.2\publish

04/05/2019  11:00 AM    <DIR>          .
04/05/2019  11:00 AM    <DIR>          ..
04/05/2019  11:00 AM               447 myapp.deps.json
04/05/2019  11:00 AM             4,608 myapp.dll
04/05/2019  11:00 AM               448 myapp.pdb
04/05/2019  11:00 AM               154 myapp.runtimeconfig.json
```

```bash
me@DESKTOP:/path-to-working-dir/app$ ls bin/Release/netcoreapp2.2/publish
myapp.deps.json  myapp.dll  myapp.pdb  myapp.runtimeconfig.json
```

<span data-ttu-id="88272-153">No seu terminal, suba um diretório para o diretório de trabalho.</span><span class="sxs-lookup"><span data-stu-id="88272-153">In your terminal, go up a directory to the working directory.</span></span>

## <a name="create-the-dockerfile"></a><span data-ttu-id="88272-154">Criar o Dockerfile</span><span class="sxs-lookup"><span data-stu-id="88272-154">Create the Dockerfile</span></span>

<span data-ttu-id="88272-155">O arquivo *Dockerfile* é usado pelo comando `docker build` para criar uma imagem de contêiner.</span><span class="sxs-lookup"><span data-stu-id="88272-155">The *Dockerfile* file is used by the `docker build` command to create a container image.</span></span> <span data-ttu-id="88272-156">Esse arquivo é um arquivo de texto não criptografado chamado *Dockerfile* que não possui uma extensão.</span><span class="sxs-lookup"><span data-stu-id="88272-156">This file is a plaintext file named *Dockerfile* that does not have an extension.</span></span> <span data-ttu-id="88272-157">Crie um arquivo chamado *Dockerfile* em seu diretório de trabalho e abra-o em um editor de texto.</span><span class="sxs-lookup"><span data-stu-id="88272-157">Create a file named *Dockerfile* in your working directory and open it in a text editor.</span></span> <span data-ttu-id="88272-158">Adicione o seguinte comando como a primeira linha do arquivo:</span><span class="sxs-lookup"><span data-stu-id="88272-158">Add the following command as the first line of the file:</span></span>

```dockerfile
FROM mcr.microsoft.com/dotnet/core/runtime:2.2
```

<span data-ttu-id="88272-159">O comando `FROM` instrui o Docker a extrair a imagem marcada **2.2** do repositório **mcr.microsoft.com/dotnet/core/runtime**.</span><span class="sxs-lookup"><span data-stu-id="88272-159">The `FROM` command tells Docker to pull down the image tagged **2.2** from the **mcr.microsoft.com/dotnet/core/runtime** repository.</span></span> <span data-ttu-id="88272-160">Certifique-se de executar o tempo de execução do .NET Core que corresponda ao tempo de execução direcionado pelo seu SDK.</span><span class="sxs-lookup"><span data-stu-id="88272-160">Make sure that you pull the .NET Core runtime that matches the runtime targeted by your SDK.</span></span> <span data-ttu-id="88272-161">Por exemplo, o aplicativo criado na seção anterior usou o SDK do .NET Core 2.2 e criou um aplicativo destinado ao .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="88272-161">For example, the app created in the previous section used the .NET Core 2.2 SDK and created an app that targeted .NET Core 2.2.</span></span> <span data-ttu-id="88272-162">Portanto, a imagem de base mencionada no *Dockerfile* é marcada com **2.2**.</span><span class="sxs-lookup"><span data-stu-id="88272-162">So the base image referred to in the *Dockerfile* is tagged with **2.2**.</span></span>

<span data-ttu-id="88272-163">Salve o arquivo.</span><span class="sxs-lookup"><span data-stu-id="88272-163">Save the file.</span></span> <span data-ttu-id="88272-164">No seu terminal, execute `docker build -t myimage .`, e o Docker processará cada linha no *Dockerfile*.</span><span class="sxs-lookup"><span data-stu-id="88272-164">From your terminal, run `docker build -t myimage .` and Docker will process each line in the *Dockerfile*.</span></span> <span data-ttu-id="88272-165">O `.` no comando `docker build` instrui o docker a usar o diretório atual para encontrar um *Dockerfile*.</span><span class="sxs-lookup"><span data-stu-id="88272-165">The `.` in the `docker build` command tells docker to use the current directory to find a *Dockerfile*.</span></span> <span data-ttu-id="88272-166">Esse comando constrói a imagem e cria um repositório local chamado **myimage** que aponta para essa imagem.</span><span class="sxs-lookup"><span data-stu-id="88272-166">This command builds the image and creates a local repository named **myimage** that points to that image.</span></span> <span data-ttu-id="88272-167">Após a conclusão desse comando, execute `docker images` para ver uma lista de imagens instaladas:</span><span class="sxs-lookup"><span data-stu-id="88272-167">After this command finishes, run `docker images` to see a list of images installed:</span></span>

```console
> docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
mcr.microsoft.com/dotnet/core/runtime   2.2                 d51bb4452469        2 days ago          314MB
myimage                                 latest              d51bb4452469        2 days ago          314MB
```

<span data-ttu-id="88272-168">Observe que as duas imagens compartilham o mesmo valor de **ID DA IMAGEM**.</span><span class="sxs-lookup"><span data-stu-id="88272-168">Notice that the two images share the same **IMAGE ID** value.</span></span> <span data-ttu-id="88272-169">O valor é o mesmo entre as duas imagens porque o único comando no *Dockerfile* era basear a nova imagem em uma imagem existente.</span><span class="sxs-lookup"><span data-stu-id="88272-169">The value is the same between both images because the only command in the *Dockerfile* was to base the new image on an existing image.</span></span> <span data-ttu-id="88272-170">Vamos adicionar dois comandos ao *Dockerfile*.</span><span class="sxs-lookup"><span data-stu-id="88272-170">Let's add two commands to the *Dockerfile*.</span></span> <span data-ttu-id="88272-171">Cada comando cria uma nova camada de imagem com o comando final representando a imagem para aqual o repositório **myimage** apontará.</span><span class="sxs-lookup"><span data-stu-id="88272-171">Each command creates a new image layer with the final command representing the image the **myimage** repository will point to.</span></span>

```dockerfile
COPY app/bin/Release/netcoreapp2.2/publish/ app/

ENTRYPOINT ["dotnet", "app/myapp.dll"]
```

<span data-ttu-id="88272-172">O comando `COPY` informa ao Docker para copiar a pasta especificada em seu computador para uma pasta no contêiner.</span><span class="sxs-lookup"><span data-stu-id="88272-172">The `COPY` command tells Docker to copy the specified folder on your computer to a folder in the container.</span></span> <span data-ttu-id="88272-173">Nesse exemplo, a pasta **publish** é copiada para uma pasta chamada **app** no contêiner.</span><span class="sxs-lookup"><span data-stu-id="88272-173">In this example, the **publish** folder is copied to a folder named **app** in the container.</span></span>

<span data-ttu-id="88272-174">O próximo comando, `ENTRYPOINT`, informa ao docker para configurar o contêiner para ser executado como um executável.</span><span class="sxs-lookup"><span data-stu-id="88272-174">The next command, `ENTRYPOINT`, tells docker to configure the container to run as an executable.</span></span> <span data-ttu-id="88272-175">Quando o contêiner é iniciado, o comando `ENTRYPOINT` é executado.</span><span class="sxs-lookup"><span data-stu-id="88272-175">When the container starts, the `ENTRYPOINT` command runs.</span></span> <span data-ttu-id="88272-176">Quando esse comando terminar, o contêiner será interrompido automaticamente.</span><span class="sxs-lookup"><span data-stu-id="88272-176">When this command ends, the container will automatically stop.</span></span>

<span data-ttu-id="88272-177">Salve o arquivo.</span><span class="sxs-lookup"><span data-stu-id="88272-177">Save the file.</span></span> <span data-ttu-id="88272-178">No seu terminal, execute `docker build -t myimage .` e, quando o comando terminar, execute `docker images`.</span><span class="sxs-lookup"><span data-stu-id="88272-178">From your terminal, run `docker build -t myimage .` and when that command finishes, run `docker images`.</span></span>

```console
> docker build -t myimage .
Sending build context to Docker daemon  819.7kB
Step 1/3 : FROM mcr.microsoft.com/dotnet/core/runtime:2.2
 ---> d51bb4452469
Step 2/3 : COPY app/bin/Release/netcoreapp2.2/publish/ app/
 ---> a1e98ac62017
Step 3/3 : ENTRYPOINT ["dotnet", "app/myapp.dll"]
 ---> Running in f34da5c18e7c
Removing intermediate container f34da5c18e7c
 ---> ddcc6646461b
Successfully built ddcc6646461b
Successfully tagged myimage:latest


> docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
myimage                                 latest              ddcc6646461b        10 seconds ago      314MB
mcr.microsoft.com/dotnet/core/runtime   2.2                 d51bb4452469        2 days ago          314MB
```

<span data-ttu-id="88272-179">Cada comando no *Dockerfile* gerou uma camada e criou uma **ID DA IMAGEM**.</span><span class="sxs-lookup"><span data-stu-id="88272-179">Each command in the *Dockerfile* generated a layer and created an **IMAGE ID**.</span></span> <span data-ttu-id="88272-180">A **ID DA IMAGEM** final (a sua será diferente) é **ddcc6646461b** e, a seguir, você criará um contêiner baseado nessa imagem.</span><span class="sxs-lookup"><span data-stu-id="88272-180">The final **IMAGE ID** (yours will be different) is **ddcc6646461b** and next you'll create a container based on this image.</span></span>

## <a name="create-a-container"></a><span data-ttu-id="88272-181">Criar um contêiner</span><span class="sxs-lookup"><span data-stu-id="88272-181">Create a container</span></span>

<span data-ttu-id="88272-182">Agora que você tem uma imagem que contém o seu aplicativo, você pode criar um contêiner.</span><span class="sxs-lookup"><span data-stu-id="88272-182">Now that you have an image that contains your app, you can create a container.</span></span> <span data-ttu-id="88272-183">Você pode criar um contêiner de duas maneiras.</span><span class="sxs-lookup"><span data-stu-id="88272-183">You can create a container in two ways.</span></span> <span data-ttu-id="88272-184">Primeiro, criar um novo contêiner que foi interrompido.</span><span class="sxs-lookup"><span data-stu-id="88272-184">First, create a new container that is stopped.</span></span>

```console
> docker create myimage
0e8f3c2ca32ce773712a5cca38750f41259a4e54e04bdf0946087e230ad7066c
```

<span data-ttu-id="88272-185">O comando `docker create` acima criará um contêiner baseado na imagem **myimage**.</span><span class="sxs-lookup"><span data-stu-id="88272-185">The `docker create` command from above will create a container based on the **myimage** image.</span></span> <span data-ttu-id="88272-186">A saída desse comando mostra a **ID DO CONTÊINER** (a sua será diferente) do contêiner criado.</span><span class="sxs-lookup"><span data-stu-id="88272-186">The output of that command shows you the **CONTAINER ID** (yours will be different) of the created container.</span></span> <span data-ttu-id="88272-187">Para ver uma lista de *todos* os contêineres, use o comando `docker ps -a`:</span><span class="sxs-lookup"><span data-stu-id="88272-187">To see a list of *all* containers, use the `docker ps -a` command:</span></span>

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS        PORTS   NAMES
0e8f3c2ca32c        myimage             "dotnet app/myapp.dll"   4 seconds ago       Created               boring_matsumoto
```

### <a name="manage-the-container"></a><span data-ttu-id="88272-188">Gerenciar o contêiner</span><span class="sxs-lookup"><span data-stu-id="88272-188">Manage the container</span></span>

<span data-ttu-id="88272-189">Cada contêiner é atribuído a um nome aleatório que você pode usar para se referir a essa instância de contêiner.</span><span class="sxs-lookup"><span data-stu-id="88272-189">Each container is assigned a random name that you can use to refer to that container instance.</span></span> <span data-ttu-id="88272-190">Por exemplo, o contêiner criado automaticamente escolheu o nome **boring_matsumoto** (o seu será diferente), e esse nome pode ser usado para iniciar o contêiner.</span><span class="sxs-lookup"><span data-stu-id="88272-190">For example, the container that was created automatically chose the name **boring_matsumoto** (yours will be different) and that name can be used to start the container.</span></span> <span data-ttu-id="88272-191">Você substitui o nome automático por um específico usando o parâmetro `docker create --name`.</span><span class="sxs-lookup"><span data-stu-id="88272-191">You override the automatic name with a specific one by using the `docker create --name` parameter.</span></span>

<span data-ttu-id="88272-192">O exemplo a seguir usa o comando `docker start` para iniciar o contêiner e, em seguida, usa o comando `docker ps` para mostrar apenas os contêineres em execução:</span><span class="sxs-lookup"><span data-stu-id="88272-192">The following example uses the `docker start` command to start the container, and then uses the `docker ps` command to only show containers that are running:</span></span>

```console
> docker start boring_matsumoto
boring_matsumoto

> docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS         PORTS   NAMES
0e8f3c2ca32c        myimage             "dotnet app/myapp.dll"   7 minutes ago       Up 8 seconds           boring_matsumoto
```

<span data-ttu-id="88272-193">Da mesma forma, o comando `docker stop` interromperá o contêiner.</span><span class="sxs-lookup"><span data-stu-id="88272-193">Similarly, the `docker stop` command will stop the container.</span></span> <span data-ttu-id="88272-194">O exemplo a seguir usa o comando `docker stop` para interromper o contêiner e, em seguida, usa o comando `docker ps` para mostrar que nenhum contêiner está em execução.</span><span class="sxs-lookup"><span data-stu-id="88272-194">The following example uses the `docker stop` command to stop the container, and then uses the `docker ps` command to show that no containers are running.</span></span>

```console
> docker stop boring_matsumoto
boring_matsumoto

> docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS     PORTS   NAMES
```

### <a name="connect-to-a-container"></a><span data-ttu-id="88272-195">Conectar-se a um contêiner</span><span class="sxs-lookup"><span data-stu-id="88272-195">Connect to a container</span></span>

<span data-ttu-id="88272-196">Depois que um contêiner estiver em execução, você poderá se conectar a ele para ver a saída.</span><span class="sxs-lookup"><span data-stu-id="88272-196">After a container is running, you can connect to it to see the output.</span></span> <span data-ttu-id="88272-197">Use os comandos `docker start` e `docker attach` para iniciar o contêiner e inspecionar o fluxo de saída.</span><span class="sxs-lookup"><span data-stu-id="88272-197">Use the `docker start` and `docker attach` commands to start the container and peek at the output stream.</span></span> <span data-ttu-id="88272-198">Neste exemplo, o comando <kbd>Ctrl+C</kbd> é usado para desanexar do contêiner em execução.</span><span class="sxs-lookup"><span data-stu-id="88272-198">In this example, the <kbd>CTRL + C</kbd> command is used to detach from the running container.</span></span> <span data-ttu-id="88272-199">Isso pode realmente encerrar o processo no contêiner, o que interromperá o contêiner.</span><span class="sxs-lookup"><span data-stu-id="88272-199">This may actually end the process in the container, which will stop the container.</span></span> <span data-ttu-id="88272-200">O parâmetro `--sig-proxy=false` garante que <kbd>Ctrl+C</kbd> não interrompa o processo no contêiner.</span><span class="sxs-lookup"><span data-stu-id="88272-200">The `--sig-proxy=false` parameter ensures that <kbd>CTRL + C</kbd> will not stop the process in the container.</span></span>

<span data-ttu-id="88272-201">Depois de desanexar do contêiner, reanexe para verificar se ele ainda está em execução e contando.</span><span class="sxs-lookup"><span data-stu-id="88272-201">After you detach from the container, reattach to verify that it's still running and counting.</span></span>

```console
> docker start boring_matsumoto
boring_matsumoto

> docker attach --sig-proxy=false boring_matsumoto
Counter: 7
Counter: 8
Counter: 9
^C

> docker attach --sig-proxy=false boring_matsumoto
Counter: 17
Counter: 18
Counter: 19
^C
```

### <a name="delete-a-container"></a><span data-ttu-id="88272-202">Criar um contêiner</span><span class="sxs-lookup"><span data-stu-id="88272-202">Delete a container</span></span>

<span data-ttu-id="88272-203">Para os fins desse artigo, você não quer contêineres sem função alguma.</span><span class="sxs-lookup"><span data-stu-id="88272-203">For the purposes of this article you don't want containers just hanging around doing nothing.</span></span> <span data-ttu-id="88272-204">Exclua o contêiner que você criou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="88272-204">Delete the container you previously created.</span></span> <span data-ttu-id="88272-205">Se o contêiner estiver em execução, interrompa-o.</span><span class="sxs-lookup"><span data-stu-id="88272-205">If the container is running, stop it.</span></span>

```console
> docker stop boring_matsumoto
```

<span data-ttu-id="88272-206">O exemplo a seguir lista todos os contêineres.</span><span class="sxs-lookup"><span data-stu-id="88272-206">The following example lists all containers.</span></span> <span data-ttu-id="88272-207">Em seguida, ele usa o comando `docker rm` para excluir o contêiner e, em seguida, verifica uma segunda vez para verificar qualquer contêiner em execução.</span><span class="sxs-lookup"><span data-stu-id="88272-207">It then uses the `docker rm` command to delete the container, and then checks a second time for any running containers.</span></span>

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS     PORTS   NAMES
0e8f3c2ca32c        myimage             "dotnet app/myapp.dll"   19 minutes ago      Exited             boring_matsumoto

> docker rm boring_matsumoto
boring_matsumoto

> docker ps -a
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS     PORTS    NAMES
```

### <a name="single-run"></a><span data-ttu-id="88272-208">Execução única</span><span class="sxs-lookup"><span data-stu-id="88272-208">Single run</span></span>

<span data-ttu-id="88272-209">O Docker fornece o comando `docker run` para criar e executar o contêiner como um único comando.</span><span class="sxs-lookup"><span data-stu-id="88272-209">Docker provides the `docker run` command to create and run the container as a single command.</span></span> <span data-ttu-id="88272-210">Este comando elimina a necessidade de executar `docker create` e, em seguida, `docker start`.</span><span class="sxs-lookup"><span data-stu-id="88272-210">This command eliminates the need to run `docker create` and then `docker start`.</span></span> <span data-ttu-id="88272-211">Você também pode definir esse comando para excluir automaticamente o contêiner quando o contêiner for interrompido.</span><span class="sxs-lookup"><span data-stu-id="88272-211">You can also set this command to automatically delete the container when the container stops.</span></span> <span data-ttu-id="88272-212">Por exemplo, use `docker run -it --rm` para fazer duas coisas: primeiro, use automaticamente o terminal atual para se conectar ao contêiner e, quando o contêiner terminar, remova-o:</span><span class="sxs-lookup"><span data-stu-id="88272-212">For example, use `docker run -it --rm` to do two things, first, automatically use the current terminal to connect to the container, and then when the container finishes, remove it:</span></span>

```
> docker run -it --rm myimage
Counter: 1
Counter: 2
Counter: 3
Counter: 4
Counter: 5
^C
```

<span data-ttu-id="88272-213">Com `docker run -it`, o comando <kbd>Ctrl+C</kbd> interromperá o processo em execução no contêiner, que, por sua vez, interrompe o contêiner.</span><span class="sxs-lookup"><span data-stu-id="88272-213">With `docker run -it`, the <kbd>CTRL + C</kbd> command will stop process that is running in the container, which in turn, stops the container.</span></span> <span data-ttu-id="88272-214">Como o parâmetro `--rm` foi fornecido, o contêiner é automaticamente excluído quando o processo é interrompido.</span><span class="sxs-lookup"><span data-stu-id="88272-214">Since the `--rm` parameter was provided, the container is automatically deleted when the process is stopped.</span></span> <span data-ttu-id="88272-215">Verifique se ele não existe:</span><span class="sxs-lookup"><span data-stu-id="88272-215">Verify that it does not exist:</span></span>

```
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS    PORTS   NAMES
```

### <a name="change-the-entrypoint"></a><span data-ttu-id="88272-216">Alterar o ENTRYPOINT</span><span class="sxs-lookup"><span data-stu-id="88272-216">Change the ENTRYPOINT</span></span>

<span data-ttu-id="88272-217">O comando `docker run` também permite modificar o comando `ENTRYPOINT` do *Dockerfile* e executar outra coisa, mas apenas para esse contêiner.</span><span class="sxs-lookup"><span data-stu-id="88272-217">The `docker run` command also lets you modify the `ENTRYPOINT` command from the *Dockerfile* and run something else, but only for that container.</span></span> <span data-ttu-id="88272-218">Por exemplo, use o seguinte comando para executar `bash` ou `cmd.exe`.</span><span class="sxs-lookup"><span data-stu-id="88272-218">For example, use the following command to run `bash` or `cmd.exe`.</span></span> <span data-ttu-id="88272-219">Edite o comando conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="88272-219">Edit the command as necessary.</span></span>

#### <a name="windows"></a><span data-ttu-id="88272-220">Windows</span><span class="sxs-lookup"><span data-stu-id="88272-220">Windows</span></span>
<span data-ttu-id="88272-221">Neste exemplo o `ENTRYPOINT` é alterado para `cmd.exe`.</span><span class="sxs-lookup"><span data-stu-id="88272-221">In this example the `ENTRYPOINT` is changed to `cmd.exe`.</span></span> <span data-ttu-id="88272-222"><kbd>Ctrl+C</kbd> é pressionado para finalizar o processo e interromper o contêiner.</span><span class="sxs-lookup"><span data-stu-id="88272-222"><kbd>CTRL + C</kbd> is pressed to end the process and stop the container.</span></span>

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

#### <a name="linux"></a><span data-ttu-id="88272-223">Linux</span><span class="sxs-lookup"><span data-stu-id="88272-223">Linux</span></span>

<span data-ttu-id="88272-224">Neste exemplo, o `ENTRYPOINT` é alterado para `bash`.</span><span class="sxs-lookup"><span data-stu-id="88272-224">In this example the `ENTRYPOINT` is changed to `bash`.</span></span> <span data-ttu-id="88272-225">O comando `quit` é executado, o que encerra o processo e interrompe o contêiner.</span><span class="sxs-lookup"><span data-stu-id="88272-225">The `quit` command is run which ends the process and stop the container.</span></span>

```bash
root@user:~# docker run -it --rm --entrypoint "bash" myimage
root@8515e897c893:/# ls app
myapp.deps.json  myapp.dll  myapp.pdb  myapp.runtimeconfig.json
root@8515e897c893:/# exit
exit
```

## <a name="essential-commands"></a><span data-ttu-id="88272-226">Comandos essenciais</span><span class="sxs-lookup"><span data-stu-id="88272-226">Essential commands</span></span>

<span data-ttu-id="88272-227">O Docker tem muitos comandos diferentes que englobam o que você deseja fazer com o contêiner e as imagens.</span><span class="sxs-lookup"><span data-stu-id="88272-227">Docker has many different commands that cover what you want to do with your container and images.</span></span> <span data-ttu-id="88272-228">Esses comandos do Docker são essenciais para gerenciar seus contêineres:</span><span class="sxs-lookup"><span data-stu-id="88272-228">These Docker commands are essential to managing your containers:</span></span>

* [<span data-ttu-id="88272-229">docker build</span><span class="sxs-lookup"><span data-stu-id="88272-229">docker build</span></span>](https://docs.docker.com/engine/reference/commandline/build/)
* [<span data-ttu-id="88272-230">docker run</span><span class="sxs-lookup"><span data-stu-id="88272-230">docker run</span></span>](https://docs.docker.com/engine/reference/commandline/run/)
* [<span data-ttu-id="88272-231">docker ps</span><span class="sxs-lookup"><span data-stu-id="88272-231">docker ps</span></span>](https://docs.docker.com/engine/reference/commandline/ps/)
* [<span data-ttu-id="88272-232">docker stop</span><span class="sxs-lookup"><span data-stu-id="88272-232">docker stop</span></span>](https://docs.docker.com/engine/reference/commandline/stop/)
* [<span data-ttu-id="88272-233">docker rm</span><span class="sxs-lookup"><span data-stu-id="88272-233">docker rm</span></span>](https://docs.docker.com/engine/reference/commandline/rm/)
* [<span data-ttu-id="88272-234">docker rmi</span><span class="sxs-lookup"><span data-stu-id="88272-234">docker rmi</span></span>](https://docs.docker.com/engine/reference/commandline/rmi/)
* [<span data-ttu-id="88272-235">docker image</span><span class="sxs-lookup"><span data-stu-id="88272-235">docker image</span></span>](https://docs.docker.com/engine/reference/commandline/image/)

## <a name="clean-up-resources"></a><span data-ttu-id="88272-236">Limpar recursos</span><span class="sxs-lookup"><span data-stu-id="88272-236">Clean up resources</span></span>

<span data-ttu-id="88272-237">Durante este tutorial, você criou contêineres e imagens.</span><span class="sxs-lookup"><span data-stu-id="88272-237">During this tutorial you created containers and images.</span></span> <span data-ttu-id="88272-238">Se quiser, exclua esses recursos.</span><span class="sxs-lookup"><span data-stu-id="88272-238">If you want, delete these resources.</span></span> <span data-ttu-id="88272-239">Use os seguintes comandos para:</span><span class="sxs-lookup"><span data-stu-id="88272-239">Use the following commands to</span></span>

01. <span data-ttu-id="88272-240">Listar todos os contêineres</span><span class="sxs-lookup"><span data-stu-id="88272-240">List all containers</span></span>

    ```console
    > docker ps -a
    ```

02. <span data-ttu-id="88272-241">Interromper os contêineres em execução.</span><span class="sxs-lookup"><span data-stu-id="88272-241">Stop containers that are running.</span></span> <span data-ttu-id="88272-242">`CONTAINER_NAME` representa o nome atribuído automaticamente ao contêiner.</span><span class="sxs-lookup"><span data-stu-id="88272-242">The `CONTAINER_NAME` represents the name automatically assigned to the container.</span></span>

    ```console
    > docker stop CONTAINER_NAME
    ```

03. <span data-ttu-id="88272-243">Excluir o contêiner</span><span class="sxs-lookup"><span data-stu-id="88272-243">Delete the container</span></span>

    ```console
    > docker rm CONTAINER_NAME
    ```

<span data-ttu-id="88272-244">Em seguida, exclua todas as imagens que você não deseja mais em seu computador.</span><span class="sxs-lookup"><span data-stu-id="88272-244">Next, delete any images that you no longer want on your machine.</span></span> <span data-ttu-id="88272-245">Exclua a imagem criada pelo seu *Dockerfile* e exclua a imagem do .NET Core na qual o *Dockerfile* teve base.</span><span class="sxs-lookup"><span data-stu-id="88272-245">Delete the image created by your *Dockerfile* and then delete the .NET Core image the *Dockerfile* was based on.</span></span> <span data-ttu-id="88272-246">Você pode usar a **ID DA IMAGEM** ou a cadeia de caracteres formatada **REPOSITÓRIO:TAG**.</span><span class="sxs-lookup"><span data-stu-id="88272-246">You can use the **IMAGE ID** or the **REPOSITORY:TAG** formatted string.</span></span>

```console
docker rmi myimage:latest
docker rmi mcr.microsoft.com/dotnet/core/runtime:2.2
```

<span data-ttu-id="88272-247">Use o comando `docker images` para ver uma lista de imagens instaladas.</span><span class="sxs-lookup"><span data-stu-id="88272-247">Use the `docker images` command to see a list of images installed.</span></span>

> [!NOTE]
> <span data-ttu-id="88272-248">Arquivos de imagem podem ser grandes.</span><span class="sxs-lookup"><span data-stu-id="88272-248">Image files can be large.</span></span> <span data-ttu-id="88272-249">Normalmente, você removeria contêineres temporários criados durante o teste e o desenvolvimento de seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="88272-249">Typically, you would remove temporary containers you created while testing and developing your app.</span></span> <span data-ttu-id="88272-250">Em geral, mantenha as imagens de base com o tempo de execução instalado se você planeja construir outras imagens com base nesse tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="88272-250">You usually keep the base images with the runtime installed if you plan on building other images based on that runtime.</span></span>

## <a name="next-steps"></a><span data-ttu-id="88272-251">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="88272-251">Next steps</span></span>

* [<span data-ttu-id="88272-252">Experimentar o Tutorial de Microsserviço do ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="88272-252">Try the ASP.NET Core Microservice Tutorial.</span></span>](https://dotnet.microsoft.com/learn/web/aspnet-microservice-tutorial/intro)
* [<span data-ttu-id="88272-253">Revisar os serviços do Azure que oferecem suporte a contêineres.</span><span class="sxs-lookup"><span data-stu-id="88272-253">Review the Azure services that support containers.</span></span>](https://azure.microsoft.com/en-us/overview/containers/)
* [<span data-ttu-id="88272-254">Ler mais sobre os comandos do Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="88272-254">Read about Dockerfile commands.</span></span>](https://docs.docker.com/engine/reference/builder/)
