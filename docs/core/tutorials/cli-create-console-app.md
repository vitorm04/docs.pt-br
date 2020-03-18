---
title: Introdução ao .NET Core, usando as ferramentas da CLI
description: Um tutorial passo-a-passo mostrando como começar com o .NET Core no Windows, Linux ou macOS usando o .NET Core CLI.
author: thraka
ms.author: adegeo
ms.date: 12/05/2019
ms.technology: dotnet-cli
ms.custom: updateeachrelease
ms.openlocfilehash: fe69521a6ac88055e3e8c8502a7e19a72667dbef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240851"
---
# <a name="get-started-with-net-core-using-the-net-core-cli"></a><span data-ttu-id="86d39-103">Comece com o .NET Core usando o .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="86d39-103">Get started with .NET Core using the .NET Core CLI</span></span>

<span data-ttu-id="86d39-104">Este artigo mostrará como começar a desenvolver aplicativos .NET Core que funcionam no Windows, Linux e macOS usando o .NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="86d39-104">This article will show you how to start developing .NET Core apps that work on Windows, Linux, and macOS using the .NET Core CLI.</span></span>

<span data-ttu-id="86d39-105">Se você não estiver familiarizado com o .NET Core CLI, consulte a visão geral do [.NET Core CLI](../tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="86d39-105">If you're unfamiliar with the .NET Core CLI, see the [.NET Core CLI overview](../tools/index.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="86d39-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="86d39-106">Prerequisites</span></span>

- <span data-ttu-id="86d39-107">[.NET Core SDK 3.1](https://dotnet.microsoft.com/download) ou versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="86d39-107">[.NET Core SDK 3.1](https://dotnet.microsoft.com/download) or later versions.</span></span>
- <span data-ttu-id="86d39-108">Um editor de texto ou editor de código de sua escolha.</span><span class="sxs-lookup"><span data-stu-id="86d39-108">A text editor or code editor of your choice.</span></span>

## <a name="hello-console-app"></a><span data-ttu-id="86d39-109">Olá, Aplicativo de Console.</span><span class="sxs-lookup"><span data-stu-id="86d39-109">Hello, Console App!</span></span>

<span data-ttu-id="86d39-110">Você pode [exibir ou baixar o código de exemplo](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild) do repositório dotnet/samples do GitHub.</span><span class="sxs-lookup"><span data-stu-id="86d39-110">You can [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild) from the dotnet/samples GitHub repository.</span></span> <span data-ttu-id="86d39-111">Para obter instruções de download, consulte [Exemplos e tutoriais](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="86d39-111">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

<span data-ttu-id="86d39-112">Abra um prompt de comando e crie uma pasta chamada *Hello*.</span><span class="sxs-lookup"><span data-stu-id="86d39-112">Open a command prompt and create a folder named *Hello*.</span></span> <span data-ttu-id="86d39-113">Navegue até a pasta que você criou e digite o seguinte.</span><span class="sxs-lookup"><span data-stu-id="86d39-113">Navigate to the folder you created and type the following.</span></span>

```dotnetcli
dotnet new console
dotnet run
```

<span data-ttu-id="86d39-114">Vejamos um breve passo a passo:</span><span class="sxs-lookup"><span data-stu-id="86d39-114">Let's do a quick walkthrough:</span></span>

01. `dotnet new console`

    <span data-ttu-id="86d39-115">[dotnet new](../tools/dotnet-new.md) cria um arquivo de projeto *Hello.csproj* atualizado com as dependências necessárias para construir um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="86d39-115">[dotnet new](../tools/dotnet-new.md) creates an up-to-date *Hello.csproj* project file with the dependencies necessary to build a console app.</span></span> <span data-ttu-id="86d39-116">Ele também cria um *Program.cs*, um arquivo básico contendo o ponto de entrada para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="86d39-116">It also creates a *Program.cs*, a basic file containing the entry point for the application.</span></span>

    <span data-ttu-id="86d39-117">*Olá.csproj:*</span><span class="sxs-lookup"><span data-stu-id="86d39-117">*Hello.csproj*:</span></span>

    [!code-xml[Hello.csproj](~/samples/snippets/core/tutorials/cli-create-console-app/HelloMsBuild/csharp/Hello.csproj)]

    <span data-ttu-id="86d39-118">O arquivo de projeto especifica tudo o que é necessário para restaurar as dependências e compilar o programa.</span><span class="sxs-lookup"><span data-stu-id="86d39-118">The project file specifies everything that's needed to restore dependencies and build the program.</span></span>

    - <span data-ttu-id="86d39-119">O `<OutputType>` elemento especifica que estamos construindo um executável, ou seja, um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="86d39-119">The `<OutputType>` element specifies that we're building an executable, in other words a console application.</span></span>
    - <span data-ttu-id="86d39-120">O `<TargetFramework>` elemento especifica qual a implementação .NET que estamos direcionando.</span><span class="sxs-lookup"><span data-stu-id="86d39-120">The `<TargetFramework>` element specifies what .NET implementation we're targeting.</span></span> <span data-ttu-id="86d39-121">Em um cenário avançado, é possível especificar várias estruturas de destino e criar para todas elas em uma única operação.</span><span class="sxs-lookup"><span data-stu-id="86d39-121">In an advanced scenario, you can specify multiple target frameworks and build to all those in a single operation.</span></span> <span data-ttu-id="86d39-122">Neste tutorial, vamos continuar a construir apenas para .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="86d39-122">In this tutorial, we'll stick to building only for .NET Core 3.1.</span></span>

    <span data-ttu-id="86d39-123">*Program.cs:*</span><span class="sxs-lookup"><span data-stu-id="86d39-123">*Program.cs*:</span></span>

    [!code-csharp[Program.cs](~/samples/snippets/core/tutorials/cli-create-console-app/HelloMsBuild/csharp/Program.cs)]

    <span data-ttu-id="86d39-124">O programa é iniciado pelo `using System`, que significa "colocar tudo no namespace `System` no escopo para este arquivo".</span><span class="sxs-lookup"><span data-stu-id="86d39-124">The program starts by `using System`, which means "bring everything in the `System` namespace into scope for this file".</span></span> <span data-ttu-id="86d39-125">O `System` namespace inclui `Console` a classe.</span><span class="sxs-lookup"><span data-stu-id="86d39-125">The `System` namespace includes the `Console` class.</span></span>

    <span data-ttu-id="86d39-126">Em seguida, definimos um namespace chamado `Hello`.</span><span class="sxs-lookup"><span data-stu-id="86d39-126">We then define a namespace called `Hello`.</span></span> <span data-ttu-id="86d39-127">Você pode alterar isso de acordo com a sua vontade.</span><span class="sxs-lookup"><span data-stu-id="86d39-127">You can change this to anything you want.</span></span> <span data-ttu-id="86d39-128">Uma classe `Program` nomeada é definida dentro `Main` desse namespace, com um `args`método que leva uma matriz de strings nomeada .</span><span class="sxs-lookup"><span data-stu-id="86d39-128">A class named `Program` is defined within that namespace, with a `Main` method that takes an array of strings named `args`.</span></span> <span data-ttu-id="86d39-129">Esta matriz contém a lista de argumentos aprovados quando o programa é executado.</span><span class="sxs-lookup"><span data-stu-id="86d39-129">This array contains the list of arguments passed in when the program is run.</span></span> <span data-ttu-id="86d39-130">Como é, esta matriz não é usada e o programa simplesmente escreve o texto "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="86d39-130">As it is, this array is not used and the program simply writes the text "Hello World!"</span></span> <span data-ttu-id="86d39-131">no console.</span><span class="sxs-lookup"><span data-stu-id="86d39-131">to the console.</span></span> <span data-ttu-id="86d39-132">Posteriormente, faremos alterações no código que usará esse argumento.</span><span class="sxs-lookup"><span data-stu-id="86d39-132">Later, we'll make changes to the code that will make use of this argument.</span></span>

    <span data-ttu-id="86d39-133">`dotnet new`chamadas [dotnet restaurar](../tools/dotnet-restore.md) implicitamente.</span><span class="sxs-lookup"><span data-stu-id="86d39-133">`dotnet new` calls [dotnet restore](../tools/dotnet-restore.md) implicitly.</span></span> <span data-ttu-id="86d39-134">`dotnet restore` chama o [NuGet](https://www.nuget.org/) (gerenciador de pacotes do .NET) para restaurar a árvore de dependências.</span><span class="sxs-lookup"><span data-stu-id="86d39-134">`dotnet restore` calls into [NuGet](https://www.nuget.org/) (.NET package manager) to restore the tree of dependencies.</span></span> <span data-ttu-id="86d39-135">O NuGet analisa o arquivo *Hello.csproj*, baixa as dependências definidas no arquivo (ou captura-as de um cache no computador) e grava o arquivo *obj/project.assets.json*, que é necessário para compilar e executar a amostra.</span><span class="sxs-lookup"><span data-stu-id="86d39-135">NuGet analyzes the *Hello.csproj* file, downloads the dependencies defined in the file (or grabs them from a cache on your machine), and writes the *obj/project.assets.json* file, which is necessary to compile and run the sample.</span></span>

02. `dotnet run`

    <span data-ttu-id="86d39-136">[dotnet executar](../tools/dotnet-run.md) chamadas [dotnet build](../tools/dotnet-build.md) para garantir que os alvos `dotnet <assembly.dll>` de compilação foram construídos e, em seguida, chamadas para executar o aplicativo de destino.</span><span class="sxs-lookup"><span data-stu-id="86d39-136">[dotnet run](../tools/dotnet-run.md) calls [dotnet build](../tools/dotnet-build.md) to ensure that the build targets have been built, and then calls `dotnet <assembly.dll>` to run the target application.</span></span>

    ```dotnetcli
    dotnet run
    ```

    <span data-ttu-id="86d39-137">Você tem a seguinte saída.</span><span class="sxs-lookup"><span data-stu-id="86d39-137">You get the following output.</span></span>

    ```console
    Hello World!
    ```

    <span data-ttu-id="86d39-138">Alternativamente, você também `dotnet build` pode executar para compilar o código sem executar os aplicativos de console de compilação.</span><span class="sxs-lookup"><span data-stu-id="86d39-138">Alternatively, you can also run `dotnet build` to compile the code without running the build console applications.</span></span> <span data-ttu-id="86d39-139">Isso resulta em um aplicativo compilado, como um arquivo DLL, com base no nome do projeto.</span><span class="sxs-lookup"><span data-stu-id="86d39-139">This results in a compiled application, as a DLL file, based on the name of the project.</span></span> <span data-ttu-id="86d39-140">Neste caso, o arquivo criado é chamado *Hello.dll*.</span><span class="sxs-lookup"><span data-stu-id="86d39-140">In this case, the file created is named *Hello.dll*.</span></span> <span data-ttu-id="86d39-141">Este aplicativo pode `dotnet bin\Debug\netcoreapp3.1\Hello.dll` ser executado `/` com o Windows (uso para sistemas não-Windows).</span><span class="sxs-lookup"><span data-stu-id="86d39-141">This app can be run with `dotnet bin\Debug\netcoreapp3.1\Hello.dll` on Windows (use `/` for non-Windows systems).</span></span>

    ```dotnetcli
    dotnet bin\Debug\netcoreapp3.1\Hello.dll
    ```

    <span data-ttu-id="86d39-142">Você tem a seguinte saída.</span><span class="sxs-lookup"><span data-stu-id="86d39-142">You get the following output.</span></span>

    ```console
    Hello World!
    ```

    <span data-ttu-id="86d39-143">Quando o aplicativo é compilado, um executável específico do `Hello.dll`sistema operacional foi criado junto com o .</span><span class="sxs-lookup"><span data-stu-id="86d39-143">When the app is compiled, an operating system-specific executable was created along with the `Hello.dll`.</span></span> <span data-ttu-id="86d39-144">No Windows, isso `Hello.exe`seria; no Linux ou macOS, `hello`isso seria .</span><span class="sxs-lookup"><span data-stu-id="86d39-144">On Windows, this would be `Hello.exe`; on Linux or macOS, this would be `hello`.</span></span> <span data-ttu-id="86d39-145">Com o exemplo acima, o `Hello.exe` `Hello`arquivo é nomeado com ou .</span><span class="sxs-lookup"><span data-stu-id="86d39-145">With the example above, the file is named with `Hello.exe` or `Hello`.</span></span> <span data-ttu-id="86d39-146">Você pode executar isso executável diretamente.</span><span class="sxs-lookup"><span data-stu-id="86d39-146">You can run that executable directly.</span></span>

    ```console
    .\bin\Debug\netcoreapp3.1\Hello.exe

    Hello World!
    ```

## <a name="modify-the-program"></a><span data-ttu-id="86d39-147">Modificar o programa</span><span class="sxs-lookup"><span data-stu-id="86d39-147">Modify the program</span></span>

<span data-ttu-id="86d39-148">Vamos alterar o programa um pouco.</span><span class="sxs-lookup"><span data-stu-id="86d39-148">Let's change the program a bit.</span></span> <span data-ttu-id="86d39-149">Os números de Fibonacci são divertidos, então vamos adicionar isso e também usar o argumento para cumprimentar a pessoa que está executando o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="86d39-149">Fibonacci numbers are fun, so let's add that and also to use the argument to greet the person running the app.</span></span>

01. <span data-ttu-id="86d39-150">Substitua o conteúdo do arquivo *Program.cs* pelo seguinte código:</span><span class="sxs-lookup"><span data-stu-id="86d39-150">Replace the contents of your *Program.cs*  file with the following code:</span></span>

    [!code-csharp[Fibonacci](~/samples/snippets/core/tutorials/cli-create-console-app/fibonacci-msbuild/csharp/Program.cs)]

02. <span data-ttu-id="86d39-151">Executar [a compilação dotnet](../tools/dotnet-build.md) para compilar as alterações.</span><span class="sxs-lookup"><span data-stu-id="86d39-151">Run [dotnet build](../tools/dotnet-build.md) to compile the changes.</span></span>

03. <span data-ttu-id="86d39-152">Execute o programa passando um parâmetro para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="86d39-152">Run the program passing a parameter to the app.</span></span> <span data-ttu-id="86d39-153">Quando você `dotnet` usar o comando para `--` executar um aplicativo, adicione ao final.</span><span class="sxs-lookup"><span data-stu-id="86d39-153">When you use the `dotnet` command to run an app, add `--` to the end.</span></span> <span data-ttu-id="86d39-154">Qualquer coisa à `--` direita será passada como parâmetro para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="86d39-154">Anything to the right of `--` will be passed as a parameter to the app.</span></span> <span data-ttu-id="86d39-155">No exemplo a seguir, o valor `John` é passado para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="86d39-155">In the following example, the value `John` is passed to the app.</span></span>

    ```dotnetcli
    dotnet run -- John
    ```

    <span data-ttu-id="86d39-156">Você tem a seguinte saída.</span><span class="sxs-lookup"><span data-stu-id="86d39-156">You get the following output.</span></span>

    ```console
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

<span data-ttu-id="86d39-157">E isso é tudo!</span><span class="sxs-lookup"><span data-stu-id="86d39-157">And that's it!</span></span> <span data-ttu-id="86d39-158">Você pode modificar *Program.cs* do jeito que quiser.</span><span class="sxs-lookup"><span data-stu-id="86d39-158">You can modify *Program.cs* any way you like.</span></span>

## <a name="working-with-multiple-files"></a><span data-ttu-id="86d39-159">Trabalhando com vários arquivos</span><span class="sxs-lookup"><span data-stu-id="86d39-159">Working with multiple files</span></span>

<span data-ttu-id="86d39-160">Arquivos únicos são bons para programas pontuais simples, mas se você está construindo um aplicativo mais complexo, você provavelmente terá vários arquivos de código em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="86d39-160">Single files are fine for simple one-off programs, but if you're building a more complex app, you're probably going to have multiple code files on your project.</span></span> <span data-ttu-id="86d39-161">Vamos nos basear no exemplo de Fibonacci anterior armazenando em cache alguns valores de Fibonacci e adicionar alguns recursos recursivos.</span><span class="sxs-lookup"><span data-stu-id="86d39-161">Let's build off of the previous Fibonacci example by caching some Fibonacci values and add some recursive features.</span></span>

01. <span data-ttu-id="86d39-162">Adicione um novo arquivo no diretório *Hello* chamado *FibonacciGenerator.cs* com o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="86d39-162">Add a new file inside the *Hello* directory named *FibonacciGenerator.cs* with the following code:</span></span>

    [!code-csharp[Fibonacci Generator](~/samples/snippets/core/tutorials/cli-create-console-app/FibonacciBetterMsBuild/csharp/FibonacciGenerator.cs)]

02. <span data-ttu-id="86d39-163">Altere o método `Main` no arquivo *Program.cs* para criar uma instância da nova classe e chame seu método como no seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="86d39-163">Change the `Main` method in your *Program.cs* file to instantiate the new class and call its method as in the following example:</span></span>

    [!code-csharp[New Program.cs](~/samples/snippets/core/tutorials/cli-create-console-app/FibonacciBetterMsBuild/csharp/Program.cs)]

03. <span data-ttu-id="86d39-164">Executar [a compilação dotnet](../tools/dotnet-build.md) para compilar as alterações.</span><span class="sxs-lookup"><span data-stu-id="86d39-164">Run [dotnet build](../tools/dotnet-build.md) to compile the changes.</span></span>

04. <span data-ttu-id="86d39-165">Execute seu aplicativo executando [a execução dotnet run](../tools/dotnet-run.md).</span><span class="sxs-lookup"><span data-stu-id="86d39-165">Run your app by executing [dotnet run](../tools/dotnet-run.md).</span></span>

    ```dotnetcli
    dotnet run
    ```

    <span data-ttu-id="86d39-166">Você tem a seguinte saída.</span><span class="sxs-lookup"><span data-stu-id="86d39-166">You get the following output.</span></span>

    ```console
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

## <a name="publish-your-app"></a><span data-ttu-id="86d39-167">Publicar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="86d39-167">Publish your app</span></span>

<span data-ttu-id="86d39-168">Uma vez que você esteja pronto para distribuir seu aplicativo, use o comando [dotnet publish](../tools/dotnet-publish.md) para `/` gerar a pasta de _publicação_ no _\\bin debug\\netcoreapp3.1\\publish\\ _ (uso para sistemas não-Windows).</span><span class="sxs-lookup"><span data-stu-id="86d39-168">Once you're ready to distribute your app, use the [dotnet publish](../tools/dotnet-publish.md) command to generate the _publish_ folder at _bin\\debug\\netcoreapp3.1\\publish\\_ (use `/` for non-Windows systems).</span></span> <span data-ttu-id="86d39-169">Você pode distribuir o conteúdo da pasta _publicar_ para outras plataformas, desde que já tenha instalado o runtime dotnet.</span><span class="sxs-lookup"><span data-stu-id="86d39-169">You can distribute the contents of the _publish_ folder to other platforms as long as they've already installed the dotnet runtime.</span></span>

```dotnetcli
dotnet publish
```

<span data-ttu-id="86d39-170">Você tem saída semelhante à seguinte.</span><span class="sxs-lookup"><span data-stu-id="86d39-170">You get output similar to the following.</span></span>

```console
Microsoft (R) Build Engine version 16.4.0+e901037fe for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 20 ms for C:\Code\Temp\Hello\Hello.csproj.
  Hello -> C:\Code\Temp\Hello\bin\Debug\netcoreapp3.1\Hello.dll
  Hello -> C:\Code\Temp\Hello\bin\Debug\netcoreapp3.1\publish\
```

<span data-ttu-id="86d39-171">A saída acima pode diferir com base na pasta atual e no sistema operacional, mas a saída deve ser semelhante.</span><span class="sxs-lookup"><span data-stu-id="86d39-171">The output above may differ based on your current folder and operating system, but the output should be similar.</span></span>

<span data-ttu-id="86d39-172">Você pode executar o aplicativo publicado com o comando [dotnet](../tools/dotnet.md):</span><span class="sxs-lookup"><span data-stu-id="86d39-172">You can run your published app with the [dotnet](../tools/dotnet.md) command:</span></span>

```dotnetcli
dotnet bin\Debug\netcoreapp3.1\publish\Hello.dll
```

<span data-ttu-id="86d39-173">Você tem a seguinte saída.</span><span class="sxs-lookup"><span data-stu-id="86d39-173">You get the following output.</span></span>

```console
Hello World!
```

<span data-ttu-id="86d39-174">Como mencionado no início deste artigo, foi criado um executável `Hello.dll`específico do sistema operacional juntamente com o .</span><span class="sxs-lookup"><span data-stu-id="86d39-174">As mentioned at the start of this article, an operating system-specific executable was created along with the `Hello.dll`.</span></span> <span data-ttu-id="86d39-175">No Windows, isso `Hello.exe`seria; no Linux ou macOS, `hello`isso seria .</span><span class="sxs-lookup"><span data-stu-id="86d39-175">On Windows, this would be `Hello.exe`; on Linux or macOS, this would be `hello`.</span></span> <span data-ttu-id="86d39-176">Com o exemplo acima, o `Hello.exe` `Hello`arquivo é nomeado com ou .</span><span class="sxs-lookup"><span data-stu-id="86d39-176">With the example above, the file is named with `Hello.exe` or `Hello`.</span></span> <span data-ttu-id="86d39-177">Você pode executar este executável publicado diretamente.</span><span class="sxs-lookup"><span data-stu-id="86d39-177">You can run this published executable directly.</span></span>

```console
.\bin\Debug\netcoreapp3.1\publish\Hello.exe

Hello World!
```

## <a name="conclusion"></a><span data-ttu-id="86d39-178">Conclusão</span><span class="sxs-lookup"><span data-stu-id="86d39-178">Conclusion</span></span>

<span data-ttu-id="86d39-179">E isso é tudo!</span><span class="sxs-lookup"><span data-stu-id="86d39-179">And that's it!</span></span> <span data-ttu-id="86d39-180">Agora, é possível começar a usar os conceitos básicos aprendidos aqui para criar seus próprios programas.</span><span class="sxs-lookup"><span data-stu-id="86d39-180">Now, you can start using the basic concepts learned here to create your own programs.</span></span>

## <a name="see-also"></a><span data-ttu-id="86d39-181">Confira também</span><span class="sxs-lookup"><span data-stu-id="86d39-181">See also</span></span>

- [<span data-ttu-id="86d39-182">Organização e teste de projetos com o .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="86d39-182">Organizing and testing projects with the .NET Core CLI</span></span>](testing-with-cli.md)
- [<span data-ttu-id="86d39-183">Publique os aplicativos .NET Core com o .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="86d39-183">Publish .NET Core apps with the .NET Core CLI</span></span>](../deploying/deploy-with-cli.md)
- [<span data-ttu-id="86d39-184">Implantação de aplicativos .NET Core</span><span class="sxs-lookup"><span data-stu-id="86d39-184">.NET Core application deployment</span></span>](../deploying/index.md)
