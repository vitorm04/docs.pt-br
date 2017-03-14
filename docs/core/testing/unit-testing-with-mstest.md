---
title: Usar o MSTest com o .NET Core | Microsoft Docs
description: Como usar o MSTest com o .NET Core
keywords: MSTest, .NET, .NET Core
author: ncarandini
ms.author: wiwagn
ms.date: 02/10/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: ed447641-3e85-4e50-b7ed-004630048a3e
translationtype: Human Translation
ms.sourcegitcommit: 195664ae6409be02ca132900d9c513a7b412acd4
ms.openlocfilehash: 4ffc7dd4e11820a3c50ca83847a7ab418bf2faf3
ms.lasthandoff: 03/07/2017

---

# <a name="unit-testing-with-mstest-and-net-core"></a>Teste de unidade com o MSTest e .NET Core

## <a name="creating-the-projects"></a>Criando os projetos

[Criando bibliotecas com as Ferramentas de Plataforma Cruzada](../tutorials/libraries.md) traz informações sobre como organizar soluções de vários projetos para a fonte e os testes. Este artigo segue as convenções. A estrutura do projeto final será semelhante a esta:

```
/unit-testing-using-mstest
|__/PrimeService
   |__Source Files
   |__PrimeService.csproj
|__/PrimeService.Tests
   |__Test Files
   |__PrimeService.csproj
```

### <a name="creating-the-source-project"></a>Criando o projeto de origem

Abra uma janela do shell. Comece no diretório *unit-testing-using-mstest* e crie o diretório *PrimeService*.
Torne *PrimeService* o diretório atual e execute `dotnet new classlib` para criar o projeto de origem.

Renomeie *Class1.cs* como *PrimeService.cs*. Para usar TDD (Desenvolvimento Orientado por Testes), você criará uma implementação com falha da classe `PrimeService`:

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

Em seguida, altere o diretório de volta ao diretório *unit-testing-using-mstest* e crie o diretório *PrimeServices.Tests*.
Torne o diretório *PrimeService.Tests* o diretório atual e crie um novo projeto usando `dotnet new mstest`. Isso cria um projeto de teste que usa o MSTest como a biblioteca de teste. 

O modelo gerado configurou o executor de teste no arquivo *PrimeServiceTests.csproj*:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.0.0-preview-20170123-02" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.10-rc2" />
  <PackageReference Include="MSTest.TestFramework" Version="1.0.8-rc2" />
</ItemGroup>
```

O projeto de teste requer outros pacotes para criar e executar testes de unidade.
`dotnet new` adicionou o SDK do MSTest, a estrutura de teste do MSTest e o executor do MSTest. É necessário adicionar o pacote PrimeService como outra dependência ao projeto. É possível fazer isso usando a CLI `dotnet`:

```
dotnet add reference ../PrimeService/PrimeService.csproj
```

Se preferir, é possível editar manualmente o arquivo *PrimeService.Tests.csproj*.
Diretamente sob o primeiro nó `<ItemGroup>`, adicione outro nó `<ItemGroup>` com uma referência ao projeto de biblioteca:

```xml
  <ItemGroup>
    <ProjectReference Include="..\PrimeService\PrimeService.csproj" />
  </ItemGroup>
```

Você pode ver o arquivo inteiro no [repositório de exemplos](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService.Tests.csproj) no GitHub.

Depois que essa estrutura inicial estiver em vigor, você poderá criar seu primeiro teste.
Depois de verificar esse primeiro teste de unidade, tudo estará configurado e deverá ser executado sem problemas ao adicionar recursos e testes.

## <a name="creating-the-first-test"></a>Criando o primeiro teste

Antes de compilar a biblioteca ou os testes, é necessário executar `dotnet restore` nos diretórios *PrimeService* e *PrimeService.Tests*. Este comando restaura todos os pacotes NuGet necessários para cada projeto.

A abordagem de TDD pede a criação de um teste com falha para então fazê-lo passar e depois repetindo o processo. Portanto, vamos escrever esse teste com falha. Remova *UnitTest1.cs* do diretório *PrimeService.Tests* e crie um novo arquivo C# chamado *PrimeService_IsPrimeShould.cs* com o seguinte conteúdo:

```cs
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

Os atributos `[TestClass]` indicam uma classe que contém testes de unidade. O atributo `[TestMethod]` indica um método como um único teste. 

Salve esse arquivo e execute `dotnet build` para compilar o projeto de teste.
Se você ainda não criou o projeto `PrimeService`, o sistema de build detectará isso e o compilará, pois ele é uma dependência do projeto de teste.

Agora, execute `dotnet test` para executar os testes no console.
O executor de teste do MSTest tem o ponto de entrada do programa para executar os testes por meio do Console. `dotnet test` inicia o executor de teste e fornece um argumento de linha de comando para o executor de teste, indicando o assembly que contém os testes.

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

No diretório *PrimeService.Tests*, execute `dotnet test` novamente. O comando `dotnet test` primeiro executará um build do projeto Prime.Services e, depois, do projeto PrimeService.Tests. Depois de criar os dois projetos, ele executará esse teste único. Ele é aprovado.

## <a name="adding-more-features"></a>Adicionando mais recursos

Agora que você fez um teste ser aprovado, é hora de escrever mais.
Existem alguns outros casos simples de números primos: 0, -1. Você pode adicioná-los como novos testes, com o atributo `[TestMethod]`, porém isso se torna entediante rapidamente. Há outros atributos do MSTest que permitem escrever um pacote de testes semelhantes.  Um `DataTestMethod` representa um pacote de testes que executa o mesmo código, mas têm diferentes argumentos de entrada.
Você pode usar o atributo `[DataRow]` para especificar valores para essas entradas. 
 
 Em vez de criar novos testes, aproveite esses dois atributos para criar um único método de teste de dados que testa alguns valores inferiores a 2, que é o menor número primo:

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs#Sample_TestCode "Primeiros testes")]

Execute `dotnet test` e você verá que dois desses testes falham.
Você pode fazê-los serem aprovados alterando o serviço. Você precisa alterar a cláusula `if` no início do método:

```cs
if(candidate < 2)
```

Agora, todos os testes são aprovados.

Você continuar a iterar adicionando mais testes, mais teorias e mais código da biblioteca principal. Você acabará rapidamente com a [versão concluída dos testes](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs) e a [implementação completa da biblioteca](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-mstest/PrimeService/PrimeService.cs).

Você criou uma pequena biblioteca e um conjunto de testes de unidade para essa biblioteca.
Você estruturou essa solução para que a adição de novos pacotes de testes seja simples, assim você pode se concentrar no problema em questão. As ferramentas serão executadas automaticamente.
