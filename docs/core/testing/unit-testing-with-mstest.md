---
title: C# de teste de unidade com MSTest e .NET Core
description: Aprenda os conceitos de teste de unidade no C# e .NET Core por meio de uma experiência interativa de criação passo a passo de uma solução de exemplo usando dotnet test e MSTest.
author: ncarandini
ms.author: wiwagn
ms.date: 09/08/2017
ms.custom: seodec18
ms.openlocfilehash: f6c1580d3f596c638969e668a87ee70d75e6d9bf
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68626392"
---
# <a name="unit-testing-c-with-mstest-and-net-core"></a><span data-ttu-id="2925e-103">C# de teste de unidade com MSTest e .NET Core</span><span class="sxs-lookup"><span data-stu-id="2925e-103">Unit testing C# with MSTest and .NET Core</span></span>

<span data-ttu-id="2925e-104">Este tutorial apresenta uma experiência interativa de compilação de uma solução de exemplo passo a passo para aprender os conceitos do teste de unidade.</span><span class="sxs-lookup"><span data-stu-id="2925e-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="2925e-105">Se você preferir acompanhar o tutorial usando uma solução interna, [veja ou baixe o exemplo de código](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/) antes de começar.</span><span class="sxs-lookup"><span data-stu-id="2925e-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/) before you begin.</span></span> <span data-ttu-id="2925e-106">Para obter instruções de download, consulte [Exemplos e tutoriais](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="2925e-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

### <a name="create-the-source-project"></a><span data-ttu-id="2925e-107">Crie o projeto de origem</span><span class="sxs-lookup"><span data-stu-id="2925e-107">Create the source project</span></span>

<span data-ttu-id="2925e-108">Abra uma janela do shell.</span><span class="sxs-lookup"><span data-stu-id="2925e-108">Open a shell window.</span></span> <span data-ttu-id="2925e-109">Crie um diretório chamado *unit-testing-using-mstest* no qual manter a solução.</span><span class="sxs-lookup"><span data-stu-id="2925e-109">Create a directory called *unit-testing-using-mstest* to hold the solution.</span></span> <span data-ttu-id="2925e-110">Nesse diretório, execute [`dotnet new sln`](../tools/dotnet-new.md) a fim de criar um novo arquivo de solução para a biblioteca de classes e o projeto de teste.</span><span class="sxs-lookup"><span data-stu-id="2925e-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution file for the class library and the test project.</span></span> <span data-ttu-id="2925e-111">Em seguida, crie um diretório *PrimeService*.</span><span class="sxs-lookup"><span data-stu-id="2925e-111">Next, create a *PrimeService* directory.</span></span> <span data-ttu-id="2925e-112">O seguinte esquema mostra a estrutura de arquivo e diretório até aqui:</span><span class="sxs-lookup"><span data-stu-id="2925e-112">The following outline shows the directory and file structure thus far:</span></span>

```
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
```

<span data-ttu-id="2925e-113">Torne *PrimeService* o diretório atual e execute [`dotnet new classlib`](../tools/dotnet-new.md) para criar o projeto de origem.</span><span class="sxs-lookup"><span data-stu-id="2925e-113">Make *PrimeService* the current directory and run [`dotnet new classlib`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="2925e-114">Renomeie *Class1.cs* como *PrimeService.cs*.</span><span class="sxs-lookup"><span data-stu-id="2925e-114">Rename *Class1.cs* to *PrimeService.cs*.</span></span> <span data-ttu-id="2925e-115">Crie uma implementação com falha da classe `PrimeService`:</span><span class="sxs-lookup"><span data-stu-id="2925e-115">You create a failing implementation of the `PrimeService` class:</span></span>

```csharp
using System;

namespace Prime.Services
{
    public class PrimeService
    {
        public bool IsPrime(int candidate) 
        {
            throw new NotImplementedException("Please create a test first.");
        } 
    }
}
```

<span data-ttu-id="2925e-116">Altere o diretório de volta para o diretório *unit-testing-using-mstest*.</span><span class="sxs-lookup"><span data-stu-id="2925e-116">Change the directory back to the *unit-testing-using-mstest* directory.</span></span> <span data-ttu-id="2925e-117">Execute [`dotnet sln add PrimeService/PrimeService.csproj`](../tools/dotnet-sln.md) para adicionar o projeto de biblioteca de classes à solução.</span><span class="sxs-lookup"><span data-stu-id="2925e-117">Run [`dotnet sln add PrimeService/PrimeService.csproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span> 

### <a name="create-the-test-project"></a><span data-ttu-id="2925e-118">Criar um projeto de teste</span><span class="sxs-lookup"><span data-stu-id="2925e-118">Create the test project</span></span>

<span data-ttu-id="2925e-119">Em seguida, crie o diretório *PrimeService.Tests*.</span><span class="sxs-lookup"><span data-stu-id="2925e-119">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="2925e-120">O seguinte esquema mostra a estrutura do diretório:</span><span class="sxs-lookup"><span data-stu-id="2925e-120">The following outline shows the directory structure:</span></span>

```
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

<span data-ttu-id="2925e-121">Torne o diretório *PrimeService.Tests* o diretório atual e crie um novo projeto usando [`dotnet new mstest`](../tools/dotnet-new.md).</span><span class="sxs-lookup"><span data-stu-id="2925e-121">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new mstest`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="2925e-122">O comando dotnet new cria um projeto de teste que usa o MSTest como a biblioteca de teste.</span><span class="sxs-lookup"><span data-stu-id="2925e-122">The dotnet new command creates a test project that uses MSTest as the test library.</span></span> <span data-ttu-id="2925e-123">O modelo gerado configura o executor de teste no arquivo *PrimeServiceTests.csproj*:</span><span class="sxs-lookup"><span data-stu-id="2925e-123">The generated template configures the test runner in the *PrimeServiceTests.csproj* file:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.18" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.18" />
</ItemGroup>
```

<span data-ttu-id="2925e-124">O projeto de teste requer outros pacotes para criar e executar testes de unidade.</span><span class="sxs-lookup"><span data-stu-id="2925e-124">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="2925e-125">`dotnet new` da etapa anterior adicionou o SDK do MSTest, a estrutura de teste do MSTest e o executor do MSTest.</span><span class="sxs-lookup"><span data-stu-id="2925e-125">`dotnet new` in the previous step added the MSTest SDK, the MSTest test framework, and the MSTest runner.</span></span> <span data-ttu-id="2925e-126">Agora, adicione a biblioteca de classes `PrimeService` como outra dependência ao projeto.</span><span class="sxs-lookup"><span data-stu-id="2925e-126">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="2925e-127">Use o comando [`dotnet add reference`](../tools/dotnet-add-reference.md):</span><span class="sxs-lookup"><span data-stu-id="2925e-127">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../PrimeService/PrimeService.csproj
```

<span data-ttu-id="2925e-128">Você pode ver o arquivo inteiro no [repositório de exemplos](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService.Tests.csproj) no GitHub.</span><span class="sxs-lookup"><span data-stu-id="2925e-128">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService.Tests.csproj) on GitHub.</span></span>

<span data-ttu-id="2925e-129">O seguinte esquema mostra o layout da solução final:</span><span class="sxs-lookup"><span data-stu-id="2925e-129">The following outline shows the final solution layout:</span></span>

```
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.csproj
```

<span data-ttu-id="2925e-130">Execute [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj`](../tools/dotnet-sln.md) no diretório *unit-testing-using-mstest*.</span><span class="sxs-lookup"><span data-stu-id="2925e-130">Execute [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj`](../tools/dotnet-sln.md) in the *unit-testing-using-mstest* directory.</span></span> 

## <a name="create-the-first-test"></a><span data-ttu-id="2925e-131">Crie o primeiro teste</span><span class="sxs-lookup"><span data-stu-id="2925e-131">Create the first test</span></span>

<span data-ttu-id="2925e-132">Escreva um teste com falha, faça-o ser aprovado e, em seguida, repita o processo.</span><span class="sxs-lookup"><span data-stu-id="2925e-132">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="2925e-133">Remova *UnitTest1.cs* do diretório *PrimeService.Tests* e crie um novo arquivo C# chamado *PrimeService_IsPrimeShould.cs* com o seguinte conteúdo:</span><span class="sxs-lookup"><span data-stu-id="2925e-133">Remove *UnitTest1.cs* from the *PrimeService.Tests* directory and create a new C# file named *PrimeService_IsPrimeShould.cs* with the following content:</span></span>

```csharp
using Microsoft.VisualStudio.TestTools.UnitTesting;
using Prime.Services;

namespace Prime.UnitTests.Services
{
    [TestClass]
    public class PrimeService_IsPrimeShould
    {
        private readonly PrimeService _primeService;

        public PrimeService_IsPrimeShould()
        {
            _primeService = new PrimeService();
        }

        [TestMethod]
        public void IsPrime_InputIs1_ReturnFalse()
        {
            var result = _primeService.IsPrime(1);

            Assert.IsFalse(result, "1 should not be prime");
        }
    }
}
```

<span data-ttu-id="2925e-134">O [atributo TestClass](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) indica uma classe que contém testes de unidade.</span><span class="sxs-lookup"><span data-stu-id="2925e-134">The [TestClass attribute](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) denotes a class that contains unit tests.</span></span> <span data-ttu-id="2925e-135">O [atributo TestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) indica um método que é um método de teste.</span><span class="sxs-lookup"><span data-stu-id="2925e-135">The [TestMethod attribute](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) indicates a method is a test method.</span></span> 

<span data-ttu-id="2925e-136">Salve esse arquivo e execute [`dotnet test`](../tools/dotnet-test.md) para compilar os testes e a biblioteca de classes e, em seguida, execute os testes.</span><span class="sxs-lookup"><span data-stu-id="2925e-136">Save this file and execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="2925e-137">O executor de teste do MSTest contém o ponto de entrada do programa para executar os testes.</span><span class="sxs-lookup"><span data-stu-id="2925e-137">The MSTest test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="2925e-138">`dotnet test` inicia o executor de teste usando o projeto de teste de unidade que você criou.</span><span class="sxs-lookup"><span data-stu-id="2925e-138">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="2925e-139">O teste falha.</span><span class="sxs-lookup"><span data-stu-id="2925e-139">Your test fails.</span></span> <span data-ttu-id="2925e-140">Você ainda não criou a implementação.</span><span class="sxs-lookup"><span data-stu-id="2925e-140">You haven't created the implementation yet.</span></span> <span data-ttu-id="2925e-141">Faça esse teste ser aprovado escrevendo o código mais simples na classe `PrimeService` que funciona:</span><span class="sxs-lookup"><span data-stu-id="2925e-141">Make this test pass by writing the simplest code in the `PrimeService` class that works:</span></span>

```csharp
public bool IsPrime(int candidate)
{
    if (candidate == 1)
    {
        return false;
    }
    throw new NotImplementedException("Please create a test first.");
}
```

<span data-ttu-id="2925e-142">No diretório *unit-testing-using-mstest*, execute `dotnet test` novamente.</span><span class="sxs-lookup"><span data-stu-id="2925e-142">In the *unit-testing-using-mstest* directory, run `dotnet test` again.</span></span> <span data-ttu-id="2925e-143">O comando `dotnet test` executa uma compilação para o projeto `PrimeService` e, depois, para o projeto `PrimeService.Tests`.</span><span class="sxs-lookup"><span data-stu-id="2925e-143">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="2925e-144">Depois de compilar os dois projetos, ele executará esse teste único.</span><span class="sxs-lookup"><span data-stu-id="2925e-144">After building both projects, it runs this single test.</span></span> <span data-ttu-id="2925e-145">Ele é aprovado.</span><span class="sxs-lookup"><span data-stu-id="2925e-145">It passes.</span></span>

## <a name="add-more-features"></a><span data-ttu-id="2925e-146">Adicionar mais recursos</span><span class="sxs-lookup"><span data-stu-id="2925e-146">Add more features</span></span>

<span data-ttu-id="2925e-147">Agora que você fez um teste ser aprovado, é hora de escrever mais.</span><span class="sxs-lookup"><span data-stu-id="2925e-147">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="2925e-148">Existem alguns outros casos simples de números primos: 0 e -1.</span><span class="sxs-lookup"><span data-stu-id="2925e-148">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="2925e-149">Você pode adicionar novos testes com o [atributo TestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute), mas isso se torna rapidamente entediante.</span><span class="sxs-lookup"><span data-stu-id="2925e-149">You could add new tests with the [TestMethod attribute](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute), but that quickly becomes tedious.</span></span> <span data-ttu-id="2925e-150">Há outros atributos do MSTest que permitem escrever um pacote de testes semelhantes.</span><span class="sxs-lookup"><span data-stu-id="2925e-150">There are other MSTest attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="2925e-151">Um [atributo DataTestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataTestMethodAttribute) representa um pacote de testes que executa o mesmo código, mas com diferentes argumentos de entrada.</span><span class="sxs-lookup"><span data-stu-id="2925e-151">A [DataTestMethod attribute](xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataTestMethodAttribute) represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="2925e-152">Você pode usar o [atributo DataRow](xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataRowAttribute) para especificar valores para essas entradas.</span><span class="sxs-lookup"><span data-stu-id="2925e-152">You can use the [DataRow attribute](xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataRowAttribute) to specify values for those inputs.</span></span>

<span data-ttu-id="2925e-153">Em vez de criar novos testes, aplique esses dois atributos para criar um único teste orientado a dados.</span><span class="sxs-lookup"><span data-stu-id="2925e-153">Instead of creating new tests, apply these two attributes to create a single data driven test.</span></span> <span data-ttu-id="2925e-154">O teste controlado por dados é um método que testa vários valores menores que dois, que é o menor número primo:</span><span class="sxs-lookup"><span data-stu-id="2925e-154">The data driven test is a method that tests several values less than two, which is the lowest prime number:</span></span>

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

<span data-ttu-id="2925e-155">Execute `dotnet test`, e dois desses testes falham.</span><span class="sxs-lookup"><span data-stu-id="2925e-155">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="2925e-156">Para fazer todos os testes serem aprovados, altere a cláusula `if` no início do método:</span><span class="sxs-lookup"><span data-stu-id="2925e-156">To make all of the tests pass, change the `if` clause at the beginning of the method:</span></span>

```csharp
if (candidate < 2)
```

<span data-ttu-id="2925e-157">Continue iterando adicionando mais testes, mais teorias e mais código na biblioteca principal.</span><span class="sxs-lookup"><span data-stu-id="2925e-157">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="2925e-158">Você tem a [versão concluída dos testes](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs) e a [implementação completa da biblioteca](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService/PrimeService.cs).</span><span class="sxs-lookup"><span data-stu-id="2925e-158">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService/PrimeService.cs).</span></span>

<span data-ttu-id="2925e-159">Você criou uma pequena biblioteca e um conjunto de testes de unidade para essa biblioteca.</span><span class="sxs-lookup"><span data-stu-id="2925e-159">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="2925e-160">Você estruturou a solução para que a adição de novos pacotes e testes fizesse parte do fluxo de trabalho normal.</span><span class="sxs-lookup"><span data-stu-id="2925e-160">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="2925e-161">Você concentrou grande parte do seu tempo e esforço em resolver as metas do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2925e-161">You've concentrated most of your time and effort on solving the goals of the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="2925e-162">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2925e-162">See also</span></span>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting>
- [<span data-ttu-id="2925e-163">Usar a estrutura do MSTest em testes de unidade</span><span class="sxs-lookup"><span data-stu-id="2925e-163">Use the MSTest framework in unit tests</span></span>](/visualstudio/test/using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests)
- [<span data-ttu-id="2925e-164">Documentos da estrutura de teste do MSTest V2</span><span class="sxs-lookup"><span data-stu-id="2925e-164">MSTest V2 test framework docs</span></span>](https://github.com/Microsoft/testfx-docs)
