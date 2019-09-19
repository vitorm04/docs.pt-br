---
title: 'Tutorial: Criar uma solução .NET Core no macOS usando Visual Studio Code'
description: Este documento fornece as etapas e o fluxo de trabalho para criar uma Solução do .NET Core usando o Visual Studio Code.
ms.date: 03/23/2017
ms.custom: seodec18
ms.openlocfilehash: 5df43ae235b9fd901a65f7f8898bec67e24de682
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117364"
---
# <a name="tutorial-create-a-net-core-solution-in-macos-using-visual-studio-code"></a><span data-ttu-id="17394-103">Tutorial: Criar uma solução .NET Core no macOS usando Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="17394-103">Tutorial: Create a .NET Core solution in macOS using Visual Studio Code</span></span>

<span data-ttu-id="17394-104">Este documento fornece as etapas e o fluxo de trabalho para criar uma solução do .NET Core para macOS.</span><span class="sxs-lookup"><span data-stu-id="17394-104">This document provides the steps and workflow to create a .NET Core solution for macOS.</span></span> <span data-ttu-id="17394-105">Saiba como criar projetos, testes de unidade, usar as ferramentas de depuração e incorporar bibliotecas de terceiros por meio do [NuGet](https://www.nuget.org/).</span><span class="sxs-lookup"><span data-stu-id="17394-105">Learn how to create projects, unit tests, use the debugging tools, and incorporate third-party libraries via [NuGet](https://www.nuget.org/).</span></span>

> [!NOTE]
> <span data-ttu-id="17394-106">Esse artigo usa o [Visual Studio Code](https://code.visualstudio.com) no macOS.</span><span class="sxs-lookup"><span data-stu-id="17394-106">This article uses [Visual Studio Code](https://code.visualstudio.com) on macOS.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="17394-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="17394-107">Prerequisites</span></span>

<span data-ttu-id="17394-108">Instalar o [SDK do .NET Core](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="17394-108">Install the [.NET Core SDK](https://dotnet.microsoft.com/download).</span></span> <span data-ttu-id="17394-109">O SDK do .NET Core inclui a versão mais recente da estrutura do .NET Core e do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="17394-109">The .NET Core SDK includes the latest release of the .NET Core framework and runtime.</span></span>

<span data-ttu-id="17394-110">Instalar o [Visual Studio Code](https://code.visualstudio.com).</span><span class="sxs-lookup"><span data-stu-id="17394-110">Install [Visual Studio Code](https://code.visualstudio.com).</span></span> <span data-ttu-id="17394-111">No decorrer deste artigo, você vai instalar as extensões do Visual Studio Code que melhoram a experiência de desenvolvimento do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="17394-111">During the course of this article, you also install Visual Studio Code extensions that improve the .NET Core development experience.</span></span>

<span data-ttu-id="17394-112">Para instalar a extensão de C# do Visual Studio Code, abra o Visual Studio Code e pressione <kbd>F1</kbd> para abrir a paleta do programa.</span><span class="sxs-lookup"><span data-stu-id="17394-112">Install the Visual Studio Code C# extension by opening Visual Studio Code and pressing <kbd>F1</kbd> to open the Visual Studio Code palette.</span></span> <span data-ttu-id="17394-113">Digite **ext install** para ver a lista de extensões.</span><span class="sxs-lookup"><span data-stu-id="17394-113">Type **ext install** to see the list of extensions.</span></span> <span data-ttu-id="17394-114">Selecione a extensão de C#.</span><span class="sxs-lookup"><span data-stu-id="17394-114">Select the C# extension.</span></span> <span data-ttu-id="17394-115">Reinicie o Visual Studio Code para ativar a extensão.</span><span class="sxs-lookup"><span data-stu-id="17394-115">Restart Visual Studio Code to activate the extension.</span></span> <span data-ttu-id="17394-116">Para obter mais informações, consulte a [Documentação da Extensão de C# do Visual Studio Code](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span><span class="sxs-lookup"><span data-stu-id="17394-116">For more information, see the [Visual Studio Code C# Extension documentation](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span></span>

## <a name="get-started"></a><span data-ttu-id="17394-117">Introdução</span><span class="sxs-lookup"><span data-stu-id="17394-117">Get started</span></span>

<span data-ttu-id="17394-118">Neste tutorial, você criará três projetos: um projeto de biblioteca, testes para esse projeto de biblioteca e um aplicativo de console que usa a biblioteca.</span><span class="sxs-lookup"><span data-stu-id="17394-118">In this tutorial, you create three projects: a library project, tests for that library project, and a console application that makes use of the library.</span></span> <span data-ttu-id="17394-119">Você pode [exibir ou baixar a fonte](https://github.com/dotnet/samples/tree/master/core/getting-started/golden) para este tópico no repositório dotnet/samples do GitHub.</span><span class="sxs-lookup"><span data-stu-id="17394-119">You can [view or download the source](https://github.com/dotnet/samples/tree/master/core/getting-started/golden) for this topic at the dotnet/samples repository on GitHub.</span></span> <span data-ttu-id="17394-120">Para obter instruções de download, consulte [Exemplos e tutoriais](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="17394-120">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

<span data-ttu-id="17394-121">Inicie o Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="17394-121">Start Visual Studio Code.</span></span> <span data-ttu-id="17394-122">Pressione <kbd>Ctrl</kbd>+<kbd>\`</kbd> (o caractere de acento grave) ou escolha **Exibir > Terminal Integrado** no menu para abrir um terminal inserido no Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="17394-122">Press <kbd>Ctrl</kbd>+<kbd>\`</kbd> (the backquote or backtick character) or select **View > Integrated Terminal** from the menu to open an embedded terminal in Visual Studio Code.</span></span> <span data-ttu-id="17394-123">Você ainda pode abrir um shell externo com o comando **Abrir no Prompt de Comando** do Gerenciador (**Abrir no Terminal**, no Mac ou Linux), caso prefira trabalhar fora do Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="17394-123">You can still open an external shell with the Explorer **Open in Command Prompt** command (**Open in Terminal** on Mac or Linux) if you prefer to work outside of Visual Studio Code.</span></span>

<span data-ttu-id="17394-124">Comece criando um arquivo de solução, que serve como um contêiner para um ou mais projetos do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="17394-124">Begin by creating a solution file, which serves as a container for one or more .NET Core projects.</span></span> <span data-ttu-id="17394-125">No terminal, execute o [`dotnet new`](../tools/dotnet-new.md) comando para criar uma nova solução *Golden. sln* dentro de uma nova pasta chamada *Golden*:</span><span class="sxs-lookup"><span data-stu-id="17394-125">In the terminal, run the [`dotnet new`](../tools/dotnet-new.md) command to create a new solution *golden.sln* inside a new folder named *golden*:</span></span>

```dotnetcli
dotnet new sln -o golden
```

<span data-ttu-id="17394-126">Navegue até a nova pasta *Golden* e execute o comando a seguir para criar um projeto de biblioteca, que produz dois arquivos,*library. csproj* e *Class1.cs*, na pasta *biblioteca* :</span><span class="sxs-lookup"><span data-stu-id="17394-126">Navigate to the new *golden* folder and execute the following command to create a library project, which produces two files,*library.csproj* and *Class1.cs*, in the *library* folder:</span></span>

```dotnetcli
dotnet new classlib -o library
```

<span data-ttu-id="17394-127">Execute o comando [`dotnet sln`](../tools/dotnet-sln.md) para adicionar o projeto *library.csproj* recém-criado à solução:</span><span class="sxs-lookup"><span data-stu-id="17394-127">Execute the [`dotnet sln`](../tools/dotnet-sln.md) command to add the newly created *library.csproj* project to the solution:</span></span>

```dotnetcli
dotnet sln add library/library.csproj
```

<span data-ttu-id="17394-128">O arquivo *library.csproj* contém as seguintes informações:</span><span class="sxs-lookup"><span data-stu-id="17394-128">The *library.csproj* file contains the following information:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="17394-129">Nossos métodos da biblioteca serializam e desserializam os objetos no formato JSON.</span><span class="sxs-lookup"><span data-stu-id="17394-129">Our library methods serialize and deserialize objects in JSON format.</span></span> <span data-ttu-id="17394-130">Para dar suporte à serialização e desserialização JSON, adicione uma referência ao pacote NuGet `Newtonsoft.Json`.</span><span class="sxs-lookup"><span data-stu-id="17394-130">To support JSON serialization and deserialization, add a reference to the `Newtonsoft.Json` NuGet package.</span></span> <span data-ttu-id="17394-131">O comando `dotnet add` adiciona novos itens a um projeto.</span><span class="sxs-lookup"><span data-stu-id="17394-131">The `dotnet add` command adds new items to a project.</span></span> <span data-ttu-id="17394-132">Para adicionar uma referência a um pacote NuGet, use o comando [`dotnet add package`](../tools/dotnet-add-package.md) e especifique o nome do pacote:</span><span class="sxs-lookup"><span data-stu-id="17394-132">To add a reference to a NuGet package, use the [`dotnet add package`](../tools/dotnet-add-package.md) command and specify the name of the package:</span></span>

```dotnetcli
dotnet add library package Newtonsoft.Json
```

<span data-ttu-id="17394-133">Isso adiciona `Newtonsoft.Json` e suas dependências ao projeto de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="17394-133">This adds `Newtonsoft.Json` and its dependencies to the library project.</span></span> <span data-ttu-id="17394-134">Como alternativa, edite manualmente o arquivo *library.csproj* e adicione o seguinte nó:</span><span class="sxs-lookup"><span data-stu-id="17394-134">Alternatively, manually edit the *library.csproj* file and add the following node:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="12.0.2" />
</ItemGroup>
```

<span data-ttu-id="17394-135">Execute [`dotnet restore`](../tools/dotnet-restore.md), ([veja observação](#dotnet-restore-note)), que restaura as dependências e cria uma pasta *obj* dentro de *library* com três arquivos, incluindo um arquivo *project.assets.json*:</span><span class="sxs-lookup"><span data-stu-id="17394-135">Execute [`dotnet restore`](../tools/dotnet-restore.md), ([see note](#dotnet-restore-note)) which restores dependencies and creates an *obj* folder inside *library* with three files in it, including a *project.assets.json* file:</span></span>

```dotnetcli
dotnet restore
```

<span data-ttu-id="17394-136">Na pasta *library*, renomeie o arquivo *Class1.cs* como *Thing.cs*.</span><span class="sxs-lookup"><span data-stu-id="17394-136">In the *library* folder, rename the file *Class1.cs* to *Thing.cs*.</span></span> <span data-ttu-id="17394-137">Substitua o código pelo seguinte:</span><span class="sxs-lookup"><span data-stu-id="17394-137">Replace the code with the following:</span></span>

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

<span data-ttu-id="17394-138">A classe `Thing` contém um método público, `Get`, que retorna a soma de dois números, mas faz isso ao converter a soma em uma cadeia de caracteres e, em seguida, desserializá-los em um inteiro.</span><span class="sxs-lookup"><span data-stu-id="17394-138">The `Thing` class contains one public method, `Get`, which returns the sum of two numbers but does so by converting the sum into a string and then deserializing it into an integer.</span></span> <span data-ttu-id="17394-139">Isso usa diversos recursos modernos do C#, tais como [diretivas `using static`](../../csharp/language-reference/keywords/using-static.md), [membros aptos para expressão](../../csharp/whats-new/csharp-7.md#more-expression-bodied-members) e [interpolação de cadeia de caracteres](../../csharp/language-reference/tokens/interpolated.md).</span><span class="sxs-lookup"><span data-stu-id="17394-139">This makes use of a number of modern C# features, such as [`using static` directives](../../csharp/language-reference/keywords/using-static.md), [expression-bodied members](../../csharp/whats-new/csharp-7.md#more-expression-bodied-members), and [string interpolation](../../csharp/language-reference/tokens/interpolated.md).</span></span>

<span data-ttu-id="17394-140">Crie a biblioteca com o comando [`dotnet build`](../tools/dotnet-build.md).</span><span class="sxs-lookup"><span data-stu-id="17394-140">Build the library with the [`dotnet build`](../tools/dotnet-build.md) command.</span></span> <span data-ttu-id="17394-141">Isso produz um arquivo *library.dll* em *golden/library/bin/Debug/netstandard1.4*:</span><span class="sxs-lookup"><span data-stu-id="17394-141">This produces a *library.dll* file under *golden/library/bin/Debug/netstandard1.4*:</span></span>

```dotnetcli
dotnet build
```

## <a name="create-the-test-project"></a><span data-ttu-id="17394-142">Criar um projeto de teste</span><span class="sxs-lookup"><span data-stu-id="17394-142">Create the test project</span></span>

<span data-ttu-id="17394-143">Crie um projeto de teste para a biblioteca.</span><span class="sxs-lookup"><span data-stu-id="17394-143">Build a test project for the library.</span></span> <span data-ttu-id="17394-144">Na pasta *golden*, crie um novo projeto de teste:</span><span class="sxs-lookup"><span data-stu-id="17394-144">From the *golden* folder, create a new test project:</span></span>

```dotnetcli
dotnet new xunit -o test-library
```

<span data-ttu-id="17394-145">Adicione o projeto de teste à solução:</span><span class="sxs-lookup"><span data-stu-id="17394-145">Add the test project to the solution:</span></span>

```dotnetcli
dotnet sln add test-library/test-library.csproj
```

<span data-ttu-id="17394-146">Adicione uma referência do projeto à biblioteca que você criou na seção anterior para que o compilador possa localizar e usar o projeto de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="17394-146">Add a project reference the library you created in the previous section so that the compiler can find and use the library project.</span></span> <span data-ttu-id="17394-147">Use o comando [`dotnet add reference`](../tools/dotnet-add-reference.md):</span><span class="sxs-lookup"><span data-stu-id="17394-147">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```dotnetcli
dotnet add test-library/test-library.csproj reference library/library.csproj
```

<span data-ttu-id="17394-148">Como alternativa, edite manualmente o arquivo *test-library.csproj* e adicione o seguinte nó:</span><span class="sxs-lookup"><span data-stu-id="17394-148">Alternatively, manually edit the *test-library.csproj* file and add the following node:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\library\library.csproj" />
</ItemGroup>
```

<span data-ttu-id="17394-149">Agora que as dependências foram devidamente configuradas, crie os testes para sua biblioteca.</span><span class="sxs-lookup"><span data-stu-id="17394-149">Now that the dependencies have been properly configured, create the tests for your library.</span></span> <span data-ttu-id="17394-150">Abra *UnitTest1.cs* e substitua o conteúdo pelo seguinte código:</span><span class="sxs-lookup"><span data-stu-id="17394-150">Open *UnitTest1.cs* and replace its contents with the following code:</span></span>

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

<span data-ttu-id="17394-151">Observe que você declara que o valor 42 não é igual a 19+23 (ou 42) quando você cria o teste de unidade pela primeira vez (`Assert.NotEqual`), que falhará.</span><span class="sxs-lookup"><span data-stu-id="17394-151">Note that you assert the value 42 is not equal to 19+23 (or 42) when you first create the unit test (`Assert.NotEqual`), which will fail.</span></span> <span data-ttu-id="17394-152">Uma etapa importante na criação de testes de unidade é criar o teste para falhar uma vez primeiro para confirmar sua lógica.</span><span class="sxs-lookup"><span data-stu-id="17394-152">An important step in building unit tests is to create the test to fail once first to confirm its logic.</span></span>

<span data-ttu-id="17394-153">Na pasta *golden*, execute os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="17394-153">From the *golden* folder, execute the following commands:</span></span>

```dotnetcli
dotnet restore 
dotnet test test-library/test-library.csproj
```

<span data-ttu-id="17394-154">Esses comandos localizarão recursivamente todos os projetos para restaurar dependências, para compilá-las e para ativar o executor de teste xUnit para executar os testes.</span><span class="sxs-lookup"><span data-stu-id="17394-154">These commands will recursively find all projects to restore dependencies, build them, and activate the xUnit test runner to run the tests.</span></span> <span data-ttu-id="17394-155">O teste único falha, conforme esperado.</span><span class="sxs-lookup"><span data-stu-id="17394-155">The single test fails, as you expect.</span></span>

<span data-ttu-id="17394-156">Edite o arquivo *UnitTest1.cs* e altere a asserção de `Assert.NotEqual` para `Assert.Equal`.</span><span class="sxs-lookup"><span data-stu-id="17394-156">Edit the *UnitTest1.cs* file and change the assertion from `Assert.NotEqual` to `Assert.Equal`.</span></span> <span data-ttu-id="17394-157">Execute o seguinte comando da pasta *golden* para executar o teste novamente, que é aprovado dessa vez:</span><span class="sxs-lookup"><span data-stu-id="17394-157">Execute the following command from the *golden* folder to re-run the test, which passes this time:</span></span>

```dotnetcli
dotnet test test-library/test-library.csproj
```

## <a name="create-the-console-app"></a><span data-ttu-id="17394-158">Criar o aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="17394-158">Create the console app</span></span>

<span data-ttu-id="17394-159">O aplicativo de console criado ao longo das etapas a seguir usa uma dependência no projeto de biblioteca criado anteriormente e chama seu método de biblioteca quando é executado.</span><span class="sxs-lookup"><span data-stu-id="17394-159">The console app you create over the following steps takes a dependency on the library project you created earlier and calls its library method when it runs.</span></span> <span data-ttu-id="17394-160">Usando esse padrão de desenvolvimento, você verá como criar bibliotecas reutilizáveis para vários projetos.</span><span class="sxs-lookup"><span data-stu-id="17394-160">Using this pattern of development, you see how to create reusable libraries for multiple projects.</span></span>

<span data-ttu-id="17394-161">Crie um novo aplicativo de console da pasta *golden*:</span><span class="sxs-lookup"><span data-stu-id="17394-161">Create a new console application from the *golden* folder:</span></span>

```dotnetcli
dotnet new console -o app
```

<span data-ttu-id="17394-162">Adicione o projeto de aplicativo de console à solução:</span><span class="sxs-lookup"><span data-stu-id="17394-162">Add the console app project to the solution:</span></span>

```dotnetcli
dotnet sln add app/app.csproj
```

<span data-ttu-id="17394-163">Crie a dependência na biblioteca executando o comando `dotnet add reference`:</span><span class="sxs-lookup"><span data-stu-id="17394-163">Create the dependency on the library by running the `dotnet add reference` command:</span></span>

```dotnetcli
dotnet add app/app.csproj reference library/library.csproj
```

<span data-ttu-id="17394-164">Execute `dotnet restore` ([veja observação](#dotnet-restore-note)) para restaurar as dependências dos três projetos na solução.</span><span class="sxs-lookup"><span data-stu-id="17394-164">Run `dotnet restore` ([see note](#dotnet-restore-note)) to restore the dependencies of the three projects in the solution.</span></span> <span data-ttu-id="17394-165">Abra *Program.cs* e substitua o conteúdo do método `Main` pela seguinte linha:</span><span class="sxs-lookup"><span data-stu-id="17394-165">Open *Program.cs* and replace the contents of the `Main` method with the following line:</span></span>

```csharp
WriteLine($"The answer is {new Thing().Get(19, 23)}");
```

<span data-ttu-id="17394-166">Adicione duas diretivas `using` à parte superior do arquivo *Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="17394-166">Add two `using` directives to the top of the *Program.cs* file:</span></span>

```csharp
using static System.Console;
using Library;
```

<span data-ttu-id="17394-167">Execute o seguinte comando `dotnet run` para executar o executável, em que a opção `-p` para `dotnet run` especifica o projeto para o aplicativo principal.</span><span class="sxs-lookup"><span data-stu-id="17394-167">Execute the following `dotnet run` command to run the executable, where the `-p` option to `dotnet run` specifies the project for the main application.</span></span> <span data-ttu-id="17394-168">O aplicativo produz a cadeia de caracteres "A resposta é 42".</span><span class="sxs-lookup"><span data-stu-id="17394-168">The app produces the string "The answer is 42".</span></span>

```dotnetcli
dotnet run -p app/app.csproj
```

## <a name="debug-the-application"></a><span data-ttu-id="17394-169">Depurar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="17394-169">Debug the application</span></span>

<span data-ttu-id="17394-170">Defina um ponto de interrupção na instrução `WriteLine` no método `Main`.</span><span class="sxs-lookup"><span data-stu-id="17394-170">Set a breakpoint at the `WriteLine` statement in the `Main` method.</span></span> <span data-ttu-id="17394-171">Faça isso pressionando a tecla <kbd>F9</kbd> quando o cursor estiver sobre a linha `WriteLine` ou clicando com o mouse na margem esquerda na linha em que deseja definir o ponto de interrupção.</span><span class="sxs-lookup"><span data-stu-id="17394-171">Do this by either pressing the <kbd>F9</kbd> key when the cursor is over the `WriteLine` line or by clicking the mouse in the left margin on the line where you want to set the breakpoint.</span></span> <span data-ttu-id="17394-172">Um círculo vermelho será exibido na margem ao lado da linha de código.</span><span class="sxs-lookup"><span data-stu-id="17394-172">A red circle will appear in the margin next to the line of code.</span></span> <span data-ttu-id="17394-173">Quando o ponto de interrupção for atingido, a execução do código será interrompida *antes* de a linha do ponto de interrupção ser executada.</span><span class="sxs-lookup"><span data-stu-id="17394-173">When the breakpoint is reached, code execution will stop *before* the breakpoint line is executed.</span></span>

<span data-ttu-id="17394-174">Abra a guia do depurador selecionando o ícone Depurar na barra de ferramentas do Visual Studio Code, selecionando **Exibir > Depurar** na barra de menus ou usando o atalho de teclado <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>:</span><span class="sxs-lookup"><span data-stu-id="17394-174">Open the debugger tab by selecting the Debug icon in the Visual Studio Code toolbar, selecting **View > Debug** from the menu bar, or using the keyboard shortcut <kbd>CTRL</kbd>+<kbd>SHIFT</kbd>+<kbd>D</kbd>:</span></span>

![Depurador do Visual Studio Code](./media/using-on-macos/visual-studio-code-debugger.png)

<span data-ttu-id="17394-176">Pressione o botão Reproduzir para iniciar o aplicativo no depurador.</span><span class="sxs-lookup"><span data-stu-id="17394-176">Press the Play button to start the application under the debugger.</span></span> <span data-ttu-id="17394-177">O aplicativo inicia a execução e é executado até o ponto de interrupção, quando ele para.</span><span class="sxs-lookup"><span data-stu-id="17394-177">The app begins execution and runs to the breakpoint, where it stops.</span></span> <span data-ttu-id="17394-178">Inspecione o método `Get` e verifique se você transmitiu os argumentos corretos.</span><span class="sxs-lookup"><span data-stu-id="17394-178">Step into the `Get` method and make sure that you have passed in the correct arguments.</span></span> <span data-ttu-id="17394-179">Confirme se a resposta é 42.</span><span class="sxs-lookup"><span data-stu-id="17394-179">Confirm that the answer is 42.</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
