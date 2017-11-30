---
title: "Guia de Introdução ao .NET Core no macOS"
description: "Este documento fornece as etapas e o fluxo de trabalho para criar uma Solução do .NET Core usando o Visual Studio Code."
keywords: .NET, .NET Core, Mac, macOS, Visual Studio Code
author: bleroy
ms.author: mairaw
ms.date: 03/23/2017
ms.topic: get-started-article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 8ad82148-dac8-4b31-9128-b0e9610f4d9b
ms.openlocfilehash: b172e5fc4fcf9dd5c1e6f268f3c046e77592ebd3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="getting-started-with-net-core-on-macos"></a><span data-ttu-id="bd7ee-104">Guia de Introdução ao .NET Core no macOS</span><span class="sxs-lookup"><span data-stu-id="bd7ee-104">Getting started with .NET Core on macOS</span></span>

<span data-ttu-id="bd7ee-105">Este documento fornece as etapas e o fluxo de trabalho para criar uma solução do .NET Core para macOS.</span><span class="sxs-lookup"><span data-stu-id="bd7ee-105">This document provides the steps and workflow to create a .NET Core solution for macOS.</span></span> <span data-ttu-id="bd7ee-106">Saiba como criar projetos, testes de unidade, usar as ferramentas de depuração e incorporar bibliotecas de terceiros por meio do [NuGet](https://www.nuget.org/).</span><span class="sxs-lookup"><span data-stu-id="bd7ee-106">Learn how to create projects, unit tests, use the debugging tools, and incorporate third-party libraries via [NuGet](https://www.nuget.org/).</span></span>

> [!NOTE]
> <span data-ttu-id="bd7ee-107">Esse artigo usa o [Visual Studio Code](http://code.visualstudio.com) no macOS.</span><span class="sxs-lookup"><span data-stu-id="bd7ee-107">This article uses [Visual Studio Code](http://code.visualstudio.com) on macOS.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="bd7ee-108">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="bd7ee-108">Prerequisites</span></span>

<span data-ttu-id="bd7ee-109">Instalar o [SDK do .NET Core](https://www.microsoft.com/net/core).</span><span class="sxs-lookup"><span data-stu-id="bd7ee-109">Install the [.NET Core SDK](https://www.microsoft.com/net/core).</span></span> <span data-ttu-id="bd7ee-110">O SDK do .NET Core inclui a versão mais recente da estrutura do .NET Core e do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="bd7ee-110">The .NET Core SDK includes the latest release of the .NET Core framework and runtime.</span></span>

<span data-ttu-id="bd7ee-111">Instalar o [Visual Studio Code](http://code.visualstudio.com).</span><span class="sxs-lookup"><span data-stu-id="bd7ee-111">Install [Visual Studio Code](http://code.visualstudio.com).</span></span> <span data-ttu-id="bd7ee-112">No decorrer deste artigo, você vai instalar as extensões do Visual Studio Code que melhoram a experiência de desenvolvimento do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bd7ee-112">During the course of this article, you also install Visual Studio Code extensions that improve the .NET Core development experience.</span></span>

<span data-ttu-id="bd7ee-113">Para instalar a extensão de C# do Visual Studio Code, abra o Visual Studio Code e pressione <kbd>F1</kbd> para abrir a paleta do programa.</span><span class="sxs-lookup"><span data-stu-id="bd7ee-113">Install the Visual Studio Code C# extension by opening Visual Studio Code and pressing <kbd>F1</kbd> to open the Visual Studio Code palette.</span></span> <span data-ttu-id="bd7ee-114">Digite **ext install** para ver a lista de extensões.</span><span class="sxs-lookup"><span data-stu-id="bd7ee-114">Type **ext install** to see the list of extensions.</span></span> <span data-ttu-id="bd7ee-115">Selecione a extensão de C#.</span><span class="sxs-lookup"><span data-stu-id="bd7ee-115">Select the C# extension.</span></span> <span data-ttu-id="bd7ee-116">Reinicie o Visual Studio Code para ativar a extensão.</span><span class="sxs-lookup"><span data-stu-id="bd7ee-116">Restart Visual Studio Code to activate the extension.</span></span> <span data-ttu-id="bd7ee-117">Para obter mais informações, consulte a [Documentação da Extensão de C# do Visual Studio Code](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span><span class="sxs-lookup"><span data-stu-id="bd7ee-117">For more information, see the [Visual Studio Code C# Extension documentation](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span></span>

## <a name="getting-started"></a><span data-ttu-id="bd7ee-118">Introdução</span><span class="sxs-lookup"><span data-stu-id="bd7ee-118">Getting started</span></span>

<span data-ttu-id="bd7ee-119">Neste tutorial, você criará três projetos: um projeto de biblioteca, testes para esse projeto de biblioteca e um aplicativo de console que usa a biblioteca.</span><span class="sxs-lookup"><span data-stu-id="bd7ee-119">In this tutorial, you create three projects: a library project, tests for that library project, and a console application that makes use of the library.</span></span> <span data-ttu-id="bd7ee-120">Você pode [exibir ou baixar a fonte](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/golden) para este tópico no repositório dotnet/docs do GitHub.</span><span class="sxs-lookup"><span data-stu-id="bd7ee-120">You can [view or download the source](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/golden) for this topic at the dotnet/docs repository on GitHub.</span></span> <span data-ttu-id="bd7ee-121">Para obter instruções de download, consulte [Exemplos e tutoriais](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="bd7ee-121">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

<span data-ttu-id="bd7ee-122">Inicie o Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="bd7ee-122">Start Visual Studio Code.</span></span> <span data-ttu-id="bd7ee-123">Pressione <kbd>Ctrl</kbd>+<kbd>\\`</kbd> (o caractere de acento grave) ou escolha **Exibir > Terminal Integrado** no menu para abrir um terminal inserido no Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="bd7ee-123">Press <kbd>Ctrl</kbd>+<kbd>\\`</kbd> (the backquote or backtick character) or select **View > Integrated Terminal** from the menu to open an embedded terminal in Visual Studio Code.</span></span> <span data-ttu-id="bd7ee-124">Você ainda pode abrir um shell externo com o comando **Abrir no Prompt de Comando** do Gerenciador (**Abrir no Terminal**, no Mac ou Linux), caso prefira trabalhar fora do Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="bd7ee-124">You can still open an external shell with the Explorer **Open in Command Prompt** command (**Open in Terminal** on Mac or Linux) if you prefer to work outside of Visual Studio Code.</span></span>

<span data-ttu-id="bd7ee-125">Comece criando um arquivo de solução, que serve como um contêiner para um ou mais projetos do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bd7ee-125">Begin by creating a solution file, which serves as a container for one or more .NET Core projects.</span></span> <span data-ttu-id="bd7ee-126">No terminal, crie uma pasta *golden* e abra a pasta.</span><span class="sxs-lookup"><span data-stu-id="bd7ee-126">In the terminal, create a *golden* folder and open the folder.</span></span> <span data-ttu-id="bd7ee-127">Essa pasta é a raiz da sua solução.</span><span class="sxs-lookup"><span data-stu-id="bd7ee-127">This folder is the root of your solution.</span></span> <span data-ttu-id="bd7ee-128">Execute o comando [`dotnet new`](../tools/dotnet-new.md) para criar uma nova solução, *golden.sln*:</span><span class="sxs-lookup"><span data-stu-id="bd7ee-128">Run the [`dotnet new`](../tools/dotnet-new.md) command to create a new solution, *golden.sln*:</span></span>

```console
dotnet new sln
```

<span data-ttu-id="bd7ee-129">Na pasta *golden*, execute o seguinte comando para criar um projeto de biblioteca, que produz dois arquivos, *library.csproj* e *Class1.cs*, na pasta *library*:</span><span class="sxs-lookup"><span data-stu-id="bd7ee-129">From the *golden* folder, execute the following command to create a library project, which produces two files,*library.csproj* and *Class1.cs*, in the *library* folder:</span></span>

```console
dotnet new classlib -o library
```

<span data-ttu-id="bd7ee-130">Execute o comando [`dotnet sln`](../tools/dotnet-sln.md) para adicionar o projeto *library.csproj* recém-criado à solução:</span><span class="sxs-lookup"><span data-stu-id="bd7ee-130">Execute the [`dotnet sln`](../tools/dotnet-sln.md) command to add the newly created *library.csproj* project to the solution:</span></span>

```console
dotnet sln add library/library.csproj
```

<span data-ttu-id="bd7ee-131">O arquivo *library.csproj* contém as seguintes informações:</span><span class="sxs-lookup"><span data-stu-id="bd7ee-131">The *library.csproj* file contains the following information:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netstandard1.4</TargetFramework>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="bd7ee-132">Nossos métodos da biblioteca serializam e desserializam os objetos no formato JSON.</span><span class="sxs-lookup"><span data-stu-id="bd7ee-132">Our library methods serialize and deserialize objects in JSON format.</span></span> <span data-ttu-id="bd7ee-133">Para dar suporte à serialização e desserialização JSON, adicione uma referência ao pacote NuGet `Newtonsoft.Json`.</span><span class="sxs-lookup"><span data-stu-id="bd7ee-133">To support JSON serialization and deserialization, add a reference to the `Newtonsoft.Json` NuGet package.</span></span> <span data-ttu-id="bd7ee-134">O comando `dotnet add` adiciona novos itens a um projeto.</span><span class="sxs-lookup"><span data-stu-id="bd7ee-134">The `dotnet add` command adds new items to a project.</span></span> <span data-ttu-id="bd7ee-135">Para adicionar uma referência a um pacote NuGet, use o comando [`dotnet add package`](../tools/dotnet-add-package.md) e especifique o nome do pacote:</span><span class="sxs-lookup"><span data-stu-id="bd7ee-135">To add a reference to a NuGet package, use the [`dotnet add package`](../tools/dotnet-add-package.md) command and specify the name of the package:</span></span>

```console
dotnet add library package Newtonsoft.Json
```

<span data-ttu-id="bd7ee-136">Isso adiciona `Newtonsoft.Json` e suas dependências ao projeto de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="bd7ee-136">This adds `Newtonsoft.Json` and its dependencies to the library project.</span></span> <span data-ttu-id="bd7ee-137">Como alternativa, edite manualmente o arquivo *library.csproj* e adicione o seguinte nó:</span><span class="sxs-lookup"><span data-stu-id="bd7ee-137">Alternatively, manually edit the *library.csproj* file and add the following node:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="10.0.1" />
</ItemGroup>
```

<span data-ttu-id="bd7ee-138">Executar [ `dotnet restore` ](../tools/dotnet-restore.md), ([consulte a Observação](#dotnet-restore-note)) que restaura as dependências e cria um *obj* pasta dentro de *biblioteca* com três arquivos, incluindo um *project.assets.json* arquivo:</span><span class="sxs-lookup"><span data-stu-id="bd7ee-138">Execute [`dotnet restore`](../tools/dotnet-restore.md), ([see note](#dotnet-restore-note)) which restores dependencies and creates an *obj* folder inside *library* with three files in it, including a *project.assets.json* file:</span></span>

```console
dotnet restore
```

<span data-ttu-id="bd7ee-139">Na pasta *library*, renomeie o arquivo *Class1.cs* como *Thing.cs*.</span><span class="sxs-lookup"><span data-stu-id="bd7ee-139">In the *library* folder, rename the file *Class1.cs* to *Thing.cs*.</span></span> <span data-ttu-id="bd7ee-140">Substitua o código pelo seguinte:</span><span class="sxs-lookup"><span data-stu-id="bd7ee-140">Replace the code with the following:</span></span>

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

<span data-ttu-id="bd7ee-141">A classe `Thing` contém um método público, `Get`, que retorna a soma de dois números, mas faz isso ao converter a soma em uma cadeia de caracteres e, em seguida, desserializá-los em um inteiro.</span><span class="sxs-lookup"><span data-stu-id="bd7ee-141">The `Thing` class contains one public method, `Get`, which returns the sum of two numbers but does so by converting the sum into a string and then deserializing it into an integer.</span></span> <span data-ttu-id="bd7ee-142">Isso usa diversas funcionalidades modernas de C#, tais como [diretivas `using static`](../../csharp/language-reference/keywords/using-static.md), [membros aptos para expressão](../../csharp/whats-new/csharp-7.md#more-expression-bodied-members) e [cadeias de caracteres interpoladas](../../csharp/language-reference/keywords/interpolated-strings.md).</span><span class="sxs-lookup"><span data-stu-id="bd7ee-142">This makes use of a number of modern C# features, such as [`using static` directives](../../csharp/language-reference/keywords/using-static.md), [expression-bodied members](../../csharp/whats-new/csharp-7.md#more-expression-bodied-members), and [interpolated strings](../../csharp/language-reference/keywords/interpolated-strings.md).</span></span>

<span data-ttu-id="bd7ee-143">Crie a biblioteca com o comando [`dotnet build`](../tools/dotnet-build.md).</span><span class="sxs-lookup"><span data-stu-id="bd7ee-143">Build the library with the [`dotnet build`](../tools/dotnet-build.md) command.</span></span> <span data-ttu-id="bd7ee-144">Isso produz um arquivo *library.dll* em *golden/library/bin/Debug/netstandard1.4*:</span><span class="sxs-lookup"><span data-stu-id="bd7ee-144">This produces a *library.dll* file under *golden/library/bin/Debug/netstandard1.4*:</span></span>

```console
dotnet build
```

## <a name="create-the-test-project"></a><span data-ttu-id="bd7ee-145">Criar um projeto de teste</span><span class="sxs-lookup"><span data-stu-id="bd7ee-145">Create the test project</span></span>

<span data-ttu-id="bd7ee-146">Crie um projeto de teste para a biblioteca.</span><span class="sxs-lookup"><span data-stu-id="bd7ee-146">Build a test project for the library.</span></span> <span data-ttu-id="bd7ee-147">Na pasta *golden*, crie um novo projeto de teste:</span><span class="sxs-lookup"><span data-stu-id="bd7ee-147">From the *golden* folder, create a new test project:</span></span>

```console
dotnet new xunit -o test-library
```

<span data-ttu-id="bd7ee-148">Adicione o projeto de teste à solução:</span><span class="sxs-lookup"><span data-stu-id="bd7ee-148">Add the test project to the solution:</span></span>

```console
dotnet sln add test-library/test-library.csproj
```

<span data-ttu-id="bd7ee-149">Adicione uma referência do projeto à biblioteca que você criou na seção anterior para que o compilador possa localizar e usar o projeto de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="bd7ee-149">Add a project reference the library you created in the previous section so that the compiler can find and use the library project.</span></span> <span data-ttu-id="bd7ee-150">Use o comando [`dotnet add reference`](../tools/dotnet-add-reference.md):</span><span class="sxs-lookup"><span data-stu-id="bd7ee-150">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```console
dotnet add test-library/test-library.csproj reference library/library.csproj
```

<span data-ttu-id="bd7ee-151">Como alternativa, edite manualmente o arquivo *test-library.csproj* e adicione o seguinte nó:</span><span class="sxs-lookup"><span data-stu-id="bd7ee-151">Alternatively, manually edit the *test-library.csproj* file and add the following node:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\library\library.csproj" />
</ItemGroup>
```

<span data-ttu-id="bd7ee-152">Agora que as dependências foram devidamente configuradas, crie os testes para sua biblioteca.</span><span class="sxs-lookup"><span data-stu-id="bd7ee-152">Now that the dependencies have been properly configured, create the tests for your library.</span></span> <span data-ttu-id="bd7ee-153">Abra *UnitTest1.cs* e substitua o conteúdo pelo seguinte código:</span><span class="sxs-lookup"><span data-stu-id="bd7ee-153">Open *UnitTest1.cs* and replace its contents with the following code:</span></span>

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

<span data-ttu-id="bd7ee-154">Observe que você declara que o valor 42 não é igual a 19+23 (ou 42) quando você cria o teste de unidade pela primeira vez (`Assert.NotEqual`), que falhará.</span><span class="sxs-lookup"><span data-stu-id="bd7ee-154">Note that you assert the value 42 is not equal to 19+23 (or 42) when you first create the unit test (`Assert.NotEqual`), which will fail.</span></span> <span data-ttu-id="bd7ee-155">Uma etapa importante na criação de testes de unidade é criar o teste para falhar uma vez primeiro para confirmar sua lógica.</span><span class="sxs-lookup"><span data-stu-id="bd7ee-155">An important step in building unit tests is to create the test to fail once first to confirm its logic.</span></span>

<span data-ttu-id="bd7ee-156">Na pasta *golden*, execute os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="bd7ee-156">From the *golden* folder, execute the following commands:</span></span>

```console
dotnet restore 
dotnet test test-library/test-library.csproj
```

<span data-ttu-id="bd7ee-157">Esses comandos localizarão recursivamente todos os projetos para restaurar dependências, para compilá-las e para ativar o executor de teste xUnit para executar os testes.</span><span class="sxs-lookup"><span data-stu-id="bd7ee-157">These commands will recursively find all projects to restore dependencies, build them, and activate the xUnit test runner to run the tests.</span></span> <span data-ttu-id="bd7ee-158">O teste único falha, conforme esperado.</span><span class="sxs-lookup"><span data-stu-id="bd7ee-158">The single test fails, as you expect.</span></span>

<span data-ttu-id="bd7ee-159">Edite o arquivo *UnitTest1.cs* e altere a asserção de `Assert.NotEqual` para `Assert.Equal`.</span><span class="sxs-lookup"><span data-stu-id="bd7ee-159">Edit the *UnitTest1.cs* file and change the assertion from `Assert.NotEqual` to `Assert.Equal`.</span></span> <span data-ttu-id="bd7ee-160">Execute o seguinte comando da pasta *golden* para executar o teste novamente, que é aprovado dessa vez:</span><span class="sxs-lookup"><span data-stu-id="bd7ee-160">Execute the following command from the *golden* folder to re-run the test, which passes this time:</span></span>

```console
dotnet test test-library/test-library.csproj
```

## <a name="create-the-console-app"></a><span data-ttu-id="bd7ee-161">Criar o aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="bd7ee-161">Create the console app</span></span>

<span data-ttu-id="bd7ee-162">O aplicativo de console criado ao longo das etapas a seguir usa uma dependência no projeto de biblioteca criado anteriormente e chama seu método de biblioteca quando é executado.</span><span class="sxs-lookup"><span data-stu-id="bd7ee-162">The console app you create over the following steps takes a dependency on the library project you created earlier and calls its library method when it runs.</span></span> <span data-ttu-id="bd7ee-163">Usando esse padrão de desenvolvimento, você verá como criar bibliotecas reutilizáveis para vários projetos.</span><span class="sxs-lookup"><span data-stu-id="bd7ee-163">Using this pattern of development, you see how to create reusable libraries for multiple projects.</span></span>

<span data-ttu-id="bd7ee-164">Crie um novo aplicativo de console da pasta *golden*:</span><span class="sxs-lookup"><span data-stu-id="bd7ee-164">Create a new console application from the *golden* folder:</span></span>

```console
dotnet new console -o app
```

<span data-ttu-id="bd7ee-165">Adicione o projeto de aplicativo de console à solução:</span><span class="sxs-lookup"><span data-stu-id="bd7ee-165">Add the console app project to the solution:</span></span>

```console
dotnet sln add app/app.csproj
```

<span data-ttu-id="bd7ee-166">Crie a dependência na biblioteca executando o comando `dotnet add reference`:</span><span class="sxs-lookup"><span data-stu-id="bd7ee-166">Create the dependency on the library by running the `dotnet add reference` command:</span></span>

```console
dotnet add app/app.csproj reference library/library.csproj
```

<span data-ttu-id="bd7ee-167">Executar `dotnet restore` ([consulte a Observação](#dotnet-restore-note)) para restaurar as dependências de três projetos na solução.</span><span class="sxs-lookup"><span data-stu-id="bd7ee-167">Run `dotnet restore` ([see note](#dotnet-restore-note)) to restore the dependencies of the three projects in the solution.</span></span> <span data-ttu-id="bd7ee-168">Abra *Program.cs* e substitua o conteúdo do método `Main` pela seguinte linha:</span><span class="sxs-lookup"><span data-stu-id="bd7ee-168">Open *Program.cs* and replace the contents of the `Main` method with the following line:</span></span>

```csharp
WriteLine($"The answer is {new Thing().Get(19, 23)}");
```

<span data-ttu-id="bd7ee-169">Adicione duas diretivas `using` à parte superior do arquivo *Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="bd7ee-169">Add two `using` directives to the top of the *Program.cs* file:</span></span>

```csharp
using static System.Console;
using Library;
```

<span data-ttu-id="bd7ee-170">Execute o seguinte comando `dotnet run` para executar o executável, em que a opção `-p` para `dotnet run` especifica o projeto para o aplicativo principal.</span><span class="sxs-lookup"><span data-stu-id="bd7ee-170">Execute the following `dotnet run` command to run the executable, where the `-p` option to `dotnet run` specifies the project for the main application.</span></span> <span data-ttu-id="bd7ee-171">O aplicativo produz a cadeia de caracteres "A resposta é 42".</span><span class="sxs-lookup"><span data-stu-id="bd7ee-171">The app produces the string "The answer is 42".</span></span>

```console
dotnet run -p app/app.csproj
```

## <a name="debug-the-application"></a><span data-ttu-id="bd7ee-172">Depurar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="bd7ee-172">Debug the application</span></span>

<span data-ttu-id="bd7ee-173">Defina um ponto de interrupção na instrução `WriteLine` no método `Main`.</span><span class="sxs-lookup"><span data-stu-id="bd7ee-173">Set a breakpoint at the `WriteLine` statement in the `Main` method.</span></span> <span data-ttu-id="bd7ee-174">Faça isso pressionando a tecla <kbd>F9</kbd> quando o cursor estiver sobre a linha `WriteLine` ou clicando com o mouse na margem esquerda na linha em que deseja definir o ponto de interrupção.</span><span class="sxs-lookup"><span data-stu-id="bd7ee-174">Do this by either pressing the <kbd>F9</kbd> key when the cursor is over the `WriteLine` line or by clicking the mouse in the left margin on the line where you want to set the breakpoint.</span></span> <span data-ttu-id="bd7ee-175">Um círculo vermelho será exibido na margem ao lado da linha de código.</span><span class="sxs-lookup"><span data-stu-id="bd7ee-175">A red circle will appear in the margin next to the line of code.</span></span> <span data-ttu-id="bd7ee-176">Quando o ponto de interrupção for atingido, a execução do código será interrompida *antes* de a linha do ponto de interrupção ser executada.</span><span class="sxs-lookup"><span data-stu-id="bd7ee-176">When the breakpoint is reached, code execution will stop *before* the breakpoint line is executed.</span></span>

<span data-ttu-id="bd7ee-177">Abra a guia do depurador selecionando o ícone Depurar na barra de ferramentas do Visual Studio Code, selecionando **Exibir > Depurar** na barra de menus ou usando o atalho de teclado <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>:</span><span class="sxs-lookup"><span data-stu-id="bd7ee-177">Open the debugger tab by selecting the Debug icon in the Visual Studio Code toolbar, selecting **View > Debug** from the menu bar, or using the keyboard shortcut <kbd>CTRL</kbd>+<kbd>SHIFT</kbd>+<kbd>D</kbd>:</span></span>

![Depurador do Visual Studio Code](./media/using-on-macos/vscodedebugger.png)

<span data-ttu-id="bd7ee-179">Pressione o botão Reproduzir para iniciar o aplicativo no depurador.</span><span class="sxs-lookup"><span data-stu-id="bd7ee-179">Press the Play button to start the application under the debugger.</span></span> <span data-ttu-id="bd7ee-180">O aplicativo inicia a execução e é executado até o ponto de interrupção, quando ele para.</span><span class="sxs-lookup"><span data-stu-id="bd7ee-180">The app begins execution and runs to the breakpoint, where it stops.</span></span> <span data-ttu-id="bd7ee-181">Inspecione o método `Get` e verifique se você transmitiu os argumentos corretos.</span><span class="sxs-lookup"><span data-stu-id="bd7ee-181">Step into the `Get` method and make sure that you have passed in the correct arguments.</span></span> <span data-ttu-id="bd7ee-182">Confirme se a resposta é 42.</span><span class="sxs-lookup"><span data-stu-id="bd7ee-182">Confirm that the answer is 42.</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]