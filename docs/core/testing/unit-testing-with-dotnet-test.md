---
title: Testes de unidade no .NET Core usando o teste dotnet
description: Testes de unidade no .NET Core usando o teste dotnet
keywords: .NET, .NET Core
author: ardalis
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: bdcdb812-6f13-4f20-9e90-0c0977937142
translationtype: Human Translation
ms.sourcegitcommit: 5687fc7ded899a478d1972ffea10a1e37d40124b
ms.openlocfilehash: f1f08f550d7484869e67fe705dc789ca5dae8e2f

---

# <a name="unit-testing-in-net-core-using-dotnet-test"></a>Testes de unidade no .NET Core usando o teste dotnet

Por [Steve Smith](http://ardalis.com) e [Bill Wagner](https://github.com/BillWagner)

[Exibir ou baixar o código de exemplo](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/unit-testing-using-dotnet-test)

> [!NOTE]
> Este tópico aplica-se ao .NET Core 1.0.

## <a name="creating-the-projects"></a>Criando os Projetos

[Criando bibliotecas com as Ferramentas de Plataforma Cruzada](../tutorials/libraries.md) traz informações sobre como organizar soluções de vários projetos para a fonte e os testes. Este artigo segue as convenções. A estrutura do projeto final será semelhante a esta:

```
/unit-testing-using-dotnet-test
|__global.json
|__/src
   |__/PrimeService
      |__Source Files
      |__project.json
|__/test
   |__/PrimeService.Tests
      |__Test Files
      |__project.json
```

No diretório raiz, você precisará criar um `global.json` que contém os nomes de seu diretório `src` e `test`:

```json
{
    "projects": [
        "src",
        "test"
    ]
}
```

### <a name="creating-the-source-project"></a>Criando o projeto de origem

Em seguida, no diretório `src`, crie o diretório `PrimeService`.
Execute CD nesse diretório e execute `dotnet new -t lib` para criar o projeto de origem.


Renomeie `Library.cs` como `PrimeService.cs`. Para usar TDD (Desenvolvimento Orientado por Testes), você criará uma implementação com falha da classe `PrimeService`:

```cs
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

### <a name="creating-the-test-project"></a>Criando o projeto de teste

Em seguida, execute cd no diretório 'test' e crie o diretório `PrimeServices.Tests`.
Execute CD no diretório `PrimeServices.Tests` e crie um novo projeto usando `dotnet new -t xunittest`. `dotnet new -t xunittest` cria um projeto de teste que usa xunit como a biblioteca de teste. 

O modelo gerado configurou o executor de teste na raiz do `project.json`:

```json
{
  "version": "1.0.0-*",
  "testRunner": "xunit",
  // ...
}
```

O modelo também define o nó de estrutura para usar `netcoreapp1.0` e inclui as importações necessárias para fazer o xUnit.net funcionar com o .NET Core RTM:

```json
  "frameworks": {
    "netcoreapp1.0": {
      "imports": [
        "dotnet54",
        "portable-net45+win8" 
      ]
    }
  }
```

O projeto de teste requer outros pacotes para criar e executar testes de unidade.
`dotnet new` xunit e o executor xunit adicionados. Você precisa adicionar o pacote PrimeService como outra dependência ao projeto:

```json
"dependencies": {
  "xunit":"2.1.0",
  "dotnet-test-xunit": "1.0.0-rc2-192208-24",
  "PrimeService": {
    "target": "project"
  }
}
```

Observe que o projeto `PrimeService` não inclui nenhuma informação de caminho de diretório. Como você criou a estrutura do projeto para corresponder à organização esperada de `src` e `test`, e o arquivo `global.json` indica isso, o sistema de build encontrará o local correto para o projeto. Adicione o elemento `"target": "project"` para ordenar o NuGet a procurar nos diretórios de projetos, não no feed do NuGet. Sem essa chave, você pode baixar um pacote com o mesmo nome que a biblioteca interna.

Você pode ver o arquivo inteiro no [repositório de exemplos](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/test/PrimeService.Tests/project.json) no GitHub.

Depois que essa estrutura inicial estiver em vigor, você poderá criar seu primeiro teste.
Depois de verificar esse primeiro teste de unidade, tudo estará configurado e deverá ser executado sem problemas ao adicionar recursos e testes.

## <a name="creating-the-first-test"></a>Criando o primeiro teste

A abordagem de TDD pede a criação de um teste com falha para então fazê-lo passar e depois repetindo o processo. Portanto, vamos escrever esse teste com falha. Remova `program.cs` do diretório `PrimeService.Tests` e crie um novo arquivo C# com o seguinte conteúdo:

```cs
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

O atributo `[Fact]` indica um método como um único teste. 

Salve esse arquivo e execute `dotnet build` para compilar o projeto de teste.
Se você ainda não criou o projeto `PrimeService`, o sistema de build detectará isso e o compilará, pois ele é uma dependência do projeto de teste.

Agora, execute `dotnet test` para executar os testes no console.
O executor de teste xunit tem o ponto de entrada do programa para executar testes do Console. `dotnet test` inicia o executor de teste e fornece um argumento de linha de comando para o testrunner indicando o assembly que contém seus testes.

O teste falha. Você ainda não criou a implementação.
Escreva o código mais simples para fazer um teste ser aprovado:

```cs
public bool IsPrime(int candidate) 
{
    if(candidate == 1) 
    { 
        return false;
    } 
    throw new NotImplementedException("Please create a test first");
} 
```

### <a name="adding-more-features"></a>Adicionando mais recursos

Agora que você fez um teste ser aprovado, é hora de escrever mais.
Existem alguns outros casos simples de números primos: 0, -1. Você pode adicioná-los como novos testes, com o atributo `[Fact]`, porém isso se torna entediante rapidamente. Há outros atributos xunit que permitem escrever um pacote de testes semelhantes.  Um `Theory` representa um pacote de testes que executa o mesmo código, mas têm diferentes argumentos de entrada.
Você pode usar o atributo `[InlineData]` para especificar valores para essas entradas. 
 
 Em vez de criar novos testes, aproveite esses dois atributos para criar uma única teoria que testa alguns valores menores que 2, que é o menor número primo:

```cs
[Theory]
[InlineData(-1)]
[InlineData(0)]
[InlineData(1)]
public void ReturnFalseGivenValuesLessThan2(int value)
{
    var result = _primeService.IsPrime(value);

    Assert.False(result, $"{value} should not be prime");
}
```

Execute `dotnet test` e você verá que dois desses testes falham.
Você pode fazê-los serem aprovados alterando o serviço. Você precisa alterar a cláusula `if` no início do método:

```cs
if(candidate < 2)
```

Agora, todos os testes são aprovados.

Você continuar a iterar adicionando mais testes, mais teorias e mais código da biblioteca principal. Você acabará rapidamente com a [versão concluída dos testes](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/test/PrimeService.Tests/PrimeServie_IsPrimeShould.cs) e a [implementação completa da biblioteca](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/src/PrimeService/PrimeService.cs).

Você criou uma pequena biblioteca e um conjunto de testes de unidade para essa biblioteca.
Você estruturou essa solução para que a adição de novos pacotes de testes seja simples, assim você pode se concentrar no problema em questão. As ferramentas serão executadas automaticamente.
   
   > [!TIP]
   > Na plataforma Windows, você pode usar o MSTest. Saiba mais no [documento Usando o MSTest no Windows](./using-mstest-on-windows.md).



<!--HONumber=Jan17_HO3-->


