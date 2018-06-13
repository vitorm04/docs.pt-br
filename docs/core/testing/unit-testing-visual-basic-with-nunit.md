---
title: Teste de unidade do Visual Basic no .NET Core usando dotnet test e NUnit
description: Aprenda os conceitos de teste de unidade no .NET Core por meio de uma experiência interativa de criação passo a passo de uma solução de exemplo do Visual Basic usando NUnit.
author: rprouse
ms.date: 12/01/2017
dev_langs:
- vb
ms.openlocfilehash: 552b60dd3937abc413c1b4410213948f3b509526
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33217770"
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-nunit"></a><span data-ttu-id="57be3-103">Teste de unidade de bibliotecas do .NET Core do Visual Basic usando dotnet test e NUnit</span><span class="sxs-lookup"><span data-stu-id="57be3-103">Unit testing Visual Basic .NET Core libraries using dotnet test and NUnit</span></span>

<span data-ttu-id="57be3-104">Este tutorial apresenta uma experiência interativa de compilação de uma solução de exemplo passo a passo para aprender os conceitos do teste de unidade.</span><span class="sxs-lookup"><span data-stu-id="57be3-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="57be3-105">Se você preferir acompanhar o tutorial usando uma solução interna, [veja ou baixe o exemplo de código](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-nunit/) antes de começar.</span><span class="sxs-lookup"><span data-stu-id="57be3-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-nunit/) before you begin.</span></span> <span data-ttu-id="57be3-106">Para obter instruções de download, consulte [Exemplos e tutoriais](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="57be3-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="57be3-107">Criando o projeto de origem</span><span class="sxs-lookup"><span data-stu-id="57be3-107">Creating the source project</span></span>

<span data-ttu-id="57be3-108">Abra uma janela do shell.</span><span class="sxs-lookup"><span data-stu-id="57be3-108">Open a shell window.</span></span> <span data-ttu-id="57be3-109">Crie um diretório chamado *unit-testing-vb-nunit* para armazenar a solução.</span><span class="sxs-lookup"><span data-stu-id="57be3-109">Create a directory called *unit-testing-vb-nunit* to hold the solution.</span></span> <span data-ttu-id="57be3-110">Nesse novo diretório, execute [`dotnet new sln`](../tools/dotnet-new.md) para criar uma nova solução.</span><span class="sxs-lookup"><span data-stu-id="57be3-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution.</span></span> <span data-ttu-id="57be3-111">Essa prática facilita gerenciar a biblioteca de classes e o projeto de teste de unidade.</span><span class="sxs-lookup"><span data-stu-id="57be3-111">This practice makes it easier to manage both the class library and the unit test project.</span></span> <span data-ttu-id="57be3-112">No diretório da solução, crie um diretório *PrimeService*.</span><span class="sxs-lookup"><span data-stu-id="57be3-112">Inside the solution directory, create a *PrimeService* directory.</span></span> <span data-ttu-id="57be3-113">Você tem a seguinte estrutura de arquivo e diretório até aqui:</span><span class="sxs-lookup"><span data-stu-id="57be3-113">You have the following directory and file structure thus far:</span></span>

```
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
```

<span data-ttu-id="57be3-114">Torne *PrimeService* o diretório atual e execute [`dotnet new classlib -lang VB`](../tools/dotnet-new.md) para criar o projeto de origem.</span><span class="sxs-lookup"><span data-stu-id="57be3-114">Make *PrimeService* the current directory and run [`dotnet new classlib -lang VB`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="57be3-115">Renomeie *Class1.VB* para *PrimeService.VB*.</span><span class="sxs-lookup"><span data-stu-id="57be3-115">Rename *Class1.VB* to *PrimeService.VB*.</span></span> <span data-ttu-id="57be3-116">Para usar o TDD (Desenvolvimento Orientado por Testes), você cria uma implementação com falha da classe `PrimeService`:</span><span class="sxs-lookup"><span data-stu-id="57be3-116">To use test-driven development (TDD), you create a failing implementation of the `PrimeService` class:</span></span>

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

<span data-ttu-id="57be3-117">Altere o diretório de volta para o diretório *unit-testing-vb-using-stest*.</span><span class="sxs-lookup"><span data-stu-id="57be3-117">Change the directory back to the *unit-testing-vb-using-stest* directory.</span></span> <span data-ttu-id="57be3-118">Execute [`dotnet sln add .\PrimeService\PrimeService.vbproj`](../tools/dotnet-sln.md) para adicionar o projeto de biblioteca de classes à solução.</span><span class="sxs-lookup"><span data-stu-id="57be3-118">Run [`dotnet sln add .\PrimeService\PrimeService.vbproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="install-the-nunit-project-template"></a><span data-ttu-id="57be3-119">Instalar o modelo de projeto do NUnit</span><span class="sxs-lookup"><span data-stu-id="57be3-119">Install the NUnit project template</span></span>

<span data-ttu-id="57be3-120">Os modelos de projeto de teste do NUnit precisam ser instalados antes de criar um projeto de teste.</span><span class="sxs-lookup"><span data-stu-id="57be3-120">The NUnit test project templates need to be installed before creating a test project.</span></span> <span data-ttu-id="57be3-121">Isso precisa ser feito somente uma vez em cada computador de desenvolvedor em que você criará novos projetos NUnit.</span><span class="sxs-lookup"><span data-stu-id="57be3-121">This only needs to be done once on each developer machine where you'll create new NUnit projects.</span></span> <span data-ttu-id="57be3-122">Execute [`dotnet new -i NUnit3.DotNetNew.Template`](../tools/dotnet-new.md) para instalar os modelos do NUnit.</span><span class="sxs-lookup"><span data-stu-id="57be3-122">Run [`dotnet new -i NUnit3.DotNetNew.Template`](../tools/dotnet-new.md) to install the NUnit templates.</span></span>

 ```
 dotnet new -i NUnit3.DotNetNew.Template
 ```

## <a name="creating-the-test-project"></a><span data-ttu-id="57be3-123">Criando o projeto de teste</span><span class="sxs-lookup"><span data-stu-id="57be3-123">Creating the test project</span></span>

<span data-ttu-id="57be3-124">Em seguida, crie o diretório *PrimeService.Tests*.</span><span class="sxs-lookup"><span data-stu-id="57be3-124">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="57be3-125">O seguinte esquema mostra a estrutura do diretório:</span><span class="sxs-lookup"><span data-stu-id="57be3-125">The following outline shows the directory structure:</span></span>

```
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

<span data-ttu-id="57be3-126">Torne o diretório *PrimeService.Tests* o diretório atual e crie um novo projeto usando [`dotnet new nunit -lang VB`](../tools/dotnet-new.md).</span><span class="sxs-lookup"><span data-stu-id="57be3-126">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new nunit -lang VB`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="57be3-127">Esse comando cria um projeto de teste que usa o NUnit como a biblioteca de teste.</span><span class="sxs-lookup"><span data-stu-id="57be3-127">This command creates a test project that uses NUnit as the test library.</span></span> <span data-ttu-id="57be3-128">O modelo gerado configura o executor de teste no *PrimeServiceTests.vbproj*:</span><span class="sxs-lookup"><span data-stu-id="57be3-128">The generated template configures the test runner in the *PrimeServiceTests.vbproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.5.0" />
  <PackageReference Include="NUnit" Version="3.9.0" />
  <PackageReference Include="NUnit3TestAdapter" Version="3.9.0" />
</ItemGroup>
```

<span data-ttu-id="57be3-129">O projeto de teste requer outros pacotes para criar e executar testes de unidade.</span><span class="sxs-lookup"><span data-stu-id="57be3-129">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="57be3-130">O `dotnet new` na etapa anterior adicionou o NUnit e o adaptador de teste do NUnit.</span><span class="sxs-lookup"><span data-stu-id="57be3-130">`dotnet new` in the previous step added NUnit and the NUnit test adapter.</span></span> <span data-ttu-id="57be3-131">Agora, adicione a biblioteca de classes `PrimeService` como outra dependência ao projeto.</span><span class="sxs-lookup"><span data-stu-id="57be3-131">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="57be3-132">Use o comando [`dotnet add reference`](../tools/dotnet-add-reference.md):</span><span class="sxs-lookup"><span data-stu-id="57be3-132">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../PrimeService/PrimeService.vbproj
```

<span data-ttu-id="57be3-133">Você pode ver o arquivo inteiro no [repositório de exemplos](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService.Tests.vbproj) no GitHub.</span><span class="sxs-lookup"><span data-stu-id="57be3-133">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService.Tests.vbproj) on GitHub.</span></span>

<span data-ttu-id="57be3-134">Você tem o seguinte layout de solução final:</span><span class="sxs-lookup"><span data-stu-id="57be3-134">You have the following final solution layout:</span></span>

```
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.vbproj
```

<span data-ttu-id="57be3-135">Execute [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj`](../tools/dotnet-sln.md) no diretório *unit-testing-vb-nunit*.</span><span class="sxs-lookup"><span data-stu-id="57be3-135">Execute [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj`](../tools/dotnet-sln.md) in the *unit-testing-vb-nunit* directory.</span></span>

## <a name="creating-the-first-test"></a><span data-ttu-id="57be3-136">Criando o primeiro teste</span><span class="sxs-lookup"><span data-stu-id="57be3-136">Creating the first test</span></span>

<span data-ttu-id="57be3-137">A abordagem de TDD pede a criação de um teste com falha para fazê-lo passar e depois a repetição do processo.</span><span class="sxs-lookup"><span data-stu-id="57be3-137">The TDD approach calls for writing one failing test, making it pass, then repeating the process.</span></span> <span data-ttu-id="57be3-138">Remova *UnitTest1.vb* do diretório *PrimeService.Tests* e crie um novo arquivo do Visual Basic chamado *PrimeService_IsPrimeShould.VB*.</span><span class="sxs-lookup"><span data-stu-id="57be3-138">Remove *UnitTest1.vb* from the *PrimeService.Tests* directory and create a new Visual Basic file named *PrimeService_IsPrimeShould.VB*.</span></span> <span data-ttu-id="57be3-139">Adicione o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="57be3-139">Add the following code:</span></span>

```vb
Imports NUnit.Framework

Namespace PrimeService.Tests
    <TestFixture>
    Public Class PrimeService_IsPrimeShould
        Private _primeService As Prime.Services.PrimeService = New Prime.Services.PrimeService()

        <Test>
        Sub ReturnFalseGivenValueOf1()
            Dim result As Boolean = _primeService.IsPrime(1)

            Assert.False(result, "1 should not be prime")
        End Sub

    End Class
End Namespace
```

<span data-ttu-id="57be3-140">O atributo `<TestFixture>` indica uma classe que contém testes.</span><span class="sxs-lookup"><span data-stu-id="57be3-140">The `<TestFixture>` attribute indicates a class that contains tests.</span></span> <span data-ttu-id="57be3-141">O atributo `<Test>` indica um método que é executado pelo executor de teste.</span><span class="sxs-lookup"><span data-stu-id="57be3-141">The `<Test>` attribute denotes a method that is run by the test runner.</span></span> <span data-ttu-id="57be3-142">Em *unit-testing-vb-nunit*, execute [`dotnet test`](../tools/dotnet-test.md) para criar os testes e a biblioteca de classes e, em seguida, execute os testes.</span><span class="sxs-lookup"><span data-stu-id="57be3-142">From the *unit-testing-vb-nunit*, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="57be3-143">O executor de teste do NUnit contém o ponto de entrada do programa para executar os testes.</span><span class="sxs-lookup"><span data-stu-id="57be3-143">The NUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="57be3-144">`dotnet test` inicia o executor de teste usando o projeto de teste de unidade que você criou.</span><span class="sxs-lookup"><span data-stu-id="57be3-144">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="57be3-145">O teste falha.</span><span class="sxs-lookup"><span data-stu-id="57be3-145">Your test fails.</span></span> <span data-ttu-id="57be3-146">Você ainda não criou a implementação.</span><span class="sxs-lookup"><span data-stu-id="57be3-146">You haven't created the implementation yet.</span></span> <span data-ttu-id="57be3-147">Faça esse teste escrevendo o código mais simples na classe `PrimeService` que funciona:</span><span class="sxs-lookup"><span data-stu-id="57be3-147">Make this test by writing the simplest code in the `PrimeService` class that works:</span></span>

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first")
End Function
```

<span data-ttu-id="57be3-148">No diretório *unit-testing-vb-nunit*, execute `dotnet test` novamente.</span><span class="sxs-lookup"><span data-stu-id="57be3-148">In the *unit-testing-vb-nunit* directory, run `dotnet test` again.</span></span> <span data-ttu-id="57be3-149">O comando `dotnet test` executa uma compilação para o projeto `PrimeService` e, depois, para o projeto `PrimeService.Tests`.</span><span class="sxs-lookup"><span data-stu-id="57be3-149">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="57be3-150">Depois de compilar os dois projetos, ele executará esse teste único.</span><span class="sxs-lookup"><span data-stu-id="57be3-150">After building both projects, it runs this single test.</span></span> <span data-ttu-id="57be3-151">Ele é aprovado.</span><span class="sxs-lookup"><span data-stu-id="57be3-151">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="57be3-152">Adicionando mais recursos</span><span class="sxs-lookup"><span data-stu-id="57be3-152">Adding more features</span></span>

<span data-ttu-id="57be3-153">Agora que você fez um teste ser aprovado, é hora de escrever mais.</span><span class="sxs-lookup"><span data-stu-id="57be3-153">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="57be3-154">Existem alguns outros casos simples de números primos: 0, -1.</span><span class="sxs-lookup"><span data-stu-id="57be3-154">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="57be3-155">Você pode adicionar esses casos como novos testes com o atributo `<Test>`, mas isso se torna entediante rapidamente.</span><span class="sxs-lookup"><span data-stu-id="57be3-155">You could add those cases as new tests with the `<Test>` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="57be3-156">Há outros atributos de xUnit que permitem escrever um pacote de testes semelhantes.</span><span class="sxs-lookup"><span data-stu-id="57be3-156">There are other xUnit attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="57be3-157">Um atributo `<TestCase>` representa um pacote de testes que executa o mesmo código, mas têm diferentes argumentos de entrada.</span><span class="sxs-lookup"><span data-stu-id="57be3-157">A `<TestCase>` attribute represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="57be3-158">Você pode usar o atributo `<TestCase>` para especificar valores para essas entradas.</span><span class="sxs-lookup"><span data-stu-id="57be3-158">You can use the `<TestCase>` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="57be3-159">Em vez de criar novos testes, aplique esses dois atributos para criar uma série de testes que testa diversos valores menores que dois, que é o menor número primo:</span><span class="sxs-lookup"><span data-stu-id="57be3-159">Instead of creating new tests, apply these two attributes to create a series of tests that test several values less than two, which is the lowest prime number:</span></span>

[!code-vb[Sample_TestCode](../../../samples/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

<span data-ttu-id="57be3-160">Execute `dotnet test`, e dois desses testes falham.</span><span class="sxs-lookup"><span data-stu-id="57be3-160">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="57be3-161">Para fazer todos os testes serem aprovados, altere a cláusula `if` no início do método:</span><span class="sxs-lookup"><span data-stu-id="57be3-161">To make all of the tests pass, change the `if` clause at the beginning of the method:</span></span>

```vb
if candidate < 2
```

<span data-ttu-id="57be3-162">Continue iterando adicionando mais testes, mais teorias e mais código na biblioteca principal.</span><span class="sxs-lookup"><span data-stu-id="57be3-162">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="57be3-163">Você tem a [versão concluída dos testes](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb) e a [implementação completa da biblioteca](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService/PrimeService.vb).</span><span class="sxs-lookup"><span data-stu-id="57be3-163">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService/PrimeService.vb).</span></span>

<span data-ttu-id="57be3-164">Você criou uma pequena biblioteca e um conjunto de testes de unidade para essa biblioteca.</span><span class="sxs-lookup"><span data-stu-id="57be3-164">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="57be3-165">Você estruturou a solução para que a adição de novos pacotes e testes fizesse parte do fluxo de trabalho normal.</span><span class="sxs-lookup"><span data-stu-id="57be3-165">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="57be3-166">Você concentrou grande parte do seu tempo e esforço em resolver as metas do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="57be3-166">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
