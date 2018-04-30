---
title: Introdução ao .NET Core usando a CLI
description: Um tutorial passo a passo que mostra como começar a usar o .NET Core no Windows, Linux ou macOS com a CLI (interface de linha de comando) do .NET Core.
author: cartermp
ms.author: mairaw
ms.date: 03/08/2017
ms.topic: get-started-article
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: 23aec1b951c4b65d62bd4da4b4c94043b1411cf3
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="getting-started-with-net-core-on-windowslinuxmacos-using-the-command-line"></a><span data-ttu-id="ab8fa-103">Introdução ao .NET Core no Windows/Linux/macOS usando a linha de comando</span><span class="sxs-lookup"><span data-stu-id="ab8fa-103">Getting started with .NET Core on Windows/Linux/macOS using the command line</span></span>

<span data-ttu-id="ab8fa-104">Este tópico mostra como começar a desenvolver aplicativos de plataforma cruzada no computador usando as ferramentas da CLI do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ab8fa-104">This topic will show you how to start developing cross-platforms apps in your machine using the .NET Core CLI tools.</span></span>

<span data-ttu-id="ab8fa-105">Se não estiver familiarizado com o conjunto de ferramentas da CLI do .NET Core, leia a [Visão geral do SDK do .NET Core](../tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="ab8fa-105">If you're unfamiliar with the .NET Core CLI toolset, read the [.NET Core SDK overview](../tools/index.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ab8fa-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="ab8fa-106">Prerequisites</span></span>

- <span data-ttu-id="ab8fa-107">[SDK 1.0 do .NET Core](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="ab8fa-107">[.NET Core SDK 1.0](https://www.microsoft.com/net/download/core).</span></span>
- <span data-ttu-id="ab8fa-108">Um editor de texto ou de código de sua escolha.</span><span class="sxs-lookup"><span data-stu-id="ab8fa-108">A text editor or code editor of your choice.</span></span>

## <a name="hello-console-app"></a><span data-ttu-id="ab8fa-109">Olá, Aplicativo de Console.</span><span class="sxs-lookup"><span data-stu-id="ab8fa-109">Hello, Console App!</span></span>

<span data-ttu-id="ab8fa-110">Você pode [exibir ou baixar o código de exemplo](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild) do repositório dotnet/samples do GitHub.</span><span class="sxs-lookup"><span data-stu-id="ab8fa-110">You can [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild) from the dotnet/samples GitHub repository.</span></span> <span data-ttu-id="ab8fa-111">Para obter instruções de download, consulte [Exemplos e tutoriais](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="ab8fa-111">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

<span data-ttu-id="ab8fa-112">Abra um prompt de comando e crie uma pasta chamada *Hello*.</span><span class="sxs-lookup"><span data-stu-id="ab8fa-112">Open a command prompt and create a folder named *Hello*.</span></span> <span data-ttu-id="ab8fa-113">Navegue até a pasta que você criou e digite o seguinte:</span><span class="sxs-lookup"><span data-stu-id="ab8fa-113">Navigate to the folder you created and type the following:</span></span>

```
$ dotnet new console
$ dotnet restore
$ dotnet run
```

<span data-ttu-id="ab8fa-114">Vejamos um breve passo a passo:</span><span class="sxs-lookup"><span data-stu-id="ab8fa-114">Let's do a quick walkthrough:</span></span>

1. `$ dotnet new console`

   <span data-ttu-id="ab8fa-115">[`dotnet new`](../tools/dotnet-new.md) cria um arquivo de projeto `Hello.csproj` atualizado com as dependências necessárias para criar um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="ab8fa-115">[`dotnet new`](../tools/dotnet-new.md) creates an up-to-date `Hello.csproj` project file with the dependencies necessary to build a console app.</span></span>  <span data-ttu-id="ab8fa-116">Ele também cria um `Program.cs`, um arquivo básico que contém o ponto de entrada para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ab8fa-116">It also creates a `Program.cs`, a basic file containing the entry point for the application.</span></span>
   
   <span data-ttu-id="ab8fa-117">`Hello.csproj`:</span><span class="sxs-lookup"><span data-stu-id="ab8fa-117">`Hello.csproj`:</span></span>

   [!code[Hello.csproj](../../../samples/core/console-apps/HelloMsBuild/Hello.csproj)]   

   <span data-ttu-id="ab8fa-118">O arquivo de projeto especifica tudo o que é necessário para restaurar as dependências e compilar o programa.</span><span class="sxs-lookup"><span data-stu-id="ab8fa-118">The project file specifies everything that's needed to restore dependencies and build the program.</span></span>

   * <span data-ttu-id="ab8fa-119">A marca `OutputType` especifica que estamos copilando um executável, em outras palavras, um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="ab8fa-119">The `OutputType` tag specifies that we're building an executable, in other words a console application.</span></span>
   * <span data-ttu-id="ab8fa-120">A marca `TargetFramework` especifica qual implementação do .NET estamos direcionando.</span><span class="sxs-lookup"><span data-stu-id="ab8fa-120">The `TargetFramework` tag specifies what .NET implementation we're targeting.</span></span> <span data-ttu-id="ab8fa-121">Em um cenário avançado, é possível especificar várias estruturas de destino e criar para todas elas em uma única operação.</span><span class="sxs-lookup"><span data-stu-id="ab8fa-121">In an advanced scenario, you can specify multiple target frameworks and build to all those in a single operation.</span></span> <span data-ttu-id="ab8fa-122">Neste tutorial, veremos apenas a compilação para .NET Core 1.0.</span><span class="sxs-lookup"><span data-stu-id="ab8fa-122">In this tutorial, we'll stick to building only for .NET Core 1.0.</span></span>

   <span data-ttu-id="ab8fa-123">`Program.cs`:</span><span class="sxs-lookup"><span data-stu-id="ab8fa-123">`Program.cs`:</span></span>

   [!code-csharp[Program.cs](../../../samples/core/console-apps/HelloMsBuild/Program.cs)]   

   <span data-ttu-id="ab8fa-124">O programa é iniciado pelo `using System`, que significa "colocar tudo no namespace `System` no escopo para este arquivo".</span><span class="sxs-lookup"><span data-stu-id="ab8fa-124">The program starts by `using System`, which means "bring everything in the `System` namespace into scope for this file".</span></span> <span data-ttu-id="ab8fa-125">O namespace `System` inclui construções básicas, como `string` ou tipos numéricos.</span><span class="sxs-lookup"><span data-stu-id="ab8fa-125">The `System` namespace includes basic constructs such as `string`, or numeric types.</span></span>

   <span data-ttu-id="ab8fa-126">Em seguida, definimos um namespace chamado `Hello`.</span><span class="sxs-lookup"><span data-stu-id="ab8fa-126">We then define a namespace called `Hello`.</span></span> <span data-ttu-id="ab8fa-127">Você pode alterar isso de acordo com a sua vontade.</span><span class="sxs-lookup"><span data-stu-id="ab8fa-127">You can change this to anything you want.</span></span> <span data-ttu-id="ab8fa-128">Uma classe chamada `Program` é definida dentro desse namespace, com um método `Main` que usa uma matriz de cadeias de caracteres como argumento.</span><span class="sxs-lookup"><span data-stu-id="ab8fa-128">A class named `Program` is defined within that namespace, with a `Main` method that takes an array of strings as its argument.</span></span> <span data-ttu-id="ab8fa-129">Essa matriz contém a lista de argumentos passados quando o programa compilado é chamado.</span><span class="sxs-lookup"><span data-stu-id="ab8fa-129">This array contains the list of arguments passed in when the compiled program is called.</span></span> <span data-ttu-id="ab8fa-130">Assim, essa matriz não será usada: o que o programa faz é gravar: "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="ab8fa-130">As it is, this array is not used: all the program is doing is to write "Hello World!"</span></span> <span data-ttu-id="ab8fa-131">no console.</span><span class="sxs-lookup"><span data-stu-id="ab8fa-131">to the console.</span></span> <span data-ttu-id="ab8fa-132">Posteriormente, faremos alterações no código que usará esse argumento.</span><span class="sxs-lookup"><span data-stu-id="ab8fa-132">Later, we'll make changes to the code that will make use of this argument.</span></span>

   [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

2. `$ dotnet restore`

   <span data-ttu-id="ab8fa-133">[`dotnet restore`](../tools/dotnet-restore.md) chama o [NuGet](https://www.nuget.org/) (gerenciador de pacotes do .NET) para restaurar a árvore de dependências.</span><span class="sxs-lookup"><span data-stu-id="ab8fa-133">[`dotnet restore`](../tools/dotnet-restore.md) calls into [NuGet](https://www.nuget.org/) (.NET package manager) to restore the tree of dependencies.</span></span> <span data-ttu-id="ab8fa-134">O NuGet analisa o arquivo *Hello.csproj*, baixa as dependências declaradas no arquivo (ou captura-as de um cache no computador) e grava o arquivo *obj/project.assets.json*.</span><span class="sxs-lookup"><span data-stu-id="ab8fa-134">NuGet analyzes the *Hello.csproj* file, downloads the dependencies stated in the file (or grabs them from a cache on your machine), and writes the *obj/project.assets.json* file.</span></span>  <span data-ttu-id="ab8fa-135">O arquivo *project.assets.json* é necessário para compilar e executar.</span><span class="sxs-lookup"><span data-stu-id="ab8fa-135">The *project.assets.json* file is necessary to be able to compile and run.</span></span>
   
   <span data-ttu-id="ab8fa-136">O arquivo *project.assets.json* é um conjunto completo e persistente do grafo de dependências do NuGet e de outras informações que descrevem um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ab8fa-136">The *project.assets.json* file is a persisted and complete set of the graph of NuGet dependencies and other information describing an app.</span></span>  <span data-ttu-id="ab8fa-137">Esse arquivo é lido por outras ferramentas, como [`dotnet build`](../tools/dotnet-build.md) e [`dotnet run`](../tools/dotnet-run.md), permitindo que elas processem o código-fonte com um conjunto correto das dependências do NuGet e das resoluções de associação.</span><span class="sxs-lookup"><span data-stu-id="ab8fa-137">This file is read by other tools, such as [`dotnet build`](../tools/dotnet-build.md) and [`dotnet run`](../tools/dotnet-run.md), enabling them to process the source code with a correct set of NuGet dependencies and binding resolutions.</span></span>
   
3. `$ dotnet run`

   <span data-ttu-id="ab8fa-138">[`dotnet run`](../tools/dotnet-run.md) chama [`dotnet build`](../tools/dotnet-build.md) para garantir que os destinos de build foram criados e então chama `dotnet <assembly.dll>` para executar o aplicativo de destino.</span><span class="sxs-lookup"><span data-stu-id="ab8fa-138">[`dotnet run`](../tools/dotnet-run.md) calls [`dotnet build`](../tools/dotnet-build.md) to ensure that the build targets have been built, and then calls `dotnet <assembly.dll>` to run the target application.</span></span>
   
    ```
    $ dotnet run
    Hello World!
    ```

    <span data-ttu-id="ab8fa-139">Como alternativa, também é possível pode executar [`dotnet build`](../tools/dotnet-build.md) para compilar o código sem executar os aplicativos de console de compilação.</span><span class="sxs-lookup"><span data-stu-id="ab8fa-139">Alternatively, you can also execute [`dotnet build`](../tools/dotnet-build.md) to compile the code without running the build console applications.</span></span> <span data-ttu-id="ab8fa-140">Isso resulta em um aplicativo compilado como um arquivo DLL que pode ser executado com `dotnet bin\Debug\netcoreapp1.0\Hello.dll` no Windows (use `/` para sistemas não Windows).</span><span class="sxs-lookup"><span data-stu-id="ab8fa-140">This results in a compiled application as a DLL file that can be run with `dotnet bin\Debug\netcoreapp1.0\Hello.dll` on Windows (use `/` for non-Windows systems).</span></span> <span data-ttu-id="ab8fa-141">Também é possível especificar argumentos para o aplicativo, como você verá adiante no tópico.</span><span class="sxs-lookup"><span data-stu-id="ab8fa-141">You may also specify arguments to the application as you'll see later on the topic.</span></span>

    ```
    $ dotnet bin\Debug\netcoreapp1.0\Hello.dll
    Hello World!
    ```

    <span data-ttu-id="ab8fa-142">Como um cenário avançado, é possível compilar o aplicativo como um conjunto independente de arquivos específicos de plataforma que pode ser implantado e executado em um computador que não tem necessariamente o .NET Core instalado.</span><span class="sxs-lookup"><span data-stu-id="ab8fa-142">As an advanced scenario, it's possible to build the application as a self-contained set of platform-specific files that can be deployed and run to a machine that doesn't necessarily have .NET Core installed.</span></span> <span data-ttu-id="ab8fa-143">Consulte [Implantação do .NET Core Application](../deploying/index.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="ab8fa-143">See [.NET Core Application Deployment](../deploying/index.md) for details.</span></span>

### <a name="augmenting-the-program"></a><span data-ttu-id="ab8fa-144">Ampliando o programa</span><span class="sxs-lookup"><span data-stu-id="ab8fa-144">Augmenting the program</span></span>

<span data-ttu-id="ab8fa-145">Vamos alterar o programa um pouco.</span><span class="sxs-lookup"><span data-stu-id="ab8fa-145">Let's change the program a bit.</span></span> <span data-ttu-id="ab8fa-146">Números de Fibonacci são divertidos; portanto, vamos adicionar isso, além de usar o argumento para saudar a pessoa que executa o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ab8fa-146">Fibonacci numbers are fun, so let's add that in addition to use the argument to greet the person running the app.</span></span>

1. <span data-ttu-id="ab8fa-147">Substitua o conteúdo do arquivo *Program.cs* pelo seguinte código:</span><span class="sxs-lookup"><span data-stu-id="ab8fa-147">Replace the contents of your *Program.cs*  file with the following code:</span></span>

   [!code-csharp[Fibonacci](../../../samples/core/console-apps/fibonacci-msbuild/Program.cs)]   

2. <span data-ttu-id="ab8fa-148">Execute [`dotnet build`](../tools/dotnet-build.md) para compilar as alterações.</span><span class="sxs-lookup"><span data-stu-id="ab8fa-148">Execute [`dotnet build`](../tools/dotnet-build.md) to compile the changes.</span></span>

3. <span data-ttu-id="ab8fa-149">Execute o programa passando um parâmetro para o aplicativo:</span><span class="sxs-lookup"><span data-stu-id="ab8fa-149">Run the program passing a parameter to the app:</span></span>

   ```
   $ dotnet run -- John
   Hello John!
   Fibonacci Numbers 1-15:
   1: 0
   2: 1
   3: 1
   4: 2
   5: 3
   6: 5
   7: 8
   8: 13
   9: 21
   10: 34
   11: 55
   12: 89
   13: 144
   14: 233
   15: 377
   ```

<span data-ttu-id="ab8fa-150">E pronto.</span><span class="sxs-lookup"><span data-stu-id="ab8fa-150">And that's it!</span></span>  <span data-ttu-id="ab8fa-151">Você pode ampliar `Program.cs` como desejar.</span><span class="sxs-lookup"><span data-stu-id="ab8fa-151">You can augment `Program.cs` any way you like.</span></span>

## <a name="working-with-multiple-files"></a><span data-ttu-id="ab8fa-152">Trabalhando com vários arquivos</span><span class="sxs-lookup"><span data-stu-id="ab8fa-152">Working with multiple files</span></span>

<span data-ttu-id="ab8fa-153">Arquivos individuais são adequados para programas avulsos simples, mas se você estiver compilando um aplicativo mais complexo, provavelmente terá vários arquivos de origem no projeto. Vamos compilar com base no exemplo anterior de Fibonacci armazenando em cache alguns valores de Fibonacci e adicionar alguns recursos recursivos.</span><span class="sxs-lookup"><span data-stu-id="ab8fa-153">Single files are fine for simple one-off programs, but if you're building a more complex app, you're probably going to have multiple source files on your project Let's build off of the previous Fibonacci example by caching some Fibonacci values and add some recursive features.</span></span> 

1. <span data-ttu-id="ab8fa-154">Adicione um novo arquivo no diretório *Hello* chamado *FibonacciGenerator.cs* com o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="ab8fa-154">Add a new file inside the *Hello* directory named *FibonacciGenerator.cs* with the following code:</span></span>

   [!code-csharp[Fibonacci Generator](../../../samples/core/console-apps/FibonacciBetterMsBuild/FibonacciGenerator.cs)]   

2. <span data-ttu-id="ab8fa-155">Altere o método `Main` no arquivo *Program.cs* para criar uma instância da nova classe e chame seu método como no seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="ab8fa-155">Change the `Main` method in your *Program.cs* file to instantiate the new class and call its method as in the following example:</span></span>

   [!code-csharp[New Program.cs](../../../samples/core/console-apps/FibonacciBetterMsBuild/Program.cs)]

3. <span data-ttu-id="ab8fa-156">Execute [`dotnet build`](../tools/dotnet-build.md) para compilar as alterações.</span><span class="sxs-lookup"><span data-stu-id="ab8fa-156">Execute [`dotnet build`](../tools/dotnet-build.md) to compile the changes.</span></span>

4. <span data-ttu-id="ab8fa-157">Execute o aplicativo executando [`dotnet run`](../tools/dotnet-run.md).</span><span class="sxs-lookup"><span data-stu-id="ab8fa-157">Run your app by executing [`dotnet run`](../tools/dotnet-run.md).</span></span> <span data-ttu-id="ab8fa-158">O seguinte código mostra a saída do programa:</span><span class="sxs-lookup"><span data-stu-id="ab8fa-158">The following shows the program output:</span></span>

   ```
   0
   1
   1
   2
   3
   5
   8
   13
   21
   34
   55
   89
   144
   233
   377
   ```

<span data-ttu-id="ab8fa-159">E pronto.</span><span class="sxs-lookup"><span data-stu-id="ab8fa-159">And that's it!</span></span> <span data-ttu-id="ab8fa-160">Agora, é possível começar a usar os conceitos básicos aprendidos aqui para criar seus próprios programas.</span><span class="sxs-lookup"><span data-stu-id="ab8fa-160">Now, you can start using the basic concepts learned here to create your own programs.</span></span>

<span data-ttu-id="ab8fa-161">Observe que os comandos e as etapas mostradas neste tutorial para executar o aplicativo são usadas somente durante o tempo de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="ab8fa-161">Note that the commands and steps shown in this tutorial to run your application are used during development time only.</span></span> <span data-ttu-id="ab8fa-162">Quando estiver pronto para implantar o aplicativo, você desejará dar uma olhada nas diferentes [estratégias de implantação](../deploying/index.md) para aplicativos .NET Core e no comando [`dotnet publish`](../tools/dotnet-publish.md).</span><span class="sxs-lookup"><span data-stu-id="ab8fa-162">Once you're ready to deploy your app, you'll want to take a look at the different [deployment strategies](../deploying/index.md) for .NET Core apps and the [`dotnet publish`](../tools/dotnet-publish.md) command.</span></span>

## <a name="see-also"></a><span data-ttu-id="ab8fa-163">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ab8fa-163">See also</span></span>

[<span data-ttu-id="ab8fa-164">Organizando e testando projetos com as ferramentas da CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="ab8fa-164">Organizing and testing projects with the .NET Core CLI tools</span></span>](testing-with-cli.md)
