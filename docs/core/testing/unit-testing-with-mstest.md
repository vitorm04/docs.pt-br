---
title: Teste de unidade com o MSTest e .NET Core
description: Como usar o MSTest com o .NET Core
keywords: MSTest, .NET, .NET Core
author: ncarandini
ms.author: wiwagn
ms.date: 03/21/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: ed447641-3e85-4e50-b7ed-004630048a3e
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: d1cb9f6667e1317e74d246988ef1257d0712c431
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---

# <a name="unit-testing-with-mstest-and-net-core"></a><span data-ttu-id="82687-104">Teste de unidade com o MSTest e .NET Core</span><span class="sxs-lookup"><span data-stu-id="82687-104">Unit testing with MSTest and .NET Core</span></span>

<span data-ttu-id="82687-105">Este tutorial apresenta uma experiência interativa de compilação de uma solução de exemplo passo a passo para aprender os conceitos do teste de unidade.</span><span class="sxs-lookup"><span data-stu-id="82687-105">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="82687-106">Se você preferir acompanhar o tutorial usando uma solução interna, [veja ou baixe o exemplo de código](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-mstest/) antes de começar.</span><span class="sxs-lookup"><span data-stu-id="82687-106">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-mstest/) before you begin.</span></span> <span data-ttu-id="82687-107">Para obter instruções de download, consulte [Exemplos e tutoriais](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="82687-107">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

### <a name="creating-the-source-project"></a><span data-ttu-id="82687-108">Criando o projeto de origem</span><span class="sxs-lookup"><span data-stu-id="82687-108">Creating the source project</span></span>

<span data-ttu-id="82687-109">Abra uma janela do shell.</span><span class="sxs-lookup"><span data-stu-id="82687-109">Open a shell window.</span></span> <span data-ttu-id="82687-110">Crie um diretório chamado *unit-testing-using-dotnet-test* para armazenar a solução.</span><span class="sxs-lookup"><span data-stu-id="82687-110">Create a directory called *unit-testing-using-dotnet-test* to hold the solution.</span></span> <span data-ttu-id="82687-111">Dentro desse novo diretório, crie um diretório *PrimeService*.</span><span class="sxs-lookup"><span data-stu-id="82687-111">Inside this new directory, create a *PrimeService* directory.</span></span> <span data-ttu-id="82687-112">A estrutura do diretório até o momento é mostrada abaixo:</span><span class="sxs-lookup"><span data-stu-id="82687-112">The directory structure thus far is shown below:</span></span>

```
/unit-testing-using-mstest
    /PrimeService
```

<span data-ttu-id="82687-113">Torne *PrimeService* o diretório atual e execute [`dotnet new classlib`](../tools/dotnet-new.md) para criar o projeto de origem.</span><span class="sxs-lookup"><span data-stu-id="82687-113">Make *PrimeService* the current directory and run [`dotnet new classlib`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="82687-114">Renomeie *Class1.cs* como *PrimeService.cs*.</span><span class="sxs-lookup"><span data-stu-id="82687-114">Rename *Class1.cs* to *PrimeService.cs*.</span></span> <span data-ttu-id="82687-115">Para usar TDD (Desenvolvimento Orientado por Testes), você criará uma implementação com falha da classe `PrimeService`:</span><span class="sxs-lookup"><span data-stu-id="82687-115">To use test-driven development (TDD), you'll create a failing implementation of the `PrimeService` class:</span></span>

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

### <a name="creating-the-test-project"></a><span data-ttu-id="82687-116">Criando o projeto de teste</span><span class="sxs-lookup"><span data-stu-id="82687-116">Creating the test project</span></span>

<span data-ttu-id="82687-117">Altere o diretório de volta para o diretório *unit-testing-using-mstest* e crie o diretório *PrimeService.Tests*.</span><span class="sxs-lookup"><span data-stu-id="82687-117">Change the directory back to the *unit-testing-using-mstest* directory and create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="82687-118">A estrutura do diretório é mostrada abaixo:</span><span class="sxs-lookup"><span data-stu-id="82687-118">The directory structure is shown below:</span></span>

```
/unit-testing-using-mstest
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

<span data-ttu-id="82687-119">Torne o diretório *PrimeService.Tests* o diretório atual e crie um novo projeto usando [`dotnet new mstest`](../tools/dotnet-new.md).</span><span class="sxs-lookup"><span data-stu-id="82687-119">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new mstest`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="82687-120">Isso cria um projeto de teste que usa o MSTest como a biblioteca de teste.</span><span class="sxs-lookup"><span data-stu-id="82687-120">This creates a test project that uses MStest as the test library.</span></span> <span data-ttu-id="82687-121">O modelo gerado configura o executor de teste no arquivo *PrimeServiceTests.csproj*:</span><span class="sxs-lookup"><span data-stu-id="82687-121">The generated template configures the test runner in the *PrimeServiceTests.csproj* file:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.0.0" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.11" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.11" />
</ItemGroup>
```

<span data-ttu-id="82687-122">O projeto de teste requer outros pacotes para criar e executar testes de unidade.</span><span class="sxs-lookup"><span data-stu-id="82687-122">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="82687-123">`dotnet new` da etapa anterior adicionou o SDK do MSTest, a estrutura de teste do MSTest e o executor do MSTest.</span><span class="sxs-lookup"><span data-stu-id="82687-123">`dotnet new` in the previous step added the MSTest SDK, the MSTest test framework, and the MSTest runner.</span></span> <span data-ttu-id="82687-124">Agora, adicione a biblioteca de classes `PrimeService` como outra dependência ao projeto.</span><span class="sxs-lookup"><span data-stu-id="82687-124">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="82687-125">Use o comando [`dotnet add reference`](../tools/dotnet-add-reference.md):</span><span class="sxs-lookup"><span data-stu-id="82687-125">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../PrimeService/PrimeService.csproj
```

<span data-ttu-id="82687-126">Outra opção é editar o arquivo *PrimeService.Tests.csproj*.</span><span class="sxs-lookup"><span data-stu-id="82687-126">Another option is to edit the *PrimeService.Tests.csproj* file.</span></span> <span data-ttu-id="82687-127">Diretamente sob o primeiro nó `<ItemGroup>`, adicione outro nó `<ItemGroup>` com uma referência ao projeto de biblioteca:</span><span class="sxs-lookup"><span data-stu-id="82687-127">Directly under the first `<ItemGroup>` node, add another `<ItemGroup>` node with a reference to the library project:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\PrimeService\PrimeService.csproj" />
</ItemGroup>
```

<span data-ttu-id="82687-128">Você pode ver o arquivo inteiro no [repositório de exemplos](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService.Tests.csproj) no GitHub.</span><span class="sxs-lookup"><span data-stu-id="82687-128">You can see the entire file in the [samples repository](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService.Tests.csproj) on GitHub.</span></span>

<span data-ttu-id="82687-129">O layout da solução final é mostrada abaixo:</span><span class="sxs-lookup"><span data-stu-id="82687-129">The final solution layout is shown below:</span></span>

```
/unit-testing-using-mstest
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        PrimeService
        PrimeServiceTests.csproj
```

## <a name="creating-the-first-test"></a><span data-ttu-id="82687-130">Criando o primeiro teste</span><span class="sxs-lookup"><span data-stu-id="82687-130">Creating the first test</span></span>

<span data-ttu-id="82687-131">Antes de compilar a biblioteca ou os testes, execute [`dotnet restore`](../tools/dotnet-restore.md) no diretório *PrimeService.Tests*.</span><span class="sxs-lookup"><span data-stu-id="82687-131">Before building the library or the tests, execute [`dotnet restore`](../tools/dotnet-restore.md) in the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="82687-132">Este comando restaura todos os pacotes NuGet necessários para cada projeto.</span><span class="sxs-lookup"><span data-stu-id="82687-132">This command restores all the necessary NuGet packages for each project.</span></span>

<span data-ttu-id="82687-133">A abordagem de TDD pede a criação de um teste com falha para fazê-lo passar e depois a repetição do processo.</span><span class="sxs-lookup"><span data-stu-id="82687-133">The TDD approach calls for writing one failing test, making it pass, then repeating the process.</span></span> <span data-ttu-id="82687-134">Remova *UnitTest1.cs* do diretório *PrimeService.Tests* e crie um novo arquivo C# chamado *PrimeService_IsPrimeShould.cs* com o seguinte conteúdo:</span><span class="sxs-lookup"><span data-stu-id="82687-134">Remove *UnitTest1.cs* from the *PrimeService.Tests* directory and create a new C# file named *PrimeService_IsPrimeShould.cs* with the following content:</span></span>

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
        public void ReturnFalseGivenValueOf1()
        {
            var result = _primeService.IsPrime(1);

            Assert.IsFalse(result, $"1 should not be prime");
        }
    }
}
```

<span data-ttu-id="82687-135">O atributo `[TestClass]` indica uma classe que contém testes de unidade.</span><span class="sxs-lookup"><span data-stu-id="82687-135">The `[TestClass]` attribute denotes a class that contains unit tests.</span></span> <span data-ttu-id="82687-136">O atributo `[TestMethod]` indica um método como um único teste.</span><span class="sxs-lookup"><span data-stu-id="82687-136">The `[TestMethod]` attribute denotes a method as a single test.</span></span> 

<span data-ttu-id="82687-137">Salve esse arquivo e execute [`dotnet test`](../tools/dotnet-test.md) para compilar os testes e a biblioteca de classes e, em seguida, execute os testes.</span><span class="sxs-lookup"><span data-stu-id="82687-137">Save this file and execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="82687-138">O executor de teste do MSTest contém o ponto de entrada do programa para executar os testes.</span><span class="sxs-lookup"><span data-stu-id="82687-138">The MSTest test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="82687-139">`dotnet test` inicia o executor de teste e fornece um argumento de linha de comando para o executor de teste, indicando o assembly que contém os testes.</span><span class="sxs-lookup"><span data-stu-id="82687-139">`dotnet test` starts the test runner and provides a command-line argument to the test runner indicating the assembly that contains your tests.</span></span>

<span data-ttu-id="82687-140">O teste falha.</span><span class="sxs-lookup"><span data-stu-id="82687-140">Your test fails.</span></span> <span data-ttu-id="82687-141">Você ainda não criou a implementação.</span><span class="sxs-lookup"><span data-stu-id="82687-141">You haven't created the implementation yet.</span></span> <span data-ttu-id="82687-142">Escreva o código mais simples na classe `PrimeService` para fazer esse teste ser aprovado:</span><span class="sxs-lookup"><span data-stu-id="82687-142">Write the simplest code in the `PrimeService` class to make this test pass:</span></span>

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

<span data-ttu-id="82687-143">No diretório *PrimeService.Tests*, execute `dotnet test` novamente.</span><span class="sxs-lookup"><span data-stu-id="82687-143">In the *PrimeService.Tests* directory, run `dotnet test` again.</span></span> <span data-ttu-id="82687-144">O comando `dotnet test` executa uma compilação para o projeto `PrimeService` e, depois, para o projeto `PrimeService.Tests`.</span><span class="sxs-lookup"><span data-stu-id="82687-144">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="82687-145">Depois de compilar os dois projetos, ele executará esse teste único.</span><span class="sxs-lookup"><span data-stu-id="82687-145">After building both projects, it runs this single test.</span></span> <span data-ttu-id="82687-146">Ele é aprovado.</span><span class="sxs-lookup"><span data-stu-id="82687-146">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="82687-147">Adicionando mais recursos</span><span class="sxs-lookup"><span data-stu-id="82687-147">Adding more features</span></span>

<span data-ttu-id="82687-148">Agora que você fez um teste ser aprovado, é hora de escrever mais.</span><span class="sxs-lookup"><span data-stu-id="82687-148">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="82687-149">Existem alguns outros casos simples de números primos: 0, -1.</span><span class="sxs-lookup"><span data-stu-id="82687-149">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="82687-150">Você pode adicioná-los como novos testes, com o atributo `[TestMethod]`, porém isso se torna entediante rapidamente.</span><span class="sxs-lookup"><span data-stu-id="82687-150">You could add those as new tests with the `[TestMethod]` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="82687-151">Há outros atributos do MSTest que permitem escrever um pacote de testes semelhantes.</span><span class="sxs-lookup"><span data-stu-id="82687-151">There are other MSTest attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="82687-152">Um atributo `[DataTestMethod]` representa um pacote de testes que executa o mesmo código, mas têm diferentes argumentos de entrada.</span><span class="sxs-lookup"><span data-stu-id="82687-152">A `[DataTestMethod]`attribute represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="82687-153">Você pode usar o atributo `[DataRow]` para especificar valores para essas entradas.</span><span class="sxs-lookup"><span data-stu-id="82687-153">You can use the `[DataRow]` attribute to specify values for those inputs.</span></span> 
 
<span data-ttu-id="82687-154">Em vez de criar novos testes, aproveite esses dois atributos para criar um único método de teste de dados que testa diversos valores inferiores a dois, que é o menor número primo:</span><span class="sxs-lookup"><span data-stu-id="82687-154">Instead of creating new tests, leverage these two attributes to create a single data test method that tests several values less than two, which is the lowest prime number:</span></span>

<span data-ttu-id="82687-155">[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]</span><span class="sxs-lookup"><span data-stu-id="82687-155">[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]</span></span>

<span data-ttu-id="82687-156">Execute `dotnet test`, e dois desses testes falham.</span><span class="sxs-lookup"><span data-stu-id="82687-156">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="82687-157">Para fazer todos os testes serem aprovados, altere a cláusula `if` no início do método:</span><span class="sxs-lookup"><span data-stu-id="82687-157">To make all of the tests pass, change the `if` clause at the beginning of the method:</span></span>

```csharp
if (candidate < 2)
```

<span data-ttu-id="82687-158">Continue iterando adicionando mais testes, mais teorias e mais código na biblioteca principal.</span><span class="sxs-lookup"><span data-stu-id="82687-158">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="82687-159">Você acabará com a [versão concluída dos testes](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs) e a [implementação completa da biblioteca](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-mstest/PrimeService/PrimeService.cs).</span><span class="sxs-lookup"><span data-stu-id="82687-159">You'll end up with the [finished version of the tests](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs) and the [complete implementation of the library](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-mstest/PrimeService/PrimeService.cs).</span></span>

<span data-ttu-id="82687-160">Você criou uma pequena biblioteca e um conjunto de testes de unidade para essa biblioteca.</span><span class="sxs-lookup"><span data-stu-id="82687-160">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="82687-161">Você estruturou a solução para que a adição de novos pacotes e testes seja tranquila, e você possa concentrar mais tempo e esforço na resolução dos objetivos do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="82687-161">You've structured the solution so that adding new packages and tests is seamless, and you can concentrate most of your time and effort on solving the goals of the applicaiton.</span></span>

