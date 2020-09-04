---
title: Criar uma biblioteca de classes de .NET Standard usando Visual Studio Code
description: Saiba como criar uma biblioteca de classes de .NET Standard usando Visual Studio Code.
ms.date: 06/08/2020
ms.openlocfilehash: d37e3c663146c90f4ae4188b25ea7e501501c93b
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2020
ms.locfileid: "89465280"
---
# <a name="tutorial-create-a-net-standard-library-using-visual-studio-code"></a><span data-ttu-id="0a530-103">Tutorial: criar uma biblioteca de .NET Standard usando Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="0a530-103">Tutorial: Create a .NET Standard library using Visual Studio Code</span></span>

<span data-ttu-id="0a530-104">Neste tutorial, você cria uma biblioteca de utilitário simples que contém um único método de manipulação de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="0a530-104">In this tutorial, you create a simple utility library that contains a single string-handling method.</span></span> <span data-ttu-id="0a530-105">Implemente-o como um [método de extensão](../../csharp/programming-guide/classes-and-structs/extension-methods.md) para que você possa chamá-lo como se fosse um membro da <xref:System.String> classe.</span><span class="sxs-lookup"><span data-stu-id="0a530-105">You implement it as an [extension method](../../csharp/programming-guide/classes-and-structs/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

<span data-ttu-id="0a530-106">Uma *biblioteca de classes* define tipos e métodos que são chamados por um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0a530-106">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="0a530-107">Uma biblioteca de classes que tem como alvo .NET Standard 2,0 permite que sua biblioteca seja chamada por qualquer implementação do .NET que dê suporte a essa versão do .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="0a530-107">A class library that targets .NET Standard 2.0 allows your library to be called by any .NET implementation that supports that version of .NET Standard.</span></span> <span data-ttu-id="0a530-108">Ao concluir a biblioteca de classes, você pode distribuí-la como um componente de terceiros ou como um componente agrupado com um ou mais aplicativos.</span><span class="sxs-lookup"><span data-stu-id="0a530-108">When you finish your class library, you can distribute it as a third-party component or as a bundled component with one or more applications.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0a530-109">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="0a530-109">Prerequisites</span></span>

1. <span data-ttu-id="0a530-110">[Visual Studio Code](https://code.visualstudio.com/) com a [extensão C#](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) instalada.</span><span class="sxs-lookup"><span data-stu-id="0a530-110">[Visual Studio Code](https://code.visualstudio.com/) with the [C# extension](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) installed.</span></span> <span data-ttu-id="0a530-111">Para obter informações sobre como instalar extensões em Visual Studio Code, consulte [vs Code Marketplace de extensão](https://code.visualstudio.com/docs/editor/extension-gallery).</span><span class="sxs-lookup"><span data-stu-id="0a530-111">For information about how to install extensions on Visual Studio Code, see [VS Code Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span></span>
2. <span data-ttu-id="0a530-112">O [SDK do .NET Core 3,1 ou posterior](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="0a530-112">The [.NET Core 3.1 SDK or later](https://dotnet.microsoft.com/download)</span></span>

## <a name="create-a-solution"></a><span data-ttu-id="0a530-113">Criar uma solução</span><span class="sxs-lookup"><span data-stu-id="0a530-113">Create a solution</span></span>

<span data-ttu-id="0a530-114">Comece criando uma solução em branco para colocar o projeto de biblioteca de classes no.</span><span class="sxs-lookup"><span data-stu-id="0a530-114">Start by creating a blank solution to put the class library project in.</span></span> <span data-ttu-id="0a530-115">Uma solução serve como um contêiner para um ou mais projetos.</span><span class="sxs-lookup"><span data-stu-id="0a530-115">A solution serves as a container for one or more projects.</span></span> <span data-ttu-id="0a530-116">Você adicionará mais projetos relacionados à mesma solução.</span><span class="sxs-lookup"><span data-stu-id="0a530-116">You'll add additional, related projects to the same solution.</span></span>

1. <span data-ttu-id="0a530-117">Iniciar o Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="0a530-117">Start Visual Studio Code.</span></span>

1. <span data-ttu-id="0a530-118">Selecione **arquivo**  >  **abrir pasta** (**abrir...** no MacOS) no menu principal</span><span class="sxs-lookup"><span data-stu-id="0a530-118">Select **File** > **Open Folder** (**Open...** on macOS) from the main menu</span></span>

1. <span data-ttu-id="0a530-119">Na caixa de diálogo **abrir pasta** , crie uma pasta *ClassLibraryProjects* e clique em **Selecionar pasta** (**aberta** no MacOS).</span><span class="sxs-lookup"><span data-stu-id="0a530-119">In the **Open Folder** dialog, create a *ClassLibraryProjects* folder and click **Select Folder** (**Open** on macOS).</span></span>

1. <span data-ttu-id="0a530-120">Abra o **terminal** no Visual Studio Code selecionando **Exibir**  >  **terminal** no menu principal.</span><span class="sxs-lookup"><span data-stu-id="0a530-120">Open the **Terminal** in Visual Studio Code by selecting **View** > **Terminal** from the main menu.</span></span>

   <span data-ttu-id="0a530-121">O **terminal** é aberto com o prompt de comando na pasta *ClassLibraryProjects* .</span><span class="sxs-lookup"><span data-stu-id="0a530-121">The **Terminal** opens with the command prompt in the *ClassLibraryProjects* folder.</span></span>

1. <span data-ttu-id="0a530-122">No **terminal**, digite o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="0a530-122">In the **Terminal**, enter the following command:</span></span>

   ```dotnetcli
   dotnet new sln
   ```

   <span data-ttu-id="0a530-123">A saída do terminal é semelhante ao exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="0a530-123">The terminal output looks like the following example:</span></span>

   ```output
   The template "Solution File" was created successfully.
   ```

## <a name="create-a-class-library-project"></a><span data-ttu-id="0a530-124">Criar um projeto de biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="0a530-124">Create a class library project</span></span>

<span data-ttu-id="0a530-125">Adicione um novo projeto de biblioteca de classe .NET Standard chamado "StringLibrary" à solução.</span><span class="sxs-lookup"><span data-stu-id="0a530-125">Add a new .NET Standard class library project named "StringLibrary" to the solution.</span></span>

1. <span data-ttu-id="0a530-126">No terminal, execute o seguinte comando para criar o projeto de biblioteca:</span><span class="sxs-lookup"><span data-stu-id="0a530-126">In the terminal, run the following command to create the library project:</span></span>

   ```dotnetcli
   dotnet new classlib -o StringLibrary
   ```

   <span data-ttu-id="0a530-127">O `-o` `--output` comando ou especifica o local para posicionar a saída gerada.</span><span class="sxs-lookup"><span data-stu-id="0a530-127">The `-o` or `--output` command specifies the location to place the generated output.</span></span>

   <span data-ttu-id="0a530-128">A saída do terminal é semelhante ao exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="0a530-128">The terminal output looks like the following example:</span></span>

   ```output
   The template "Class library" was created successfully.
   Processing post-creation actions...
   Running 'dotnet restore' on StringLibrary\StringLibrary.csproj...
     Determining projects to restore...
     Restore completed in 328.13 ms for C:\Projects\ClassLibraryProjects\StringLibrary\StringLibrary.csproj.
   Restore succeeded.
   ```

1. <span data-ttu-id="0a530-129">Execute o seguinte comando para adicionar o projeto de biblioteca à solução:</span><span class="sxs-lookup"><span data-stu-id="0a530-129">Run the following command to add the library project to the solution:</span></span>

   ```dotnetcli
   dotnet sln add StringLibrary/StringLibrary.csproj
   ```

   <span data-ttu-id="0a530-130">A saída do terminal é semelhante ao exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="0a530-130">The terminal output looks like the following example:</span></span>

   ```output
   Project `StringLibrary\StringLibrary.csproj` added to the solution.
   ```

1. <span data-ttu-id="0a530-131">Verifique se a biblioteca tem como destino a versão correta do .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="0a530-131">Check to make sure that the library targets the correct version of .NET Standard.</span></span> <span data-ttu-id="0a530-132">No **Explorer**, abra *StringLibrary/StringLibrary. csproj*.</span><span class="sxs-lookup"><span data-stu-id="0a530-132">In **Explorer**, open *StringLibrary/StringLibrary.csproj*.</span></span>

   <span data-ttu-id="0a530-133">O `TargetFramework` elemento mostra que o projeto tem como destino .NET Standard 2,0.</span><span class="sxs-lookup"><span data-stu-id="0a530-133">The `TargetFramework` element shows that the project targets .NET Standard 2.0.</span></span>

   ```xml
   <Project Sdk="Microsoft.NET.Sdk">

     <PropertyGroup>
       <TargetFramework>netstandard2.0</TargetFramework>
     </PropertyGroup>

   </Project>
   ```

1. <span data-ttu-id="0a530-134">Abra *Class1.cs* e substitua o código pelo código a seguir.</span><span class="sxs-lookup"><span data-stu-id="0a530-134">Open *Class1.cs* and replace the code with the following code.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibrary/Class1.cs":::

   <span data-ttu-id="0a530-135">A biblioteca de classes, `UtilityLibraries.StringLibrary` , contém um método chamado `StartsWithUpper` .</span><span class="sxs-lookup"><span data-stu-id="0a530-135">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`.</span></span> <span data-ttu-id="0a530-136">Esse método retorna um <xref:System.Boolean> valor que indica se a instância atual da cadeia de caracteres começa com um caractere maiúsculo.</span><span class="sxs-lookup"><span data-stu-id="0a530-136">This method returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="0a530-137">O padrão Unicode distingue caracteres maiúsculos de caracteres minúsculos.</span><span class="sxs-lookup"><span data-stu-id="0a530-137">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="0a530-138">O método <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> retornará `true` se um caractere for maiúsculo.</span><span class="sxs-lookup"><span data-stu-id="0a530-138">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

1. <span data-ttu-id="0a530-139">Salve o arquivo.</span><span class="sxs-lookup"><span data-stu-id="0a530-139">Save the file.</span></span>

1. <span data-ttu-id="0a530-140">Execute o comando a seguir para compilar a solução e verificar se o projeto é compilado sem erros.</span><span class="sxs-lookup"><span data-stu-id="0a530-140">Run the following command to build the solution and verify that the project compiles without error.</span></span>

   ```dotnetcli
   dotnet build
   ```

   <span data-ttu-id="0a530-141">A saída do terminal é semelhante ao exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="0a530-141">The terminal output looks like the following example:</span></span>

   ```output
   Microsoft (R) Build Engine version 16.6.0 for .NET Core
   Copyright (C) Microsoft Corporation. All rights reserved.
     Determining projects to restore...
     All projects are up-to-date for restore.
     You are using a preview version of .NET Core. See: https://aka.ms/dotnet-core-preview
     StringLibrary -> C:\Projects\ClassLibraryProjects\StringLibrary\bin\Debug\netstandard2.0\StringLibrary.dll
   Build succeeded.
       0 Warning(s)
       0 Error(s)
   Time Elapsed 00:00:02.78
   ```

## <a name="add-a-console-app-to-the-solution"></a><span data-ttu-id="0a530-142">Adicionar um aplicativo de console à solução</span><span class="sxs-lookup"><span data-stu-id="0a530-142">Add a console app to the solution</span></span>

<span data-ttu-id="0a530-143">Adicione um aplicativo de console que usa a biblioteca de classes.</span><span class="sxs-lookup"><span data-stu-id="0a530-143">Add a console application that uses the class library.</span></span> <span data-ttu-id="0a530-144">O aplicativo solicitará que o usuário insira uma cadeia de caracteres e relate se a cadeia de caracteres começa com um caractere maiúsculo.</span><span class="sxs-lookup"><span data-stu-id="0a530-144">The app will prompt the user to enter a string and report whether the string begins with an uppercase character.</span></span>

1. <span data-ttu-id="0a530-145">No terminal, execute o seguinte comando para criar o projeto de aplicativo de console:</span><span class="sxs-lookup"><span data-stu-id="0a530-145">In the terminal, run the following command to create the console app project:</span></span>

   ```dotnetcli
   dotnet new console -o ShowCase
   ```

   <span data-ttu-id="0a530-146">A saída do terminal é semelhante ao exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="0a530-146">The terminal output looks like the following example:</span></span>

   ```output
   The template "Console Application" was created successfully.
   Processing post-creation actions...
   Running 'dotnet restore' on ShowCase\ShowCase.csproj...  
     Determining projects to restore...
     Restore completed in 210.78 ms for C:\Projects\ClassLibraryProjects\ShowCase\ShowCase.csproj.
   Restore succeeded.
   ```

1. <span data-ttu-id="0a530-147">Execute o seguinte comando para adicionar o projeto de aplicativo de console à solução:</span><span class="sxs-lookup"><span data-stu-id="0a530-147">Run the following command to add the console app project to the solution:</span></span>

   ```dotnetcli
   dotnet sln add ShowCase/ShowCase.csproj
   ```

   <span data-ttu-id="0a530-148">A saída do terminal é semelhante ao exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="0a530-148">The terminal output looks like the following example:</span></span>

   ```output
   Project `ShowCase\ShowCase.csproj` added to the solution.
   ```

1. <span data-ttu-id="0a530-149">Abra o *Showcase/Program. cs* e substitua todo o código pelo código a seguir.</span><span class="sxs-lookup"><span data-stu-id="0a530-149">Open *ShowCase/Program.cs* and replace all of the code with the following code.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/ShowCase/Program.cs":::

   <span data-ttu-id="0a530-150">O código usa a variável `row` ​​para manter uma contagem do número de linhas de dados gravadas na janela do console.</span><span class="sxs-lookup"><span data-stu-id="0a530-150">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="0a530-151">Sempre que for maior ou igual a 25, o código limpará a janela do console e exibirá uma mensagem para o usuário.</span><span class="sxs-lookup"><span data-stu-id="0a530-151">Whenever it's greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="0a530-152">O programa solicita que o usuário insira uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="0a530-152">The program prompts the user to enter a string.</span></span> <span data-ttu-id="0a530-153">Ele indica se a cadeia de caracteres começa com um caractere maiúsculo.</span><span class="sxs-lookup"><span data-stu-id="0a530-153">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="0a530-154">Se o usuário pressionar a tecla <kbd>Enter</kbd> sem inserir uma cadeia de caracteres, o aplicativo será encerrado e a janela do console será fechada.</span><span class="sxs-lookup"><span data-stu-id="0a530-154">If the user presses the <kbd>Enter</kbd> key without entering a string, the application ends, and the console window closes.</span></span>

1. <span data-ttu-id="0a530-155">Salve suas alterações.</span><span class="sxs-lookup"><span data-stu-id="0a530-155">Save your changes.</span></span>

## <a name="add-a-project-reference"></a><span data-ttu-id="0a530-156">Adicionar uma referência ao projeto</span><span class="sxs-lookup"><span data-stu-id="0a530-156">Add a project reference</span></span>

<span data-ttu-id="0a530-157">Inicialmente, o novo projeto de aplicativo de console não tem acesso à biblioteca de classes.</span><span class="sxs-lookup"><span data-stu-id="0a530-157">Initially, the new console app project doesn't have access to the class library.</span></span> <span data-ttu-id="0a530-158">Para permitir que ele chame métodos na biblioteca de classes, crie uma referência de projeto para o projeto de biblioteca de classes.</span><span class="sxs-lookup"><span data-stu-id="0a530-158">To allow it to call methods in the class library, create a project reference to the class library project.</span></span>

1. <span data-ttu-id="0a530-159">Execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="0a530-159">Run the following command:</span></span>

   ```dotnetcli
   dotnet add ShowCase/ShowCase.csproj reference StringLibrary/StringLibrary.csproj
   ```

   <span data-ttu-id="0a530-160">A saída do terminal é semelhante ao exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="0a530-160">The terminal output looks like the following example:</span></span>

   ```output
   Reference `..\StringLibrary\StringLibrary.csproj` added to the project.
   ```

## <a name="run-the-app"></a><span data-ttu-id="0a530-161">Executar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="0a530-161">Run the app</span></span>

1. <span data-ttu-id="0a530-162">Execute o seguinte comando no terminal:</span><span class="sxs-lookup"><span data-stu-id="0a530-162">Run the following command in the terminal:</span></span>

   ```dotnetcli
   dotnet run --project ShowCase/ShowCase.csproj
   ```

1. <span data-ttu-id="0a530-163">Experimente o programa digitando cadeias de caracteres e pressionando <kbd>Enter</kbd>e pressione <kbd>Enter</kbd> para sair.</span><span class="sxs-lookup"><span data-stu-id="0a530-163">Try out the program by entering strings and pressing <kbd>Enter</kbd>, then press <kbd>Enter</kbd> to exit.</span></span>

   <span data-ttu-id="0a530-164">A saída do terminal é semelhante ao exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="0a530-164">The terminal output looks like the following example:</span></span>

   ```output
   Press <Enter> only to exit; otherwise, enter a string and press <Enter>:

   A string that starts with an uppercase letter
   Input: A string that starts with an uppercase letter
   Begins with uppercase? : Yes

   a string that starts with a lowercase letter
   Input: a string that starts with a lowercase letter
   Begins with uppercase? : No
   ```

## <a name="additional-resources"></a><span data-ttu-id="0a530-165">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="0a530-165">Additional resources</span></span>

* [<span data-ttu-id="0a530-166">Desenvolver bibliotecas com o CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="0a530-166">Develop libraries with the .NET Core CLI</span></span>](libraries.md)
* <span data-ttu-id="0a530-167">[.Net Standard versões e plataformas às quais eles dão suporte](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="0a530-167">[.NET Standard versions and the platforms they support](../../standard/net-standard.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="0a530-168">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="0a530-168">Next steps</span></span>

<span data-ttu-id="0a530-169">Neste tutorial, você criou uma solução, adicionou um projeto de biblioteca e adicionou um projeto de aplicativo de console que usa a biblioteca do.</span><span class="sxs-lookup"><span data-stu-id="0a530-169">In this tutorial, you created a solution, added a library project, and added a console app project that uses the library.</span></span> <span data-ttu-id="0a530-170">No próximo tutorial, você adicionará um projeto de teste de unidade à solução.</span><span class="sxs-lookup"><span data-stu-id="0a530-170">In the next tutorial, you add a unit test project to the solution.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0a530-171">Testar uma biblioteca de .NET Standard com o .NET Core usando Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="0a530-171">Test a .NET Standard library with .NET Core using Visual Studio Code</span></span>](testing-library-with-visual-studio-code.md)
