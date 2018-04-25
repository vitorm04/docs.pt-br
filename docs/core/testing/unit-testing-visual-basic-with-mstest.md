---
title: Visual Basic de teste de unidade no .NET Core usando dotnet test e MSTest
description: Aprenda os conceitos de teste de unidade no .NET Core por meio de uma experiência interativa de criação passo a passo de uma solução de exemplo do Visual Basic usando MSTest.
author: billwagner
ms.author: wiwagn
ms.date: 09/01/2017
ms.topic: article
dev_langs:
- vb
ms.prod: .net-core
ms.workload:
- dotnetcore
ms.openlocfilehash: 667dd6ab5ee226edd6e5f57f2eff053f4758ac50
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-mstest"></a><span data-ttu-id="00aec-103">Bibliotecas do .NET Core no Visual Basic de teste de unidade usando dotnet test e MSTest</span><span class="sxs-lookup"><span data-stu-id="00aec-103">Unit testing Visual Basic .NET Core libraries using dotnet test and MStest</span></span>

<span data-ttu-id="00aec-104">Este tutorial apresenta uma experiência interativa de compilação de uma solução de exemplo passo a passo para aprender os conceitos do teste de unidade.</span><span class="sxs-lookup"><span data-stu-id="00aec-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="00aec-105">Se você preferir acompanhar o tutorial usando uma solução interna, [veja ou baixe o exemplo de código](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-mstest/) antes de começar.</span><span class="sxs-lookup"><span data-stu-id="00aec-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-mstest/) before you begin.</span></span> <span data-ttu-id="00aec-106">Para obter instruções de download, consulte [Exemplos e tutoriais](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="00aec-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="00aec-107">Criando o projeto de origem</span><span class="sxs-lookup"><span data-stu-id="00aec-107">Creating the source project</span></span>

<span data-ttu-id="00aec-108">Abra uma janela do shell.</span><span class="sxs-lookup"><span data-stu-id="00aec-108">Open a shell window.</span></span> <span data-ttu-id="00aec-109">Crie um diretório chamado *unit-testing-vb-mstest* para armazenar a solução.</span><span class="sxs-lookup"><span data-stu-id="00aec-109">Create a directory called *unit-testing-vb-mstest* to hold the solution.</span></span>
<span data-ttu-id="00aec-110">Nesse novo diretório, execute [`dotnet new sln`](../tools/dotnet-new.md) para criar uma nova solução.</span><span class="sxs-lookup"><span data-stu-id="00aec-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution.</span></span> <span data-ttu-id="00aec-111">Essa prática facilita gerenciar a biblioteca de classes e o projeto de teste de unidade.</span><span class="sxs-lookup"><span data-stu-id="00aec-111">This practice makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="00aec-112">No diretório da solução, crie um diretório *PrimeService*.</span><span class="sxs-lookup"><span data-stu-id="00aec-112">Inside the solution directory, create a *PrimeService* directory.</span></span> <span data-ttu-id="00aec-113">Você tem a seguinte estrutura de arquivo e diretório até aqui:</span><span class="sxs-lookup"><span data-stu-id="00aec-113">You have the following directory and file structure thus far:</span></span>

```
/unit-testing-vb-mstest
    unit-testing-vb-mstest.sln
    /PrimeService
```

<span data-ttu-id="00aec-114">Torne *PrimeService* o diretório atual e execute [`dotnet new classlib -lang VB`](../tools/dotnet-new.md) para criar o projeto de origem.</span><span class="sxs-lookup"><span data-stu-id="00aec-114">Make *PrimeService* the current directory and run [`dotnet new classlib -lang VB`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="00aec-115">Renomeie *Class1.VB* para *PrimeService.VB*.</span><span class="sxs-lookup"><span data-stu-id="00aec-115">Rename *Class1.VB* to *PrimeService.VB*.</span></span> <span data-ttu-id="00aec-116">Para usar o TDD (Desenvolvimento Orientado por Testes), você cria uma implementação com falha da classe `PrimeService`:</span><span class="sxs-lookup"><span data-stu-id="00aec-116">To use test-driven development (TDD), you create a failing implementation of the `PrimeService` class:</span></span>

```vb
Imports System

Namespace Prime.Services
    Public Class PrimeService
        Public Function IsPrime(candidate As Integer) As Boolean
            Throw New NotImplementedException("Please create a test first")
        End Function
    End Class
End Namespace
```

<span data-ttu-id="00aec-117">Altere o diretório de volta para o diretório *unit-testing-vb-using-stest*.</span><span class="sxs-lookup"><span data-stu-id="00aec-117">Change the directory back to the *unit-testing-vb-using-stest* directory.</span></span> <span data-ttu-id="00aec-118">Execute [`dotnet sln add .\PrimeService\PrimeService.vbproj`](../tools/dotnet-sln.md) para adicionar o projeto de biblioteca de classes à solução.</span><span class="sxs-lookup"><span data-stu-id="00aec-118">Run [`dotnet sln add .\PrimeService\PrimeService.vbproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="creating-the-test-project"></a><span data-ttu-id="00aec-119">Criando o projeto de teste</span><span class="sxs-lookup"><span data-stu-id="00aec-119">Creating the test project</span></span>

<span data-ttu-id="00aec-120">Em seguida, crie o diretório *PrimeService.Tests*.</span><span class="sxs-lookup"><span data-stu-id="00aec-120">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="00aec-121">O seguinte esquema mostra a estrutura do diretório:</span><span class="sxs-lookup"><span data-stu-id="00aec-121">The following outline shows the directory structure:</span></span>

```
/unit-testing-vb-mstest
    unit-testing-vb-mstest.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

<span data-ttu-id="00aec-122">Torne o diretório *PrimeService.Tests* o diretório atual e crie um novo projeto usando [`dotnet new mstest -lang VB`](../tools/dotnet-new.md).</span><span class="sxs-lookup"><span data-stu-id="00aec-122">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new mstest -lang VB`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="00aec-123">Esse comando cria um projeto de teste que usa o MSTest como a biblioteca de teste.</span><span class="sxs-lookup"><span data-stu-id="00aec-123">This command creates a test project that uses MSTest as the test library.</span></span> <span data-ttu-id="00aec-124">O modelo gerado configura o executor de teste no *PrimeServiceTests.vbproj*:</span><span class="sxs-lookup"><span data-stu-id="00aec-124">The generated template configures the test runner in the *PrimeServiceTests.vbproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.5.0" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.18" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.18" />
</ItemGroup>
```

<span data-ttu-id="00aec-125">O projeto de teste requer outros pacotes para criar e executar testes de unidade.</span><span class="sxs-lookup"><span data-stu-id="00aec-125">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="00aec-126">`dotnet new`, na etapa anterior, adicionou MSTest e o executor de MSTest.</span><span class="sxs-lookup"><span data-stu-id="00aec-126">`dotnet new` in the previous step added MSTest and the MSTest runner.</span></span> <span data-ttu-id="00aec-127">Agora, adicione a biblioteca de classes `PrimeService` como outra dependência ao projeto.</span><span class="sxs-lookup"><span data-stu-id="00aec-127">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="00aec-128">Use o comando [`dotnet add reference`](../tools/dotnet-add-reference.md):</span><span class="sxs-lookup"><span data-stu-id="00aec-128">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../PrimeService/PrimeService.vbproj
```

<span data-ttu-id="00aec-129">Você pode ver o arquivo inteiro no [repositório de exemplos](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService.Tests.vbproj) no GitHub.</span><span class="sxs-lookup"><span data-stu-id="00aec-129">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService.Tests.vbproj) on GitHub.</span></span>

<span data-ttu-id="00aec-130">Você tem o seguinte layout de solução final:</span><span class="sxs-lookup"><span data-stu-id="00aec-130">You have the following final solution layout:</span></span>

```
/unit-testing-vb-mstest
    unit-testing-vb-mstest.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.vbproj
```

<span data-ttu-id="00aec-131">Execute [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj`](../tools/dotnet-sln.md) no diretório *unit-testing-vb-mstest*.</span><span class="sxs-lookup"><span data-stu-id="00aec-131">Execute [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj`](../tools/dotnet-sln.md) in the *unit-testing-vb-mstest* directory.</span></span>

## <a name="creating-the-first-test"></a><span data-ttu-id="00aec-132">Criando o primeiro teste</span><span class="sxs-lookup"><span data-stu-id="00aec-132">Creating the first test</span></span>

<span data-ttu-id="00aec-133">A abordagem de TDD pede a criação de um teste com falha para fazê-lo passar e depois a repetição do processo.</span><span class="sxs-lookup"><span data-stu-id="00aec-133">The TDD approach calls for writing one failing test, making it pass, then repeating the process.</span></span> <span data-ttu-id="00aec-134">Remova *UnitTest1.vb* do diretório *PrimeService.Tests* e crie um novo arquivo do Visual Basic chamado *PrimeService_IsPrimeShould.VB*.</span><span class="sxs-lookup"><span data-stu-id="00aec-134">Remove *UnitTest1.vb* from the *PrimeService.Tests* directory and create a new Visual Basic file named *PrimeService_IsPrimeShould.VB*.</span></span> <span data-ttu-id="00aec-135">Adicione o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="00aec-135">Add the following code:</span></span>

```vb
Imports Microsoft.VisualStudio.TestTools.UnitTesting

Namespace PrimeService.Tests
    <TestClass>
    Public Class PrimeService_IsPrimeShould
        Private _primeService As Prime.Services.PrimeService = New Prime.Services.PrimeService()

        <TestMethod>
        Sub ReturnFalseGivenValueOf1()
            Dim result As Boolean = _primeService.IsPrime(1)

            Assert.False(result, "1 should not be prime")
        End Sub

    End Class
End Namespace
```

<span data-ttu-id="00aec-136">O atributo `<TestClass>` indica uma classe que contém testes.</span><span class="sxs-lookup"><span data-stu-id="00aec-136">The `<TestClass>` attribute indicates a class that contains tests.</span></span> <span data-ttu-id="00aec-137">O atributo `<TestMethod>` indica um método que é executado pelo executor de teste.</span><span class="sxs-lookup"><span data-stu-id="00aec-137">The `<TestMethod>` attribute denotes a method that is run by the test runner.</span></span> <span data-ttu-id="00aec-138">Em *unit-testing-vb-mstest*, execute [`dotnet test`](../tools/dotnet-test.md) para criar os testes e a biblioteca de classes e, em seguida, execute os testes.</span><span class="sxs-lookup"><span data-stu-id="00aec-138">From the *unit-testing-vb-mstest*, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="00aec-139">O executor de teste do MSTest contém o ponto de entrada do programa para executar os testes.</span><span class="sxs-lookup"><span data-stu-id="00aec-139">The MSTest test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="00aec-140">`dotnet test` inicia o executor de teste usando o projeto de teste de unidade que você criou.</span><span class="sxs-lookup"><span data-stu-id="00aec-140">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="00aec-141">O teste falha.</span><span class="sxs-lookup"><span data-stu-id="00aec-141">Your test fails.</span></span> <span data-ttu-id="00aec-142">Você ainda não criou a implementação.</span><span class="sxs-lookup"><span data-stu-id="00aec-142">You haven't created the implementation yet.</span></span> <span data-ttu-id="00aec-143">Faça esse teste escrevendo o código mais simples na classe `PrimeService` que funciona:</span><span class="sxs-lookup"><span data-stu-id="00aec-143">Make this test by writing the simplest code in the `PrimeService` class that works:</span></span>

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first")
End Function
```

<span data-ttu-id="00aec-144">No diretório *unit-testing-vb-mstest*, execute `dotnet test` novamente.</span><span class="sxs-lookup"><span data-stu-id="00aec-144">In the *unit-testing-vb-mstest* directory, run `dotnet test` again.</span></span> <span data-ttu-id="00aec-145">O comando `dotnet test` executa uma compilação para o projeto `PrimeService` e, depois, para o projeto `PrimeService.Tests`.</span><span class="sxs-lookup"><span data-stu-id="00aec-145">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="00aec-146">Depois de compilar os dois projetos, ele executará esse teste único.</span><span class="sxs-lookup"><span data-stu-id="00aec-146">After building both projects, it runs this single test.</span></span> <span data-ttu-id="00aec-147">Ele é aprovado.</span><span class="sxs-lookup"><span data-stu-id="00aec-147">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="00aec-148">Adicionando mais recursos</span><span class="sxs-lookup"><span data-stu-id="00aec-148">Adding more features</span></span>

<span data-ttu-id="00aec-149">Agora que você fez um teste ser aprovado, é hora de escrever mais.</span><span class="sxs-lookup"><span data-stu-id="00aec-149">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="00aec-150">Existem alguns outros casos simples de números primos: 0, -1.</span><span class="sxs-lookup"><span data-stu-id="00aec-150">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="00aec-151">Você pode adicionar esses casos como novos testes com o atributo `<TestMethod>`, mas isso se torna entediante rapidamente.</span><span class="sxs-lookup"><span data-stu-id="00aec-151">You could add those cases as new tests with the `<TestMethod>` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="00aec-152">Há outros atributos do MSTest que permitem escrever um pacote de testes semelhantes.</span><span class="sxs-lookup"><span data-stu-id="00aec-152">There are other MSTest attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="00aec-153">Um atributo `<DataTestMethod>` representa um pacote de testes que executa o mesmo código, mas têm diferentes argumentos de entrada.</span><span class="sxs-lookup"><span data-stu-id="00aec-153">A `<DataTestMethod>` attribute represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="00aec-154">Você pode usar o atributo `<DataRow>` para especificar valores para essas entradas.</span><span class="sxs-lookup"><span data-stu-id="00aec-154">You can use the `<DataRow>` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="00aec-155">Em vez de criar novos testes, aplique esses dois atributos para criar uma única teoria.</span><span class="sxs-lookup"><span data-stu-id="00aec-155">Instead of creating new tests, apply these two attributes to create a single theory.</span></span> <span data-ttu-id="00aec-156">A teoria é um método que testa vários valores inferiores a dois, que é o número primo mais baixo:</span><span class="sxs-lookup"><span data-stu-id="00aec-156">The theory is a method that tests several values less than two, which is the lowest prime number:</span></span>

[!code-vb[Sample_TestCode](../../../samples/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

<span data-ttu-id="00aec-157">Execute `dotnet test`, e dois desses testes falham.</span><span class="sxs-lookup"><span data-stu-id="00aec-157">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="00aec-158">Para fazer todos os testes serem aprovados, altere a cláusula `if` no início do método:</span><span class="sxs-lookup"><span data-stu-id="00aec-158">To make all of the tests pass, change the `if` clause at the beginning of the method:</span></span>

```vb
if candidate < 2
```

<span data-ttu-id="00aec-159">Continue iterando adicionando mais testes, mais teorias e mais código na biblioteca principal.</span><span class="sxs-lookup"><span data-stu-id="00aec-159">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="00aec-160">Você tem a [versão concluída dos testes](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.vb) e a [implementação completa da biblioteca](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService/PrimeService.vb).</span><span class="sxs-lookup"><span data-stu-id="00aec-160">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.vb) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService/PrimeService.vb).</span></span>

<span data-ttu-id="00aec-161">Você criou uma pequena biblioteca e um conjunto de testes de unidade para essa biblioteca.</span><span class="sxs-lookup"><span data-stu-id="00aec-161">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="00aec-162">Você estruturou a solução para que a adição de novos pacotes e testes fizesse parte do fluxo de trabalho normal.</span><span class="sxs-lookup"><span data-stu-id="00aec-162">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="00aec-163">Você concentrou grande parte do seu tempo e esforço em resolver as metas do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="00aec-163">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
