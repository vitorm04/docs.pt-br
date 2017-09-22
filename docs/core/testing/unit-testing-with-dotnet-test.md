---
title: "Código C# de teste de unidade no .NET Core usando dotnet test e xUnit"
description: "Aprenda os conceitos de teste de unidade no C# e .NET Core por meio de uma experiência interativa de criação passo a passo de uma solução de exemplo usando dotnet test e xUnit."
author: ardalis
ms.author: wiwagn
ms.date: 09/08/2017
ms.topic: article
ms.prod: .net-core
ms.translationtype: HT
ms.sourcegitcommit: b041fbec3ff22157d00af2447e76a7ce242007fc
ms.openlocfilehash: 89657d766771bc73777a62c14e10cde3b4f6f75f
ms.contentlocale: pt-br
ms.lasthandoff: 09/14/2017

---
# <a name="unit-testing-c-in-net-core-using-dotnet-test-and-xunit"></a>C# de teste de unidade no .NET Core usando dotnet test e xUnit

Este tutorial apresenta uma experiência interativa de compilação de uma solução de exemplo passo a passo para aprender os conceitos do teste de unidade. Se você preferir acompanhar o tutorial usando uma solução interna, [veja ou baixe o exemplo de código](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/unit-testing-using-dotnet-test/) antes de começar. Para obter instruções de download, consulte [Exemplos e tutoriais](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="creating-the-source-project"></a>Criando o projeto de origem

Abra uma janela do shell. Crie um diretório chamado *unit-testing-using-dotnet-test* para armazenar a solução.
Nesse novo diretório, execute [`dotnet new sln`](../tools/dotnet-new.md) para criar uma nova solução. Isso facilita o gerenciamento da biblioteca de classes e o projeto de teste de unidade.
No diretório da solução, crie um diretório *PrimeService*. A estrutura de arquivo e diretório até aqui é mostrada abaixo:

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
```

Torne *PrimeService* o diretório atual e execute [`dotnet new classlib`](../tools/dotnet-new.md) para criar o projeto de origem. Renomeie *Class1.cs* como *PrimeService.cs*. Para usar TDD (Desenvolvimento Orientado por Testes), você criará uma implementação com falha da classe `PrimeService`:

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

Altere o diretório de volta para o diretório *unit-testing-using-dotnet-test*. Execute [`dotnet sln add .\PrimeService\PrimeService.csproj`](../tools/dotnet-sln.md) para adicionar o projeto de biblioteca de classes à solução.

## <a name="creating-the-test-project"></a>Criando o projeto de teste

Em seguida, crie o diretório *PrimeService.Tests*. O seguinte esquema mostra a estrutura do diretório:

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

Torne o diretório *PrimeService.Tests* o diretório atual e crie um novo projeto usando [`dotnet new xunit`](../tools/dotnet-new.md). Isso cria um projeto de teste que usa o xUnit como a biblioteca de teste. O modelo gerado configura o executor de teste no *PrimeServiceTests.csproj*:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

O projeto de teste requer outros pacotes para criar e executar testes de unidade. `dotnet new` na etapa anterior adicionou xUnit e o executor de xUnit. Agora, adicione a biblioteca de classes `PrimeService` como outra dependência ao projeto. Use o comando [`dotnet add reference`](../tools/dotnet-add-reference.md):

```
dotnet add reference ../PrimeService/PrimeService.csproj
```

Você pode ver o arquivo inteiro no [repositório de exemplos](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService.Tests.csproj) no GitHub.

Veja a seguir o layout da solução final:

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

Execute [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj`](../tools/dotnet-sln.md) no diretório *unit-testing-using-dotnet-test*. 

## <a name="creating-the-first-test"></a>Criando o primeiro teste

A abordagem de TDD pede a criação de um teste com falha para fazê-lo passar e depois a repetição do processo. Remova *UnitTest1.cs* do diretório *PrimeService.Tests* e crie um novo arquivo de C# chamado *PrimeService_IsPrimeShould.cs*. Adicione o seguinte código:

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

O atributo `[Fact]` indica um método de teste que é executado pelo executor de teste. Em *unit-testing-using-dotnet-test*, execute [`dotnet test`](../tools/dotnet-test.md) para criar os testes e a biblioteca de classes e execute os testes. O executor de teste do xUnit contém o ponto de entrada do programa para executar os testes. `dotnet test` inicia o executor de teste usando o projeto de teste de unidade que você criou.

O teste falha. Você ainda não criou a implementação. Faça esse teste escrevendo o código mais simples na classe `PrimeService` que funciona:

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

No diretório *unit-testing-using-dotnet-test*, execute `dotnet test` novamente. O comando `dotnet test` executa uma compilação para o projeto `PrimeService` e, depois, para o projeto `PrimeService.Tests`. Depois de compilar os dois projetos, ele executará esse teste único. Ele é aprovado.

## <a name="adding-more-features"></a>Adicionando mais recursos

Agora que você fez um teste ser aprovado, é hora de escrever mais. Existem alguns outros casos simples de números primos: 0, -1. Você pode adicionar esses casos como novos testes com o atributo `[Fact]`, mas isso se torna entediante rapidamente. Há outros atributos de xUnit que permitem escrever um pacote de testes semelhantes.  Um atributo `[Theory]` representa um pacote de testes que executa o mesmo código, mas têm diferentes argumentos de entrada. Você pode usar o atributo `[InlineData]` para especificar valores para essas entradas.

Em vez de criar novos testes, aplique esses dois atributos para criar uma única teoria. A teoria é um método que testa vários valores inferiores a dois, que é o número primo mais baixo:

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

Execute `dotnet test`, e dois desses testes falham. Para fazer todos os testes serem aprovados, altere a cláusula `if` no início do método:

```csharp
if (candidate < 2)
```

Continue iterando adicionando mais testes, mais teorias e mais código na biblioteca principal. Você tem a [versão concluída dos testes](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs) e a [implementação completa da biblioteca](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs).

Você criou uma pequena biblioteca e um conjunto de testes de unidade para essa biblioteca. Você estruturou a solução para que a adição de novos pacotes e testes seguisse o fluxo de trabalho atual. Você concentrou grande parte do seu tempo e esforço em resolver as metas do aplicativo.

