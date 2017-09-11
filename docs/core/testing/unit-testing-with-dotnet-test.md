---
title: Teste de unidade no .NET Core com dotnet test e xUnit
description: "Aprenda os conceitos de teste de unidade no .NET Core por meio de uma experiência interativa de criação passo a passo de uma solução de exemplo usando dotnet test e xUnit."
author: ardalis
ms.author: wiwagn
ms.date: 03/21/2017
ms.topic: article
ms.prod: .net-core
ms.translationtype: HT
ms.sourcegitcommit: 867f9eb286fa7ff5ef3e9167c1ab944c81161216
ms.openlocfilehash: d989ee731d7ffd0439bac69afe1458e2aa10733a
ms.contentlocale: pt-br
ms.lasthandoff: 08/17/2017

---
# <a name="unit-testing-in-net-core-using-dotnet-test-and-xunit"></a><span data-ttu-id="91c63-103">Teste de unidade no .NET Core com dotnet test e xUnit</span><span class="sxs-lookup"><span data-stu-id="91c63-103">Unit testing in .NET Core using dotnet test and xUnit</span></span>

<span data-ttu-id="91c63-104">Este tutorial apresenta uma experiência interativa de compilação de uma solução de exemplo passo a passo para aprender os conceitos do teste de unidade.</span><span class="sxs-lookup"><span data-stu-id="91c63-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="91c63-105">Se você preferir acompanhar o tutorial usando uma solução interna, [veja ou baixe o exemplo de código](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/unit-testing-using-dotnet-test/) antes de começar.</span><span class="sxs-lookup"><span data-stu-id="91c63-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/unit-testing-using-dotnet-test/) before you begin.</span></span> <span data-ttu-id="91c63-106">Para obter instruções de download, consulte [Exemplos e tutoriais](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="91c63-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="91c63-107">Criando o projeto de origem</span><span class="sxs-lookup"><span data-stu-id="91c63-107">Creating the source project</span></span>

<span data-ttu-id="91c63-108">Abra uma janela do shell.</span><span class="sxs-lookup"><span data-stu-id="91c63-108">Open a shell window.</span></span> <span data-ttu-id="91c63-109">Crie um diretório chamado *unit-testing-using-dotnet-test* para armazenar a solução.</span><span class="sxs-lookup"><span data-stu-id="91c63-109">Create a directory called *unit-testing-using-dotnet-test* to hold the solution.</span></span> <span data-ttu-id="91c63-110">Dentro desse novo diretório, crie um diretório *PrimeService*.</span><span class="sxs-lookup"><span data-stu-id="91c63-110">Inside this new directory, create a *PrimeService* directory.</span></span> <span data-ttu-id="91c63-111">A estrutura do diretório até o momento é mostrada abaixo:</span><span class="sxs-lookup"><span data-stu-id="91c63-111">The directory structure thus far is shown below:</span></span>

```
/unit-testing-using-dotnet-test
    /PrimeService
```

<span data-ttu-id="91c63-112">Torne *PrimeService* o diretório atual e execute [`dotnet new classlib`](../tools/dotnet-new.md) para criar o projeto de origem.</span><span class="sxs-lookup"><span data-stu-id="91c63-112">Make *PrimeService* the current directory and run [`dotnet new classlib`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="91c63-113">Renomeie *Class1.cs* como *PrimeService.cs*.</span><span class="sxs-lookup"><span data-stu-id="91c63-113">Rename *Class1.cs* to *PrimeService.cs*.</span></span> <span data-ttu-id="91c63-114">Para usar TDD (Desenvolvimento Orientado por Testes), você criará uma implementação com falha da classe `PrimeService`:</span><span class="sxs-lookup"><span data-stu-id="91c63-114">To use test-driven development (TDD), you'll create a failing implementation of the `PrimeService` class:</span></span>

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

## <a name="creating-the-test-project"></a><span data-ttu-id="91c63-115">Criando o projeto de teste</span><span class="sxs-lookup"><span data-stu-id="91c63-115">Creating the test project</span></span>

<span data-ttu-id="91c63-116">Altere o diretório de volta para o diretório *unit-testing-using-dotnet-test* e crie o diretório *PrimeService.Tests*.</span><span class="sxs-lookup"><span data-stu-id="91c63-116">Change the directory back to the *unit-testing-using-dotnet-test* directory and create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="91c63-117">A estrutura do diretório é mostrada abaixo:</span><span class="sxs-lookup"><span data-stu-id="91c63-117">The directory structure is shown below:</span></span>

```
/unit-testing-using-dotnet-test
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

<span data-ttu-id="91c63-118">Torne o diretório *PrimeService.Tests* o diretório atual e crie um novo projeto usando [`dotnet new xunit`](../tools/dotnet-new.md).</span><span class="sxs-lookup"><span data-stu-id="91c63-118">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new xunit`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="91c63-119">Isso cria um projeto de teste que usa o xUnit como a biblioteca de teste.</span><span class="sxs-lookup"><span data-stu-id="91c63-119">This creates a test project that uses xUnit as the test library.</span></span> <span data-ttu-id="91c63-120">O modelo gerado configura o executor de teste no *PrimeServiceTests.csproj*:</span><span class="sxs-lookup"><span data-stu-id="91c63-120">The generated template configures the test runner in the *PrimeServiceTests.csproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.0.0" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

<span data-ttu-id="91c63-121">O projeto de teste requer outros pacotes para criar e executar testes de unidade.</span><span class="sxs-lookup"><span data-stu-id="91c63-121">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="91c63-122">`dotnet new` na etapa anterior adicionou xUnit e o executor de xUnit.</span><span class="sxs-lookup"><span data-stu-id="91c63-122">`dotnet new` in the previous step added xUnit and the xUnit runner.</span></span> <span data-ttu-id="91c63-123">Agora, adicione a biblioteca de classes `PrimeService` como outra dependência ao projeto.</span><span class="sxs-lookup"><span data-stu-id="91c63-123">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="91c63-124">Use o comando [`dotnet add reference`](../tools/dotnet-add-reference.md):</span><span class="sxs-lookup"><span data-stu-id="91c63-124">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../PrimeService/PrimeService.csproj
```

<span data-ttu-id="91c63-125">Outra opção é editar o arquivo *PrimeService.Tests.csproj*.</span><span class="sxs-lookup"><span data-stu-id="91c63-125">Another option is to edit the *PrimeService.Tests.csproj* file.</span></span> <span data-ttu-id="91c63-126">Diretamente sob o primeiro nó `<ItemGroup>`, adicione outro nó `<ItemGroup>` com uma referência ao projeto de biblioteca:</span><span class="sxs-lookup"><span data-stu-id="91c63-126">Directly under the first `<ItemGroup>` node, add another `<ItemGroup>` node with a reference to the library project:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\PrimeService\PrimeService.csproj" />
</ItemGroup>
```

<span data-ttu-id="91c63-127">Você pode ver o arquivo inteiro no [repositório de exemplos](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService.Tests.csproj) no GitHub.</span><span class="sxs-lookup"><span data-stu-id="91c63-127">You can see the entire file in the [samples repository](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService.Tests.csproj) on GitHub.</span></span>

<span data-ttu-id="91c63-128">O layout da solução final é mostrada abaixo:</span><span class="sxs-lookup"><span data-stu-id="91c63-128">The final solution layout is shown below:</span></span>

```
/unit-testing-using-mstest
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        PrimeService
        PrimeServiceTests.csproj
```

## <a name="creating-the-first-test"></a><span data-ttu-id="91c63-129">Criando o primeiro teste</span><span class="sxs-lookup"><span data-stu-id="91c63-129">Creating the first test</span></span>

<span data-ttu-id="91c63-130">Antes de compilar a biblioteca ou os testes, execute [`dotnet restore`](../tools/dotnet-restore.md) no diretório *PrimeService.Tests*.</span><span class="sxs-lookup"><span data-stu-id="91c63-130">Before building the library or the tests, execute [`dotnet restore`](../tools/dotnet-restore.md) in the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="91c63-131">Este comando restaura todos os pacotes NuGet necessários para cada projeto.</span><span class="sxs-lookup"><span data-stu-id="91c63-131">This command restores all the necessary NuGet packages for each project.</span></span>

<span data-ttu-id="91c63-132">A abordagem de TDD pede a criação de um teste com falha para fazê-lo passar e depois a repetição do processo.</span><span class="sxs-lookup"><span data-stu-id="91c63-132">The TDD approach calls for writing one failing test, making it pass, then repeating the process.</span></span> <span data-ttu-id="91c63-133">Remova *UnitTest1.cs* do diretório *PrimeService.Tests* e crie um novo arquivo C# chamado *PrimeService_IsPrimeShould.cs* com o seguinte conteúdo:</span><span class="sxs-lookup"><span data-stu-id="91c63-133">Remove *UnitTest1.cs* from the *PrimeService.Tests* directory and create a new C# file named *PrimeService_IsPrimeShould.cs* with the following content:</span></span>

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

            Assert.False(result, $"1 should not be prime");
        }
    }
}
```

<span data-ttu-id="91c63-134">O atributo `[Fact]` indica um método como um único teste.</span><span class="sxs-lookup"><span data-stu-id="91c63-134">The `[Fact]` attribute denotes a method as a single test.</span></span> <span data-ttu-id="91c63-135">Execute [`dotnet test`](../tools/dotnet-test.md) para compilar os testes e a biblioteca de classes e, em seguida, execute os testes.</span><span class="sxs-lookup"><span data-stu-id="91c63-135">Execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="91c63-136">O executor de teste do xUnit contém o ponto de entrada do programa para executar os testes.</span><span class="sxs-lookup"><span data-stu-id="91c63-136">The xUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="91c63-137">`dotnet test` inicia o executor de teste e fornece um argumento de linha de comando para o executor de teste, indicando o assembly que contém os testes.</span><span class="sxs-lookup"><span data-stu-id="91c63-137">`dotnet test` starts the test runner and provides a command-line argument to the test runner indicating the assembly that contains your tests.</span></span>

<span data-ttu-id="91c63-138">O teste falha.</span><span class="sxs-lookup"><span data-stu-id="91c63-138">Your test fails.</span></span> <span data-ttu-id="91c63-139">Você ainda não criou a implementação.</span><span class="sxs-lookup"><span data-stu-id="91c63-139">You haven't created the implementation yet.</span></span> <span data-ttu-id="91c63-140">Escreva o código mais simples na classe `PrimeService` para fazer esse teste ser aprovado:</span><span class="sxs-lookup"><span data-stu-id="91c63-140">Write the simplest code in the `PrimeService` class to make this test pass:</span></span>

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

<span data-ttu-id="91c63-141">No diretório *PrimeService.Tests*, execute `dotnet test` novamente.</span><span class="sxs-lookup"><span data-stu-id="91c63-141">In the *PrimeService.Tests* directory, run `dotnet test` again.</span></span> <span data-ttu-id="91c63-142">O comando `dotnet test` executa uma compilação para o projeto `PrimeService` e, depois, para o projeto `PrimeService.Tests`.</span><span class="sxs-lookup"><span data-stu-id="91c63-142">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="91c63-143">Depois de compilar os dois projetos, ele executará esse teste único.</span><span class="sxs-lookup"><span data-stu-id="91c63-143">After building both projects, it runs this single test.</span></span> <span data-ttu-id="91c63-144">Ele é aprovado.</span><span class="sxs-lookup"><span data-stu-id="91c63-144">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="91c63-145">Adicionando mais recursos</span><span class="sxs-lookup"><span data-stu-id="91c63-145">Adding more features</span></span>

<span data-ttu-id="91c63-146">Agora que você fez um teste ser aprovado, é hora de escrever mais.</span><span class="sxs-lookup"><span data-stu-id="91c63-146">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="91c63-147">Existem alguns outros casos simples de números primos: 0, -1.</span><span class="sxs-lookup"><span data-stu-id="91c63-147">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="91c63-148">Você pode adicioná-los como novos testes, com o atributo `[Fact]`, porém isso se torna entediante rapidamente.</span><span class="sxs-lookup"><span data-stu-id="91c63-148">You could add those as new tests with the `[Fact]` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="91c63-149">Há outros atributos de xUnit que permitem escrever um pacote de testes semelhantes.</span><span class="sxs-lookup"><span data-stu-id="91c63-149">There are other xUnit attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="91c63-150">Um atributo `[Theory]` representa um pacote de testes que executa o mesmo código, mas têm diferentes argumentos de entrada.</span><span class="sxs-lookup"><span data-stu-id="91c63-150">A `[Theory]` attribute represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="91c63-151">Você pode usar o atributo `[InlineData]` para especificar valores para essas entradas.</span><span class="sxs-lookup"><span data-stu-id="91c63-151">You can use the `[InlineData]` attribute to specify values for those inputs.</span></span> 
 
<span data-ttu-id="91c63-152">Em vez de criar novos testes, aproveite esses dois atributos para criar uma única teoria que testa diversos valores menores que dois, que é o menor número primo:</span><span class="sxs-lookup"><span data-stu-id="91c63-152">Instead of creating new tests, leverage these two attributes to create a single theory that tests several values less than two, which is the lowest prime number:</span></span>

<span data-ttu-id="91c63-153">[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]</span><span class="sxs-lookup"><span data-stu-id="91c63-153">[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]</span></span>

<span data-ttu-id="91c63-154">Execute `dotnet test`, e dois desses testes falham.</span><span class="sxs-lookup"><span data-stu-id="91c63-154">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="91c63-155">Para fazer todos os testes serem aprovados, altere a cláusula `if` no início do método:</span><span class="sxs-lookup"><span data-stu-id="91c63-155">To make all of the tests pass, change the `if` clause at the beginning of the method:</span></span>

```csharp
if (candidate < 2)
```

<span data-ttu-id="91c63-156">Continue iterando adicionando mais testes, mais teorias e mais código na biblioteca principal.</span><span class="sxs-lookup"><span data-stu-id="91c63-156">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="91c63-157">Você acabará com a [versão concluída dos testes](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs) e a [implementação completa da biblioteca](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs).</span><span class="sxs-lookup"><span data-stu-id="91c63-157">You'll end up with the [finished version of the tests](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs) and the [complete implementation of the library](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs).</span></span>

<span data-ttu-id="91c63-158">Você criou uma pequena biblioteca e um conjunto de testes de unidade para essa biblioteca.</span><span class="sxs-lookup"><span data-stu-id="91c63-158">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="91c63-159">Você estruturou a solução para que a adição de novos pacotes e testes seja tranquila, e você possa concentrar mais tempo e esforço na resolução dos objetivos do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="91c63-159">You've structured the solution so that adding new packages and tests is seamless, and you can concentrate most of your time and effort on solving the goals of the applicaiton.</span></span>

