---
title: Teste de unidade com o Visual Basic no .NET Core usando dotnet test e xUnit
description: "Aprenda os conceitos de teste de unidade no .NET Core por meio de uma experiência interativa de criação passo a passo de uma solução de exemplo do Visual Basic usando dotnet test e xUnit."
author: billwagner
ms.author: wiwagn
ms.date: 09/01/2017
ms.topic: article
dev_langs:
- vb
ms.prod: .net-core
ms.workload:
- dotnetcore
ms.openlocfilehash: 01922e3ad3b19e13ebea755decf21c6b09e4be37
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-xunit"></a><span data-ttu-id="43c9e-103">Bibliotecas do .NET Core no Visual Basic de teste de unidade usando dotnet test e xUnit</span><span class="sxs-lookup"><span data-stu-id="43c9e-103">Unit testing Visual Basic .NET Core libraries using dotnet test and xUnit</span></span>

<span data-ttu-id="43c9e-104">Este tutorial apresenta uma experiência interativa de compilação de uma solução de exemplo passo a passo para aprender os conceitos do teste de unidade.</span><span class="sxs-lookup"><span data-stu-id="43c9e-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="43c9e-105">Se você preferir acompanhar o tutorial usando uma solução interna, [veja ou baixe o exemplo de código](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/unit-testing-using-dotnet-test/) antes de começar.</span><span class="sxs-lookup"><span data-stu-id="43c9e-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/unit-testing-using-dotnet-test/) before you begin.</span></span> <span data-ttu-id="43c9e-106">Para obter instruções de download, consulte [Exemplos e tutoriais](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="43c9e-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="43c9e-107">Criando o projeto de origem</span><span class="sxs-lookup"><span data-stu-id="43c9e-107">Creating the source project</span></span>

<span data-ttu-id="43c9e-108">Abra uma janela do shell.</span><span class="sxs-lookup"><span data-stu-id="43c9e-108">Open a shell window.</span></span> <span data-ttu-id="43c9e-109">Crie um diretório chamado *unit-testing-vb-using-dotnet-test* para armazenar a solução.</span><span class="sxs-lookup"><span data-stu-id="43c9e-109">Create a directory called *unit-testing-vb-using-dotnet-test* to hold the solution.</span></span>
<span data-ttu-id="43c9e-110">Nesse novo diretório, execute [`dotnet new sln`](../tools/dotnet-new.md) para criar uma nova solução.</span><span class="sxs-lookup"><span data-stu-id="43c9e-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution.</span></span> <span data-ttu-id="43c9e-111">Essa prática facilita gerenciar a biblioteca de classes e o projeto de teste de unidade.</span><span class="sxs-lookup"><span data-stu-id="43c9e-111">This practice makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="43c9e-112">No diretório da solução, crie um diretório *PrimeService*.</span><span class="sxs-lookup"><span data-stu-id="43c9e-112">Inside the solution directory, create a *PrimeService* directory.</span></span> <span data-ttu-id="43c9e-113">Você tem a seguinte estrutura de arquivo e diretório até aqui:</span><span class="sxs-lookup"><span data-stu-id="43c9e-113">You have the following directory and file structure thus far:</span></span>

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
```

<span data-ttu-id="43c9e-114">Torne *PrimeService* o diretório atual e execute [`dotnet new classlib -lang VB`](../tools/dotnet-new.md) para criar o projeto de origem.</span><span class="sxs-lookup"><span data-stu-id="43c9e-114">Make *PrimeService* the current directory and run [`dotnet new classlib -lang VB`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="43c9e-115">Renomeie *Class1.VB* para *PrimeService.VB*.</span><span class="sxs-lookup"><span data-stu-id="43c9e-115">Rename *Class1.VB* to *PrimeService.VB*.</span></span> <span data-ttu-id="43c9e-116">Para usar o TDD (Desenvolvimento Orientado por Testes), você cria uma implementação com falha da classe `PrimeService`:</span><span class="sxs-lookup"><span data-stu-id="43c9e-116">To use test-driven development (TDD), you create a failing implementation of the `PrimeService` class:</span></span>

```vb
Namespace Prime.Services
    Public Class PrimeService
        Public Function IsPrime(candidate As Integer) As Boolean
            Throw New NotImplementedException("Please create a test first")
        End Function
    End Class
End Namespace
```

<span data-ttu-id="43c9e-117">Altere o diretório de volta para o diretório *unit-testing-vb-using-dotnet-test*.</span><span class="sxs-lookup"><span data-stu-id="43c9e-117">Change the directory back to the *unit-testing-vb-using-dotnet-test* directory.</span></span> <span data-ttu-id="43c9e-118">Execute [`dotnet sln add .\PrimeService\PrimeService.vbproj`](../tools/dotnet-sln.md) para adicionar o projeto de biblioteca de classes à solução.</span><span class="sxs-lookup"><span data-stu-id="43c9e-118">Run [`dotnet sln add .\PrimeService\PrimeService.vbproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="creating-the-test-project"></a><span data-ttu-id="43c9e-119">Criando o projeto de teste</span><span class="sxs-lookup"><span data-stu-id="43c9e-119">Creating the test project</span></span>

<span data-ttu-id="43c9e-120">Em seguida, crie o diretório *PrimeService.Tests*.</span><span class="sxs-lookup"><span data-stu-id="43c9e-120">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="43c9e-121">O seguinte esquema mostra a estrutura do diretório:</span><span class="sxs-lookup"><span data-stu-id="43c9e-121">The following outline shows the directory structure:</span></span>

```
/unit-testing-vb-using-dotnet-test
    unit-testing-vb-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

<span data-ttu-id="43c9e-122">Torne o diretório *PrimeService.Tests* o diretório atual e crie um novo projeto usando [`dotnet new xunit -lang VB`](../tools/dotnet-new.md).</span><span class="sxs-lookup"><span data-stu-id="43c9e-122">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new xunit -lang VB`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="43c9e-123">Esse comando cria um projeto de teste que usa o xUnit como a biblioteca de teste.</span><span class="sxs-lookup"><span data-stu-id="43c9e-123">This command creates a test project that uses xUnit as the test library.</span></span> <span data-ttu-id="43c9e-124">O modelo gerado configura o executor de teste no *PrimeServiceTests.vbproj*:</span><span class="sxs-lookup"><span data-stu-id="43c9e-124">The generated template configures the test runner in the *PrimeServiceTests.vbproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

<span data-ttu-id="43c9e-125">O projeto de teste requer outros pacotes para criar e executar testes de unidade.</span><span class="sxs-lookup"><span data-stu-id="43c9e-125">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="43c9e-126">`dotnet new` na etapa anterior adicionou xUnit e o executor de xUnit.</span><span class="sxs-lookup"><span data-stu-id="43c9e-126">`dotnet new` in the previous step added xUnit and the xUnit runner.</span></span> <span data-ttu-id="43c9e-127">Agora, adicione a biblioteca de classes `PrimeService` como outra dependência ao projeto.</span><span class="sxs-lookup"><span data-stu-id="43c9e-127">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="43c9e-128">Use o comando [`dotnet add reference`](../tools/dotnet-add-reference.md):</span><span class="sxs-lookup"><span data-stu-id="43c9e-128">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../PrimeService/PrimeService.vbproj
```

<span data-ttu-id="43c9e-129">Você pode ver o arquivo inteiro no [repositório de exemplos](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-vb-using-dotnet-test/PrimeService.Tests/PrimeService.Tests.vbproj) no GitHub.</span><span class="sxs-lookup"><span data-stu-id="43c9e-129">You can see the entire file in the [samples repository](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-vb-using-dotnet-test/PrimeService.Tests/PrimeService.Tests.vbproj) on GitHub.</span></span>

<span data-ttu-id="43c9e-130">Você tem o seguinte layout de pasta final:</span><span class="sxs-lookup"><span data-stu-id="43c9e-130">You have the following final folder layout:</span></span>

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.vbproj
```

<span data-ttu-id="43c9e-131">Execute [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj`](../tools/dotnet-sln.md) no diretório *unit-testing-vb-using-dotnet-test*.</span><span class="sxs-lookup"><span data-stu-id="43c9e-131">Execute [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj`](../tools/dotnet-sln.md) in the *unit-testing-vb-using-dotnet-test* directory.</span></span> 

## <a name="creating-the-first-test"></a><span data-ttu-id="43c9e-132">Criando o primeiro teste</span><span class="sxs-lookup"><span data-stu-id="43c9e-132">Creating the first test</span></span>

<span data-ttu-id="43c9e-133">A abordagem de TDD pede a criação de um teste com falha para fazê-lo passar e depois a repetição do processo.</span><span class="sxs-lookup"><span data-stu-id="43c9e-133">The TDD approach calls for writing one failing test, making it pass, then repeating the process.</span></span> <span data-ttu-id="43c9e-134">Remova *UnitTest1.vb* do diretório *PrimeService.Tests* e crie um novo arquivo do Visual Basic chamado *PrimeService_IsPrimeShould.VB*.</span><span class="sxs-lookup"><span data-stu-id="43c9e-134">Remove *UnitTest1.vb* from the *PrimeService.Tests* directory and create a new Visual Basic file named *PrimeService_IsPrimeShould.VB*.</span></span> <span data-ttu-id="43c9e-135">Adicione o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="43c9e-135">Add the following code:</span></span>

```vb
Imports Xunit

Namespace PrimeService.Tests
    Public Class PrimeService_IsPrimeShould
        Private _primeService As Prime.Services.PrimeService = New Prime.Services.PrimeService()

        <Fact>
        Sub ReturnFalseGivenValueOf1()
            Dim result As Boolean = _primeService.IsPrime(1)

            Assert.False(result, "1 should not be prime")
        End Sub

    End Class
End Namespace
```

<span data-ttu-id="43c9e-136">O atributo `<Fact>` indica um método de teste que é executado pelo executor de teste.</span><span class="sxs-lookup"><span data-stu-id="43c9e-136">The `<Fact>` attribute denotes a test method that is run by the test runner.</span></span> <span data-ttu-id="43c9e-137">Em *unit-testing-using-dotnet-test*, execute [`dotnet test`](../tools/dotnet-test.md) para criar os testes e a biblioteca de classes e execute os testes.</span><span class="sxs-lookup"><span data-stu-id="43c9e-137">From the *unit-testing-using-dotnet-test*, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="43c9e-138">O executor de teste do xUnit contém o ponto de entrada do programa para executar os testes.</span><span class="sxs-lookup"><span data-stu-id="43c9e-138">The xUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="43c9e-139">`dotnet test` inicia o executor de teste usando o projeto de teste de unidade que você criou.</span><span class="sxs-lookup"><span data-stu-id="43c9e-139">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="43c9e-140">O teste falha.</span><span class="sxs-lookup"><span data-stu-id="43c9e-140">Your test fails.</span></span> <span data-ttu-id="43c9e-141">Você ainda não criou a implementação.</span><span class="sxs-lookup"><span data-stu-id="43c9e-141">You haven't created the implementation yet.</span></span> <span data-ttu-id="43c9e-142">Faça esse teste escrevendo o código mais simples na classe `PrimeService` que funciona:</span><span class="sxs-lookup"><span data-stu-id="43c9e-142">Make this test by writing the simplest code in the `PrimeService` class that works:</span></span>

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first")
End Function
```

<span data-ttu-id="43c9e-143">No diretório *unit-testing-vb-using-dotnet-test*, execute `dotnet test` novamente.</span><span class="sxs-lookup"><span data-stu-id="43c9e-143">In the *unit-testing-vb-using-dotnet-test* directory, run `dotnet test` again.</span></span> <span data-ttu-id="43c9e-144">O comando `dotnet test` executa uma compilação para o projeto `PrimeService` e, depois, para o projeto `PrimeService.Tests`.</span><span class="sxs-lookup"><span data-stu-id="43c9e-144">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="43c9e-145">Depois de compilar os dois projetos, ele executará esse teste único.</span><span class="sxs-lookup"><span data-stu-id="43c9e-145">After building both projects, it runs this single test.</span></span> <span data-ttu-id="43c9e-146">Ele é aprovado.</span><span class="sxs-lookup"><span data-stu-id="43c9e-146">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="43c9e-147">Adicionando mais recursos</span><span class="sxs-lookup"><span data-stu-id="43c9e-147">Adding more features</span></span>

<span data-ttu-id="43c9e-148">Agora que você fez um teste ser aprovado, é hora de escrever mais.</span><span class="sxs-lookup"><span data-stu-id="43c9e-148">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="43c9e-149">Existem alguns outros casos simples de números primos: 0, -1.</span><span class="sxs-lookup"><span data-stu-id="43c9e-149">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="43c9e-150">Você pode adicionar esses casos como novos testes com o atributo `<Fact>`, mas isso se torna entediante rapidamente.</span><span class="sxs-lookup"><span data-stu-id="43c9e-150">You could add those cases as new tests with the `<Fact>` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="43c9e-151">Há outros atributos de xUnit que permitem escrever um pacote de testes semelhantes.</span><span class="sxs-lookup"><span data-stu-id="43c9e-151">There are other xUnit attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="43c9e-152">Um atributo `<Theory>` representa um pacote de testes que executa o mesmo código, mas têm diferentes argumentos de entrada.</span><span class="sxs-lookup"><span data-stu-id="43c9e-152">A `<Theory>` attribute represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="43c9e-153">Você pode usar o atributo `<InlineData>` para especificar valores para essas entradas.</span><span class="sxs-lookup"><span data-stu-id="43c9e-153">You can use the `<InlineData>` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="43c9e-154">Em vez de criar novos testes, aplique esses dois atributos para criar uma única teoria.</span><span class="sxs-lookup"><span data-stu-id="43c9e-154">Instead of creating new tests, apply these two attributes to create a single theory.</span></span> <span data-ttu-id="43c9e-155">A teoria é um método que testa vários valores inferiores a dois, que é o número primo mais baixo:</span><span class="sxs-lookup"><span data-stu-id="43c9e-155">The theory is a method that tests several values less than two, which is the lowest prime number:</span></span>

[!code-vb[Sample_TestCode](../../../samples/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

<span data-ttu-id="43c9e-156">Execute `dotnet test`, e dois desses testes falham.</span><span class="sxs-lookup"><span data-stu-id="43c9e-156">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="43c9e-157">Para fazer todos os testes serem aprovados, altere a cláusula `if` no início do método:</span><span class="sxs-lookup"><span data-stu-id="43c9e-157">To make all of the tests pass, change the `if` clause at the beginning of the method:</span></span>

```vb
if candidate < 2
```

<span data-ttu-id="43c9e-158">Continue iterando adicionando mais testes, mais teorias e mais código na biblioteca principal.</span><span class="sxs-lookup"><span data-stu-id="43c9e-158">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="43c9e-159">Você tem a [versão concluída dos testes](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-vb-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.vb) e a [implementação completa da biblioteca](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-vb-using-dotnet-test/PrimeService/PrimeService.vb).</span><span class="sxs-lookup"><span data-stu-id="43c9e-159">You have the [finished version of the tests](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-vb-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.vb) and the [complete implementation of the library](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-vb-using-dotnet-test/PrimeService/PrimeService.vb).</span></span>

<span data-ttu-id="43c9e-160">Você criou uma pequena biblioteca e um conjunto de testes de unidade para essa biblioteca.</span><span class="sxs-lookup"><span data-stu-id="43c9e-160">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="43c9e-161">Você estruturou a solução para que a adição de novos pacotes e testes fizesse parte do fluxo de trabalho normal.</span><span class="sxs-lookup"><span data-stu-id="43c9e-161">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="43c9e-162">Você concentrou grande parte do seu tempo e esforço em resolver as metas do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="43c9e-162">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
