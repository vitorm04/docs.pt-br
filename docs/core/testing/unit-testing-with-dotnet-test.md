---
title: Teste de unidade no .NET Core usando dotnet test | Microsoft Docs
description: Testes de unidade no .NET Core usando o teste dotnet
keywords: .NET, .NET Core
author: ardalis
ms.author: wiwagn
ms.date: 002/02/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: bdcdb812-6f13-4f20-9e90-0c0977937142
translationtype: Human Translation
ms.sourcegitcommit: 195664ae6409be02ca132900d9c513a7b412acd4
ms.openlocfilehash: cd860241f5f20b6a4f1ccfec60e0c9cd5079152a
ms.lasthandoff: 03/07/2017

---

# <a name="unit-testing-in-net-core-using-dotnet-test"></a>Testes de unidade no .NET Core usando o teste dotnet

Por [Steve Smith](http://ardalis.com) e [Bill Wagner](https://github.com/BillWagner)

[Exibir ou baixar o código de exemplo](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/unit-testing-using-dotnet-test)

## <a name="creating-the-projects"></a>Criando os Projetos

[Criando bibliotecas com as Ferramentas de Plataforma Cruzada](../tutorials/libraries.md) traz informações sobre como organizar soluções de vários projetos para a fonte e os testes. Este artigo segue as convenções. A estrutura do projeto final será semelhante a esta:

```
/unit-testing-using-dotnet-test
|__/PrimeService
   |__Source Files
   |__PrimeService.csproj
|__/PrimeService.Tests
   |__Test Files
   |__PrimeService.csproj
```

### <a name="creating-the-source-project"></a>Criando o projeto de origem

Comece no diretório `unit-testing-using-dotnet-test` e crie o diretório `PrimeService`.
Execute CD nesse diretório e execute `dotnet new classib` para criar o projeto de origem.


Renomeie `Class1.cs` como `PrimeService.cs`. Para usar TDD (Desenvolvimento Orientado por Testes), você criará uma implementação com falha da classe `PrimeService`:

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

Em seguida, execute cd de volta ao diretório “unit-testing-using-dotnet-test” e crie o diretório `PrimeServices.Tests`.
Execute CD no diretório `PrimeService.Tests` e crie um novo projeto usando `dotnet new xunit`. `dotnet xunit` cria um projeto de teste que usa xUnit como a biblioteca de teste. 

O modelo gerado configurou o executor de teste no PrimeServiceTests.csproj:

```xml
  <ItemGroup>
    <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.0.0-preview-20170125-04" />
    <PackageReference Include="xunit" Version="2.2.0-beta5-build3474" />
    <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0-beta5-build1225" />
  </ItemGroup>
```

O projeto de teste requer outros pacotes para criar e executar testes de unidade.
`dotnet new` adicionou xUnit e o executor de xUnit. É necessário adicionar o pacote PrimeService como outra dependência ao projeto. É possível fazer isso usando a CLI `dotnet`:

```
dotnet add reference ../PrimeService/PrimeService.csproj
```

Se preferir, é possível editar diretamente o arquivo `PrimeService.Tests.csproj`.
Diretamente sob o primeiro nó `<ItemGroup>`, adicione outro nó `<ItemGroup>` com uma referência ao projeto de biblioteca:

```xml
  <ItemGroup>
    <ProjectReference Include="..\PrimeService\PrimeService.csproj" />
  </ItemGroup>
```

Você pode ver o arquivo inteiro no [repositório de exemplos](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService.Tests.csproj) no GitHub.

Depois que essa estrutura inicial estiver em vigor, você poderá criar seu primeiro teste.
Depois de verificar esse primeiro teste de unidade, tudo estará configurado e deverá ser executado sem problemas ao adicionar recursos e testes.

## <a name="creating-the-first-test"></a>Criando o primeiro teste

Antes de compilar a biblioteca ou os testes, é necessário executar `dotnet restore` nos diretórios `PrimeService` e `PrimeService.Tests`. Este comando restaura todos os pacotes NuGet necessários para cada projeto.

A abordagem de TDD pede a criação de um teste com falha para então fazê-lo passar e depois repetindo o processo. Portanto, vamos escrever esse teste com falha. Remova `UnitTest1.cs` do diretório `PrimeService.Tests` e crie um novo arquivo C# chamado `PrimeService_IsPrimeShould.cs` com o seguinte conteúdo:

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
O executor de teste de xUnit tem o ponto de entrada do programa para executar os testes por meio do Console. `dotnet test` inicia o executor de teste e fornece um argumento de linha de comando para o testrunner indicando o assembly que contém seus testes.

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
Existem alguns outros casos simples de números primos: 0, -1. Você pode adicioná-los como novos testes, com o atributo `[Fact]`, porém isso se torna entediante rapidamente. Há outros atributos de xUnit que permitem escrever um pacote de testes semelhantes.  Um `Theory` representa um pacote de testes que executa o mesmo código, mas têm diferentes argumentos de entrada.
Você pode usar o atributo `[InlineData]` para especificar valores para essas entradas. 
 
 Em vez de criar novos testes, aproveite esses dois atributos para criar uma única teoria que testa alguns valores menores que 2, que é o menor número primo:

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs#Sample_TestCode "Primeiros testes")]
```

Run `dotnet test` and you'll see that two of these tests fail.
You can make them pass by changing the service. You need to change
the `if` clause at the beginning of the method:

```cs
if(candidate < 2)
```

Agora, todos os testes são aprovados.

Você continuar a iterar adicionando mais testes, mais teorias e mais código da biblioteca principal. Você acabará rapidamente com a [versão concluída dos testes](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/test/PrimeService.Tests/PrimeService_IsPrimeShould.cs) e a [implementação completa da biblioteca](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/src/PrimeService/PrimeService.cs).

Você criou uma pequena biblioteca e um conjunto de testes de unidade para essa biblioteca.
Você estruturou essa solução para que a adição de novos pacotes de testes seja simples, assim você pode se concentrar no problema em questão. As ferramentas serão executadas automaticamente.

