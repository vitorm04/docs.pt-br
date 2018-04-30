---
title: Guia de Introdução ao .NET Core no macOS
description: Este documento fornece as etapas e o fluxo de trabalho para criar uma Solução do .NET Core usando o Visual Studio Code.
author: bleroy
ms.author: mairaw
ms.date: 03/23/2017
ms.topic: get-started-article
ms.prod: dotnet-core
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: 18f825e75e7d32198a52a091948bc9dd064dacbd
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="getting-started-with-net-core-on-macos"></a><span data-ttu-id="ff3c4-103">Guia de Introdução ao .NET Core no macOS</span><span class="sxs-lookup"><span data-stu-id="ff3c4-103">Getting started with .NET Core on macOS</span></span>

<span data-ttu-id="ff3c4-104">Este documento fornece as etapas e o fluxo de trabalho para criar uma solução do .NET Core para macOS.</span><span class="sxs-lookup"><span data-stu-id="ff3c4-104">This document provides the steps and workflow to create a .NET Core solution for macOS.</span></span> <span data-ttu-id="ff3c4-105">Saiba como criar projetos, testes de unidade, usar as ferramentas de depuração e incorporar bibliotecas de terceiros por meio do [NuGet](https://www.nuget.org/).</span><span class="sxs-lookup"><span data-stu-id="ff3c4-105">Learn how to create projects, unit tests, use the debugging tools, and incorporate third-party libraries via [NuGet](https://www.nuget.org/).</span></span>

> [!NOTE]
> <span data-ttu-id="ff3c4-106">Esse artigo usa o [Visual Studio Code](http://code.visualstudio.com) no macOS.</span><span class="sxs-lookup"><span data-stu-id="ff3c4-106">This article uses [Visual Studio Code](http://code.visualstudio.com) on macOS.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ff3c4-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="ff3c4-107">Prerequisites</span></span>

<span data-ttu-id="ff3c4-108">Instalar o [SDK do .NET Core](https://www.microsoft.com/net/core).</span><span class="sxs-lookup"><span data-stu-id="ff3c4-108">Install the [.NET Core SDK](https://www.microsoft.com/net/core).</span></span> <span data-ttu-id="ff3c4-109">O SDK do .NET Core inclui a versão mais recente da estrutura do .NET Core e do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ff3c4-109">The .NET Core SDK includes the latest release of the .NET Core framework and runtime.</span></span>

<span data-ttu-id="ff3c4-110">Instalar o [Visual Studio Code](http://code.visualstudio.com).</span><span class="sxs-lookup"><span data-stu-id="ff3c4-110">Install [Visual Studio Code](http://code.visualstudio.com).</span></span> <span data-ttu-id="ff3c4-111">No decorrer deste artigo, você vai instalar as extensões do Visual Studio Code que melhoram a experiência de desenvolvimento do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ff3c4-111">During the course of this article, you also install Visual Studio Code extensions that improve the .NET Core development experience.</span></span>

<span data-ttu-id="ff3c4-112">Para instalar a extensão de C# do Visual Studio Code, abra o Visual Studio Code e pressione <kbd>F1</kbd> para abrir a paleta do programa.</span><span class="sxs-lookup"><span data-stu-id="ff3c4-112">Install the Visual Studio Code C# extension by opening Visual Studio Code and pressing <kbd>F1</kbd> to open the Visual Studio Code palette.</span></span> <span data-ttu-id="ff3c4-113">Digite **ext install** para ver a lista de extensões.</span><span class="sxs-lookup"><span data-stu-id="ff3c4-113">Type **ext install** to see the list of extensions.</span></span> <span data-ttu-id="ff3c4-114">Selecione a extensão de C#.</span><span class="sxs-lookup"><span data-stu-id="ff3c4-114">Select the C# extension.</span></span> <span data-ttu-id="ff3c4-115">Reinicie o Visual Studio Code para ativar a extensão.</span><span class="sxs-lookup"><span data-stu-id="ff3c4-115">Restart Visual Studio Code to activate the extension.</span></span> <span data-ttu-id="ff3c4-116">Para obter mais informações, consulte a [Documentação da Extensão de C# do Visual Studio Code](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span><span class="sxs-lookup"><span data-stu-id="ff3c4-116">For more information, see the [Visual Studio Code C# Extension documentation](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span></span>

## <a name="getting-started"></a><span data-ttu-id="ff3c4-117">Introdução</span><span class="sxs-lookup"><span data-stu-id="ff3c4-117">Getting started</span></span>

<span data-ttu-id="ff3c4-118">Neste tutorial, você criará três projetos: um projeto de biblioteca, testes para esse projeto de biblioteca e um aplicativo de console que usa a biblioteca.</span><span class="sxs-lookup"><span data-stu-id="ff3c4-118">In this tutorial, you create three projects: a library project, tests for that library project, and a console application that makes use of the library.</span></span> <span data-ttu-id="ff3c4-119">Você pode [exibir ou baixar a fonte](https://github.com/dotnet/samples/tree/master/core/getting-started/golden) para este tópico no repositório dotnet/samples do GitHub.</span><span class="sxs-lookup"><span data-stu-id="ff3c4-119">You can [view or download the source](https://github.com/dotnet/samples/tree/master/core/getting-started/golden) for this topic at the dotnet/samples repository on GitHub.</span></span> <span data-ttu-id="ff3c4-120">Para obter instruções de download, consulte [Exemplos e tutoriais](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="ff3c4-120">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

<span data-ttu-id="ff3c4-121">Inicie o Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="ff3c4-121">Start Visual Studio Code.</span></span> <span data-ttu-id="ff3c4-122">Pressione <kbd>Ctrl</kbd>+<kbd>\`</kbd> (o caractere de acento grave) ou escolha **Exibir > Terminal Integrado** no menu para abrir um terminal inserido no Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="ff3c4-122">Press <kbd>Ctrl</kbd>+<kbd>\`</kbd> (the backquote or backtick character) or select **View > Integrated Terminal** from the menu to open an embedded terminal in Visual Studio Code.</span></span> <span data-ttu-id="ff3c4-123">Você ainda pode abrir um shell externo com o comando **Abrir no Prompt de Comando** do Gerenciador (**Abrir no Terminal**, no Mac ou Linux), caso prefira trabalhar fora do Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="ff3c4-123">You can still open an external shell with the Explorer **Open in Command Prompt** command (**Open in Terminal** on Mac or Linux) if you prefer to work outside of Visual Studio Code.</span></span>

<span data-ttu-id="ff3c4-124">Comece criando um arquivo de solução, que serve como um contêiner para um ou mais projetos do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ff3c4-124">Begin by creating a solution file, which serves as a container for one or more .NET Core projects.</span></span> <span data-ttu-id="ff3c4-125">No terminal, crie uma pasta *golden* e abra a pasta.</span><span class="sxs-lookup"><span data-stu-id="ff3c4-125">In the terminal, create a *golden* folder and open the folder.</span></span> <span data-ttu-id="ff3c4-126">Essa pasta é a raiz da sua solução.</span><span class="sxs-lookup"><span data-stu-id="ff3c4-126">This folder is the root of your solution.</span></span> <span data-ttu-id="ff3c4-127">Execute o comando [`dotnet new`](../tools/dotnet-new.md) para criar uma nova solução, *golden.sln*:</span><span class="sxs-lookup"><span data-stu-id="ff3c4-127">Run the [`dotnet new`](../tools/dotnet-new.md) command to create a new solution, *golden.sln*:</span></span>

```console
dotnet new sln
```

<span data-ttu-id="ff3c4-128">Na pasta *golden*, execute o seguinte comando para criar um projeto de biblioteca, que produz dois arquivos, *library.csproj* e *Class1.cs*, na pasta *library*:</span><span class="sxs-lookup"><span data-stu-id="ff3c4-128">From the *golden* folder, execute the following command to create a library project, which produces two files,*library.csproj* and *Class1.cs*, in the *library* folder:</span></span>

```console
dotnet new classlib -o library
```

<span data-ttu-id="ff3c4-129">Execute o comando [`dotnet sln`](../tools/dotnet-sln.md) para adicionar o projeto *library.csproj* recém-criado à solução:</span><span class="sxs-lookup"><span data-stu-id="ff3c4-129">Execute the [`dotnet sln`](../tools/dotnet-sln.md) command to add the newly created *library.csproj* project to the solution:</span></span>

```console
dotnet sln add library/library.csproj
```

<span data-ttu-id="ff3c4-130">O arquivo *library.csproj* contém as seguintes informações:</span><span class="sxs-lookup"><span data-stu-id="ff3c4-130">The *library.csproj* file contains the following information:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netstandard1.4</TargetFramework>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="ff3c4-131">Nossos métodos da biblioteca serializam e desserializam os objetos no formato JSON.</span><span class="sxs-lookup"><span data-stu-id="ff3c4-131">Our library methods serialize and deserialize objects in JSON format.</span></span> <span data-ttu-id="ff3c4-132">Para dar suporte à serialização e desserialização JSON, adicione uma referência ao pacote NuGet `Newtonsoft.Json`.</span><span class="sxs-lookup"><span data-stu-id="ff3c4-132">To support JSON serialization and deserialization, add a reference to the `Newtonsoft.Json` NuGet package.</span></span> <span data-ttu-id="ff3c4-133">O comando `dotnet add` adiciona novos itens a um projeto.</span><span class="sxs-lookup"><span data-stu-id="ff3c4-133">The `dotnet add` command adds new items to a project.</span></span> <span data-ttu-id="ff3c4-134">Para adicionar uma referência a um pacote NuGet, use o comando [`dotnet add package`](../tools/dotnet-add-package.md) e especifique o nome do pacote:</span><span class="sxs-lookup"><span data-stu-id="ff3c4-134">To add a reference to a NuGet package, use the [`dotnet add package`](../tools/dotnet-add-package.md) command and specify the name of the package:</span></span>

```console
dotnet add library package Newtonsoft.Json
```

<span data-ttu-id="ff3c4-135">Isso adiciona `Newtonsoft.Json` e suas dependências ao projeto de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="ff3c4-135">This adds `Newtonsoft.Json` and its dependencies to the library project.</span></span> <span data-ttu-id="ff3c4-136">Como alternativa, edite manualmente o arquivo *library.csproj* e adicione o seguinte nó:</span><span class="sxs-lookup"><span data-stu-id="ff3c4-136">Alternatively, manually edit the *library.csproj* file and add the following node:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="10.0.1" />
</ItemGroup>
```

<span data-ttu-id="ff3c4-137">Execute [`dotnet restore`](../tools/dotnet-restore.md), ([veja observação](#dotnet-restore-note)), que restaura as dependências e cria uma pasta *obj* dentro de *library* com três arquivos, incluindo um arquivo *project.assets.json*:</span><span class="sxs-lookup"><span data-stu-id="ff3c4-137">Execute [`dotnet restore`](../tools/dotnet-restore.md), ([see note](#dotnet-restore-note)) which restores dependencies and creates an *obj* folder inside *library* with three files in it, including a *project.assets.json* file:</span></span>

```console
dotnet restore
```

<span data-ttu-id="ff3c4-138">Na pasta *library*, renomeie o arquivo *Class1.cs* como *Thing.cs*.</span><span class="sxs-lookup"><span data-stu-id="ff3c4-138">In the *library* folder, rename the file *Class1.cs* to *Thing.cs*.</span></span> <span data-ttu-id="ff3c4-139">Substitua o código pelo seguinte:</span><span class="sxs-lookup"><span data-stu-id="ff3c4-139">Replace the code with the following:</span></span>

```csharp
using static Newtonsoft.Json.JsonConvert;

namespace Library
{
    public class Thing
    {
        public int Get(int left, int right) =>
            DeserializeObject<int>($"{left + right}");
    }
}
```

<span data-ttu-id="ff3c4-140">A classe `Thing` contém um método público, `Get`, que retorna a soma de dois números, mas faz isso ao converter a soma em uma cadeia de caracteres e, em seguida, desserializá-los em um inteiro.</span><span class="sxs-lookup"><span data-stu-id="ff3c4-140">The `Thing` class contains one public method, `Get`, which returns the sum of two numbers but does so by converting the sum into a string and then deserializing it into an integer.</span></span> <span data-ttu-id="ff3c4-141">Isso usa diversos recursos modernos do C#, tais como [diretivas `using static`](../../csharp/language-reference/keywords/using-static.md), [membros aptos para expressão](../../csharp/whats-new/csharp-7.md#more-expression-bodied-members) e [interpolação de cadeia de caracteres](../../csharp/language-reference/tokens/interpolated.md).</span><span class="sxs-lookup"><span data-stu-id="ff3c4-141">This makes use of a number of modern C# features, such as [`using static` directives](../../csharp/language-reference/keywords/using-static.md), [expression-bodied members](../../csharp/whats-new/csharp-7.md#more-expression-bodied-members), and [string interpolation](../../csharp/language-reference/tokens/interpolated.md).</span></span>

<span data-ttu-id="ff3c4-142">Crie a biblioteca com o comando [`dotnet build`](../tools/dotnet-build.md).</span><span class="sxs-lookup"><span data-stu-id="ff3c4-142">Build the library with the [`dotnet build`](../tools/dotnet-build.md) command.</span></span> <span data-ttu-id="ff3c4-143">Isso produz um arquivo *library.dll* em *golden/library/bin/Debug/netstandard1.4*:</span><span class="sxs-lookup"><span data-stu-id="ff3c4-143">This produces a *library.dll* file under *golden/library/bin/Debug/netstandard1.4*:</span></span>

```console
dotnet build
```

## <a name="create-the-test-project"></a><span data-ttu-id="ff3c4-144">Criar um projeto de teste</span><span class="sxs-lookup"><span data-stu-id="ff3c4-144">Create the test project</span></span>

<span data-ttu-id="ff3c4-145">Crie um projeto de teste para a biblioteca.</span><span class="sxs-lookup"><span data-stu-id="ff3c4-145">Build a test project for the library.</span></span> <span data-ttu-id="ff3c4-146">Na pasta *golden*, crie um novo projeto de teste:</span><span class="sxs-lookup"><span data-stu-id="ff3c4-146">From the *golden* folder, create a new test project:</span></span>

```console
dotnet new xunit -o test-library
```

<span data-ttu-id="ff3c4-147">Adicione o projeto de teste à solução:</span><span class="sxs-lookup"><span data-stu-id="ff3c4-147">Add the test project to the solution:</span></span>

```console
dotnet sln add test-library/test-library.csproj
```

<span data-ttu-id="ff3c4-148">Adicione uma referência do projeto à biblioteca que você criou na seção anterior para que o compilador possa localizar e usar o projeto de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="ff3c4-148">Add a project reference the library you created in the previous section so that the compiler can find and use the library project.</span></span> <span data-ttu-id="ff3c4-149">Use o comando [`dotnet add reference`](../tools/dotnet-add-reference.md):</span><span class="sxs-lookup"><span data-stu-id="ff3c4-149">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```console
dotnet add test-library/test-library.csproj reference library/library.csproj
```

<span data-ttu-id="ff3c4-150">Como alternativa, edite manualmente o arquivo *test-library.csproj* e adicione o seguinte nó:</span><span class="sxs-lookup"><span data-stu-id="ff3c4-150">Alternatively, manually edit the *test-library.csproj* file and add the following node:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\library\library.csproj" />
</ItemGroup>
```

<span data-ttu-id="ff3c4-151">Agora que as dependências foram devidamente configuradas, crie os testes para sua biblioteca.</span><span class="sxs-lookup"><span data-stu-id="ff3c4-151">Now that the dependencies have been properly configured, create the tests for your library.</span></span> <span data-ttu-id="ff3c4-152">Abra *UnitTest1.cs* e substitua o conteúdo pelo seguinte código:</span><span class="sxs-lookup"><span data-stu-id="ff3c4-152">Open *UnitTest1.cs* and replace its contents with the following code:</span></span>

```csharp
using Library;
using Xunit;

namespace TestApp
{
    public class LibraryTests
    {
        [Fact]
        public void TestThing() {
            Assert.NotEqual(42, new Thing().Get(19, 23));
        }
    }
}
```

<span data-ttu-id="ff3c4-153">Observe que você declara que o valor 42 não é igual a 19+23 (ou 42) quando você cria o teste de unidade pela primeira vez (`Assert.NotEqual`), que falhará.</span><span class="sxs-lookup"><span data-stu-id="ff3c4-153">Note that you assert the value 42 is not equal to 19+23 (or 42) when you first create the unit test (`Assert.NotEqual`), which will fail.</span></span> <span data-ttu-id="ff3c4-154">Uma etapa importante na criação de testes de unidade é criar o teste para falhar uma vez primeiro para confirmar sua lógica.</span><span class="sxs-lookup"><span data-stu-id="ff3c4-154">An important step in building unit tests is to create the test to fail once first to confirm its logic.</span></span>

<span data-ttu-id="ff3c4-155">Na pasta *golden*, execute os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="ff3c4-155">From the *golden* folder, execute the following commands:</span></span>

```console
dotnet restore 
dotnet test test-library/test-library.csproj
```

<span data-ttu-id="ff3c4-156">Esses comandos localizarão recursivamente todos os projetos para restaurar dependências, para compilá-las e para ativar o executor de teste xUnit para executar os testes.</span><span class="sxs-lookup"><span data-stu-id="ff3c4-156">These commands will recursively find all projects to restore dependencies, build them, and activate the xUnit test runner to run the tests.</span></span> <span data-ttu-id="ff3c4-157">O teste único falha, conforme esperado.</span><span class="sxs-lookup"><span data-stu-id="ff3c4-157">The single test fails, as you expect.</span></span>

<span data-ttu-id="ff3c4-158">Edite o arquivo *UnitTest1.cs* e altere a asserção de `Assert.NotEqual` para `Assert.Equal`.</span><span class="sxs-lookup"><span data-stu-id="ff3c4-158">Edit the *UnitTest1.cs* file and change the assertion from `Assert.NotEqual` to `Assert.Equal`.</span></span> <span data-ttu-id="ff3c4-159">Execute o seguinte comando da pasta *golden* para executar o teste novamente, que é aprovado dessa vez:</span><span class="sxs-lookup"><span data-stu-id="ff3c4-159">Execute the following command from the *golden* folder to re-run the test, which passes this time:</span></span>

```console
dotnet test test-library/test-library.csproj
```

## <a name="create-the-console-app"></a><span data-ttu-id="ff3c4-160">Criar o aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="ff3c4-160">Create the console app</span></span>

<span data-ttu-id="ff3c4-161">O aplicativo de console criado ao longo das etapas a seguir usa uma dependência no projeto de biblioteca criado anteriormente e chama seu método de biblioteca quando é executado.</span><span class="sxs-lookup"><span data-stu-id="ff3c4-161">The console app you create over the following steps takes a dependency on the library project you created earlier and calls its library method when it runs.</span></span> <span data-ttu-id="ff3c4-162">Usando esse padrão de desenvolvimento, você verá como criar bibliotecas reutilizáveis para vários projetos.</span><span class="sxs-lookup"><span data-stu-id="ff3c4-162">Using this pattern of development, you see how to create reusable libraries for multiple projects.</span></span>

<span data-ttu-id="ff3c4-163">Crie um novo aplicativo de console da pasta *golden*:</span><span class="sxs-lookup"><span data-stu-id="ff3c4-163">Create a new console application from the *golden* folder:</span></span>

```console
dotnet new console -o app
```

<span data-ttu-id="ff3c4-164">Adicione o projeto de aplicativo de console à solução:</span><span class="sxs-lookup"><span data-stu-id="ff3c4-164">Add the console app project to the solution:</span></span>

```console
dotnet sln add app/app.csproj
```

<span data-ttu-id="ff3c4-165">Crie a dependência na biblioteca executando o comando `dotnet add reference`:</span><span class="sxs-lookup"><span data-stu-id="ff3c4-165">Create the dependency on the library by running the `dotnet add reference` command:</span></span>

```console
dotnet add app/app.csproj reference library/library.csproj
```

<span data-ttu-id="ff3c4-166">Execute `dotnet restore` ([veja observação](#dotnet-restore-note)) para restaurar as dependências dos três projetos na solução.</span><span class="sxs-lookup"><span data-stu-id="ff3c4-166">Run `dotnet restore` ([see note](#dotnet-restore-note)) to restore the dependencies of the three projects in the solution.</span></span> <span data-ttu-id="ff3c4-167">Abra *Program.cs* e substitua o conteúdo do método `Main` pela seguinte linha:</span><span class="sxs-lookup"><span data-stu-id="ff3c4-167">Open *Program.cs* and replace the contents of the `Main` method with the following line:</span></span>

```csharp
WriteLine($"The answer is {new Thing().Get(19, 23)}");
```

<span data-ttu-id="ff3c4-168">Adicione duas diretivas `using` à parte superior do arquivo *Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="ff3c4-168">Add two `using` directives to the top of the *Program.cs* file:</span></span>

```csharp
using static System.Console;
using Library;
```

<span data-ttu-id="ff3c4-169">Execute o seguinte comando `dotnet run` para executar o executável, em que a opção `-p` para `dotnet run` especifica o projeto para o aplicativo principal.</span><span class="sxs-lookup"><span data-stu-id="ff3c4-169">Execute the following `dotnet run` command to run the executable, where the `-p` option to `dotnet run` specifies the project for the main application.</span></span> <span data-ttu-id="ff3c4-170">O aplicativo produz a cadeia de caracteres "A resposta é 42".</span><span class="sxs-lookup"><span data-stu-id="ff3c4-170">The app produces the string "The answer is 42".</span></span>

```console
dotnet run -p app/app.csproj
```

## <a name="debug-the-application"></a><span data-ttu-id="ff3c4-171">Depurar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="ff3c4-171">Debug the application</span></span>

<span data-ttu-id="ff3c4-172">Defina um ponto de interrupção na instrução `WriteLine` no método `Main`.</span><span class="sxs-lookup"><span data-stu-id="ff3c4-172">Set a breakpoint at the `WriteLine` statement in the `Main` method.</span></span> <span data-ttu-id="ff3c4-173">Faça isso pressionando a tecla <kbd>F9</kbd> quando o cursor estiver sobre a linha `WriteLine` ou clicando com o mouse na margem esquerda na linha em que deseja definir o ponto de interrupção.</span><span class="sxs-lookup"><span data-stu-id="ff3c4-173">Do this by either pressing the <kbd>F9</kbd> key when the cursor is over the `WriteLine` line or by clicking the mouse in the left margin on the line where you want to set the breakpoint.</span></span> <span data-ttu-id="ff3c4-174">Um círculo vermelho será exibido na margem ao lado da linha de código.</span><span class="sxs-lookup"><span data-stu-id="ff3c4-174">A red circle will appear in the margin next to the line of code.</span></span> <span data-ttu-id="ff3c4-175">Quando o ponto de interrupção for atingido, a execução do código será interrompida *antes* de a linha do ponto de interrupção ser executada.</span><span class="sxs-lookup"><span data-stu-id="ff3c4-175">When the breakpoint is reached, code execution will stop *before* the breakpoint line is executed.</span></span>

<span data-ttu-id="ff3c4-176">Abra a guia do depurador selecionando o ícone Depurar na barra de ferramentas do Visual Studio Code, selecionando **Exibir > Depurar** na barra de menus ou usando o atalho de teclado <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>:</span><span class="sxs-lookup"><span data-stu-id="ff3c4-176">Open the debugger tab by selecting the Debug icon in the Visual Studio Code toolbar, selecting **View > Debug** from the menu bar, or using the keyboard shortcut <kbd>CTRL</kbd>+<kbd>SHIFT</kbd>+<kbd>D</kbd>:</span></span>

![Depurador do Visual Studio Code](./media/using-on-macos/vscodedebugger.png)

<span data-ttu-id="ff3c4-178">Pressione o botão Reproduzir para iniciar o aplicativo no depurador.</span><span class="sxs-lookup"><span data-stu-id="ff3c4-178">Press the Play button to start the application under the debugger.</span></span> <span data-ttu-id="ff3c4-179">O aplicativo inicia a execução e é executado até o ponto de interrupção, quando ele para.</span><span class="sxs-lookup"><span data-stu-id="ff3c4-179">The app begins execution and runs to the breakpoint, where it stops.</span></span> <span data-ttu-id="ff3c4-180">Inspecione o método `Get` e verifique se você transmitiu os argumentos corretos.</span><span class="sxs-lookup"><span data-stu-id="ff3c4-180">Step into the `Get` method and make sure that you have passed in the correct arguments.</span></span> <span data-ttu-id="ff3c4-181">Confirme se a resposta é 42.</span><span class="sxs-lookup"><span data-stu-id="ff3c4-181">Confirm that the answer is 42.</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]