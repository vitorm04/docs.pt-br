---
title: Teste de unidade do F# no .NET Core com dotnet test e NUnit
description: Aprenda os conceitos de teste de unidade para F# no .NET Core por meio de uma experiência interativa de criação passo a passo de uma solução de exemplo usando dotnet test e NUnit.
author: rprouse
ms.date: 10/04/2018
dev_langs:
- fsharp
ms.custom: seodec18
ms.openlocfilehash: 1a5320f47b880c2d84132d70e1d0be19d6de486b
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71116209"
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-nunit"></a><span data-ttu-id="9fe84-103">Teste de unidade de bibliotecas do F# no .NET Core usando dotnet test e NUnit</span><span class="sxs-lookup"><span data-stu-id="9fe84-103">Unit testing F# libraries in .NET Core using dotnet test and NUnit</span></span>

<span data-ttu-id="9fe84-104">Este tutorial apresenta uma experiência interativa de compilação de uma solução de exemplo passo a passo para aprender os conceitos do teste de unidade.</span><span class="sxs-lookup"><span data-stu-id="9fe84-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="9fe84-105">Se você preferir acompanhar o tutorial usando uma solução interna, [veja ou baixe o exemplo de código](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-nunit/) antes de começar.</span><span class="sxs-lookup"><span data-stu-id="9fe84-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-nunit/) before you begin.</span></span> <span data-ttu-id="9fe84-106">Para obter instruções de download, consulte [Exemplos e tutoriais](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="9fe84-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="prerequisites"></a><span data-ttu-id="9fe84-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="9fe84-107">Prerequisites</span></span>

- <span data-ttu-id="9fe84-108">[SDK do .NET Core 2.1](https://dotnet.microsoft.com/download) ou versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="9fe84-108">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) or later versions.</span></span>
- <span data-ttu-id="9fe84-109">Um editor de texto ou de código de sua escolha.</span><span class="sxs-lookup"><span data-stu-id="9fe84-109">A text editor or code editor of your choice.</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="9fe84-110">Criando o projeto de origem</span><span class="sxs-lookup"><span data-stu-id="9fe84-110">Creating the source project</span></span>

<span data-ttu-id="9fe84-111">Abra uma janela do shell.</span><span class="sxs-lookup"><span data-stu-id="9fe84-111">Open a shell window.</span></span> <span data-ttu-id="9fe84-112">Crie um diretório chamado *unit-testing-with-fsharp* para armazenar a solução.</span><span class="sxs-lookup"><span data-stu-id="9fe84-112">Create a directory called *unit-testing-with-fsharp* to hold the solution.</span></span>
<span data-ttu-id="9fe84-113">Nesse diretório, execute o seguinte comando a fim de criar um novo arquivo de solução para a biblioteca de classes e o projeto de teste:</span><span class="sxs-lookup"><span data-stu-id="9fe84-113">Inside this new directory, run the following command to create a new solution file for the class library and the test project:</span></span>

```dotnetcli
dotnet new sln
```

<span data-ttu-id="9fe84-114">Em seguida, crie um diretório *MathService*.</span><span class="sxs-lookup"><span data-stu-id="9fe84-114">Next, create a *MathService* directory.</span></span> <span data-ttu-id="9fe84-115">A seguinte estrutura de tópicos mostra a estrutura de arquivo e o diretório até aqui:</span><span class="sxs-lookup"><span data-stu-id="9fe84-115">The following outline shows the directory and file structure so far:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

<span data-ttu-id="9fe84-116">Torne *MathService* o diretório atual e execute o seguinte comando para criar o projeto de origem:</span><span class="sxs-lookup"><span data-stu-id="9fe84-116">Make *MathService* the current directory and run the following command to create the source project:</span></span>

```dotnetcli
dotnet new classlib -lang F#
```

<span data-ttu-id="9fe84-117">Crie uma implementação com falha do serviço de matemática:</span><span class="sxs-lookup"><span data-stu-id="9fe84-117">You create a failing implementation of the math service:</span></span>

```fsharp
module MyMath =
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

<span data-ttu-id="9fe84-118">Altere o diretório de volta para o diretório *unit-testing-with-fsharp*.</span><span class="sxs-lookup"><span data-stu-id="9fe84-118">Change the directory back to the *unit-testing-with-fsharp* directory.</span></span> <span data-ttu-id="9fe84-119">Execute o seguinte comando para adicionar o projeto de biblioteca de classes à solução:</span><span class="sxs-lookup"><span data-stu-id="9fe84-119">Run the following command to add the class library project to the solution:</span></span>

```dotnetcli
dotnet sln add .\MathService\MathService.fsproj
```

## <a name="creating-the-test-project"></a><span data-ttu-id="9fe84-120">Criando o projeto de teste</span><span class="sxs-lookup"><span data-stu-id="9fe84-120">Creating the test project</span></span>

<span data-ttu-id="9fe84-121">Em seguida, crie o diretório *MathService.Tests*.</span><span class="sxs-lookup"><span data-stu-id="9fe84-121">Next, create the *MathService.Tests* directory.</span></span> <span data-ttu-id="9fe84-122">O seguinte esquema mostra a estrutura do diretório:</span><span class="sxs-lookup"><span data-stu-id="9fe84-122">The following outline shows the directory structure:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

<span data-ttu-id="9fe84-123">Torne o diretório *MathService.Tests* o diretório atual e crie um novo projeto usando o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="9fe84-123">Make the *MathService.Tests* directory the current directory and create a new project using the following command:</span></span>

```dotnetcli
dotnet new nunit -lang F#
```

<span data-ttu-id="9fe84-124">Isso cria um projeto de teste que usa o NUnit como a estrutura de teste.</span><span class="sxs-lookup"><span data-stu-id="9fe84-124">This creates a test project that uses NUnit as the test framework.</span></span> <span data-ttu-id="9fe84-125">O modelo gerado configura o executor de teste no *MathServiceTests.fsproj*:</span><span class="sxs-lookup"><span data-stu-id="9fe84-125">The generated template configures the test runner in the *MathServiceTests.fsproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.5.0" />
  <PackageReference Include="NUnit" Version="3.9.0" />
  <PackageReference Include="NUnit3TestAdapter" Version="3.9.0" />
</ItemGroup>
```

<span data-ttu-id="9fe84-126">O projeto de teste requer outros pacotes para criar e executar testes de unidade.</span><span class="sxs-lookup"><span data-stu-id="9fe84-126">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="9fe84-127">O `dotnet new` na etapa anterior adicionou o NUnit e o adaptador de teste do NUnit.</span><span class="sxs-lookup"><span data-stu-id="9fe84-127">`dotnet new` in the previous step added NUnit and the NUnit test adapter.</span></span> <span data-ttu-id="9fe84-128">Agora, adicione a biblioteca de classes `MathService` como outra dependência ao projeto.</span><span class="sxs-lookup"><span data-stu-id="9fe84-128">Now, add the `MathService` class library as another dependency to the project.</span></span> <span data-ttu-id="9fe84-129">Use o comando [`dotnet add reference`](../tools/dotnet-add-reference.md):</span><span class="sxs-lookup"><span data-stu-id="9fe84-129">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```dotnetcli
dotnet add reference ../MathService/MathService.fsproj
```

<span data-ttu-id="9fe84-130">Você pode ver o arquivo inteiro no [repositório de exemplos](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) no GitHub.</span><span class="sxs-lookup"><span data-stu-id="9fe84-130">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) on GitHub.</span></span>

<span data-ttu-id="9fe84-131">Você tem o seguinte layout de solução final:</span><span class="sxs-lookup"><span data-stu-id="9fe84-131">You have the following final solution layout:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
        Test Source Files
        MathService.Tests.fsproj
```

<span data-ttu-id="9fe84-132">Execute o seguinte comando no diretório *unit-testing-with-fsharp*:</span><span class="sxs-lookup"><span data-stu-id="9fe84-132">Execute the following command in the *unit-testing-with-fsharp* directory:</span></span>

```dotnetcli
dotnet sln add .\MathService.Tests\MathService.Tests.fsproj
```

## <a name="creating-the-first-test"></a><span data-ttu-id="9fe84-133">Criando o primeiro teste</span><span class="sxs-lookup"><span data-stu-id="9fe84-133">Creating the first test</span></span>

<span data-ttu-id="9fe84-134">Escreva um teste com falha, faça-o ser aprovado e, em seguida, repita o processo.</span><span class="sxs-lookup"><span data-stu-id="9fe84-134">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="9fe84-135">Abra *UnitTest1.fs* e adicione o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="9fe84-135">Open *UnitTest1.fs* and add the following code:</span></span>

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

<span data-ttu-id="9fe84-136">O atributo `[<TestFixture>]` indica uma classe que contém testes.</span><span class="sxs-lookup"><span data-stu-id="9fe84-136">The `[<TestFixture>]` attribute denotes a class that contains tests.</span></span> <span data-ttu-id="9fe84-137">O atributo `[<Test>]` indica um método de teste que é executado pelo executor de teste.</span><span class="sxs-lookup"><span data-stu-id="9fe84-137">The `[<Test>]` attribute denotes a test method that is run by the test runner.</span></span> <span data-ttu-id="9fe84-138">No diretório *unit-testing-with-fsharp*, execute [`dotnet test`](../tools/dotnet-test.md) para criar os testes e a biblioteca de classes e execute os testes.</span><span class="sxs-lookup"><span data-stu-id="9fe84-138">From the *unit-testing-with-fsharp* directory, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="9fe84-139">O executor de teste do NUnit contém o ponto de entrada do programa para executar os testes.</span><span class="sxs-lookup"><span data-stu-id="9fe84-139">The NUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="9fe84-140">`dotnet test` inicia o executor de teste usando o projeto de teste de unidade que você criou.</span><span class="sxs-lookup"><span data-stu-id="9fe84-140">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="9fe84-141">Esses dois testes mostram testes com aprovação e falha mais básicos.</span><span class="sxs-lookup"><span data-stu-id="9fe84-141">These two tests show the most basic passing and failing tests.</span></span> <span data-ttu-id="9fe84-142">`My test` é aprovado e `Fail every time` falha.</span><span class="sxs-lookup"><span data-stu-id="9fe84-142">`My test` passes, and `Fail every time` fails.</span></span> <span data-ttu-id="9fe84-143">Agora, crie um teste para o método `squaresOfOdds`.</span><span class="sxs-lookup"><span data-stu-id="9fe84-143">Now, create a test for the `squaresOfOdds` method.</span></span> <span data-ttu-id="9fe84-144">O método `squaresOfOdds` retorna uma sequência dos quadrados de todos os valores inteiros ímpares que fazem parte da sequência de entrada.</span><span class="sxs-lookup"><span data-stu-id="9fe84-144">The `squaresOfOdds` method returns a sequence of the squares of all odd integer values that are part of the input sequence.</span></span> <span data-ttu-id="9fe84-145">Em vez de tentar gravar todas as funções de uma vez, você pode criar testes iterativamente que validam a funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="9fe84-145">Rather than trying to write all of those functions at once, you can iteratively create tests that validate the functionality.</span></span> <span data-ttu-id="9fe84-146">Fazer com que cada teste passe significa criar a funcionalidade necessária para o método.</span><span class="sxs-lookup"><span data-stu-id="9fe84-146">Making each test pass means creating the necessary functionality for the method.</span></span>

<span data-ttu-id="9fe84-147">O teste mais simples que podemos escrever é chamar `squaresOfOdds` com todos os números pares, em que o resultado deve ser uma sequência vazia de inteiros.</span><span class="sxs-lookup"><span data-stu-id="9fe84-147">The simplest test we can write is to call `squaresOfOdds` with all even numbers, where the result should be an empty sequence of integers.</span></span>  <span data-ttu-id="9fe84-148">Este é o teste:</span><span class="sxs-lookup"><span data-stu-id="9fe84-148">Here's that test:</span></span>

```fsharp
[<Test>]
member this.TestEvenSequence() =
    let expected = Seq.empty<int>
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

<span data-ttu-id="9fe84-149">Observe que a sequência `expected` foi convertida em uma lista.</span><span class="sxs-lookup"><span data-stu-id="9fe84-149">Notice that the `expected` sequence has been converted to a list.</span></span> <span data-ttu-id="9fe84-150">A estrutura do NUnit depende de muitos tipos padrão de .NET.</span><span class="sxs-lookup"><span data-stu-id="9fe84-150">The NUnit framework relies on many standard .NET types.</span></span> <span data-ttu-id="9fe84-151">Essa dependência significa que sua interface pública e os resultados esperados dão suporte a <xref:System.Collections.ICollection> em vez de <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="9fe84-151">That dependency means that your public interface and expected results support <xref:System.Collections.ICollection> rather than <xref:System.Collections.IEnumerable>.</span></span>

<span data-ttu-id="9fe84-152">Ao executar o teste, você verá que ele falha.</span><span class="sxs-lookup"><span data-stu-id="9fe84-152">When you run the test, you see that your test fails.</span></span> <span data-ttu-id="9fe84-153">Você ainda não criou a implementação.</span><span class="sxs-lookup"><span data-stu-id="9fe84-153">You haven't created the implementation yet.</span></span> <span data-ttu-id="9fe84-154">Faça esse teste passar escrevendo o código mais simples na classe *Library.fs* em seu projeto MathService que funciona:</span><span class="sxs-lookup"><span data-stu-id="9fe84-154">Make this test pass by writing the simplest code in the *Library.fs* class in your MathService project that works:</span></span>

```fsharp
let squaresOfOdds xs =
    Seq.empty<int>
```

<span data-ttu-id="9fe84-155">No diretório *unit-testing-with-fsharp*, execute `dotnet test` novamente.</span><span class="sxs-lookup"><span data-stu-id="9fe84-155">In the *unit-testing-with-fsharp* directory, run `dotnet test` again.</span></span> <span data-ttu-id="9fe84-156">O comando `dotnet test` executa uma compilação para o projeto `MathService` e, depois, para o projeto `MathService.Tests`.</span><span class="sxs-lookup"><span data-stu-id="9fe84-156">The `dotnet test` command runs a build for the `MathService` project and then for the `MathService.Tests` project.</span></span> <span data-ttu-id="9fe84-157">Depois de compilar os dois projetos, ele executa os seus testes.</span><span class="sxs-lookup"><span data-stu-id="9fe84-157">After building both projects, it runs your tests.</span></span> <span data-ttu-id="9fe84-158">Agora, dois testes são aprovados.</span><span class="sxs-lookup"><span data-stu-id="9fe84-158">Two tests pass now.</span></span>

## <a name="completing-the-requirements"></a><span data-ttu-id="9fe84-159">Como atender aos requisitos</span><span class="sxs-lookup"><span data-stu-id="9fe84-159">Completing the requirements</span></span>

<span data-ttu-id="9fe84-160">Agora que você fez um teste ser aprovado, é hora de escrever mais.</span><span class="sxs-lookup"><span data-stu-id="9fe84-160">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="9fe84-161">O próximo caso simples funciona com uma sequência cujo único número ímpar é `1`.</span><span class="sxs-lookup"><span data-stu-id="9fe84-161">The next simple case works with a sequence whose only odd number is `1`.</span></span> <span data-ttu-id="9fe84-162">O número 1 é mais fácil, pois o quadrado de 1 é 1.</span><span class="sxs-lookup"><span data-stu-id="9fe84-162">The number 1 is easier because the square of 1 is 1.</span></span> <span data-ttu-id="9fe84-163">Este é o próximo teste:</span><span class="sxs-lookup"><span data-stu-id="9fe84-163">Here's that next test:</span></span>

```fsharp
[<Test>]
member public this.TestOnesAndEvens() =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

<span data-ttu-id="9fe84-164">A execução de `dotnet test` falha no novo teste.</span><span class="sxs-lookup"><span data-stu-id="9fe84-164">Executing `dotnet test` fails the new test.</span></span> <span data-ttu-id="9fe84-165">Você deve atualizar o método `squaresOfOdds` para lidar com esse novo teste.</span><span class="sxs-lookup"><span data-stu-id="9fe84-165">You must update the `squaresOfOdds` method to handle this new test.</span></span> <span data-ttu-id="9fe84-166">É preciso remover todos os números pares da sequência para que esse teste seja aprovado.</span><span class="sxs-lookup"><span data-stu-id="9fe84-166">You must filter all the even numbers out of the sequence to make this test pass.</span></span> <span data-ttu-id="9fe84-167">Faça isso escrevendo uma pequena função de filtro e usando `Seq.filter`:</span><span class="sxs-lookup"><span data-stu-id="9fe84-167">You can do that by writing a small filter function and using `Seq.filter`:</span></span>

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
```

<span data-ttu-id="9fe84-168">Observe a chamada a `Seq.toList`.</span><span class="sxs-lookup"><span data-stu-id="9fe84-168">Notice the call to `Seq.toList`.</span></span> <span data-ttu-id="9fe84-169">Isso cria uma lista, que implementa a interface <xref:System.Collections.ICollection>.</span><span class="sxs-lookup"><span data-stu-id="9fe84-169">That creates a list, which implements the <xref:System.Collections.ICollection> interface.</span></span>

<span data-ttu-id="9fe84-170">Há mais uma etapa a ser executada: eleve ao quadrado cada um dos números ímpares.</span><span class="sxs-lookup"><span data-stu-id="9fe84-170">There's one more step to go: square each of the odd numbers.</span></span> <span data-ttu-id="9fe84-171">Comece escrevendo um novo teste:</span><span class="sxs-lookup"><span data-stu-id="9fe84-171">Start by writing a new test:</span></span>

```fsharp
[<Test>]
member public this.TestSquaresOfOdds() =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

<span data-ttu-id="9fe84-172">Você pode corrigir o teste redirecionando a sequência filtrada por meio de uma operação de mapa para calcular o quadrado de cada número ímpar:</span><span class="sxs-lookup"><span data-stu-id="9fe84-172">You can fix the test by piping the filtered sequence through a map operation to compute the square of each odd number:</span></span>

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
    |> Seq.map square
```

<span data-ttu-id="9fe84-173">Você criou uma pequena biblioteca e um conjunto de testes de unidade para essa biblioteca.</span><span class="sxs-lookup"><span data-stu-id="9fe84-173">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="9fe84-174">Você estruturou a solução para que a adição de novos pacotes e testes fizesse parte do fluxo de trabalho normal.</span><span class="sxs-lookup"><span data-stu-id="9fe84-174">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="9fe84-175">Você concentrou grande parte do seu tempo e esforço em resolver as metas do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9fe84-175">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
