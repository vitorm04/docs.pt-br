---
title: Teste de unidade de bibliotecas do F# no .NET Core usando dotnet test e NUnit
description: Aprenda os conceitos de teste de unidade para F# no .NET Core por meio de uma experiência interativa de criação passo a passo de uma solução de exemplo usando dotnet test e NUnit.
author: rprouse
ms.date: 12/01/2017
ms.topic: conceptual
dev_langs:
- fsharp
ms.prod: dotnet-core
ms.workload:
- dotnetcore
ms.openlocfilehash: f5793c79177e919547b9daa9b8fd2523938d3c66
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-nunit"></a><span data-ttu-id="24371-103">Teste de unidade de bibliotecas do F# no .NET Core usando dotnet test e NUnit</span><span class="sxs-lookup"><span data-stu-id="24371-103">Unit testing F# libraries in .NET Core using dotnet test and NUnit</span></span>

<span data-ttu-id="24371-104">Este tutorial apresenta uma experiência interativa de compilação de uma solução de exemplo passo a passo para aprender os conceitos do teste de unidade.</span><span class="sxs-lookup"><span data-stu-id="24371-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="24371-105">Se você preferir acompanhar o tutorial usando uma solução interna, [veja ou baixe o exemplo de código](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-nunit/) antes de começar.</span><span class="sxs-lookup"><span data-stu-id="24371-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-nunit/) before you begin.</span></span> <span data-ttu-id="24371-106">Para obter instruções de download, consulte [Exemplos e tutoriais](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="24371-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="24371-107">Criando o projeto de origem</span><span class="sxs-lookup"><span data-stu-id="24371-107">Creating the source project</span></span>

<span data-ttu-id="24371-108">Abra uma janela do shell.</span><span class="sxs-lookup"><span data-stu-id="24371-108">Open a shell window.</span></span> <span data-ttu-id="24371-109">Crie um diretório chamado *unit-testing-with-fsharp* para armazenar a solução.</span><span class="sxs-lookup"><span data-stu-id="24371-109">Create a directory called *unit-testing-with-fsharp* to hold the solution.</span></span>
<span data-ttu-id="24371-110">Nesse novo diretório, execute [`dotnet new sln`](../tools/dotnet-new.md) para criar uma nova solução.</span><span class="sxs-lookup"><span data-stu-id="24371-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution.</span></span> <span data-ttu-id="24371-111">Isso facilita o gerenciamento da biblioteca de classes e o projeto de teste de unidade.</span><span class="sxs-lookup"><span data-stu-id="24371-111">This makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="24371-112">No diretório da solução, crie um diretório *MathService*.</span><span class="sxs-lookup"><span data-stu-id="24371-112">Inside the solution directory, create a *MathService* directory.</span></span> <span data-ttu-id="24371-113">A estrutura de arquivo e diretório até aqui é mostrada abaixo:</span><span class="sxs-lookup"><span data-stu-id="24371-113">The directory and file structure thus far is shown below:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

<span data-ttu-id="24371-114">Torne *MathService* o diretório atual e execute [`dotnet new classlib -lang F#`](../tools/dotnet-new.md) para criar o projeto de origem.</span><span class="sxs-lookup"><span data-stu-id="24371-114">Make *MathService* the current directory and run [`dotnet new classlib -lang F#`](../tools/dotnet-new.md) to create the source project.</span></span>  <span data-ttu-id="24371-115">Para usar o TDD (Desenvolvimento Orientado por Testes), você criará uma implementação com falha do serviço math:</span><span class="sxs-lookup"><span data-stu-id="24371-115">To use test-driven development (TDD), you'll create a failing implementation of the math service:</span></span>

```fsharp
module MyMath =
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

<span data-ttu-id="24371-116">Altere o diretório de volta para o diretório *unit-testing-with-fsharp*.</span><span class="sxs-lookup"><span data-stu-id="24371-116">Change the directory back to the *unit-testing-with-fsharp* directory.</span></span> <span data-ttu-id="24371-117">Execute [`dotnet sln add .\MathService\MathService.fsproj`](../tools/dotnet-sln.md) para adicionar o projeto de biblioteca de classes à solução.</span><span class="sxs-lookup"><span data-stu-id="24371-117">Run [`dotnet sln add .\MathService\MathService.fsproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="install-the-nunit-project-template"></a><span data-ttu-id="24371-118">Instalar o modelo de projeto do NUnit</span><span class="sxs-lookup"><span data-stu-id="24371-118">Install the NUnit project template</span></span>

<span data-ttu-id="24371-119">Os modelos de projeto de teste do NUnit precisam ser instalados antes de criar um projeto de teste.</span><span class="sxs-lookup"><span data-stu-id="24371-119">The NUnit test project templates need to be installed before creating a test project.</span></span> <span data-ttu-id="24371-120">Isso precisa ser feito somente uma vez em cada computador de desenvolvedor em que você criará novos projetos NUnit.</span><span class="sxs-lookup"><span data-stu-id="24371-120">This only needs to be done once on each developer machine where you'll create new NUnit projects.</span></span> <span data-ttu-id="24371-121">Execute [`dotnet new -i NUnit3.DotNetNew.Template`](../tools/dotnet-new.md) para instalar os modelos do NUnit.</span><span class="sxs-lookup"><span data-stu-id="24371-121">Run [`dotnet new -i NUnit3.DotNetNew.Template`](../tools/dotnet-new.md) to install the NUnit templates.</span></span>

 ```
 dotnet new -i NUnit3.DotNetNew.Template
 ```

## <a name="creating-the-test-project"></a><span data-ttu-id="24371-122">Criando o projeto de teste</span><span class="sxs-lookup"><span data-stu-id="24371-122">Creating the test project</span></span>

<span data-ttu-id="24371-123">Em seguida, crie o diretório *MathService.Tests*.</span><span class="sxs-lookup"><span data-stu-id="24371-123">Next, create the *MathService.Tests* directory.</span></span> <span data-ttu-id="24371-124">O seguinte esquema mostra a estrutura do diretório:</span><span class="sxs-lookup"><span data-stu-id="24371-124">The following outline shows the directory structure:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

<span data-ttu-id="24371-125">Torne o diretório *MathService.Tests* o diretório atual e crie um novo projeto usando [`dotnet new nunit -lang F#`](../tools/dotnet-new.md).</span><span class="sxs-lookup"><span data-stu-id="24371-125">Make the *MathService.Tests* directory the current directory and create a new project using [`dotnet new nunit -lang F#`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="24371-126">Isso cria um projeto de teste que usa o NUnit como a estrutura de teste.</span><span class="sxs-lookup"><span data-stu-id="24371-126">This creates a test project that uses NUnit as the test framework.</span></span> <span data-ttu-id="24371-127">O modelo gerado configura o executor de teste no *MathServiceTests.fsproj*:</span><span class="sxs-lookup"><span data-stu-id="24371-127">The generated template configures the test runner in the *MathServiceTests.fsproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.5.0" />
  <PackageReference Include="NUnit" Version="3.9.0" />
  <PackageReference Include="NUnit3TestAdapter" Version="3.9.0" />
</ItemGroup>
```

<span data-ttu-id="24371-128">O projeto de teste requer outros pacotes para criar e executar testes de unidade.</span><span class="sxs-lookup"><span data-stu-id="24371-128">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="24371-129">O `dotnet new` na etapa anterior adicionou o NUnit e o adaptador de teste do NUnit.</span><span class="sxs-lookup"><span data-stu-id="24371-129">`dotnet new` in the previous step added NUnit and the NUnit test adapter.</span></span> <span data-ttu-id="24371-130">Agora, adicione a biblioteca de classes `MathService` como outra dependência ao projeto.</span><span class="sxs-lookup"><span data-stu-id="24371-130">Now, add the `MathService` class library as another dependency to the project.</span></span> <span data-ttu-id="24371-131">Use o comando [`dotnet add reference`](../tools/dotnet-add-reference.md):</span><span class="sxs-lookup"><span data-stu-id="24371-131">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../MathService/MathService.fsproj
```

<span data-ttu-id="24371-132">Você pode ver o arquivo inteiro no [repositório de exemplos](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) no GitHub.</span><span class="sxs-lookup"><span data-stu-id="24371-132">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) on GitHub.</span></span>

<span data-ttu-id="24371-133">Você tem o seguinte layout de solução final:</span><span class="sxs-lookup"><span data-stu-id="24371-133">You have the following final solution layout:</span></span>

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

<span data-ttu-id="24371-134">Execute [`dotnet sln add .\MathService.Tests\MathService.Tests.fsproj`](../tools/dotnet-sln.md) no diretório *unit-testing-with-fsharp*.</span><span class="sxs-lookup"><span data-stu-id="24371-134">Execute [`dotnet sln add .\MathService.Tests\MathService.Tests.fsproj`](../tools/dotnet-sln.md) in the *unit-testing-with-fsharp* directory.</span></span>

## <a name="creating-the-first-test"></a><span data-ttu-id="24371-135">Criando o primeiro teste</span><span class="sxs-lookup"><span data-stu-id="24371-135">Creating the first test</span></span>

<span data-ttu-id="24371-136">A abordagem de TDD pede a criação de um teste com falha para fazê-lo passar e depois a repetição do processo.</span><span class="sxs-lookup"><span data-stu-id="24371-136">The TDD approach calls for writing one failing test, making it pass, then repeating the process.</span></span> <span data-ttu-id="24371-137">Abra *Tests.fs* e adicione o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="24371-137">Open *Tests.fs* and add the following code:</span></span>

```fsharp
namespace MathService.Tests

open System
open NUnit.Framework
open MathService

[<TestFixture>]
type TestClass () =

    [<Test>]
    member this.TestMethodPassing() =
        Assert.True(true)

    [<Test>]
     member this.FailEveryTime() = Assert.True(false)
```

<span data-ttu-id="24371-138">O atributo `[<TestFixture>]` indica uma classe que contém testes.</span><span class="sxs-lookup"><span data-stu-id="24371-138">The `[<TestFixture>]` attribute denotes a class that contains tests.</span></span> <span data-ttu-id="24371-139">O atributo `[<Test>]` indica um método de teste que é executado pelo executor de teste.</span><span class="sxs-lookup"><span data-stu-id="24371-139">The `[<Test>]` attribute denotes a test method that is run by the test runner.</span></span> <span data-ttu-id="24371-140">No diretório *unit-testing-with-fsharp*, execute [`dotnet test`](../tools/dotnet-test.md) para criar os testes e a biblioteca de classes e execute os testes.</span><span class="sxs-lookup"><span data-stu-id="24371-140">From the *unit-testing-with-fsharp* directory, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="24371-141">O executor de teste do NUnit contém o ponto de entrada do programa para executar os testes.</span><span class="sxs-lookup"><span data-stu-id="24371-141">The NUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="24371-142">`dotnet test` inicia o executor de teste usando o projeto de teste de unidade que você criou.</span><span class="sxs-lookup"><span data-stu-id="24371-142">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="24371-143">Esses dois testes mostram testes com aprovação e falha mais básicos.</span><span class="sxs-lookup"><span data-stu-id="24371-143">These two tests show the most basic passing and failing tests.</span></span> <span data-ttu-id="24371-144">`My test` é aprovado e `Fail every time` falha.</span><span class="sxs-lookup"><span data-stu-id="24371-144">`My test` passes, and `Fail every time` fails.</span></span> <span data-ttu-id="24371-145">Agora, crie um teste para o método `squaresOfOdds`.</span><span class="sxs-lookup"><span data-stu-id="24371-145">Now, create a test for the `squaresOfOdds` method.</span></span> <span data-ttu-id="24371-146">O método `squaresOfOdds` retorna uma sequência dos quadrados de todos os valores inteiros ímpares que fazem parte da sequência de entrada.</span><span class="sxs-lookup"><span data-stu-id="24371-146">The `squaresOfOdds` method returns a sequence of the squares of all odd integer values that are part of the input sequence.</span></span> <span data-ttu-id="24371-147">Em vez de tentar gravar todas as funções de uma vez, você pode criar testes iterativamente que validam a funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="24371-147">Rather than trying to write all of those functions at once, you can iteratively create tests that validate the functionality.</span></span> <span data-ttu-id="24371-148">Fazer com que cada teste passe significa criar a funcionalidade necessária para o método.</span><span class="sxs-lookup"><span data-stu-id="24371-148">Making each test pass means creating the necessary functionality for the method.</span></span>

<span data-ttu-id="24371-149">O teste mais simples que podemos escrever é chamar `squaresOfOdds` com todos os números pares, em que o resultado deve ser uma sequência vazia de inteiros.</span><span class="sxs-lookup"><span data-stu-id="24371-149">The simplest test we can write is to call `squaresOfOdds` with all even numbers, where the result should be an empty sequence of integers.</span></span>  <span data-ttu-id="24371-150">Este é o teste:</span><span class="sxs-lookup"><span data-stu-id="24371-150">Here's that test:</span></span>

```fsharp
[<Test>]
member this.TestEvenSequence() =
    let expected = Seq.empty<int>
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

<span data-ttu-id="24371-151">Observe que a sequência `expected` foi convertida em uma lista.</span><span class="sxs-lookup"><span data-stu-id="24371-151">Notice that the `expected` sequence has been converted to a list.</span></span> <span data-ttu-id="24371-152">A estrutura do NUnit depende de muitos tipos padrão de .NET.</span><span class="sxs-lookup"><span data-stu-id="24371-152">The NUnit framework relies on many standard .NET types.</span></span> <span data-ttu-id="24371-153">Essa dependência significa que sua interface pública e os resultados esperados dão suporte a <xref:System.Collections.ICollection> em vez de <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="24371-153">That dependency means that your public interface and expected results support <xref:System.Collections.ICollection> rather than <xref:System.Collections.IEnumerable>.</span></span>

<span data-ttu-id="24371-154">Ao executar o teste, você verá que ele falha.</span><span class="sxs-lookup"><span data-stu-id="24371-154">When you run the test, you see that your test fails.</span></span> <span data-ttu-id="24371-155">Você ainda não criou a implementação.</span><span class="sxs-lookup"><span data-stu-id="24371-155">You haven't created the implementation yet.</span></span> <span data-ttu-id="24371-156">Faça esse teste escrevendo o código mais simples na classe `Mathservice` que funciona:</span><span class="sxs-lookup"><span data-stu-id="24371-156">Make this test by writing the simplest code in the `Mathservice` class that works:</span></span>

```csharp
let squaresOfOdds xs =
    Seq.empty<int>
```

<span data-ttu-id="24371-157">No diretório *unit-testing-with-fsharp*, execute `dotnet test` novamente.</span><span class="sxs-lookup"><span data-stu-id="24371-157">In the *unit-testing-with-fsharp* directory, run `dotnet test` again.</span></span> <span data-ttu-id="24371-158">O comando `dotnet test` executa uma compilação para o projeto `MathService` e, depois, para o projeto `MathService.Tests`.</span><span class="sxs-lookup"><span data-stu-id="24371-158">The `dotnet test` command runs a build for the `MathService` project and then for the `MathService.Tests` project.</span></span> <span data-ttu-id="24371-159">Depois de compilar os dois projetos, ele executará esse teste único.</span><span class="sxs-lookup"><span data-stu-id="24371-159">After building both projects, it runs this single test.</span></span> <span data-ttu-id="24371-160">Ele é aprovado.</span><span class="sxs-lookup"><span data-stu-id="24371-160">It passes.</span></span>

## <a name="completing-the-requirements"></a><span data-ttu-id="24371-161">Como atender aos requisitos</span><span class="sxs-lookup"><span data-stu-id="24371-161">Completing the requirements</span></span>

<span data-ttu-id="24371-162">Agora que você fez um teste ser aprovado, é hora de escrever mais.</span><span class="sxs-lookup"><span data-stu-id="24371-162">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="24371-163">O próximo caso simples funciona com uma sequência cujo único número ímpar é `1`.</span><span class="sxs-lookup"><span data-stu-id="24371-163">The next simple case works with a sequence whose only odd number is `1`.</span></span> <span data-ttu-id="24371-164">O número 1 é mais fácil, pois o quadrado de 1 é 1.</span><span class="sxs-lookup"><span data-stu-id="24371-164">The number 1 is easier because the square of 1 is 1.</span></span> <span data-ttu-id="24371-165">Este é o próximo teste:</span><span class="sxs-lookup"><span data-stu-id="24371-165">Here's that next test:</span></span>

```fsharp
[<Test>]
member public this.TestOnesAndEvens() =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

<span data-ttu-id="24371-166">A execução de `dotnet test` falha no novo teste.</span><span class="sxs-lookup"><span data-stu-id="24371-166">Executing `dotnet test` fails the new test.</span></span> <span data-ttu-id="24371-167">Você deve atualizar o método `squaresOfOdds` para lidar com esse novo teste.</span><span class="sxs-lookup"><span data-stu-id="24371-167">You must update the `squaresOfOdds` method to handle this new test.</span></span> <span data-ttu-id="24371-168">É preciso remover todos os números pares da sequência para que esse teste seja aprovado.</span><span class="sxs-lookup"><span data-stu-id="24371-168">You must filter all the even numbers out of the sequence to make this test pass.</span></span> <span data-ttu-id="24371-169">Faça isso escrevendo uma pequena função de filtro e usando `Seq.filter`:</span><span class="sxs-lookup"><span data-stu-id="24371-169">You can do that by writing a small filter function and using `Seq.filter`:</span></span>

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
```

<span data-ttu-id="24371-170">Observe a chamada a `Seq.toList`.</span><span class="sxs-lookup"><span data-stu-id="24371-170">Notice the call to `Seq.toList`.</span></span> <span data-ttu-id="24371-171">Isso cria uma lista, que implementa a interface <xref:System.Collections.ICollection>.</span><span class="sxs-lookup"><span data-stu-id="24371-171">That creates a list, which implements the <xref:System.Collections.ICollection> interface.</span></span>

<span data-ttu-id="24371-172">Há mais uma etapa a ser executada: eleve ao quadrado cada um dos números ímpares.</span><span class="sxs-lookup"><span data-stu-id="24371-172">There's one more step to go: square each of the odd numbers.</span></span> <span data-ttu-id="24371-173">Comece escrevendo um novo teste:</span><span class="sxs-lookup"><span data-stu-id="24371-173">Start by writing a new test:</span></span>

```fsharp
[<Test>]
member public this.TestSquaresOfOdds() =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

<span data-ttu-id="24371-174">Você pode corrigir o teste redirecionando a sequência filtrada por meio de uma operação de mapa para calcular o quadrado de cada número ímpar:</span><span class="sxs-lookup"><span data-stu-id="24371-174">You can fix the test by piping the filtered sequence through a map operation to compute the square of each odd number:</span></span>

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
    |> Seq.map square
```

<span data-ttu-id="24371-175">Você criou uma pequena biblioteca e um conjunto de testes de unidade para essa biblioteca.</span><span class="sxs-lookup"><span data-stu-id="24371-175">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="24371-176">Você estruturou a solução para que a adição de novos pacotes e testes fizesse parte do fluxo de trabalho normal.</span><span class="sxs-lookup"><span data-stu-id="24371-176">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="24371-177">Você concentrou grande parte do seu tempo e esforço em resolver as metas do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="24371-177">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
