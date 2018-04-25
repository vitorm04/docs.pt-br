---
title: Teste de unidade em C# com NUnit e .NET Core
description: Aprenda conceitos de teste de unidade no C# e .NET Core por meio de uma experiência interativa, criando passo a passo uma solução de exemplo, usando dotnet test e NUnit.
keywords: NUnit, .NET, .NET Core
author: rprouse
ms.date: 12/01/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.openlocfilehash: b29912a58511305202a18e8da4ae57700605867a
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="unit-testing-c-with-nunit-and-net-core"></a><span data-ttu-id="d6d4c-104">Teste de unidade em C# com NUnit e .NET Core</span><span class="sxs-lookup"><span data-stu-id="d6d4c-104">Unit testing C# with NUnit and .NET Core</span></span>

<span data-ttu-id="d6d4c-105">Este tutorial apresenta uma experiência interativa de compilação de uma solução de exemplo passo a passo para aprender os conceitos do teste de unidade.</span><span class="sxs-lookup"><span data-stu-id="d6d4c-105">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="d6d4c-106">Se você preferir acompanhar o tutorial usando uma solução interna, [veja ou baixe o exemplo de código](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/) antes de começar.</span><span class="sxs-lookup"><span data-stu-id="d6d4c-106">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/) before you begin.</span></span> <span data-ttu-id="d6d4c-107">Para obter instruções de download, consulte [Exemplos e tutoriais](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="d6d4c-107">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="d6d4c-108">Criando o projeto de origem</span><span class="sxs-lookup"><span data-stu-id="d6d4c-108">Creating the source project</span></span>

<span data-ttu-id="d6d4c-109">Abra uma janela do shell.</span><span class="sxs-lookup"><span data-stu-id="d6d4c-109">Open a shell window.</span></span> <span data-ttu-id="d6d4c-110">Crie um diretório chamado *unit-testing-using-nunit* para armazenar a solução.</span><span class="sxs-lookup"><span data-stu-id="d6d4c-110">Create a directory called *unit-testing-using-nunit* to hold the solution.</span></span> <span data-ttu-id="d6d4c-111">Nesse diretório, execute [`dotnet new sln`](../tools/dotnet-new.md) a fim de criar um novo arquivo de solução para a biblioteca de classes e o projeto de teste.</span><span class="sxs-lookup"><span data-stu-id="d6d4c-111">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution file for the class library and the test project.</span></span> <span data-ttu-id="d6d4c-112">Em seguida, crie um diretório *PrimeService*.</span><span class="sxs-lookup"><span data-stu-id="d6d4c-112">Next, create a *PrimeService* directory.</span></span> <span data-ttu-id="d6d4c-113">O seguinte esquema mostra a estrutura de arquivo e diretório até aqui:</span><span class="sxs-lookup"><span data-stu-id="d6d4c-113">The following outline shows the directory and file structure thus far:</span></span>

```
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
```

<span data-ttu-id="d6d4c-114">Torne *PrimeService* o diretório atual e execute [`dotnet new classlib`](../tools/dotnet-new.md) para criar o projeto de origem.</span><span class="sxs-lookup"><span data-stu-id="d6d4c-114">Make *PrimeService* the current directory and run [`dotnet new classlib`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="d6d4c-115">Renomeie *Class1.cs* como *PrimeService.cs*.</span><span class="sxs-lookup"><span data-stu-id="d6d4c-115">Rename *Class1.cs* to *PrimeService.cs*.</span></span> <span data-ttu-id="d6d4c-116">Para usar o TDD (Desenvolvimento Orientado por Testes), você cria uma implementação com falha da classe `PrimeService`:</span><span class="sxs-lookup"><span data-stu-id="d6d4c-116">To use test-driven development (TDD), you create a failing implementation of the `PrimeService` class:</span></span>

```csharp
using System;

namespace Prime.Services
{
    public class PrimeService
    {
        public bool IsPrime(int candidate)
        {
            throw new NotImplementedException("Please create a test first");
        }
    }
}
```

<span data-ttu-id="d6d4c-117">Altere o diretório de volta para o diretório *unit-testing-using-nunit*.</span><span class="sxs-lookup"><span data-stu-id="d6d4c-117">Change the directory back to the *unit-testing-using-nunit* directory.</span></span> <span data-ttu-id="d6d4c-118">Execute [`dotnet sln add PrimeService/PrimeService.csproj`](../tools/dotnet-sln.md) para adicionar o projeto de biblioteca de classes à solução.</span><span class="sxs-lookup"><span data-stu-id="d6d4c-118">Run [`dotnet sln add PrimeService/PrimeService.csproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="install-the-nunit-project-template"></a><span data-ttu-id="d6d4c-119">Instalar o modelo de projeto do NUnit</span><span class="sxs-lookup"><span data-stu-id="d6d4c-119">Install the NUnit project template</span></span>

<span data-ttu-id="d6d4c-120">Os modelos de projeto de teste do NUnit precisam ser instalados antes de criar um projeto de teste.</span><span class="sxs-lookup"><span data-stu-id="d6d4c-120">The NUnit test project templates need to be installed before creating a test project.</span></span> <span data-ttu-id="d6d4c-121">Isso precisa ser feito somente uma vez em cada computador de desenvolvedor em que você criará novos projetos NUnit.</span><span class="sxs-lookup"><span data-stu-id="d6d4c-121">This only needs to be done once on each developer machine where you'll create new NUnit projects.</span></span> <span data-ttu-id="d6d4c-122">Execute [`dotnet new -i NUnit3.DotNetNew.Template`](../tools/dotnet-new.md) para instalar os modelos do NUnit.</span><span class="sxs-lookup"><span data-stu-id="d6d4c-122">Run [`dotnet new -i NUnit3.DotNetNew.Template`](../tools/dotnet-new.md) to install the NUnit templates.</span></span>

```
dotnet new -i NUnit3.DotNetNew.Template
```

### <a name="creating-the-test-project"></a><span data-ttu-id="d6d4c-123">Criando o projeto de teste</span><span class="sxs-lookup"><span data-stu-id="d6d4c-123">Creating the test project</span></span>

<span data-ttu-id="d6d4c-124">Em seguida, crie o diretório *PrimeService.Tests*.</span><span class="sxs-lookup"><span data-stu-id="d6d4c-124">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="d6d4c-125">O seguinte esquema mostra a estrutura do diretório:</span><span class="sxs-lookup"><span data-stu-id="d6d4c-125">The following outline shows the directory structure:</span></span>

```
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

<span data-ttu-id="d6d4c-126">Torne o diretório *PrimeService.Tests* o diretório atual e crie um novo projeto usando [`dotnet new nunit`](../tools/dotnet-new.md).</span><span class="sxs-lookup"><span data-stu-id="d6d4c-126">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new nunit`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="d6d4c-127">O comando dotnet new cria um projeto de teste que usa o NUnit como a biblioteca de teste.</span><span class="sxs-lookup"><span data-stu-id="d6d4c-127">The dotnet new command creates a test project that uses NUnit as the test library.</span></span> <span data-ttu-id="d6d4c-128">O modelo gerado configura o executor de teste no arquivo *PrimeServiceTests.csproj*:</span><span class="sxs-lookup"><span data-stu-id="d6d4c-128">The generated template configures the test runner in the *PrimeServiceTests.csproj* file:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.5.0" />
  <PackageReference Include="NUnit" Version="3.9.0" />
  <PackageReference Include="NUnit3TestAdapter" Version="3.9.0" />
</ItemGroup>
```

<span data-ttu-id="d6d4c-129">O projeto de teste requer outros pacotes para criar e executar testes de unidade.</span><span class="sxs-lookup"><span data-stu-id="d6d4c-129">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="d6d4c-130">O `dotnet new`, na etapa anterior, adicionou o SDK de teste da Microsoft, a estrutura de teste do NUnit e o adaptador de teste do NUnit.</span><span class="sxs-lookup"><span data-stu-id="d6d4c-130">`dotnet new` in the previous step added the Microsoft test SDK, the NUnit test framework, and the NUnit test adapter.</span></span> <span data-ttu-id="d6d4c-131">Agora, adicione a biblioteca de classes `PrimeService` como outra dependência ao projeto.</span><span class="sxs-lookup"><span data-stu-id="d6d4c-131">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="d6d4c-132">Use o comando [`dotnet add reference`](../tools/dotnet-add-reference.md):</span><span class="sxs-lookup"><span data-stu-id="d6d4c-132">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../PrimeService/PrimeService.csproj
```

<span data-ttu-id="d6d4c-133">Você pode ver o arquivo inteiro no [repositório de exemplos](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService.Tests.csproj) no GitHub.</span><span class="sxs-lookup"><span data-stu-id="d6d4c-133">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService.Tests.csproj) on GitHub.</span></span>

<span data-ttu-id="d6d4c-134">O seguinte esquema mostra o layout da solução final:</span><span class="sxs-lookup"><span data-stu-id="d6d4c-134">The following outline shows the final solution layout:</span></span>

```
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.csproj
```

<span data-ttu-id="d6d4c-135">Execute [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj`](../tools/dotnet-sln.md) no diretório *unit-testing-using-dotnet-test*.</span><span class="sxs-lookup"><span data-stu-id="d6d4c-135">Execute [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj`](../tools/dotnet-sln.md) in the *unit-testing-using-dotnet-test* directory.</span></span>

## <a name="creating-the-first-test"></a><span data-ttu-id="d6d4c-136">Criando o primeiro teste</span><span class="sxs-lookup"><span data-stu-id="d6d4c-136">Creating the first test</span></span>

<span data-ttu-id="d6d4c-137">A abordagem de TDD pede a criação de um teste com falha para fazê-lo passar e depois a repetição do processo.</span><span class="sxs-lookup"><span data-stu-id="d6d4c-137">The TDD approach calls for writing one failing test, making it pass, then repeating the process.</span></span> <span data-ttu-id="d6d4c-138">Remova *UnitTest1.cs* do diretório *PrimeService.Tests* e crie um novo arquivo C# chamado *PrimeService_IsPrimeShould.cs* com o seguinte conteúdo:</span><span class="sxs-lookup"><span data-stu-id="d6d4c-138">Remove *UnitTest1.cs* from the *PrimeService.Tests* directory and create a new C# file named *PrimeService_IsPrimeShould.cs* with the following content:</span></span>

```csharp
using NUnit.Framework;
using Prime.Services;

namespace Prime.UnitTests.Services
{
    [TestFixture]
    public class PrimeService_IsPrimeShould
    {
        private readonly PrimeService _primeService;

        public PrimeService_IsPrimeShould()
        {
            _primeService = new PrimeService();
        }

        [Test]
        public void ReturnFalseGivenValueOf1()
        {
            var result = _primeService.IsPrime(1);

            Assert.IsFalse(result, "1 should not be prime");
        }
    }
}
```

<span data-ttu-id="d6d4c-139">O atributo `[TestFixture]` indica uma classe que contém testes de unidade.</span><span class="sxs-lookup"><span data-stu-id="d6d4c-139">The `[TestFixture]` attribute denotes a class that contains unit tests.</span></span> <span data-ttu-id="d6d4c-140">O atributo `[Test]` indica um método que é um método de teste.</span><span class="sxs-lookup"><span data-stu-id="d6d4c-140">The `[Test]` attribute indicates a method is a test method.</span></span>

<span data-ttu-id="d6d4c-141">Salve esse arquivo e execute [`dotnet test`](../tools/dotnet-test.md) para compilar os testes e a biblioteca de classes e, em seguida, execute os testes.</span><span class="sxs-lookup"><span data-stu-id="d6d4c-141">Save this file and execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="d6d4c-142">O executor de teste do NUnit contém o ponto de entrada do programa para executar os testes.</span><span class="sxs-lookup"><span data-stu-id="d6d4c-142">The NUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="d6d4c-143">`dotnet test` inicia o executor de teste usando o projeto de teste de unidade que você criou.</span><span class="sxs-lookup"><span data-stu-id="d6d4c-143">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="d6d4c-144">O teste falha.</span><span class="sxs-lookup"><span data-stu-id="d6d4c-144">Your test fails.</span></span> <span data-ttu-id="d6d4c-145">Você ainda não criou a implementação.</span><span class="sxs-lookup"><span data-stu-id="d6d4c-145">You haven't created the implementation yet.</span></span> <span data-ttu-id="d6d4c-146">Faça esse teste ser aprovado escrevendo o código mais simples na classe `PrimeService` que funciona:</span><span class="sxs-lookup"><span data-stu-id="d6d4c-146">Make this test pass by writing the simplest code in the `PrimeService` class that works:</span></span>

```csharp
public bool IsPrime(int candidate)
{
    if (candidate == 1)
    {
        return false;
    }
    throw new NotImplementedException("Please create a test first");
}
```

<span data-ttu-id="d6d4c-147">No diretório *unit-testing-using-nunit*, execute `dotnet test` novamente.</span><span class="sxs-lookup"><span data-stu-id="d6d4c-147">In the *unit-testing-using-nunit* directory, run `dotnet test` again.</span></span> <span data-ttu-id="d6d4c-148">O comando `dotnet test` executa uma compilação para o projeto `PrimeService` e, depois, para o projeto `PrimeService.Tests`.</span><span class="sxs-lookup"><span data-stu-id="d6d4c-148">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="d6d4c-149">Depois de compilar os dois projetos, ele executará esse teste único.</span><span class="sxs-lookup"><span data-stu-id="d6d4c-149">After building both projects, it runs this single test.</span></span> <span data-ttu-id="d6d4c-150">Ele é aprovado.</span><span class="sxs-lookup"><span data-stu-id="d6d4c-150">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="d6d4c-151">Adicionando mais recursos</span><span class="sxs-lookup"><span data-stu-id="d6d4c-151">Adding more features</span></span>

<span data-ttu-id="d6d4c-152">Agora que você fez um teste ser aprovado, é hora de escrever mais.</span><span class="sxs-lookup"><span data-stu-id="d6d4c-152">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="d6d4c-153">Existem alguns outros casos simples de números primos: 0, -1.</span><span class="sxs-lookup"><span data-stu-id="d6d4c-153">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="d6d4c-154">Você pode adicionar novos testes com o atributo `[Test]`, mas isso se torna entediante rapidamente.</span><span class="sxs-lookup"><span data-stu-id="d6d4c-154">You could add new tests with the `[Test]` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="d6d4c-155">Há outros atributos de NUnit que permitem que você grave um pacote com testes semelhantes.</span><span class="sxs-lookup"><span data-stu-id="d6d4c-155">There are other NUnit attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="d6d4c-156">Um atributo `[TestCase]` é usado para criar um pacote com testes que executa o mesmo código, mas têm diferentes argumentos de entrada.</span><span class="sxs-lookup"><span data-stu-id="d6d4c-156">A `[TestCase]` attribute is used to create a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="d6d4c-157">Você pode usar o atributo `[TestCase]` para especificar valores para essas entradas.</span><span class="sxs-lookup"><span data-stu-id="d6d4c-157">You can use the `[TestCase]` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="d6d4c-158">Em vez de criar novos testes, aplique esse atributo para criar um único teste controlado por dados.</span><span class="sxs-lookup"><span data-stu-id="d6d4c-158">Instead of creating new tests, apply this attribute to create a single data driven test.</span></span> <span data-ttu-id="d6d4c-159">O teste controlado por dados é um método que testa vários valores menores que dois, que é o menor número primo:</span><span class="sxs-lookup"><span data-stu-id="d6d4c-159">The data driven test is a method that tests several values less than two, which is the lowest prime number:</span></span>

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

<span data-ttu-id="d6d4c-160">Execute `dotnet test`, e dois desses testes falham.</span><span class="sxs-lookup"><span data-stu-id="d6d4c-160">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="d6d4c-161">Para fazer todos os testes serem aprovados, altere a cláusula `if` no início do método:</span><span class="sxs-lookup"><span data-stu-id="d6d4c-161">To make all of the tests pass, change the `if` clause at the beginning of the method:</span></span>

```csharp
if (candidate < 2)
```

<span data-ttu-id="d6d4c-162">Continue iterando adicionando mais testes, mais teorias e mais código na biblioteca principal.</span><span class="sxs-lookup"><span data-stu-id="d6d4c-162">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="d6d4c-163">Você tem a [versão concluída dos testes](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.cs) e a [implementação completa da biblioteca](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService/PrimeService.cs).</span><span class="sxs-lookup"><span data-stu-id="d6d4c-163">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.cs) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService/PrimeService.cs).</span></span>

<span data-ttu-id="d6d4c-164">Você criou uma pequena biblioteca e um conjunto de testes de unidade para essa biblioteca.</span><span class="sxs-lookup"><span data-stu-id="d6d4c-164">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="d6d4c-165">Você estruturou a solução para que a adição de novos pacotes e testes fizesse parte do fluxo de trabalho normal.</span><span class="sxs-lookup"><span data-stu-id="d6d4c-165">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="d6d4c-166">Você concentrou grande parte do seu tempo e esforço em resolver as metas do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d6d4c-166">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
