---
title: Código C# de teste de unidade no .NET Core usando dotnet test e xUnit
description: Aprenda os conceitos de teste de unidade no C# e .NET Core por meio de uma experiência interativa de criação passo a passo de uma solução de exemplo usando dotnet test e xUnit.
author: ardalis
ms.author: wiwagn
ms.date: 11/29/2017
ms.openlocfilehash: 560ba58076fedbb1174da2cfe93796030aa9d46f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43507824"
---
# <a name="unit-testing-c-in-net-core-using-dotnet-test-and-xunit"></a><span data-ttu-id="ed38f-103">C# de teste de unidade no .NET Core usando dotnet test e xUnit</span><span class="sxs-lookup"><span data-stu-id="ed38f-103">Unit testing C# in .NET Core using dotnet test and xUnit</span></span>

<span data-ttu-id="ed38f-104">Este tutorial apresenta uma experiência interativa de compilação de uma solução de exemplo passo a passo para aprender os conceitos do teste de unidade.</span><span class="sxs-lookup"><span data-stu-id="ed38f-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="ed38f-105">Se você preferir acompanhar o tutorial usando uma solução interna, [veja ou baixe o exemplo de código](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-using-dotnet-test/) antes de começar.</span><span class="sxs-lookup"><span data-stu-id="ed38f-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-using-dotnet-test/) before you begin.</span></span> <span data-ttu-id="ed38f-106">Para obter instruções de download, consulte [Exemplos e tutoriais](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="ed38f-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="ed38f-107">Criando o projeto de origem</span><span class="sxs-lookup"><span data-stu-id="ed38f-107">Creating the source project</span></span>

<span data-ttu-id="ed38f-108">Abra uma janela do shell.</span><span class="sxs-lookup"><span data-stu-id="ed38f-108">Open a shell window.</span></span> <span data-ttu-id="ed38f-109">Crie um diretório chamado *unit-testing-using-dotnet-test* para armazenar a solução.</span><span class="sxs-lookup"><span data-stu-id="ed38f-109">Create a directory called *unit-testing-using-dotnet-test* to hold the solution.</span></span>
<span data-ttu-id="ed38f-110">Nesse novo diretório, execute [`dotnet new sln`](../tools/dotnet-new.md) para criar uma nova solução.</span><span class="sxs-lookup"><span data-stu-id="ed38f-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution.</span></span> <span data-ttu-id="ed38f-111">Ter uma solução facilita o gerenciamento da biblioteca de classes e o projeto de teste de unidade.</span><span class="sxs-lookup"><span data-stu-id="ed38f-111">Having a solution makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="ed38f-112">No diretório da solução, crie um diretório *PrimeService*.</span><span class="sxs-lookup"><span data-stu-id="ed38f-112">Inside the solution directory, create a *PrimeService* directory.</span></span> <span data-ttu-id="ed38f-113">A estrutura de arquivo e diretório até aqui deve ser da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="ed38f-113">The directory and file structure thus far should be as follows:</span></span>

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
```

<span data-ttu-id="ed38f-114">Torne *PrimeService* o diretório atual e execute [`dotnet new classlib`](../tools/dotnet-new.md) para criar o projeto de origem.</span><span class="sxs-lookup"><span data-stu-id="ed38f-114">Make *PrimeService* the current directory and run [`dotnet new classlib`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="ed38f-115">Renomeie *Class1.cs* como *PrimeService.cs*.</span><span class="sxs-lookup"><span data-stu-id="ed38f-115">Rename *Class1.cs* to *PrimeService.cs*.</span></span> <span data-ttu-id="ed38f-116">Para usar o TDD (Desenvolvimento Orientado por Testes), primeiro você cria uma implementação com falha da classe `PrimeService`:</span><span class="sxs-lookup"><span data-stu-id="ed38f-116">To use test-driven development (TDD), you first create a failing implementation of the `PrimeService` class:</span></span>

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

<span data-ttu-id="ed38f-117">Altere o diretório de volta para o diretório *unit-testing-using-dotnet-test*.</span><span class="sxs-lookup"><span data-stu-id="ed38f-117">Change the directory back to the *unit-testing-using-dotnet-test* directory.</span></span>

<span data-ttu-id="ed38f-118">Execute o comando [dotnet sln](../tools/dotnet-sln.md) para adicionar o projeto de biblioteca de classes à solução:</span><span class="sxs-lookup"><span data-stu-id="ed38f-118">Run the [dotnet sln](../tools/dotnet-sln.md) command to add the class library project to the solution:</span></span>

```
dotnet sln add .\PrimeService\PrimeService.csproj
```

## <a name="creating-the-test-project"></a><span data-ttu-id="ed38f-119">Criando o projeto de teste</span><span class="sxs-lookup"><span data-stu-id="ed38f-119">Creating the test project</span></span>

<span data-ttu-id="ed38f-120">Em seguida, crie o diretório *PrimeService.Tests*.</span><span class="sxs-lookup"><span data-stu-id="ed38f-120">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="ed38f-121">O seguinte esquema mostra a estrutura do diretório:</span><span class="sxs-lookup"><span data-stu-id="ed38f-121">The following outline shows the directory structure:</span></span>

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

<span data-ttu-id="ed38f-122">Torne o diretório *PrimeService.Tests* o diretório atual e crie um novo projeto usando [`dotnet new xunit`](../tools/dotnet-new.md).</span><span class="sxs-lookup"><span data-stu-id="ed38f-122">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new xunit`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="ed38f-123">Esse comando cria um projeto de teste que usa o xUnit como a biblioteca de teste.</span><span class="sxs-lookup"><span data-stu-id="ed38f-123">This command creates a test project that uses xUnit as the test library.</span></span> <span data-ttu-id="ed38f-124">O modelo gerado configura o executor de teste no arquivo *PrimeServiceTests.csproj* semelhante ao código a seguir:</span><span class="sxs-lookup"><span data-stu-id="ed38f-124">The generated template configures the test runner in the *PrimeServiceTests.csproj* file similar to the following code:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

<span data-ttu-id="ed38f-125">O projeto de teste requer outros pacotes para criar e executar testes de unidade.</span><span class="sxs-lookup"><span data-stu-id="ed38f-125">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="ed38f-126">`dotnet new` na etapa anterior adicionou xUnit e o executor de xUnit.</span><span class="sxs-lookup"><span data-stu-id="ed38f-126">`dotnet new` in the previous step added xUnit and the xUnit runner.</span></span> <span data-ttu-id="ed38f-127">Agora, adicione a biblioteca de classes `PrimeService` como outra dependência ao projeto.</span><span class="sxs-lookup"><span data-stu-id="ed38f-127">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="ed38f-128">Use o comando [`dotnet add reference`](../tools/dotnet-add-reference.md):</span><span class="sxs-lookup"><span data-stu-id="ed38f-128">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../PrimeService/PrimeService.csproj
```

<span data-ttu-id="ed38f-129">Você pode ver o arquivo inteiro no [repositório de exemplos](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService.Tests.csproj) no GitHub.</span><span class="sxs-lookup"><span data-stu-id="ed38f-129">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService.Tests.csproj) on GitHub.</span></span>

<span data-ttu-id="ed38f-130">Veja a seguir o layout da solução final:</span><span class="sxs-lookup"><span data-stu-id="ed38f-130">The following shows the final solution layout:</span></span>

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.csproj
```

<span data-ttu-id="ed38f-131">Para adicionar o projeto de teste na solução, execute o comando [dotnet sln](../tools/dotnet-sln.md) do diretório *unit-testing-using-dotnet-test*:</span><span class="sxs-lookup"><span data-stu-id="ed38f-131">To add the test project to the solution, run the [dotnet sln](../tools/dotnet-sln.md) command in the *unit-testing-using-dotnet-test* directory:</span></span>

```
dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj
```

## <a name="creating-the-first-test"></a><span data-ttu-id="ed38f-132">Criando o primeiro teste</span><span class="sxs-lookup"><span data-stu-id="ed38f-132">Creating the first test</span></span>

<span data-ttu-id="ed38f-133">A abordagem de TDD pede a criação de um teste com falha para fazê-lo passar e depois a repetição do processo.</span><span class="sxs-lookup"><span data-stu-id="ed38f-133">The TDD approach calls for writing one failing test, making it pass, then repeating the process.</span></span> <span data-ttu-id="ed38f-134">Remova *UnitTest1.cs* do diretório *PrimeService.Tests* e crie um novo arquivo de C# chamado *PrimeService_IsPrimeShould.cs*.</span><span class="sxs-lookup"><span data-stu-id="ed38f-134">Remove *UnitTest1.cs* from the *PrimeService.Tests* directory and create a new C# file named *PrimeService_IsPrimeShould.cs*.</span></span> <span data-ttu-id="ed38f-135">Adicione o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="ed38f-135">Add the following code:</span></span>

```csharp
using Xunit;
using Prime.Services;

namespace Prime.UnitTests.Services
{
    public class PrimeService_IsPrimeShould
    {
        private readonly PrimeService _primeService;

        public PrimeService_IsPrimeShould()
        {
            _primeService = new PrimeService();
        }

        [Fact]
        public void ReturnFalseGivenValueOf1()
        {
            var result = _primeService.IsPrime(1);

            Assert.False(result, "1 should not be prime");
        }
    }
}
```

<span data-ttu-id="ed38f-136">O atributo `[Fact]` indica um método de teste que é executado pelo executor de teste.</span><span class="sxs-lookup"><span data-stu-id="ed38f-136">The `[Fact]` attribute indicates a test method that is run by the test runner.</span></span> <span data-ttu-id="ed38f-137">Na pasta *PrimeService.Tests*, execute [`dotnet test`](../tools/dotnet-test.md) para compilar os testes e a biblioteca de classes e execute os testes.</span><span class="sxs-lookup"><span data-stu-id="ed38f-137">From the *PrimeService.Tests* folder, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="ed38f-138">O executor de teste do xUnit contém o ponto de entrada do programa para executar os testes.</span><span class="sxs-lookup"><span data-stu-id="ed38f-138">The xUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="ed38f-139">`dotnet test` inicia o executor de teste usando o projeto de teste de unidade que você criou.</span><span class="sxs-lookup"><span data-stu-id="ed38f-139">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="ed38f-140">O teste falha.</span><span class="sxs-lookup"><span data-stu-id="ed38f-140">Your test fails.</span></span> <span data-ttu-id="ed38f-141">Você ainda não criou a implementação.</span><span class="sxs-lookup"><span data-stu-id="ed38f-141">You haven't created the implementation yet.</span></span> <span data-ttu-id="ed38f-142">Faça esse teste ser aprovado escrevendo o código mais simples na classe `PrimeService` que funciona.</span><span class="sxs-lookup"><span data-stu-id="ed38f-142">Make this test pass by writing the simplest code in the `PrimeService` class that works.</span></span> <span data-ttu-id="ed38f-143">Substitua a implementação de método `IsPrime` pelo código a seguir:</span><span class="sxs-lookup"><span data-stu-id="ed38f-143">Replace the existing `IsPrime` method implementation with the following code:</span></span>

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

<span data-ttu-id="ed38f-144">No diretório *PrimeService.Tests*, execute `dotnet test` novamente.</span><span class="sxs-lookup"><span data-stu-id="ed38f-144">In the *PrimeService.Tests* directory, run `dotnet test` again.</span></span> <span data-ttu-id="ed38f-145">O comando `dotnet test` executa uma compilação para o projeto `PrimeService` e, depois, para o projeto `PrimeService.Tests`.</span><span class="sxs-lookup"><span data-stu-id="ed38f-145">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="ed38f-146">Depois de compilar os dois projetos, ele executará esse teste único.</span><span class="sxs-lookup"><span data-stu-id="ed38f-146">After building both projects, it runs this single test.</span></span> <span data-ttu-id="ed38f-147">Ele é aprovado.</span><span class="sxs-lookup"><span data-stu-id="ed38f-147">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="ed38f-148">Adicionando mais recursos</span><span class="sxs-lookup"><span data-stu-id="ed38f-148">Adding more features</span></span>

<span data-ttu-id="ed38f-149">Agora que você fez um teste ser aprovado, é hora de escrever mais.</span><span class="sxs-lookup"><span data-stu-id="ed38f-149">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="ed38f-150">Existem alguns outros casos simples de números primos: 0, -1.</span><span class="sxs-lookup"><span data-stu-id="ed38f-150">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="ed38f-151">Você pode adicionar esses casos como novos testes com o atributo `[Fact]`, mas isso se torna entediante rapidamente.</span><span class="sxs-lookup"><span data-stu-id="ed38f-151">You could add those cases as new tests with the `[Fact]` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="ed38f-152">Há outros atributos de xUnit que permitem que você grave um pacote de testes semelhantes:</span><span class="sxs-lookup"><span data-stu-id="ed38f-152">There are other xUnit attributes that enable you to write a suite of similar tests:</span></span>

- <span data-ttu-id="ed38f-153">O `[Theory]` representa um pacote de testes que executa o mesmo código, mas têm diferentes argumentos de entrada.</span><span class="sxs-lookup"><span data-stu-id="ed38f-153">`[Theory]` represents a suite of tests that execute the same code but have different input arguments.</span></span>

- <span data-ttu-id="ed38f-154">O atributo `[InlineData]` especifica valores para essas entradas.</span><span class="sxs-lookup"><span data-stu-id="ed38f-154">`[InlineData]` attribute specifies values for those inputs.</span></span>

<span data-ttu-id="ed38f-155">Em vez de criar novos testes, aplique esses dois atributos, `[Theory]` e `[InlineData]`, para criar uma única teoria no arquivo *PrimeService_IsPrimeShould.cs*.</span><span class="sxs-lookup"><span data-stu-id="ed38f-155">Instead of creating new tests, apply these two attributes, `[Theory]` and `[InlineData]`, to create a single theory in the *PrimeService_IsPrimeShould.cs* file.</span></span> <span data-ttu-id="ed38f-156">A teoria é um método que testa vários valores inferiores a dois, que é o número primo mais baixo:</span><span class="sxs-lookup"><span data-stu-id="ed38f-156">The theory is a method that tests several values less than two, which is the lowest prime number:</span></span>

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

<span data-ttu-id="ed38f-157">Execute `dotnet test` novamente, e dois desses testes deverão falhar.</span><span class="sxs-lookup"><span data-stu-id="ed38f-157">Run `dotnet test` again, and two of these tests should fail.</span></span> <span data-ttu-id="ed38f-158">Para fazer com que todos os testes sejam aprovados, altere a cláusula `if` no início do método `IsPrime` no arquivo *PrimeService.cs*:</span><span class="sxs-lookup"><span data-stu-id="ed38f-158">To make all of the tests pass, change the `if` clause at the beginning of the `IsPrime` method in the *PrimeService.cs* file:</span></span>

```csharp
if (candidate < 2)
```

<span data-ttu-id="ed38f-159">Continue iterando adicionando mais testes, mais teorias e mais código na biblioteca principal.</span><span class="sxs-lookup"><span data-stu-id="ed38f-159">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="ed38f-160">Você tem a [versão concluída dos testes](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs) e a [implementação completa da biblioteca](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs).</span><span class="sxs-lookup"><span data-stu-id="ed38f-160">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs).</span></span>

### <a name="additional-resources"></a><span data-ttu-id="ed38f-161">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="ed38f-161">Additional resources</span></span>

- [<span data-ttu-id="ed38f-162">Lógica do controlador de teste no ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ed38f-162">Testing controller logic in ASP.NET Core</span></span>](/aspnet/core/mvc/controllers/testing)
