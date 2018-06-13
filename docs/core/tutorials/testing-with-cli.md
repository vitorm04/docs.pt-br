---
title: Organizando e testando projetos com a linha de comando do .NET Core
description: Este tutorial explica como organizar e testar projetos do .NET Core por meio da linha de comando.
author: cartermp
ms.author: mairaw
ms.date: 05/16/2017
ms.openlocfilehash: a49eb1d398ab80a4ece703b7889083ea967df862
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33217637"
---
# <a name="organizing-and-testing-projects-with-the-net-core-command-line"></a><span data-ttu-id="88a09-103">Organizando e testando projetos com a linha de comando do .NET Core</span><span class="sxs-lookup"><span data-stu-id="88a09-103">Organizing and testing projects with the .NET Core command line</span></span>

<span data-ttu-id="88a09-104">Este tutorial segue a [Introdução ao .NET Core no Windows/Linux/macOS usando a linha de comando](using-with-xplat-cli.md), levando você além da criação de um simples aplicativo de console para desenvolver aplicativos avançados e bem organizados.</span><span class="sxs-lookup"><span data-stu-id="88a09-104">This tutorial follows [Getting started with .NET Core on Windows/Linux/macOS using the command line](using-with-xplat-cli.md), taking you beyond the creation of a simple console app to develop advanced and well-organized applications.</span></span> <span data-ttu-id="88a09-105">Depois de mostrar como usar pastas para organizar seu código, este tutorial mostra como estender um aplicativo de console com a estrutura de teste [xUnit](https://xunit.github.io/).</span><span class="sxs-lookup"><span data-stu-id="88a09-105">After showing you how to use folders to organize your code, this tutorial shows you how to extend a console application with the [xUnit](https://xunit.github.io/) testing framework.</span></span>

## <a name="using-folders-to-organize-code"></a><span data-ttu-id="88a09-106">Usar pastas para organizar o código</span><span class="sxs-lookup"><span data-stu-id="88a09-106">Using folders to organize code</span></span>

<span data-ttu-id="88a09-107">Se você quiser introduzir novos tipos em um aplicativo de console, poderá fazer isso adicionando arquivos que contêm os tipos para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="88a09-107">If you want to introduce new types into a console app, you can do so by adding files containing the types to the app.</span></span> <span data-ttu-id="88a09-108">Por exemplo, se você adicionar arquivos contendo os tipos `AccountInformation` e `MonthlyReportRecords` ao seu projeto, a estrutura do arquivo de projeto será simples e fácil de navegar:</span><span class="sxs-lookup"><span data-stu-id="88a09-108">For example if you add files containing `AccountInformation` and `MonthlyReportRecords` types to your project, the project file structure is flat and easy to navigate:</span></span>

```
/MyProject
|__AccountInformation.cs
|__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

<span data-ttu-id="88a09-109">No entanto, isso funciona bem apenas quando o projeto é relativamente pequeno.</span><span class="sxs-lookup"><span data-stu-id="88a09-109">However, this only works well when the size of your project is relatively small.</span></span> <span data-ttu-id="88a09-110">Você pode imaginar o que acontecerá se adicionar 20 tipos ao projeto?</span><span class="sxs-lookup"><span data-stu-id="88a09-110">Can you imagine what will happen if you add 20 types to the project?</span></span> <span data-ttu-id="88a09-111">O projeto definitivamente não será fácil navegar e manter com tantos arquivos dividindo o diretório raiz do projeto.</span><span class="sxs-lookup"><span data-stu-id="88a09-111">The project definitely wouldn't be easy to navigate and maintain with that many files littering the project's root directory.</span></span>

<span data-ttu-id="88a09-112">Para organizar o projeto, crie uma nova pasta e nomeie-a como *Modelos* para armazenar os arquivos do tipo.</span><span class="sxs-lookup"><span data-stu-id="88a09-112">To organize the project, create a new folder and name it *Models* to hold the type files.</span></span> <span data-ttu-id="88a09-113">Coloque os arquivos de tipo na pasta *Modelos*:</span><span class="sxs-lookup"><span data-stu-id="88a09-113">Place the type files into the *Models* folder:</span></span>

```
/MyProject
|__/Models
   |__AccountInformation.cs
   |__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

<span data-ttu-id="88a09-114">Projetos que agrupam arquivos em pastas de forma lógica são fáceis de navegar e manter.</span><span class="sxs-lookup"><span data-stu-id="88a09-114">Projects that logically group files into folders are easy to navigate and maintain.</span></span> <span data-ttu-id="88a09-115">Na próxima seção, você criará um exemplo mais complexo com pastas e testes de unidade.</span><span class="sxs-lookup"><span data-stu-id="88a09-115">In the next section, you create a more complex sample with folders and unit testing.</span></span>

## <a name="organizing-and-testing-using-the-newtypes-pets-sample"></a><span data-ttu-id="88a09-116">Organizando e testando usando o Exemplo Pets de NewTypes</span><span class="sxs-lookup"><span data-stu-id="88a09-116">Organizing and testing using the NewTypes Pets Sample</span></span>

### <a name="building-the-sample"></a><span data-ttu-id="88a09-117">Compilando o exemplo</span><span class="sxs-lookup"><span data-stu-id="88a09-117">Building the sample</span></span>

<span data-ttu-id="88a09-118">Para as etapas a seguir, você pode acompanhar usando o [NewTypes Pets Sample](https://github.com/dotnet/samples/tree/master/core/console-apps/NewTypesMsBuild) (Exemplo Pets de NewTypes) ou criar seus próprios arquivos e pastas.</span><span class="sxs-lookup"><span data-stu-id="88a09-118">For the following steps, you can either follow along using the [NewTypes Pets Sample](https://github.com/dotnet/samples/tree/master/core/console-apps/NewTypesMsBuild) or create your own files and folders.</span></span> <span data-ttu-id="88a09-119">Os tipos são organizados logicamente em uma estrutura de pastas que permite a adição de mais tipos posteriormente e os testes também são posicionados logicamente nas pastas, permitindo a adição de mais testes posteriormente.</span><span class="sxs-lookup"><span data-stu-id="88a09-119">The types are logically organized into a folder structure that permits the addition of more types later, and tests are also logically placed in folders permitting the addition of more tests later.</span></span>

<span data-ttu-id="88a09-120">Esse exemplo contém dois tipos, `Dog` e `Cat`, e faz com que eles implementem uma interface comum, `IPet`.</span><span class="sxs-lookup"><span data-stu-id="88a09-120">The sample contains two types, `Dog` and `Cat`, and has them implement a common interface, `IPet`.</span></span> <span data-ttu-id="88a09-121">Para o projeto `NewTypes`, sua meta é organizar os tipos relacionados a animais de estimação em uma pasta *Pets*.</span><span class="sxs-lookup"><span data-stu-id="88a09-121">For the `NewTypes` project, your goal is to organize the pet-related types into a *Pets* folder.</span></span> <span data-ttu-id="88a09-122">Se outro conjunto de tipos for adicionado posteriormente, *WildAnimals* por exemplo, ele será colocado na pasta *NewTypes* junto com a pasta *Pets*.</span><span class="sxs-lookup"><span data-stu-id="88a09-122">If another set of types is added later, *WildAnimals* for example, they're placed in the *NewTypes* folder alongside the *Pets* folder.</span></span> <span data-ttu-id="88a09-123">A pasta *WildAnimals* pode conter tipos de animais que não são animais de estimação, como os tipos `Squirrel` e `Rabbit`.</span><span class="sxs-lookup"><span data-stu-id="88a09-123">The *WildAnimals* folder may contain types for animals that aren't pets, such as `Squirrel` and `Rabbit` types.</span></span> <span data-ttu-id="88a09-124">Dessa forma, conforme os tipos são adicionados, o projeto continua bem organizado.</span><span class="sxs-lookup"><span data-stu-id="88a09-124">In this way as types are added, the project remains well organized.</span></span> 

<span data-ttu-id="88a09-125">Crie a seguinte estrutura de pasta com o conteúdo do arquivo indicado:</span><span class="sxs-lookup"><span data-stu-id="88a09-125">Create the following folder structure with file content indicated:</span></span>

```
/NewTypes
|__/src
   |__/NewTypes
      |__/Pets
         |__Dog.cs
         |__Cat.cs
         |__IPet.cs
      |__Program.cs
      |__NewTypes.csproj
```

<span data-ttu-id="88a09-126">*IPet.cs*:</span><span class="sxs-lookup"><span data-stu-id="88a09-126">*IPet.cs*:</span></span>

[!code-csharp[IPet interface](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Pets/IPet.cs)]

<span data-ttu-id="88a09-127">*Dog.cs*:</span><span class="sxs-lookup"><span data-stu-id="88a09-127">*Dog.cs*:</span></span>

[!code-csharp[Dog class](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Pets/Dog.cs)]

<span data-ttu-id="88a09-128">*Cat.cs*:</span><span class="sxs-lookup"><span data-stu-id="88a09-128">*Cat.cs*:</span></span>

[!code-csharp[Cat class](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Pets/Cat.cs)]

<span data-ttu-id="88a09-129">*Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="88a09-129">*Program.cs*:</span></span>

[!code-csharp[Main](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Program.cs)]

<span data-ttu-id="88a09-130">*NewTypes.csproj*:</span><span class="sxs-lookup"><span data-stu-id="88a09-130">*NewTypes.csproj*:</span></span>

[!code-xml[NewTypes csproj](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/NewTypes.csproj)]

<span data-ttu-id="88a09-131">Execute os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="88a09-131">Execute the following commands:</span></span>

```console
dotnet run
```

<span data-ttu-id="88a09-132">Obtenha a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="88a09-132">Obtain the following output:</span></span>

```console
Woof!
Meow!
```

<span data-ttu-id="88a09-133">Exercício opcional: você pode adicionar um novo tipo de animal de estimação, como um `Bird`, estendendo esse projeto.</span><span class="sxs-lookup"><span data-stu-id="88a09-133">Optional exercise: You can add a new pet type, such as a `Bird`, by extending this project.</span></span> <span data-ttu-id="88a09-134">Faça com que o método `TalkToOwner` de pássaro dê um `Tweet!` para o proprietário.</span><span class="sxs-lookup"><span data-stu-id="88a09-134">Make the bird's `TalkToOwner` method give a `Tweet!` to the owner.</span></span> <span data-ttu-id="88a09-135">Execute o aplicativo novamente.</span><span class="sxs-lookup"><span data-stu-id="88a09-135">Run the app again.</span></span> <span data-ttu-id="88a09-136">A saída incluirá `Tweet!`</span><span class="sxs-lookup"><span data-stu-id="88a09-136">The output will include `Tweet!`</span></span>

### <a name="testing-the-sample"></a><span data-ttu-id="88a09-137">Testando o exemplo</span><span class="sxs-lookup"><span data-stu-id="88a09-137">Testing the sample</span></span>

<span data-ttu-id="88a09-138">O projeto `NewTypes` está em funcionamento e você o organizou mantendo os tipos relacionados a animais de estimação em uma pasta.</span><span class="sxs-lookup"><span data-stu-id="88a09-138">The `NewTypes` project is in place, and you've organized it by keeping the pets-related types in a folder.</span></span> <span data-ttu-id="88a09-139">Em seguida, crie seu projeto de teste e comece a escrever testes com a estrutura de teste [xUnit](https://xunit.github.io/).</span><span class="sxs-lookup"><span data-stu-id="88a09-139">Next, create your test project and start writing tests with the [xUnit](https://xunit.github.io/) test framework.</span></span> <span data-ttu-id="88a09-140">O teste de unidade permite que você verifique automaticamente o comportamento dos seus tipos de animais de estimação para confirmar se eles estão funcionando corretamente.</span><span class="sxs-lookup"><span data-stu-id="88a09-140">Unit testing allows you to automatically check the bevahior of your pet types to confirm that they're operating properly.</span></span>

<span data-ttu-id="88a09-141">Crie uma pasta *test* com a pasta *NewTypesTests* nela.</span><span class="sxs-lookup"><span data-stu-id="88a09-141">Create a *test* folder with a *NewTypesTests* folder within it.</span></span> <span data-ttu-id="88a09-142">Em um prompt de comando da pasta *NewTypesTests*, execute `dotnet new xunit`.</span><span class="sxs-lookup"><span data-stu-id="88a09-142">At a command prompt from the *NewTypesTests* folder, execute `dotnet new xunit`.</span></span> <span data-ttu-id="88a09-143">Isso gera dois arquivos: *NewTypesTests.csproj* e *UnitTest1.cs*.</span><span class="sxs-lookup"><span data-stu-id="88a09-143">This produces two files: *NewTypesTests.csproj* and *UnitTest1.cs*.</span></span>

<span data-ttu-id="88a09-144">No momento, o projeto de teste não pode testar os tipos no `NewTypes` e requer uma referência de projeto para o projeto `NewTypes`.</span><span class="sxs-lookup"><span data-stu-id="88a09-144">The test project cannot currently test the types in `NewTypes` and requires a project reference to the `NewTypes` project.</span></span> <span data-ttu-id="88a09-145">Para adicionar uma referência de projeto, use o comando [`dotnet add reference`](../tools/dotnet-add-reference.md):</span><span class="sxs-lookup"><span data-stu-id="88a09-145">To add a project reference, use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../../src/NewTypes/NewTypes.csproj
```

<span data-ttu-id="88a09-146">Você também tem a opção de adicionar manualmente a referência de projeto adicionando um nó `<ItemGroup>` ao arquivo *NewTypesTests.csproj*:</span><span class="sxs-lookup"><span data-stu-id="88a09-146">You also have the option of manually adding the project reference by adding an `<ItemGroup>` node to the *NewTypesTests.csproj* file:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="../../src/NewTypes/NewTypes.csproj" />
</ItemGroup>
```

<span data-ttu-id="88a09-147">*NewTypesTests.csproj*:</span><span class="sxs-lookup"><span data-stu-id="88a09-147">*NewTypesTests.csproj*:</span></span>

[!code-xml[NewTypesTests csproj](../../../samples/core/console-apps/NewTypesMsBuild/test/NewTypesTests/NewTypesTests.csproj)]

<span data-ttu-id="88a09-148">O arquivo *NewTypesTests.csproj* com o seguinte:</span><span class="sxs-lookup"><span data-stu-id="88a09-148">The *NewTypesTests.csproj* file contains the following:</span></span>

* <span data-ttu-id="88a09-149">Referência de pacote para `Microsoft.NET.Test.Sdk`, a infraestrutura de teste do .NET</span><span class="sxs-lookup"><span data-stu-id="88a09-149">Package reference to `Microsoft.NET.Test.Sdk`, the .NET testing infrastructure</span></span>
* <span data-ttu-id="88a09-150">Referência de pacote para `xunit`, a estrutura de teste do xUnit</span><span class="sxs-lookup"><span data-stu-id="88a09-150">Package reference to `xunit`, the xUnit testing framework</span></span>
* <span data-ttu-id="88a09-151">Referência de pacote para `xunit.runner.visualstudio`, o executor de teste</span><span class="sxs-lookup"><span data-stu-id="88a09-151">Package reference to `xunit.runner.visualstudio`, the test runner</span></span>
* <span data-ttu-id="88a09-152">Referência de projeto para `NewTypes`, o código a ser testado</span><span class="sxs-lookup"><span data-stu-id="88a09-152">Project reference to `NewTypes`, the code to test</span></span>

<span data-ttu-id="88a09-153">Altere o nome de *UnitTest1.cs* para *PetTests.cs* e substitua o código no arquivo pelo seguinte:</span><span class="sxs-lookup"><span data-stu-id="88a09-153">Change the name of *UnitTest1.cs* to *PetTests.cs* and replace the code in the file with the following:</span></span>

```csharp
using System;
using Xunit;
using Pets;

public class PetTests
{
    [Fact]
    public void DogTalkToOwnerReturnsWoof()
    {
        string expected = "Woof!";
        string actual = new Dog().TalkToOwner();
        
        Assert.NotEqual(expected, actual);
    }
    
    [Fact]
    public void CatTalkToOwnerReturnsMeow()
    {
        string expected = "Meow!";
        string actual = new Cat().TalkToOwner();
        
        Assert.NotEqual(expected, actual);
    }
}
```

<span data-ttu-id="88a09-154">Exercício opcional: se você adicionou um tipo `Bird` anteriormente que produz um `Tweet!` para o proprietário, adicione um método de teste ao arquivo *PetTests.cs*, `BirdTalkToOwnerReturnsTweet`, para verificar se o método `TalkToOwner` funciona corretamente para o tipo `Bird`.</span><span class="sxs-lookup"><span data-stu-id="88a09-154">Optional exercise: If you added a `Bird` type earlier that yields a `Tweet!` to the owner, add a test method to the *PetTests.cs* file, `BirdTalkToOwnerReturnsTweet`, to check that the `TalkToOwner` method works correctly for the `Bird` type.</span></span>

> [!NOTE]
> <span data-ttu-id="88a09-155">Embora você espere que os valores `expected` e `actual` sejam iguais, as asserções inicias com as verificações `Assert.NotEqual` especificam que eles *não são iguais*.</span><span class="sxs-lookup"><span data-stu-id="88a09-155">Although you expect that the `expected` and `actual` values are equal, the initial assertions with the `Assert.NotEqual` checks specify that they are *not equal*.</span></span> <span data-ttu-id="88a09-156">Sempre crie inicialmente os testes para falhar uma vez para verificar a lógica dos testes.</span><span class="sxs-lookup"><span data-stu-id="88a09-156">Always initially create your tests to fail once in order to check the logic of the tests.</span></span> <span data-ttu-id="88a09-157">Essa é uma etapa importante na metodologia TDD (design orientado a testes).</span><span class="sxs-lookup"><span data-stu-id="88a09-157">This is an important step in test-driven design (TDD) methodology.</span></span> <span data-ttu-id="88a09-158">Depois de confirmar que os testes falham, ajuste as asserções para permitir que eles sejam aprovados.</span><span class="sxs-lookup"><span data-stu-id="88a09-158">After you confirm the tests fail, you adjust the assertions to allow them to pass.</span></span>

<span data-ttu-id="88a09-159">O código a seguir mostra a estrutura do projeto completo:</span><span class="sxs-lookup"><span data-stu-id="88a09-159">The following shows the complete project structure:</span></span>

```
/NewTypes
|__/src
   |__/NewTypes
      |__/Pets
         |__Dog.cs
         |__Cat.cs
         |__IPet.cs
      |__Program.cs
      |__NewTypes.csproj
|__/test
   |__NewTypesTests
      |__PetTests.cs
      |__NewTypesTests.csproj
```

<span data-ttu-id="88a09-160">Inicie no diretório *test/NewTypesTests*.</span><span class="sxs-lookup"><span data-stu-id="88a09-160">Start in the *test/NewTypesTests* directory.</span></span> <span data-ttu-id="88a09-161">Restaure o projeto de teste com o comando [`dotnet restore`](../tools/dotnet-restore.md).</span><span class="sxs-lookup"><span data-stu-id="88a09-161">Restore the test project with the [`dotnet restore`](../tools/dotnet-restore.md) command.</span></span> <span data-ttu-id="88a09-162">Execute os testes com o comando [`dotnet test`](../tools/dotnet-test.md).</span><span class="sxs-lookup"><span data-stu-id="88a09-162">Run the tests with the [`dotnet test`](../tools/dotnet-test.md) command.</span></span> <span data-ttu-id="88a09-163">Esse comando inicia o executor de teste especificado no arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="88a09-163">This command starts the test runner specified in the project file.</span></span>

 [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

 
<span data-ttu-id="88a09-164">Conforme o esperado, o teste falha e o console exibe a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="88a09-164">As expected, testing fails, and the console displays the following output:</span></span>
 
```
Test run for C:\NewTypesMsBuild\test\NewTypesTests\bin\Debug\netcoreapp1.1\NewTypesTests.dll(.NETCoreApp,Version=v1.1)
Microsoft (R) Test Execution Command Line Tool Version 15.0.0.0
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...
[xUnit.net 00:00:00.7271827]   Discovering: NewTypesTests
[xUnit.net 00:00:00.8258687]   Discovered:  NewTypesTests
[xUnit.net 00:00:00.8663545]   Starting:    NewTypesTests
[xUnit.net 00:00:01.0109236]     PetTests.CatTalkToOwnerReturnsMeow [FAIL]
[xUnit.net 00:00:01.0119107]       Assert.NotEqual() Failure
[xUnit.net 00:00:01.0120278]       Expected: Not "Meow!"
[xUnit.net 00:00:01.0120968]       Actual:   "Meow!"
[xUnit.net 00:00:01.0130500]       Stack Trace:
[xUnit.net 00:00:01.0141240]         C:\NewTypesMsBuild\test\NewTypesTests\PetTests.cs(22,0): at PetTests.CatTalkToOwnerReturnsMeow()
[xUnit.net 00:00:01.0272364]     PetTests.DogTalkToOwnerReturnsWoof [FAIL]
[xUnit.net 00:00:01.0273649]       Assert.NotEqual() Failure
[xUnit.net 00:00:01.0274166]       Expected: Not "Woof!"
[xUnit.net 00:00:01.0274690]       Actual:   "Woof!"
[xUnit.net 00:00:01.0275264]       Stack Trace:
[xUnit.net 00:00:01.0275960]         C:\NewTypesMsBuild\test\NewTypesTests\PetTests.cs(13,0): at PetTests.DogTalkToOwnerReturnsWoof()
[xUnit.net 00:00:01.0294509]   Finished:    NewTypesTests
Failed   PetTests.CatTalkToOwnerReturnsMeow
Error Message:
 Assert.NotEqual() Failure
Expected: Not "Meow!"
Actual:   "Meow!"
Stack Trace:
   at PetTests.CatTalkToOwnerReturnsMeow() in C:\NewTypesMsBuild\test\NewTypesTests\PetTests.cs:line 22
Failed   PetTests.DogTalkToOwnerReturnsWoof
Error Message:
 Assert.NotEqual() Failure
Expected: Not "Woof!"
Actual:   "Woof!"
Stack Trace:
   at PetTests.DogTalkToOwnerReturnsWoof() in C:\NewTypesMsBuild\test\NewTypesTests\PetTests.cs:line 13

Total tests: 2. Passed: 0. Failed: 2. Skipped: 0.
Test Run Failed.
Test execution time: 2.1371 Seconds
```

<span data-ttu-id="88a09-165">Altere as asserções de seus testes de `Assert.NotEqual` para `Assert.Equal`:</span><span class="sxs-lookup"><span data-stu-id="88a09-165">Change the assertions of your tests from `Assert.NotEqual` to `Assert.Equal`:</span></span>

[!code-csharp[PetTests class](../../../samples/core/console-apps/NewTypesMsBuild/test/NewTypesTests/PetTests.cs)]

<span data-ttu-id="88a09-166">Execute novamente os testes com o comando `dotnet test` e obtenha a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="88a09-166">Re-run the tests with the `dotnet test` command and obtain the following output:</span></span>

```
Microsoft (R) Test Execution Command Line Tool Version 15.0.0.0
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...
[xUnit.net 00:00:01.3882374]   Discovering: NewTypesTests
[xUnit.net 00:00:01.4767970]   Discovered:  NewTypesTests
[xUnit.net 00:00:01.5157667]   Starting:    NewTypesTests
[xUnit.net 00:00:01.6408870]   Finished:    NewTypesTests

Total tests: 2. Passed: 2. Failed: 0. Skipped: 0.
Test Run Successful.
Test execution time: 1.6634 Seconds
```

<span data-ttu-id="88a09-167">O teste é aprovado.</span><span class="sxs-lookup"><span data-stu-id="88a09-167">Testing passes.</span></span> <span data-ttu-id="88a09-168">Os métodos dos tipos de animais de estimação retornam os valores corretos ao conversar com o proprietário.</span><span class="sxs-lookup"><span data-stu-id="88a09-168">The pet types' methods return the correct values when talking to the owner.</span></span>

<span data-ttu-id="88a09-169">Você aprendeu técnicas para organizar e testar projetos usando xUnit.</span><span class="sxs-lookup"><span data-stu-id="88a09-169">You've learned techniques for organizing and testing projects using xUnit.</span></span> <span data-ttu-id="88a09-170">Prossiga com essas técnicas aplicando-as em seus próprios projetos.</span><span class="sxs-lookup"><span data-stu-id="88a09-170">Go forward with these techniques applying them in your own projects.</span></span> <span data-ttu-id="88a09-171">*Boa codificação!*</span><span class="sxs-lookup"><span data-stu-id="88a09-171">*Happy coding!*</span></span>

