---
title: Criar uma biblioteca de classes de .NET Standard no Visual Studio Code
description: Saiba como criar uma biblioteca de classes de .NET Standard usando Visual Studio Code.
ms.date: 05/29/2020
ms.openlocfilehash: 5720ac374d50ef27a07d463e57af1bd95a352d83
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/05/2020
ms.locfileid: "84446946"
---
# <a name="tutorial-create-a-net-standard-library-in-visual-studio-code"></a><span data-ttu-id="b6efb-103">Tutorial: criar uma biblioteca de .NET Standard no Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="b6efb-103">Tutorial: Create a .NET Standard library in Visual Studio Code</span></span>

<span data-ttu-id="b6efb-104">Uma *biblioteca de classes* define tipos e métodos que são chamados por um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b6efb-104">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="b6efb-105">Uma biblioteca de classes que tem como alvo .NET Standard 2,0 permite que sua biblioteca seja chamada por qualquer implementação do .NET que dê suporte a essa versão do .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="b6efb-105">A class library that targets .NET Standard 2.0 allows your library to be called by any .NET implementation that supports that version of .NET Standard.</span></span> <span data-ttu-id="b6efb-106">Ao concluir a biblioteca de classes, você pode decidir se deseja distribuí-la como um pacote NuGet ou incluí-la como um componente agrupado com um ou mais aplicativos.</span><span class="sxs-lookup"><span data-stu-id="b6efb-106">When you finish your class library, you can decide whether you want to distribute it as a NuGet package or include it as a bundled component with one or more applications.</span></span>

> [!NOTE]
> <span data-ttu-id="b6efb-107">Para obter uma lista de versões de .NET Standard e as plataformas às quais eles dão suporte, consulte [.net Standard](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="b6efb-107">For a list of .NET Standard versions and the platforms they support, see [.NET Standard](../../standard/net-standard.md).</span></span>

<span data-ttu-id="b6efb-108">Neste tutorial, você cria uma biblioteca de utilitário simples que contém um único método de manipulação de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="b6efb-108">In this tutorial, you create a simple utility library that contains a single string-handling method.</span></span> <span data-ttu-id="b6efb-109">Implemente-o como um [método de extensão](../../csharp/programming-guide/classes-and-structs/extension-methods.md) para que você possa chamá-lo como se fosse um membro da <xref:System.String> classe.</span><span class="sxs-lookup"><span data-stu-id="b6efb-109">You implement it as an [extension method](../../csharp/programming-guide/classes-and-structs/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b6efb-110">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="b6efb-110">Prerequisites</span></span>

1. <span data-ttu-id="b6efb-111">[Visual Studio Code](https://code.visualstudio.com/) com a [extensão C#](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) instalada.</span><span class="sxs-lookup"><span data-stu-id="b6efb-111">[Visual Studio Code](https://code.visualstudio.com/) with the [C# extension](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) installed.</span></span> <span data-ttu-id="b6efb-112">Para obter informações sobre como instalar extensões em Visual Studio Code, consulte [vs Code Marketplace de extensão](https://code.visualstudio.com/docs/editor/extension-gallery).</span><span class="sxs-lookup"><span data-stu-id="b6efb-112">For information about how to install extensions on Visual Studio Code, see [VS Code Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span></span>
2. <span data-ttu-id="b6efb-113">O [SDK do .NET Core 3,1 ou posterior](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="b6efb-113">The [.NET Core 3.1 SDK or later](https://dotnet.microsoft.com/download)</span></span>

## <a name="create-a-solution"></a><span data-ttu-id="b6efb-114">Criar uma solução</span><span class="sxs-lookup"><span data-stu-id="b6efb-114">Create a solution</span></span>

<span data-ttu-id="b6efb-115">Comece criando uma solução em branco para colocar o projeto de biblioteca de classes no.</span><span class="sxs-lookup"><span data-stu-id="b6efb-115">Start by creating a blank solution to put the class library project in.</span></span> <span data-ttu-id="b6efb-116">Uma solução serve como um contêiner para um ou mais projetos.</span><span class="sxs-lookup"><span data-stu-id="b6efb-116">A solution serves as a container for one or more projects.</span></span> <span data-ttu-id="b6efb-117">Você adicionará mais projetos relacionados à mesma solução.</span><span class="sxs-lookup"><span data-stu-id="b6efb-117">You'll add additional, related projects to the same solution.</span></span>

1. <span data-ttu-id="b6efb-118">Abra o Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="b6efb-118">Open Visual Studio Code.</span></span>

1. <span data-ttu-id="b6efb-119">Selecione **arquivo**  >  **abrir pasta** / **abrir...** no menu principal, crie uma pasta *ClassLibraryProjects* e clique em **Selecionar pasta** / **abrir**.</span><span class="sxs-lookup"><span data-stu-id="b6efb-119">Select **File** > **Open Folder**/**Open...** from the main menu, create a *ClassLibraryProjects* folder, and click **Select Folder**/**Open**.</span></span>

1. <span data-ttu-id="b6efb-120">Abra o **terminal** no Visual Studio Code selecionando **Exibir**  >  **terminal** no menu principal.</span><span class="sxs-lookup"><span data-stu-id="b6efb-120">Open the **Terminal** in Visual Studio Code by selecting **View** > **Terminal** from the main menu.</span></span>

   <span data-ttu-id="b6efb-121">O **terminal** é aberto com o prompt de comando na pasta *ClassLibraryProjects* .</span><span class="sxs-lookup"><span data-stu-id="b6efb-121">The **Terminal** opens with the command prompt in the *ClassLibraryProjects* folder.</span></span>

1. <span data-ttu-id="b6efb-122">No **terminal**, digite o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="b6efb-122">In the **Terminal**, enter the following command:</span></span>

   ```dotnetcli
   dotnet new sln
   ```

   <span data-ttu-id="b6efb-123">A saída do terminal é semelhante ao exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="b6efb-123">The terminal output looks like the following example:</span></span>

   ```
   The template "Solution File" was created successfully.
   ```

## <a name="create-a-class-library-project"></a><span data-ttu-id="b6efb-124">Criar um projeto de biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="b6efb-124">Create a class library project</span></span>

<span data-ttu-id="b6efb-125">Adicione um novo projeto de biblioteca de classe .NET Standard chamado "StringLibrary" à solução.</span><span class="sxs-lookup"><span data-stu-id="b6efb-125">Add a new .NET Standard class library project named "StringLibrary" to the solution.</span></span>

1. <span data-ttu-id="b6efb-126">No terminal, execute o seguinte comando para criar o projeto de biblioteca:</span><span class="sxs-lookup"><span data-stu-id="b6efb-126">In the terminal, run the following command to create the library project:</span></span>

   ```dotnetcli
   dotnet new classlib -o StringLibrary
   ```

   <span data-ttu-id="b6efb-127">A saída do terminal é semelhante ao exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="b6efb-127">The terminal output looks like the following example:</span></span>

   ```
   The template "Class library" was created successfully.
   Processing post-creation actions...
   Running 'dotnet restore' on StringLibrary\StringLibrary.csproj...
     Determining projects to restore...
     Restore completed in 328.13 ms for C:\Projects\ClassLibraryProjects\StringLibrary\StringLibrary.csproj.
   Restore succeeded.
   ```

1. <span data-ttu-id="b6efb-128">Execute o seguinte comando para adicionar o projeto de biblioteca à solução:</span><span class="sxs-lookup"><span data-stu-id="b6efb-128">Run the following command to add the library project to the solution:</span></span>

   ```dotnetcli
   dotnet sln add StringLibrary/StringLibrary.csproj
   ```

   <span data-ttu-id="b6efb-129">A saída do terminal é semelhante ao exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="b6efb-129">The terminal output looks like the following example:</span></span>

   ```
   Project `StringLibrary\StringLibrary.csproj` added to the solution.
   ```

1. <span data-ttu-id="b6efb-130">Verifique se a biblioteca tem como destino a versão correta do .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="b6efb-130">Check to make sure that the library targets the correct version of .NET Standard.</span></span> <span data-ttu-id="b6efb-131">No **Explorer**, abra *StringLibrary/StringLibrary. csproj*.</span><span class="sxs-lookup"><span data-stu-id="b6efb-131">In **Explorer**, open *StringLibrary/StringLibrary.csproj*.</span></span>

   <span data-ttu-id="b6efb-132">O `TargetFramework` elemento mostra que o projeto tem como destino .NET Standard 2,0.</span><span class="sxs-lookup"><span data-stu-id="b6efb-132">The `TargetFramework` element shows that the project targets .NET Standard 2.0.</span></span>

   ```xml
   <Project Sdk="Microsoft.NET.Sdk">

     <PropertyGroup>
       <TargetFramework>netstandard2.0</TargetFramework>
     </PropertyGroup>

   </Project>
   ```

1. <span data-ttu-id="b6efb-133">Abra *Class1.cs* e substitua o código pelo código a seguir.</span><span class="sxs-lookup"><span data-stu-id="b6efb-133">Open *Class1.cs* and replace the code with the following code.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibrary/Class1.cs":::

   <span data-ttu-id="b6efb-134">A biblioteca de classes, `UtilityLibraries.StringLibrary` , contém um método chamado `StartsWithUpper` .</span><span class="sxs-lookup"><span data-stu-id="b6efb-134">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`.</span></span> <span data-ttu-id="b6efb-135">Esse método retorna um <xref:System.Boolean> valor que indica se a instância atual da cadeia de caracteres começa com um caractere maiúsculo.</span><span class="sxs-lookup"><span data-stu-id="b6efb-135">This method returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="b6efb-136">O padrão Unicode distingue caracteres maiúsculos de caracteres minúsculos.</span><span class="sxs-lookup"><span data-stu-id="b6efb-136">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="b6efb-137">O método <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> retornará `true` se um caractere for maiúsculo.</span><span class="sxs-lookup"><span data-stu-id="b6efb-137">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

1. <span data-ttu-id="b6efb-138">Salve o arquivo.</span><span class="sxs-lookup"><span data-stu-id="b6efb-138">Save the file.</span></span>

1. <span data-ttu-id="b6efb-139">Execute o comando a seguir para compilar a solução e verificar se o projeto é compilado sem erros.</span><span class="sxs-lookup"><span data-stu-id="b6efb-139">Run the following command to build the solution and verify that the project compiles without error.</span></span>

   ```dotnetcli
   dotnet build
   ```

   <span data-ttu-id="b6efb-140">A saída do terminal é semelhante ao exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="b6efb-140">The terminal output looks like the following example:</span></span>

   ```
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

## <a name="add-a-console-app-to-the-solution"></a><span data-ttu-id="b6efb-141">Adicionar um aplicativo de console à solução</span><span class="sxs-lookup"><span data-stu-id="b6efb-141">Add a console app to the solution</span></span>

<span data-ttu-id="b6efb-142">Adicione um aplicativo de console que usa a biblioteca de classes.</span><span class="sxs-lookup"><span data-stu-id="b6efb-142">Add a console application that uses the class library.</span></span> <span data-ttu-id="b6efb-143">O aplicativo solicitará que o usuário insira uma cadeia de caracteres e relate se a cadeia de caracteres começa com um caractere maiúsculo.</span><span class="sxs-lookup"><span data-stu-id="b6efb-143">The app will prompt the user to enter a string and report whether the string begins with an uppercase character.</span></span>

1. <span data-ttu-id="b6efb-144">No terminal, execute o seguinte comando para criar o projeto de aplicativo de console:</span><span class="sxs-lookup"><span data-stu-id="b6efb-144">In the terminal, run the following command to create the console app project:</span></span>

   ```dotnetcli
   dotnet new console -o ShowCase
   ```

   <span data-ttu-id="b6efb-145">A saída do terminal é semelhante ao exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="b6efb-145">The terminal output looks like the following example:</span></span>

   ```
   The template "Console Application" was created successfully.
   Processing post-creation actions...
   Running 'dotnet restore' on ShowCase\ShowCase.csproj...  
     Determining projects to restore...
     Restore completed in 210.78 ms for C:\Projects\ClassLibraryProjects\ShowCase\ShowCase.csproj.
   Restore succeeded.
   ```

1. <span data-ttu-id="b6efb-146">Execute o seguinte comando para adicionar o projeto de aplicativo de console à solução:</span><span class="sxs-lookup"><span data-stu-id="b6efb-146">Run the following command to add the console app project to the solution:</span></span>

   ```dotnetcli
   dotnet sln add ShowCase/ShowCase.csproj
   ```

   <span data-ttu-id="b6efb-147">A saída do terminal é semelhante ao exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="b6efb-147">The terminal output looks like the following example:</span></span>

   ```
   Project `ShowCase\ShowCase.csproj` added to the solution.
   ```

1. <span data-ttu-id="b6efb-148">Inicialmente, o novo projeto de aplicativo de console não tem acesso à biblioteca de classes.</span><span class="sxs-lookup"><span data-stu-id="b6efb-148">Initially, the new console app project doesn't have access to the class library.</span></span> <span data-ttu-id="b6efb-149">Para permitir que ele chame métodos na biblioteca de classes, crie uma referência de projeto para o projeto de biblioteca de classes executando o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="b6efb-149">To allow it to call methods in the class library, create a project reference to the class library project by running the following command:</span></span>

   ```dotnetcli
   dotnet add ShowCase/Showcase.csproj reference StringLibrary/StringLibrary.csproj
   ```

   <span data-ttu-id="b6efb-150">A saída do terminal é semelhante ao exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="b6efb-150">The terminal output looks like the following example:</span></span>

   ```
   Reference `..\StringLibrary\StringLibrary.csproj` added to the project.
   ```

1. <span data-ttu-id="b6efb-151">Abra o *Showcase/Program. cs* e substitua todo o código pelo código a seguir.</span><span class="sxs-lookup"><span data-stu-id="b6efb-151">Open *ShowCase/Program.cs* and replace all of the code with the following code.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/ShowCase/Program.cs":::

   <span data-ttu-id="b6efb-152">O código usa a variável `row` ​​para manter uma contagem do número de linhas de dados gravadas na janela do console.</span><span class="sxs-lookup"><span data-stu-id="b6efb-152">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="b6efb-153">Sempre que for maior ou igual a 25, o código limpará a janela do console e exibirá uma mensagem para o usuário.</span><span class="sxs-lookup"><span data-stu-id="b6efb-153">Whenever it's greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="b6efb-154">O programa solicita que o usuário insira uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="b6efb-154">The program prompts the user to enter a string.</span></span> <span data-ttu-id="b6efb-155">Ele indica se a cadeia de caracteres começa com um caractere maiúsculo.</span><span class="sxs-lookup"><span data-stu-id="b6efb-155">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="b6efb-156">Se o usuário pressionar a tecla Enter sem inserir uma cadeia de caracteres, o aplicativo será encerrado e a janela do console será fechada.</span><span class="sxs-lookup"><span data-stu-id="b6efb-156">If the user presses the Enter key without entering a string, the application ends, and the console window closes.</span></span>

1. <span data-ttu-id="b6efb-157">Salve suas alterações.</span><span class="sxs-lookup"><span data-stu-id="b6efb-157">Save your changes.</span></span>

1. <span data-ttu-id="b6efb-158">Execute o programa.</span><span class="sxs-lookup"><span data-stu-id="b6efb-158">Run the program.</span></span>

   ```dotnetcli
   dotnet run --project ShowCase/ShowCase.csproj
   ```

1. <span data-ttu-id="b6efb-159">Experimente o programa digitando cadeias de caracteres e pressionando <kbd>Enter</kbd>e pressione <kbd>Enter</kbd> para sair.</span><span class="sxs-lookup"><span data-stu-id="b6efb-159">Try out the program by entering strings and pressing <kbd>Enter</kbd>, then press <kbd>Enter</kbd> to exit.</span></span>

   <span data-ttu-id="b6efb-160">A saída do terminal é semelhante ao exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="b6efb-160">The terminal output looks like the following example:</span></span>

   ```
   Press <Enter> only to exit; otherwise, enter a string and press <Enter>:

   A string that starts with an uppercase letter
   Input: A string that starts with an uppercase letter
   Begins with uppercase? : Yes

   A string that starts with a lowercase letter
   Input: A string that starts with a lowercase letter
   Begins with uppercase? : Yes
   ```

## <a name="additional-resources"></a><span data-ttu-id="b6efb-161">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="b6efb-161">Additional resources</span></span>

* [<span data-ttu-id="b6efb-162">Desenvolver bibliotecas com o CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="b6efb-162">Develop libraries with the .NET Core CLI</span></span>](libraries.md)

## <a name="next-steps"></a><span data-ttu-id="b6efb-163">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="b6efb-163">Next steps</span></span>

<span data-ttu-id="b6efb-164">Neste tutorial, você criou uma solução, adicionou um projeto de biblioteca e adicionou um projeto de aplicativo de console que usa a biblioteca do.</span><span class="sxs-lookup"><span data-stu-id="b6efb-164">In this tutorial, you created a solution, added a library project, and added a console app project that uses the library.</span></span> <span data-ttu-id="b6efb-165">No próximo tutorial, você adicionará um projeto de teste de unidade à solução.</span><span class="sxs-lookup"><span data-stu-id="b6efb-165">In the next tutorial, you add a unit test project to the solution.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b6efb-166">Testar uma biblioteca de .NET Standard com o .NET Core no Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="b6efb-166">Test a .NET Standard library with .NET Core in Visual Studio Code</span></span>](testing-library-with-visual-studio-code.md)
