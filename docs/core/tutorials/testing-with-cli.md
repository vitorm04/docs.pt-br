---
title: Organizando e testando projetos com a linha de comando do .NET Core
description: Este tutorial explica como organizar e testar projetos do .NET Core por meio da linha de comando.
author: cartermp
ms.date: 09/10/2018
ms.custom: seodec18
ms.openlocfilehash: 38017a788a8e43601f49a98230cb4d96e0390061
ms.sourcegitcommit: 68a4b28242da50e1d25aab597c632767713a6f81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/06/2019
ms.locfileid: "74884209"
---
# <a name="organizing-and-testing-projects-with-the-net-core-command-line"></a><span data-ttu-id="e00de-103">Organizando e testando projetos com a linha de comando do .NET Core</span><span class="sxs-lookup"><span data-stu-id="e00de-103">Organizing and testing projects with the .NET Core command line</span></span>

<span data-ttu-id="e00de-104">Este tutorial segue a [Introdução ao .NET Core no Windows/Linux/macOS, usando a linha de comando](cli-create-console-app.md), e leva você além da criação de um simples aplicativo de console para desenvolver aplicativos avançados e bem organizados.</span><span class="sxs-lookup"><span data-stu-id="e00de-104">This tutorial follows [Get started with .NET Core on Windows/Linux/macOS using the command line](cli-create-console-app.md), taking you beyond the creation of a simple console app to develop advanced and well-organized applications.</span></span> <span data-ttu-id="e00de-105">Depois de mostrar como usar pastas para organizar seu código, este tutorial mostra como estender um aplicativo de console com a estrutura de teste [xUnit](https://xunit.github.io/).</span><span class="sxs-lookup"><span data-stu-id="e00de-105">After showing you how to use folders to organize your code, this tutorial shows you how to extend a console application with the [xUnit](https://xunit.github.io/) testing framework.</span></span>

## <a name="using-folders-to-organize-code"></a><span data-ttu-id="e00de-106">Usar pastas para organizar o código</span><span class="sxs-lookup"><span data-stu-id="e00de-106">Using folders to organize code</span></span>

<span data-ttu-id="e00de-107">Se você quiser introduzir novos tipos em um aplicativo de console, poderá fazer isso adicionando arquivos que contêm os tipos para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e00de-107">If you want to introduce new types into a console app, you can do so by adding files containing the types to the app.</span></span> <span data-ttu-id="e00de-108">Por exemplo, se você adicionar arquivos contendo os tipos `AccountInformation` e `MonthlyReportRecords` ao seu projeto, a estrutura do arquivo de projeto será simples e fácil de navegar:</span><span class="sxs-lookup"><span data-stu-id="e00de-108">For example if you add files containing `AccountInformation` and `MonthlyReportRecords` types to your project, the project file structure is flat and easy to navigate:</span></span>

```
/MyProject
|__AccountInformation.cs
|__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

<span data-ttu-id="e00de-109">No entanto, isso funciona bem apenas quando o projeto é relativamente pequeno.</span><span class="sxs-lookup"><span data-stu-id="e00de-109">However, this only works well when the size of your project is relatively small.</span></span> <span data-ttu-id="e00de-110">Você pode imaginar o que acontecerá se adicionar 20 tipos ao projeto?</span><span class="sxs-lookup"><span data-stu-id="e00de-110">Can you imagine what will happen if you add 20 types to the project?</span></span> <span data-ttu-id="e00de-111">O projeto definitivamente não será fácil navegar e manter com tantos arquivos dividindo o diretório raiz do projeto.</span><span class="sxs-lookup"><span data-stu-id="e00de-111">The project definitely wouldn't be easy to navigate and maintain with that many files littering the project's root directory.</span></span>

<span data-ttu-id="e00de-112">Para organizar o projeto, crie uma nova pasta e nomeie-a como *Modelos* para armazenar os arquivos do tipo.</span><span class="sxs-lookup"><span data-stu-id="e00de-112">To organize the project, create a new folder and name it *Models* to hold the type files.</span></span> <span data-ttu-id="e00de-113">Coloque os arquivos de tipo na pasta *Modelos*:</span><span class="sxs-lookup"><span data-stu-id="e00de-113">Place the type files into the *Models* folder:</span></span>

```
/MyProject
|__/Models
   |__AccountInformation.cs
   |__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

<span data-ttu-id="e00de-114">Projetos que agrupam arquivos em pastas de forma lógica são fáceis de navegar e manter.</span><span class="sxs-lookup"><span data-stu-id="e00de-114">Projects that logically group files into folders are easy to navigate and maintain.</span></span> <span data-ttu-id="e00de-115">Na próxima seção, você criará um exemplo mais complexo com pastas e testes de unidade.</span><span class="sxs-lookup"><span data-stu-id="e00de-115">In the next section, you create a more complex sample with folders and unit testing.</span></span>

## <a name="organizing-and-testing-using-the-newtypes-pets-sample"></a><span data-ttu-id="e00de-116">Organizando e testando usando o Exemplo Pets de NewTypes</span><span class="sxs-lookup"><span data-stu-id="e00de-116">Organizing and testing using the NewTypes Pets Sample</span></span>

### <a name="building-the-sample"></a><span data-ttu-id="e00de-117">Compilando o exemplo</span><span class="sxs-lookup"><span data-stu-id="e00de-117">Building the sample</span></span>

<span data-ttu-id="e00de-118">Para as etapas a seguir, você pode acompanhar usando o [NewTypes Pets Sample](https://github.com/dotnet/samples/tree/master/core/console-apps/NewTypesMsBuild) (Exemplo Pets de NewTypes) ou criar seus próprios arquivos e pastas.</span><span class="sxs-lookup"><span data-stu-id="e00de-118">For the following steps, you can either follow along using the [NewTypes Pets Sample](https://github.com/dotnet/samples/tree/master/core/console-apps/NewTypesMsBuild) or create your own files and folders.</span></span> <span data-ttu-id="e00de-119">Os tipos são organizados logicamente em uma estrutura de pastas que permite a adição de mais tipos posteriormente e os testes também são posicionados logicamente nas pastas, permitindo a adição de mais testes posteriormente.</span><span class="sxs-lookup"><span data-stu-id="e00de-119">The types are logically organized into a folder structure that permits the addition of more types later, and tests are also logically placed in folders permitting the addition of more tests later.</span></span>

<span data-ttu-id="e00de-120">Esse exemplo contém dois tipos, `Dog` e `Cat`, e faz com que eles implementem uma interface comum, `IPet`.</span><span class="sxs-lookup"><span data-stu-id="e00de-120">The sample contains two types, `Dog` and `Cat`, and has them implement a common interface, `IPet`.</span></span> <span data-ttu-id="e00de-121">Para o projeto `NewTypes`, sua meta é organizar os tipos relacionados a animais de estimação em uma pasta *Pets*.</span><span class="sxs-lookup"><span data-stu-id="e00de-121">For the `NewTypes` project, your goal is to organize the pet-related types into a *Pets* folder.</span></span> <span data-ttu-id="e00de-122">Se outro conjunto de tipos for adicionado posteriormente, *WildAnimals* por exemplo, ele será colocado na pasta *NewTypes* junto com a pasta *Pets*.</span><span class="sxs-lookup"><span data-stu-id="e00de-122">If another set of types is added later, *WildAnimals* for example, they're placed in the *NewTypes* folder alongside the *Pets* folder.</span></span> <span data-ttu-id="e00de-123">A pasta *WildAnimals* pode conter tipos de animais que não são animais de estimação, como os tipos `Squirrel` e `Rabbit`.</span><span class="sxs-lookup"><span data-stu-id="e00de-123">The *WildAnimals* folder may contain types for animals that aren't pets, such as `Squirrel` and `Rabbit` types.</span></span> <span data-ttu-id="e00de-124">Dessa forma, conforme os tipos são adicionados, o projeto continua bem organizado.</span><span class="sxs-lookup"><span data-stu-id="e00de-124">In this way as types are added, the project remains well organized.</span></span>

<span data-ttu-id="e00de-125">Crie a seguinte estrutura de pasta com o conteúdo do arquivo indicado:</span><span class="sxs-lookup"><span data-stu-id="e00de-125">Create the following folder structure with file content indicated:</span></span>

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

<span data-ttu-id="e00de-126">*IPet.cs*:</span><span class="sxs-lookup"><span data-stu-id="e00de-126">*IPet.cs*:</span></span>

[!code-csharp[IPet interface](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Pets/IPet.cs)]

<span data-ttu-id="e00de-127">*Dog.cs*:</span><span class="sxs-lookup"><span data-stu-id="e00de-127">*Dog.cs*:</span></span>

[!code-csharp[Dog class](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Pets/Dog.cs)]

<span data-ttu-id="e00de-128">*Cat.cs*:</span><span class="sxs-lookup"><span data-stu-id="e00de-128">*Cat.cs*:</span></span>

[!code-csharp[Cat class](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Pets/Cat.cs)]

<span data-ttu-id="e00de-129">*Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="e00de-129">*Program.cs*:</span></span>

[!code-csharp[Main](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Program.cs)]

<span data-ttu-id="e00de-130">*NewTypes.csproj*:</span><span class="sxs-lookup"><span data-stu-id="e00de-130">*NewTypes.csproj*:</span></span>

[!code-xml[NewTypes csproj](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/NewTypes.csproj)]

<span data-ttu-id="e00de-131">Execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="e00de-131">Execute the following command:</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="e00de-132">Obtenha a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="e00de-132">Obtain the following output:</span></span>

```console
Woof!
Meow!
```

<span data-ttu-id="e00de-133">Exercício opcional: você pode adicionar um novo tipo de animal de estimação, como um `Bird`, estendendo esse projeto.</span><span class="sxs-lookup"><span data-stu-id="e00de-133">Optional exercise: You can add a new pet type, such as a `Bird`, by extending this project.</span></span> <span data-ttu-id="e00de-134">Faça com que o método `TalkToOwner` de pássaro dê um `Tweet!` para o proprietário.</span><span class="sxs-lookup"><span data-stu-id="e00de-134">Make the bird's `TalkToOwner` method give a `Tweet!` to the owner.</span></span> <span data-ttu-id="e00de-135">Execute o aplicativo novamente.</span><span class="sxs-lookup"><span data-stu-id="e00de-135">Run the app again.</span></span> <span data-ttu-id="e00de-136">A saída incluirá `Tweet!`</span><span class="sxs-lookup"><span data-stu-id="e00de-136">The output will include `Tweet!`</span></span>

### <a name="testing-the-sample"></a><span data-ttu-id="e00de-137">Testando o exemplo</span><span class="sxs-lookup"><span data-stu-id="e00de-137">Testing the sample</span></span>

<span data-ttu-id="e00de-138">O projeto `NewTypes` está em funcionamento e você o organizou mantendo os tipos relacionados a animais de estimação em uma pasta.</span><span class="sxs-lookup"><span data-stu-id="e00de-138">The `NewTypes` project is in place, and you've organized it by keeping the pets-related types in a folder.</span></span> <span data-ttu-id="e00de-139">Em seguida, crie seu projeto de teste e comece a escrever testes com a estrutura de teste [xUnit](https://xunit.github.io/).</span><span class="sxs-lookup"><span data-stu-id="e00de-139">Next, create your test project and start writing tests with the [xUnit](https://xunit.github.io/) test framework.</span></span> <span data-ttu-id="e00de-140">O teste de unidade permite que você verifique automaticamente o comportamento dos seus tipos de animal de estimação para confirmar se eles estão funcionando corretamente.</span><span class="sxs-lookup"><span data-stu-id="e00de-140">Unit testing allows you to automatically check the behavior of your pet types to confirm that they're operating properly.</span></span>

<span data-ttu-id="e00de-141">Navegue de volta para a pasta *src* e crie uma pasta *test* com uma pasta *NewTypesTests* dentro dela.</span><span class="sxs-lookup"><span data-stu-id="e00de-141">Navigate back to the *src* folder and create a *test* folder with a *NewTypesTests* folder within it.</span></span> <span data-ttu-id="e00de-142">Em um prompt de comando da pasta *NewTypesTests*, execute `dotnet new xunit`.</span><span class="sxs-lookup"><span data-stu-id="e00de-142">At a command prompt from the *NewTypesTests* folder, execute `dotnet new xunit`.</span></span> <span data-ttu-id="e00de-143">Isso gera dois arquivos: *NewTypesTests.csproj* e *UnitTest1.cs*.</span><span class="sxs-lookup"><span data-stu-id="e00de-143">This produces two files: *NewTypesTests.csproj* and *UnitTest1.cs*.</span></span>

<span data-ttu-id="e00de-144">No momento, o projeto de teste não pode testar os tipos no `NewTypes` e requer uma referência de projeto para o projeto `NewTypes`.</span><span class="sxs-lookup"><span data-stu-id="e00de-144">The test project cannot currently test the types in `NewTypes` and requires a project reference to the `NewTypes` project.</span></span> <span data-ttu-id="e00de-145">Para adicionar uma referência de projeto, use o comando [`dotnet add reference`](../tools/dotnet-add-reference.md):</span><span class="sxs-lookup"><span data-stu-id="e00de-145">To add a project reference, use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```dotnetcli
dotnet add reference ../../src/NewTypes/NewTypes.csproj
```

<span data-ttu-id="e00de-146">Se preferir, adicione manualmente a referência de projeto adicionando um nó `<ItemGroup>` ao arquivo *NewTypesTests.csproj*:</span><span class="sxs-lookup"><span data-stu-id="e00de-146">Or, you also have the option of manually adding the project reference by adding an `<ItemGroup>` node to the *NewTypesTests.csproj* file:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="../../src/NewTypes/NewTypes.csproj" />
</ItemGroup>
```

<span data-ttu-id="e00de-147">*NewTypesTests.csproj*:</span><span class="sxs-lookup"><span data-stu-id="e00de-147">*NewTypesTests.csproj*:</span></span>

[!code-xml[NewTypesTests csproj](../../../samples/core/console-apps/NewTypesMsBuild/test/NewTypesTests/NewTypesTests.csproj)]

<span data-ttu-id="e00de-148">O arquivo *NewTypesTests.csproj* com o seguinte:</span><span class="sxs-lookup"><span data-stu-id="e00de-148">The *NewTypesTests.csproj* file contains the following:</span></span>

* <span data-ttu-id="e00de-149">Referência de pacote para `Microsoft.NET.Test.Sdk`, a infraestrutura de teste do .NET</span><span class="sxs-lookup"><span data-stu-id="e00de-149">Package reference to `Microsoft.NET.Test.Sdk`, the .NET testing infrastructure</span></span>
* <span data-ttu-id="e00de-150">Referência de pacote para `xunit`, a estrutura de teste do xUnit</span><span class="sxs-lookup"><span data-stu-id="e00de-150">Package reference to `xunit`, the xUnit testing framework</span></span>
* <span data-ttu-id="e00de-151">Referência de pacote para `xunit.runner.visualstudio`, o executor de teste</span><span class="sxs-lookup"><span data-stu-id="e00de-151">Package reference to `xunit.runner.visualstudio`, the test runner</span></span>
* <span data-ttu-id="e00de-152">Referência de projeto para `NewTypes`, o código a ser testado</span><span class="sxs-lookup"><span data-stu-id="e00de-152">Project reference to `NewTypes`, the code to test</span></span>

<span data-ttu-id="e00de-153">Altere o nome de *UnitTest1.cs* para *PetTests.cs* e substitua o código no arquivo pelo seguinte:</span><span class="sxs-lookup"><span data-stu-id="e00de-153">Change the name of *UnitTest1.cs* to *PetTests.cs* and replace the code in the file with the following:</span></span>

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

<span data-ttu-id="e00de-154">Exercício opcional: se você adicionou um tipo `Bird` anteriormente que produz um `Tweet!` para o proprietário, adicione um método de teste ao arquivo *PetTests.cs*, `BirdTalkToOwnerReturnsTweet`, para verificar se o método `TalkToOwner` funciona corretamente para o tipo `Bird`.</span><span class="sxs-lookup"><span data-stu-id="e00de-154">Optional exercise: If you added a `Bird` type earlier that yields a `Tweet!` to the owner, add a test method to the *PetTests.cs* file, `BirdTalkToOwnerReturnsTweet`, to check that the `TalkToOwner` method works correctly for the `Bird` type.</span></span>

> [!NOTE]
> <span data-ttu-id="e00de-155">Embora você espere que os valores `expected` e `actual` sejam iguais, uma declaração inicial com a verificação `Assert.NotEqual` especifica que esses valores *não são iguais*.</span><span class="sxs-lookup"><span data-stu-id="e00de-155">Although you expect that the `expected` and `actual` values are equal, an initial assertion with the `Assert.NotEqual` check specifies that these values are *not equal*.</span></span> <span data-ttu-id="e00de-156">Sempre crie inicialmente os testes para falhar para verificar a lógica do teste.</span><span class="sxs-lookup"><span data-stu-id="e00de-156">Always initially create a test to fail in order to check the logic of the test.</span></span> <span data-ttu-id="e00de-157">Depois de confirmar que o teste falhou, ajuste a declaração para permitir que o teste seja aprovado.</span><span class="sxs-lookup"><span data-stu-id="e00de-157">After you confirm that the test fails, adjust the assertion to allow the test to pass.</span></span>

<span data-ttu-id="e00de-158">O código a seguir mostra a estrutura do projeto completo:</span><span class="sxs-lookup"><span data-stu-id="e00de-158">The following shows the complete project structure:</span></span>

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

<span data-ttu-id="e00de-159">Inicie no diretório *test/NewTypesTests*.</span><span class="sxs-lookup"><span data-stu-id="e00de-159">Start in the *test/NewTypesTests* directory.</span></span> <span data-ttu-id="e00de-160">Restaure o projeto de teste com o comando [`dotnet restore`](../tools/dotnet-restore.md).</span><span class="sxs-lookup"><span data-stu-id="e00de-160">Restore the test project with the [`dotnet restore`](../tools/dotnet-restore.md) command.</span></span> <span data-ttu-id="e00de-161">Execute os testes com o comando [`dotnet test`](../tools/dotnet-test.md).</span><span class="sxs-lookup"><span data-stu-id="e00de-161">Run the tests with the [`dotnet test`](../tools/dotnet-test.md) command.</span></span> <span data-ttu-id="e00de-162">Esse comando inicia o executor de teste especificado no arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="e00de-162">This command starts the test runner specified in the project file.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="e00de-163">Conforme o esperado, o teste falha e o console exibe a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="e00de-163">As expected, testing fails, and the console displays the following output:</span></span>

```output
Test run for c:\Users\ronpet\repos\samples\core\console-apps\NewTypesMsBuild\test\NewTypesTests\bin\Debug\netcoreapp2.1\NewTypesTests.dll(.NETCoreApp,Version=v2.1)
Microsoft (R) Test Execution Command Line Tool Version 15.8.0
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...
[xUnit.net 00:00:00.77]     PetTests.DogTalkToOwnerReturnsWoof [FAIL]
[xUnit.net 00:00:00.78]     PetTests.CatTalkToOwnerReturnsMeow [FAIL]
Failed   PetTests.DogTalkToOwnerReturnsWoof
Error Message:
 Assert.NotEqual() Failure
Expected: Not "Woof!"
Actual:   "Woof!"
Stack Trace:
   at PetTests.DogTalkToOwnerReturnsWoof() in c:\Users\ronpet\repos\samples\core\console-apps\NewTypesMsBuild\test\NewTypesTests\PetTests.cs:line 13
Failed   PetTests.CatTalkToOwnerReturnsMeow
Error Message:
 Assert.NotEqual() Failure
Expected: Not "Meow!"
Actual:   "Meow!"
Stack Trace:
   at PetTests.CatTalkToOwnerReturnsMeow() in c:\Users\ronpet\repos\samples\core\console-apps\NewTypesMsBuild\test\NewTypesTests\PetTests.cs:line 22

Total tests: 2. Passed: 0. Failed: 2. Skipped: 0.
Test Run Failed.
Test execution time: 1.7000 Seconds
```

<span data-ttu-id="e00de-164">Altere as asserções de seus testes de `Assert.NotEqual` para `Assert.Equal`:</span><span class="sxs-lookup"><span data-stu-id="e00de-164">Change the assertions of your tests from `Assert.NotEqual` to `Assert.Equal`:</span></span>

[!code-csharp[PetTests class](../../../samples/core/console-apps/NewTypesMsBuild/test/NewTypesTests/PetTests.cs)]

<span data-ttu-id="e00de-165">Execute novamente os testes com o comando `dotnet test` e obtenha a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="e00de-165">Re-run the tests with the `dotnet test` command and obtain the following output:</span></span>

```output
Test run for c:\Users\ronpet\repos\samples\core\console-apps\NewTypesMsBuild\test\NewTypesTests\bin\Debug\netcoreapp2.1\NewTypesTests.dll(.NETCoreApp,Version=v2.1)
Microsoft (R) Test Execution Command Line Tool Version 15.8.0
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...

Total tests: 2. Passed: 2. Failed: 0. Skipped: 0.
Test Run Successful.
Test execution time: 1.6029 Seconds
```

<span data-ttu-id="e00de-166">O teste é aprovado.</span><span class="sxs-lookup"><span data-stu-id="e00de-166">Testing passes.</span></span> <span data-ttu-id="e00de-167">Os métodos dos tipos de animais de estimação retornam os valores corretos ao conversar com o proprietário.</span><span class="sxs-lookup"><span data-stu-id="e00de-167">The pet types' methods return the correct values when talking to the owner.</span></span>

<span data-ttu-id="e00de-168">Você aprendeu técnicas para organizar e testar projetos usando xUnit.</span><span class="sxs-lookup"><span data-stu-id="e00de-168">You've learned techniques for organizing and testing projects using xUnit.</span></span> <span data-ttu-id="e00de-169">Prossiga com essas técnicas aplicando-as em seus próprios projetos.</span><span class="sxs-lookup"><span data-stu-id="e00de-169">Go forward with these techniques applying them in your own projects.</span></span> <span data-ttu-id="e00de-170">*Boa codificação!*</span><span class="sxs-lookup"><span data-stu-id="e00de-170">*Happy coding!*</span></span>
