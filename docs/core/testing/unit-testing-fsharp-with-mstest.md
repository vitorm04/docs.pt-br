---
title: Bibliotecas do F# de teste de unidade no .NET Core usando dotnet test e MSTest
description: "Aprenda os conceitos de teste de unidade para F# no .NET Core por meio de uma experiência interativa de criação passo a passo de uma solução de exemplo usando dotnet test e MSTest."
author: billwagner
ms.author: wiwagn
ms.date: 08/30/2017
ms.topic: article
dev_langs:
- fsharp
ms.prod: .net-core
ms.workload:
- dotnetcore
ms.openlocfilehash: 6dc5388f8e5645530cdd12986a9e1e53e4115c9a
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-mstest"></a><span data-ttu-id="ada81-103">Bibliotecas do F# de teste de unidade no .NET Core usando dotnet test e MSTest</span><span class="sxs-lookup"><span data-stu-id="ada81-103">Unit testing F# libraries in .NET Core using dotnet test and MSTest</span></span>

<span data-ttu-id="ada81-104">Este tutorial apresenta uma experiência interativa de compilação de uma solução de exemplo passo a passo para aprender os conceitos do teste de unidade.</span><span class="sxs-lookup"><span data-stu-id="ada81-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="ada81-105">Se você preferir acompanhar o tutorial usando uma solução interna, [veja ou baixe o exemplo de código](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/unit-testing-with-fsharp-mstest/) antes de começar.</span><span class="sxs-lookup"><span data-stu-id="ada81-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/unit-testing-with-fsharp-mstest/) before you begin.</span></span> <span data-ttu-id="ada81-106">Para obter instruções de download, consulte [Exemplos e tutoriais](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="ada81-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="ada81-107">Criando o projeto de origem</span><span class="sxs-lookup"><span data-stu-id="ada81-107">Creating the source project</span></span>

<span data-ttu-id="ada81-108">Abra uma janela do shell.</span><span class="sxs-lookup"><span data-stu-id="ada81-108">Open a shell window.</span></span> <span data-ttu-id="ada81-109">Crie um diretório chamado *unit-testing-with-fsharp* para armazenar a solução.</span><span class="sxs-lookup"><span data-stu-id="ada81-109">Create a directory called *unit-testing-with-fsharp* to hold the solution.</span></span>
<span data-ttu-id="ada81-110">Nesse novo diretório, execute [`dotnet new sln`](../tools/dotnet-new.md) para criar uma nova solução.</span><span class="sxs-lookup"><span data-stu-id="ada81-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution.</span></span> <span data-ttu-id="ada81-111">Isso facilita o gerenciamento da biblioteca de classes e o projeto de teste de unidade.</span><span class="sxs-lookup"><span data-stu-id="ada81-111">This makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="ada81-112">No diretório da solução, crie um diretório *MathService*.</span><span class="sxs-lookup"><span data-stu-id="ada81-112">Inside the solution directory, create a *MathService* directory.</span></span> <span data-ttu-id="ada81-113">A estrutura de arquivo e diretório até aqui é mostrada abaixo:</span><span class="sxs-lookup"><span data-stu-id="ada81-113">The directory and file structure thus far is shown below:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

<span data-ttu-id="ada81-114">Torne *MathService* o diretório atual e execute [`dotnet new classlib -lang F#`](../tools/dotnet-new.md) para criar o projeto de origem.</span><span class="sxs-lookup"><span data-stu-id="ada81-114">Make *MathService* the current directory and run [`dotnet new classlib -lang F#`](../tools/dotnet-new.md) to create the source project.</span></span>  <span data-ttu-id="ada81-115">Para usar o TDD (Desenvolvimento Orientado por Testes), você criará uma implementação com falha do serviço math:</span><span class="sxs-lookup"><span data-stu-id="ada81-115">To use test-driven development (TDD), you'll create a failing implementation of the math service:</span></span>

```fsharp
module MyMath =
    let sumOfSquares xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

<span data-ttu-id="ada81-116">Altere o diretório de volta para o diretório *unit-testing-with-fsharp*.</span><span class="sxs-lookup"><span data-stu-id="ada81-116">Change the directory back to the *unit-testing-with-fsharp* directory.</span></span> <span data-ttu-id="ada81-117">Execute [`dotnet sln add .\MathService\MathService.fsproj`](../tools/dotnet-sln.md) para adicionar o projeto de biblioteca de classes à solução.</span><span class="sxs-lookup"><span data-stu-id="ada81-117">Run [`dotnet sln add .\MathService\MathService.fsproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="creating-the-test-project"></a><span data-ttu-id="ada81-118">Criando o projeto de teste</span><span class="sxs-lookup"><span data-stu-id="ada81-118">Creating the test project</span></span>

<span data-ttu-id="ada81-119">Em seguida, crie o diretório *MathService.Tests*.</span><span class="sxs-lookup"><span data-stu-id="ada81-119">Next, create the *MathService.Tests* directory.</span></span> <span data-ttu-id="ada81-120">O seguinte esquema mostra a estrutura do diretório:</span><span class="sxs-lookup"><span data-stu-id="ada81-120">The following outline shows the directory structure:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

<span data-ttu-id="ada81-121">Torne o diretório *MathService.Tests* o diretório atual e crie um novo projeto usando [`dotnet new mstest -lang F#`](../tools/dotnet-new.md).</span><span class="sxs-lookup"><span data-stu-id="ada81-121">Make the *MathService.Tests* directory the current directory and create a new project using [`dotnet new mstest -lang F#`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="ada81-122">Isso cria um projeto de teste que usa o MSTest como a estrutura de teste.</span><span class="sxs-lookup"><span data-stu-id="ada81-122">This creates a test project that uses MSTest as the test framework.</span></span> <span data-ttu-id="ada81-123">O modelo gerado configura o executor de teste no *MathServiceTests.fsproj*:</span><span class="sxs-lookup"><span data-stu-id="ada81-123">The generated template configures the test runner in the *MathServiceTests.fsproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.18" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.18" />
</ItemGroup>
```

<span data-ttu-id="ada81-124">O projeto de teste requer outros pacotes para criar e executar testes de unidade.</span><span class="sxs-lookup"><span data-stu-id="ada81-124">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="ada81-125">`dotnet new`, na etapa anterior, adicionou MSTest e o executor de MSTest.</span><span class="sxs-lookup"><span data-stu-id="ada81-125">`dotnet new` in the previous step added MSTest and the MSTest runner.</span></span> <span data-ttu-id="ada81-126">Agora, adicione a biblioteca de classes `MathService` como outra dependência ao projeto.</span><span class="sxs-lookup"><span data-stu-id="ada81-126">Now, add the `MathService` class library as another dependency to the project.</span></span> <span data-ttu-id="ada81-127">Use o comando [`dotnet add reference`](../tools/dotnet-add-reference.md):</span><span class="sxs-lookup"><span data-stu-id="ada81-127">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../MathService/MathService.fsproj
```

<span data-ttu-id="ada81-128">Você pode ver o arquivo inteiro no [repositório de exemplos](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) no GitHub.</span><span class="sxs-lookup"><span data-stu-id="ada81-128">You can see the entire file in the [samples repository](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) on GitHub.</span></span>

<span data-ttu-id="ada81-129">Você tem o seguinte layout de solução final:</span><span class="sxs-lookup"><span data-stu-id="ada81-129">You have the following final solution layout:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
        Test Source Files
        MathServiceTests.fsproj
```

<span data-ttu-id="ada81-130">Execute [`dotnet sln add .\MathService.Tests\MathService.Tests.fsproj`](../tools/dotnet-sln.md) no diretório *unit-testing-with-fsharp*.</span><span class="sxs-lookup"><span data-stu-id="ada81-130">Execute [`dotnet sln add .\MathService.Tests\MathService.Tests.fsproj`](../tools/dotnet-sln.md) in the *unit-testing-with-fsharp* directory.</span></span>

## <a name="creating-the-first-test"></a><span data-ttu-id="ada81-131">Criando o primeiro teste</span><span class="sxs-lookup"><span data-stu-id="ada81-131">Creating the first test</span></span>

<span data-ttu-id="ada81-132">A abordagem de TDD pede a criação de um teste com falha para fazê-lo passar e depois a repetição do processo.</span><span class="sxs-lookup"><span data-stu-id="ada81-132">The TDD approach calls for writing one failing test, making it pass, then repeating the process.</span></span> <span data-ttu-id="ada81-133">Abra *Tests.fs* e adicione o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="ada81-133">Open *Tests.fs* and add the following code:</span></span>

```fsharp
namespace MathService.Tests

open System
open Microsoft.VisualStudio.TestTools.UnitTesting
open MathService

[<TestClass>]
type TestClass () =

    [<TestMethod>]
    member this.TestMethodPassing() =
        Assert.IsTrue(true)

    [<TestMethod>]
     member this.FailEveryTime() = Assert.IsTrue(false)
```

<span data-ttu-id="ada81-134">O atributo `[<TestClass>]` indica uma classe que contém testes.</span><span class="sxs-lookup"><span data-stu-id="ada81-134">The `[<TestClass>]` attribute denotes a class that contains tests.</span></span> <span data-ttu-id="ada81-135">O atributo `[<TestMethod>]` indica um método de teste que é executado pelo executor de teste.</span><span class="sxs-lookup"><span data-stu-id="ada81-135">The `[<TestMethod>]` attribute denotes a test method that is run by the test runner.</span></span> <span data-ttu-id="ada81-136">No diretório *unit-testing-with-fsharp*, execute [`dotnet test`](../tools/dotnet-test.md) para criar os testes e a biblioteca de classes e execute os testes.</span><span class="sxs-lookup"><span data-stu-id="ada81-136">From the *unit-testing-with-fsharp* directory, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="ada81-137">O executor de teste do MSTest contém o ponto de entrada do programa para executar os testes.</span><span class="sxs-lookup"><span data-stu-id="ada81-137">The MSTest test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="ada81-138">`dotnet test` inicia o executor de teste usando o projeto de teste de unidade que você criou.</span><span class="sxs-lookup"><span data-stu-id="ada81-138">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="ada81-139">Esses dois testes mostram testes com aprovação e falha mais básicos.</span><span class="sxs-lookup"><span data-stu-id="ada81-139">These two tests show the most basic passing and failing tests.</span></span> <span data-ttu-id="ada81-140">`My test` é aprovado e `Fail every time` falha.</span><span class="sxs-lookup"><span data-stu-id="ada81-140">`My test` passes, and `Fail every time` fails.</span></span> <span data-ttu-id="ada81-141">Agora, crie um teste para o método `sumOfSquares`.</span><span class="sxs-lookup"><span data-stu-id="ada81-141">Now, create a test for the `sumOfSquares` method.</span></span> <span data-ttu-id="ada81-142">O método `sumOfSquares` retorna a soma dos quadrados de todos os valores inteiros ímpares que fazem parte da sequência de entrada.</span><span class="sxs-lookup"><span data-stu-id="ada81-142">The `sumOfSquares` method returns the sum of the squares of all odd integer values that are part of the input sequence.</span></span> <span data-ttu-id="ada81-143">Em vez de tentar gravar todas as funções de uma vez, você pode criar testes iterativamente que validam a funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="ada81-143">Rather than trying to write all of those functions at once, you can iteratively create tests that validate the functionality.</span></span> <span data-ttu-id="ada81-144">Fazer com que cada teste passe significa criar a funcionalidade necessária para o método.</span><span class="sxs-lookup"><span data-stu-id="ada81-144">Making each test pass means creating the necessary functionality for the method.</span></span>

<span data-ttu-id="ada81-145">O teste mais simples que podemos escrever é chamar `sumOfSquares` com todos os números pares, em que o resultado deve ser uma sequência vazia de inteiros.</span><span class="sxs-lookup"><span data-stu-id="ada81-145">The simplest test we can write is to call `sumOfSquares` with all even numbers, where the result should be an empty sequence of integers.</span></span>  <span data-ttu-id="ada81-146">Este é o teste:</span><span class="sxs-lookup"><span data-stu-id="ada81-146">Here's that test:</span></span>

```fsharp
[<TestMethod>]
member this.TestEvenSequence() =
    let expected = Seq.empty<int> |> Seq.toList
    let actual = MyMath.sumOfSquares [2; 4; 6; 8; 10]
    Assert.AreEqual(expected, actual)
```

<span data-ttu-id="ada81-147">Observe que a sequência `expected` foi convertida em uma lista.</span><span class="sxs-lookup"><span data-stu-id="ada81-147">Notice that the `expected` sequence has been converted to a list.</span></span> <span data-ttu-id="ada81-148">A biblioteca do MSTest depende de muitos tipos padrão de .NET.</span><span class="sxs-lookup"><span data-stu-id="ada81-148">The MSTest library relies on many standard .NET types.</span></span> <span data-ttu-id="ada81-149">Essa dependência significa que sua interface pública e os resultados esperados dão suporte a <xref:System.Collections.ICollection> em vez de <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="ada81-149">That dependency means that your public interface and expected results support <xref:System.Collections.ICollection> rather than <xref:System.Collections.IEnumerable>.</span></span>

<span data-ttu-id="ada81-150">Ao executar o teste, você verá que ele falha.</span><span class="sxs-lookup"><span data-stu-id="ada81-150">When you run the test, you see that your test fails.</span></span> <span data-ttu-id="ada81-151">Você ainda não criou a implementação.</span><span class="sxs-lookup"><span data-stu-id="ada81-151">You haven't created the implementation yet.</span></span> <span data-ttu-id="ada81-152">Faça esse teste escrevendo o código mais simples na classe `Mathservice` que funciona:</span><span class="sxs-lookup"><span data-stu-id="ada81-152">Make this test by writing the simplest code in the `Mathservice` class that works:</span></span>

```csharp
let sumOfSquares xs =
    Seq.empty<int> |> Seq.toList
```

<span data-ttu-id="ada81-153">No diretório *unit-testing-with-fsharp*, execute `dotnet test` novamente.</span><span class="sxs-lookup"><span data-stu-id="ada81-153">In the *unit-testing-with-fsharp* directory, run `dotnet test` again.</span></span> <span data-ttu-id="ada81-154">O comando `dotnet test` executa uma compilação para o projeto `MathService` e, depois, para o projeto `MathService.Tests`.</span><span class="sxs-lookup"><span data-stu-id="ada81-154">The `dotnet test` command runs a build for the `MathService` project and then for the `MathService.Tests` project.</span></span> <span data-ttu-id="ada81-155">Depois de compilar os dois projetos, ele executará esse teste único.</span><span class="sxs-lookup"><span data-stu-id="ada81-155">After building both projects, it runs this single test.</span></span> <span data-ttu-id="ada81-156">Ele é aprovado.</span><span class="sxs-lookup"><span data-stu-id="ada81-156">It passes.</span></span>

## <a name="completing-the-requirements"></a><span data-ttu-id="ada81-157">Como atender aos requisitos</span><span class="sxs-lookup"><span data-stu-id="ada81-157">Completing the requirements</span></span>

<span data-ttu-id="ada81-158">Agora que você fez um teste ser aprovado, é hora de escrever mais.</span><span class="sxs-lookup"><span data-stu-id="ada81-158">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="ada81-159">O próximo caso simples funciona com uma sequência cujo único número ímpar é `1`.</span><span class="sxs-lookup"><span data-stu-id="ada81-159">The next simple case works with a sequence whose only odd number is `1`.</span></span> <span data-ttu-id="ada81-160">O número 1 é mais fácil, pois o quadrado de 1 é 1.</span><span class="sxs-lookup"><span data-stu-id="ada81-160">The number 1 is easier because the square of 1 is 1.</span></span> <span data-ttu-id="ada81-161">Este é o próximo teste:</span><span class="sxs-lookup"><span data-stu-id="ada81-161">Here's that next test:</span></span>

```fsharp
[<TestMethod>]
member public this.SumOnesAndEvens() =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.sumOfSquares [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.AreEqual(expected, actual)
```

<span data-ttu-id="ada81-162">A execução de `dotnet test` falha no novo teste.</span><span class="sxs-lookup"><span data-stu-id="ada81-162">Executing `dotnet test` fails the new test.</span></span> <span data-ttu-id="ada81-163">Você deve atualizar o método `sumOfSquares` para lidar com esse novo teste.</span><span class="sxs-lookup"><span data-stu-id="ada81-163">You must update the `sumOfSquares` method to handle this new test.</span></span> <span data-ttu-id="ada81-164">É preciso remover todos os números pares da sequência para que esse teste seja aprovado.</span><span class="sxs-lookup"><span data-stu-id="ada81-164">You must filter all the even numbers out of the sequence to make this test pass.</span></span> <span data-ttu-id="ada81-165">Faça isso escrevendo uma pequena função de filtro e usando `Seq.filter`:</span><span class="sxs-lookup"><span data-stu-id="ada81-165">You can do that by writing a small filter function and using `Seq.filter`:</span></span>

```fsharp
let private isOdd x = x % 2 <> 0

let sumOfSquares xs =
    xs
    |> Seq.filter isOdd |> Seq.toList
```

<span data-ttu-id="ada81-166">Observe a chamada a `Seq.toList`.</span><span class="sxs-lookup"><span data-stu-id="ada81-166">Notice the call to `Seq.toList`.</span></span> <span data-ttu-id="ada81-167">Isso cria uma lista, que implementa a interface <xref:System.Collections.ICollection>.</span><span class="sxs-lookup"><span data-stu-id="ada81-167">That creates a list, which implements the <xref:System.Collections.ICollection> interface.</span></span>

<span data-ttu-id="ada81-168">Há mais uma etapa a ser executada: eleve ao quadrado cada um dos números ímpares.</span><span class="sxs-lookup"><span data-stu-id="ada81-168">There's one more step to go: square each of the odd numbers.</span></span> <span data-ttu-id="ada81-169">Comece escrevendo um novo teste:</span><span class="sxs-lookup"><span data-stu-id="ada81-169">Start by writing a new test:</span></span>

```fsharp
[<TestMethod>]
member public this.TestSquaresOfOdds() =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.sumOfSquares [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.AreEqual(expected, actual)
```

<span data-ttu-id="ada81-170">Você pode corrigir o teste redirecionando a sequência filtrada por meio de uma operação de mapa para calcular o quadrado de cada número ímpar:</span><span class="sxs-lookup"><span data-stu-id="ada81-170">You can fix the test by piping the filtered sequence through a map operation to compute the square of each odd number:</span></span>

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let sumOfSquares xs =
    xs
    |> Seq.filter isOdd
    |> Seq.map square
    |> Seq.toList
```

<span data-ttu-id="ada81-171">Você criou uma pequena biblioteca e um conjunto de testes de unidade para essa biblioteca.</span><span class="sxs-lookup"><span data-stu-id="ada81-171">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="ada81-172">Você estruturou a solução para que a adição de novos pacotes e testes fizesse parte do fluxo de trabalho normal.</span><span class="sxs-lookup"><span data-stu-id="ada81-172">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="ada81-173">Você concentrou grande parte do seu tempo e esforço em resolver as metas do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ada81-173">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
