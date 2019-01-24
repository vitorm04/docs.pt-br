---
title: Teste de unidade em C# com NUnit e .NET Core
description: Aprenda conceitos de teste de unidade no C# e .NET Core por meio de uma experiência interativa, criando passo a passo uma solução de exemplo, usando dotnet test e NUnit.
author: rprouse
ms.date: 08/31/2018
ms.custom: seodec18
ms.openlocfilehash: 00be8c2fdef88861cc1119b1593155e027a3ade5
ms.sourcegitcommit: 75567a3cb437009db55949c6092f4e77ed1a9da4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/15/2019
ms.locfileid: "54307208"
---
# <a name="unit-testing-c-with-nunit-and-net-core"></a><span data-ttu-id="b4dd1-103">Teste de unidade em C# com NUnit e .NET Core</span><span class="sxs-lookup"><span data-stu-id="b4dd1-103">Unit testing C# with NUnit and .NET Core</span></span>

<span data-ttu-id="b4dd1-104">Este tutorial apresenta uma experiência interativa de compilação de uma solução de exemplo passo a passo para aprender os conceitos do teste de unidade.</span><span class="sxs-lookup"><span data-stu-id="b4dd1-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="b4dd1-105">Se você preferir acompanhar o tutorial usando uma solução interna, [veja ou baixe o exemplo de código](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/) antes de começar.</span><span class="sxs-lookup"><span data-stu-id="b4dd1-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/) before you begin.</span></span> <span data-ttu-id="b4dd1-106">Para obter instruções de download, consulte [Exemplos e tutoriais](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="b4dd1-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b4dd1-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="b4dd1-107">Prerequisites</span></span>

- <span data-ttu-id="b4dd1-108">[SDK do .NET Core 2.1](https://www.microsoft.com/net/download) ou versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="b4dd1-108">[.NET Core 2.1 SDK](https://www.microsoft.com/net/download) or later versions.</span></span>
- <span data-ttu-id="b4dd1-109">Um editor de texto ou de código de sua escolha.</span><span class="sxs-lookup"><span data-stu-id="b4dd1-109">A text editor or code editor of your choice.</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="b4dd1-110">Criando o projeto de origem</span><span class="sxs-lookup"><span data-stu-id="b4dd1-110">Creating the source project</span></span>

<span data-ttu-id="b4dd1-111">Abra uma janela do shell.</span><span class="sxs-lookup"><span data-stu-id="b4dd1-111">Open a shell window.</span></span> <span data-ttu-id="b4dd1-112">Crie um diretório chamado *unit-testing-using-nunit* para armazenar a solução.</span><span class="sxs-lookup"><span data-stu-id="b4dd1-112">Create a directory called *unit-testing-using-nunit* to hold the solution.</span></span> <span data-ttu-id="b4dd1-113">Nesse diretório, execute o seguinte comando a fim de criar um novo arquivo de solução para a biblioteca de classes e o projeto de teste:</span><span class="sxs-lookup"><span data-stu-id="b4dd1-113">Inside this new directory, run the following command to create a new solution file for the class library and the test project:</span></span>

```console
dotnet new sln
```
 
<span data-ttu-id="b4dd1-114">Em seguida, crie um diretório *PrimeService*.</span><span class="sxs-lookup"><span data-stu-id="b4dd1-114">Next, create a *PrimeService* directory.</span></span> <span data-ttu-id="b4dd1-115">A seguinte estrutura de tópicos mostra a estrutura de arquivo e o diretório até aqui:</span><span class="sxs-lookup"><span data-stu-id="b4dd1-115">The following outline shows the directory and file structure so far:</span></span>

```
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
```

<span data-ttu-id="b4dd1-116">Torne *PrimeService* o diretório atual e execute o seguinte comando para criar o projeto de origem:</span><span class="sxs-lookup"><span data-stu-id="b4dd1-116">Make *PrimeService* the current directory and run the following command to create the source project:</span></span>

```console
dotnet new classlib
```

<span data-ttu-id="b4dd1-117">Renomeie *Class1.cs* como *PrimeService.cs*.</span><span class="sxs-lookup"><span data-stu-id="b4dd1-117">Rename *Class1.cs* to *PrimeService.cs*.</span></span> <span data-ttu-id="b4dd1-118">Para usar o TDD (Desenvolvimento Orientado por Testes), você cria uma implementação com falha da classe `PrimeService`:</span><span class="sxs-lookup"><span data-stu-id="b4dd1-118">To use test-driven development (TDD), you create a failing implementation of the `PrimeService` class:</span></span>

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

<span data-ttu-id="b4dd1-119">Altere o diretório de volta para o diretório *unit-testing-using-nunit*.</span><span class="sxs-lookup"><span data-stu-id="b4dd1-119">Change the directory back to the *unit-testing-using-nunit* directory.</span></span> <span data-ttu-id="b4dd1-120">Execute o seguinte comando para adicionar o projeto de biblioteca de classes à solução:</span><span class="sxs-lookup"><span data-stu-id="b4dd1-120">Run the following command to add the class library project to the solution:</span></span>

```console
dotnet sln add PrimeService/PrimeService.csproj
```

## <a name="creating-the-test-project"></a><span data-ttu-id="b4dd1-121">Criando o projeto de teste</span><span class="sxs-lookup"><span data-stu-id="b4dd1-121">Creating the test project</span></span>

<span data-ttu-id="b4dd1-122">Em seguida, crie o diretório *PrimeService.Tests*.</span><span class="sxs-lookup"><span data-stu-id="b4dd1-122">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="b4dd1-123">O seguinte esquema mostra a estrutura do diretório:</span><span class="sxs-lookup"><span data-stu-id="b4dd1-123">The following outline shows the directory structure:</span></span>

```
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

<span data-ttu-id="b4dd1-124">Torne o diretório *PrimeService.Tests* o diretório atual e crie um novo projeto usando o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="b4dd1-124">Make the *PrimeService.Tests* directory the current directory and create a new project using the following command:</span></span>

```console
dotnet new nunit
```

<span data-ttu-id="b4dd1-125">O comando [dotnet new](../tools/dotnet-new.md) cria um projeto de teste que usa o NUnit como a biblioteca de teste.</span><span class="sxs-lookup"><span data-stu-id="b4dd1-125">The [dotnet new](../tools/dotnet-new.md) command creates a test project that uses NUnit as the test library.</span></span> <span data-ttu-id="b4dd1-126">O modelo gerado configura o executor de teste no arquivo *PrimeService.Tests.csproj*:</span><span class="sxs-lookup"><span data-stu-id="b4dd1-126">The generated template configures the test runner in the *PrimeService.Tests.csproj* file:</span></span>

[!code-xml[Packages](~/samples/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService.Tests.csproj#Packages)]

<span data-ttu-id="b4dd1-127">O projeto de teste requer outros pacotes para criar e executar testes de unidade.</span><span class="sxs-lookup"><span data-stu-id="b4dd1-127">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="b4dd1-128">O `dotnet new`, na etapa anterior, adicionou o SDK de teste da Microsoft, a estrutura de teste do NUnit e o adaptador de teste do NUnit.</span><span class="sxs-lookup"><span data-stu-id="b4dd1-128">`dotnet new` in the previous step added the Microsoft test SDK, the NUnit test framework, and the NUnit test adapter.</span></span> <span data-ttu-id="b4dd1-129">Agora, adicione a biblioteca de classes `PrimeService` como outra dependência ao projeto.</span><span class="sxs-lookup"><span data-stu-id="b4dd1-129">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="b4dd1-130">Use o comando [`dotnet add reference`](../tools/dotnet-add-reference.md):</span><span class="sxs-lookup"><span data-stu-id="b4dd1-130">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```console
dotnet add reference ../PrimeService/PrimeService.csproj
```

<span data-ttu-id="b4dd1-131">Você pode ver o arquivo inteiro no [repositório de exemplos](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService.Tests.csproj) no GitHub.</span><span class="sxs-lookup"><span data-stu-id="b4dd1-131">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService.Tests.csproj) on GitHub.</span></span>

<span data-ttu-id="b4dd1-132">O seguinte esquema mostra o layout da solução final:</span><span class="sxs-lookup"><span data-stu-id="b4dd1-132">The following outline shows the final solution layout:</span></span>

```
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        Test Source Files
        PrimeService.Tests.csproj
```

<span data-ttu-id="b4dd1-133">Execute o seguinte comando no diretório *unit-testing-using-nunit*:</span><span class="sxs-lookup"><span data-stu-id="b4dd1-133">Execute the following command in the *unit-testing-using-nunit* directory:</span></span>

```console
dotnet sln add ./PrimeService.Tests/PrimeService.Tests.csproj
```

## <a name="creating-the-first-test"></a><span data-ttu-id="b4dd1-134">Criando o primeiro teste</span><span class="sxs-lookup"><span data-stu-id="b4dd1-134">Creating the first test</span></span>

<span data-ttu-id="b4dd1-135">A abordagem de TDD pede a criação de um teste com falha para fazê-lo passar e depois a repetição do processo.</span><span class="sxs-lookup"><span data-stu-id="b4dd1-135">The TDD approach calls for writing one failing test, making it pass, then repeating the process.</span></span> <span data-ttu-id="b4dd1-136">No diretório *PrimeService.Tests*, renomeie o arquivo *UnitTest1.cs* para *PrimeService_IsPrimeShould.cs* e substitua todo o seu conteúdo pelo código a seguir:</span><span class="sxs-lookup"><span data-stu-id="b4dd1-136">In the *PrimeService.Tests* directory, rename the *UnitTest1.cs* file to *PrimeService_IsPrimeShould.cs* and replace its entire contents with the following code:</span></span>

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

<span data-ttu-id="b4dd1-137">O atributo `[TestFixture]` indica uma classe que contém testes de unidade.</span><span class="sxs-lookup"><span data-stu-id="b4dd1-137">The `[TestFixture]` attribute denotes a class that contains unit tests.</span></span> <span data-ttu-id="b4dd1-138">O atributo `[Test]` indica um método que é um método de teste.</span><span class="sxs-lookup"><span data-stu-id="b4dd1-138">The `[Test]` attribute indicates a method is a test method.</span></span>

<span data-ttu-id="b4dd1-139">Salve esse arquivo e execute [`dotnet test`](../tools/dotnet-test.md) para compilar os testes e a biblioteca de classes e, em seguida, execute os testes.</span><span class="sxs-lookup"><span data-stu-id="b4dd1-139">Save this file and execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="b4dd1-140">O executor de teste do NUnit contém o ponto de entrada do programa para executar os testes.</span><span class="sxs-lookup"><span data-stu-id="b4dd1-140">The NUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="b4dd1-141">`dotnet test` inicia o executor de teste usando o projeto de teste de unidade que você criou.</span><span class="sxs-lookup"><span data-stu-id="b4dd1-141">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="b4dd1-142">O teste falha.</span><span class="sxs-lookup"><span data-stu-id="b4dd1-142">Your test fails.</span></span> <span data-ttu-id="b4dd1-143">Você ainda não criou a implementação.</span><span class="sxs-lookup"><span data-stu-id="b4dd1-143">You haven't created the implementation yet.</span></span> <span data-ttu-id="b4dd1-144">Faça esse teste ser aprovado escrevendo o código mais simples na classe `PrimeService` que funciona:</span><span class="sxs-lookup"><span data-stu-id="b4dd1-144">Make this test pass by writing the simplest code in the `PrimeService` class that works:</span></span>

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

<span data-ttu-id="b4dd1-145">No diretório *unit-testing-using-nunit*, execute `dotnet test` novamente.</span><span class="sxs-lookup"><span data-stu-id="b4dd1-145">In the *unit-testing-using-nunit* directory, run `dotnet test` again.</span></span> <span data-ttu-id="b4dd1-146">O comando `dotnet test` executa uma compilação para o projeto `PrimeService` e, depois, para o projeto `PrimeService.Tests`.</span><span class="sxs-lookup"><span data-stu-id="b4dd1-146">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="b4dd1-147">Depois de compilar os dois projetos, ele executará esse teste único.</span><span class="sxs-lookup"><span data-stu-id="b4dd1-147">After building both projects, it runs this single test.</span></span> <span data-ttu-id="b4dd1-148">Ele é aprovado.</span><span class="sxs-lookup"><span data-stu-id="b4dd1-148">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="b4dd1-149">Adicionando mais recursos</span><span class="sxs-lookup"><span data-stu-id="b4dd1-149">Adding more features</span></span>

<span data-ttu-id="b4dd1-150">Agora que você fez um teste ser aprovado, é hora de escrever mais.</span><span class="sxs-lookup"><span data-stu-id="b4dd1-150">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="b4dd1-151">Existem alguns outros casos simples de números primos: 0 e -1.</span><span class="sxs-lookup"><span data-stu-id="b4dd1-151">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="b4dd1-152">Você pode adicionar novos testes com o atributo `[Test]`, mas isso se torna entediante rapidamente.</span><span class="sxs-lookup"><span data-stu-id="b4dd1-152">You could add new tests with the `[Test]` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="b4dd1-153">Há outros atributos de NUnit que permitem que você grave um pacote com testes semelhantes.</span><span class="sxs-lookup"><span data-stu-id="b4dd1-153">There are other NUnit attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="b4dd1-154">Um atributo `[TestCase]` é usado para criar um pacote com testes que executa o mesmo código, mas têm diferentes argumentos de entrada.</span><span class="sxs-lookup"><span data-stu-id="b4dd1-154">A `[TestCase]` attribute is used to create a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="b4dd1-155">Você pode usar o atributo `[TestCase]` para especificar valores para essas entradas.</span><span class="sxs-lookup"><span data-stu-id="b4dd1-155">You can use the `[TestCase]` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="b4dd1-156">Em vez de criar novos testes, aplique esse atributo para criar um único teste controlado por dados.</span><span class="sxs-lookup"><span data-stu-id="b4dd1-156">Instead of creating new tests, apply this attribute to create a single data driven test.</span></span> <span data-ttu-id="b4dd1-157">O teste controlado por dados é um método que testa vários valores menores que dois, que é o menor número primo:</span><span class="sxs-lookup"><span data-stu-id="b4dd1-157">The data driven test is a method that tests several values less than two, which is the lowest prime number:</span></span>

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

<span data-ttu-id="b4dd1-158">Execute `dotnet test`, e dois desses testes falham.</span><span class="sxs-lookup"><span data-stu-id="b4dd1-158">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="b4dd1-159">Para fazer com que todos os testes sejam aprovados, altere a cláusula `if` no início do método `Main` no arquivo *PrimeService.cs*:</span><span class="sxs-lookup"><span data-stu-id="b4dd1-159">To make all of the tests pass, change the `if` clause at the beginning of the `Main` method in the *PrimeService.cs* file:</span></span>

```csharp
if (candidate < 2)
```

<span data-ttu-id="b4dd1-160">Continue iterando adicionando mais testes, mais teorias e mais código na biblioteca principal.</span><span class="sxs-lookup"><span data-stu-id="b4dd1-160">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="b4dd1-161">Você tem a [versão concluída dos testes](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.cs) e a [implementação completa da biblioteca](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService/PrimeService.cs).</span><span class="sxs-lookup"><span data-stu-id="b4dd1-161">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.cs) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService/PrimeService.cs).</span></span>

<span data-ttu-id="b4dd1-162">Você criou uma pequena biblioteca e um conjunto de testes de unidade para essa biblioteca.</span><span class="sxs-lookup"><span data-stu-id="b4dd1-162">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="b4dd1-163">Você estruturou a solução para que a adição de novos pacotes e testes fizesse parte do fluxo de trabalho normal.</span><span class="sxs-lookup"><span data-stu-id="b4dd1-163">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="b4dd1-164">Você concentrou grande parte do seu tempo e esforço em resolver as metas do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b4dd1-164">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
