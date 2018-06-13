---
title: Teste de unidade de bibliotecas do F# no .NET Core usando dotnet test e NUnit
description: Aprenda os conceitos de teste de unidade para F# no .NET Core por meio de uma experiência interativa de criação passo a passo de uma solução de exemplo usando dotnet test e NUnit.
author: rprouse
ms.date: 12/01/2017
dev_langs:
- fsharp
ms.openlocfilehash: c5653463ce43ab8660753aa03ef79ba10f339fac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33215740"
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-nunit"></a>Teste de unidade de bibliotecas do F# no .NET Core usando dotnet test e NUnit

Este tutorial apresenta uma experiência interativa de compilação de uma solução de exemplo passo a passo para aprender os conceitos do teste de unidade. Se você preferir acompanhar o tutorial usando uma solução interna, [veja ou baixe o exemplo de código](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-nunit/) antes de começar. Para obter instruções de download, consulte [Exemplos e tutoriais](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="creating-the-source-project"></a>Criando o projeto de origem

Abra uma janela do shell. Crie um diretório chamado *unit-testing-with-fsharp* para armazenar a solução.
Nesse novo diretório, execute [`dotnet new sln`](../tools/dotnet-new.md) para criar uma nova solução. Isso facilita o gerenciamento da biblioteca de classes e o projeto de teste de unidade.
No diretório da solução, crie um diretório *MathService*. A estrutura de arquivo e diretório até aqui é mostrada abaixo:

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

Torne *MathService* o diretório atual e execute [`dotnet new classlib -lang F#`](../tools/dotnet-new.md) para criar o projeto de origem.  Para usar o TDD (Desenvolvimento Orientado por Testes), você criará uma implementação com falha do serviço math:

```fsharp
module MyMath =
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

Altere o diretório de volta para o diretório *unit-testing-with-fsharp*. Execute [`dotnet sln add .\MathService\MathService.fsproj`](../tools/dotnet-sln.md) para adicionar o projeto de biblioteca de classes à solução.

## <a name="install-the-nunit-project-template"></a>Instalar o modelo de projeto do NUnit

Os modelos de projeto de teste do NUnit precisam ser instalados antes de criar um projeto de teste. Isso precisa ser feito somente uma vez em cada computador de desenvolvedor em que você criará novos projetos NUnit. Execute [`dotnet new -i NUnit3.DotNetNew.Template`](../tools/dotnet-new.md) para instalar os modelos do NUnit.

 ```
 dotnet new -i NUnit3.DotNetNew.Template
 ```

## <a name="creating-the-test-project"></a>Criando o projeto de teste

Em seguida, crie o diretório *MathService.Tests*. O seguinte esquema mostra a estrutura do diretório:

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

Torne o diretório *MathService.Tests* o diretório atual e crie um novo projeto usando [`dotnet new nunit -lang F#`](../tools/dotnet-new.md). Isso cria um projeto de teste que usa o NUnit como a estrutura de teste. O modelo gerado configura o executor de teste no *MathServiceTests.fsproj*:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.5.0" />
  <PackageReference Include="NUnit" Version="3.9.0" />
  <PackageReference Include="NUnit3TestAdapter" Version="3.9.0" />
</ItemGroup>
```

O projeto de teste requer outros pacotes para criar e executar testes de unidade. O `dotnet new` na etapa anterior adicionou o NUnit e o adaptador de teste do NUnit. Agora, adicione a biblioteca de classes `MathService` como outra dependência ao projeto. Use o comando [`dotnet add reference`](../tools/dotnet-add-reference.md):

```
dotnet add reference ../MathService/MathService.fsproj
```

Você pode ver o arquivo inteiro no [repositório de exemplos](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) no GitHub.

Você tem o seguinte layout de solução final:

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

Execute [`dotnet sln add .\MathService.Tests\MathService.Tests.fsproj`](../tools/dotnet-sln.md) no diretório *unit-testing-with-fsharp*.

## <a name="creating-the-first-test"></a>Criando o primeiro teste

A abordagem de TDD pede a criação de um teste com falha para fazê-lo passar e depois a repetição do processo. Abra *Tests.fs* e adicione o seguinte código:

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

O atributo `[<TestFixture>]` indica uma classe que contém testes. O atributo `[<Test>]` indica um método de teste que é executado pelo executor de teste. No diretório *unit-testing-with-fsharp*, execute [`dotnet test`](../tools/dotnet-test.md) para criar os testes e a biblioteca de classes e execute os testes. O executor de teste do NUnit contém o ponto de entrada do programa para executar os testes. `dotnet test` inicia o executor de teste usando o projeto de teste de unidade que você criou.

Esses dois testes mostram testes com aprovação e falha mais básicos. `My test` é aprovado e `Fail every time` falha. Agora, crie um teste para o método `squaresOfOdds`. O método `squaresOfOdds` retorna uma sequência dos quadrados de todos os valores inteiros ímpares que fazem parte da sequência de entrada. Em vez de tentar gravar todas as funções de uma vez, você pode criar testes iterativamente que validam a funcionalidade. Fazer com que cada teste passe significa criar a funcionalidade necessária para o método.

O teste mais simples que podemos escrever é chamar `squaresOfOdds` com todos os números pares, em que o resultado deve ser uma sequência vazia de inteiros.  Este é o teste:

```fsharp
[<Test>]
member this.TestEvenSequence() =
    let expected = Seq.empty<int>
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

Observe que a sequência `expected` foi convertida em uma lista. A estrutura do NUnit depende de muitos tipos padrão de .NET. Essa dependência significa que sua interface pública e os resultados esperados dão suporte a <xref:System.Collections.ICollection> em vez de <xref:System.Collections.IEnumerable>.

Ao executar o teste, você verá que ele falha. Você ainda não criou a implementação. Faça esse teste escrevendo o código mais simples na classe `Mathservice` que funciona:

```csharp
let squaresOfOdds xs =
    Seq.empty<int>
```

No diretório *unit-testing-with-fsharp*, execute `dotnet test` novamente. O comando `dotnet test` executa uma compilação para o projeto `MathService` e, depois, para o projeto `MathService.Tests`. Depois de compilar os dois projetos, ele executará esse teste único. Ele é aprovado.

## <a name="completing-the-requirements"></a>Como atender aos requisitos

Agora que você fez um teste ser aprovado, é hora de escrever mais. O próximo caso simples funciona com uma sequência cujo único número ímpar é `1`. O número 1 é mais fácil, pois o quadrado de 1 é 1. Este é o próximo teste:

```fsharp
[<Test>]
member public this.TestOnesAndEvens() =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

A execução de `dotnet test` falha no novo teste. Você deve atualizar o método `squaresOfOdds` para lidar com esse novo teste. É preciso remover todos os números pares da sequência para que esse teste seja aprovado. Faça isso escrevendo uma pequena função de filtro e usando `Seq.filter`:

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
```

Observe a chamada a `Seq.toList`. Isso cria uma lista, que implementa a interface <xref:System.Collections.ICollection>.

Há mais uma etapa a ser executada: eleve ao quadrado cada um dos números ímpares. Comece escrevendo um novo teste:

```fsharp
[<Test>]
member public this.TestSquaresOfOdds() =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

Você pode corrigir o teste redirecionando a sequência filtrada por meio de uma operação de mapa para calcular o quadrado de cada número ímpar:

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
    |> Seq.map square
```

Você criou uma pequena biblioteca e um conjunto de testes de unidade para essa biblioteca. Você estruturou a solução para que a adição de novos pacotes e testes fizesse parte do fluxo de trabalho normal. Você concentrou grande parte do seu tempo e esforço em resolver as metas do aplicativo.
