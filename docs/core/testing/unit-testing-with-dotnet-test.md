---
title: Código C# de teste de unidade no .NET Core usando dotnet test e xUnit
description: Aprenda os conceitos de teste de unidade no C# e .NET Core por meio de uma experiência interativa de criação passo a passo de uma solução de exemplo usando dotnet test e xUnit.
author: ardalis
ms.author: wiwagn
ms.date: 12/04/2019
ms.openlocfilehash: c9e3d63a2cf4f560591459833340b729ffec1b95
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240890"
---
# <a name="unit-testing-c-in-net-core-using-dotnet-test-and-xunit"></a>C# de teste de unidade no .NET Core usando dotnet test e xUnit

Este tutorial mostra como construir uma solução contendo um projeto de teste de unidade e projeto de código fonte. Para seguir o tutorial usando uma solução pré-construída, [visualize ou baixe o código de amostra](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-using-dotnet-test/). Para obter instruções de download, consulte [Exemplos e tutoriais](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="create-the-solution"></a>Criar a solução

Nesta seção, é criada uma solução que contém a origem e os projetos de teste. A solução concluída tem a seguinte estrutura de diretório:

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        PrimeService.cs
        PrimeService.csproj
    /PrimeService.Tests
        PrimeService_IsPrimeShould.cs
        PrimeServiceTests.csproj
```

As instruções a seguir fornecem as etapas para criar a solução de teste. Consulte [Comandos para criar a solução de teste](#create-test-cmd) para obter instruções para criar a solução de teste em uma etapa.

* Abra uma janela do shell.
* Execute o comando a seguir:

  ```dotnetcli
  dotnet new sln -o unit-testing-using-dotnet-test
  ```

  O [`dotnet new sln`](../tools/dotnet-new.md) comando cria uma nova solução no diretório de teste de teste *de unidade-dotnet-test.*
* Alterar o diretório para a pasta *de teste de unidade-usando-dotnet-test.*
* Execute o comando a seguir:

  ```dotnetcli
  dotnet new classlib -o PrimeService
  ```

   O [`dotnet new classlib`](../tools/dotnet-new.md) comando cria um novo projeto de biblioteca de classes na pasta *PrimeService.* A nova biblioteca de classe conterá o código a ser testado.
* Renomeie *Class1.cs* como *PrimeService.cs*.
* Substitua o código em *PrimeService.cs* pelo seguinte código:
  
  ```csharp
    using System;

    namespace Prime.Services
    {
        public class PrimeService
        {
            public bool IsPrime(int candidate)
            {
                throw new NotImplementedException("Not implemented.");
            }
        }
    }
  ```

* O código anterior:
  * Joga <xref:System.NotImplementedException> um com uma mensagem indicando que não foi implementado.
  * É atualizado mais tarde no tutorial.

<!-- preceding code shows an english bias. Message makes no sense outside english -->

* No diretório *de teste de unidade-usando-dotnet-test,* execute o seguinte comando para adicionar o projeto da biblioteca de classe à solução:

  ```dotnetcli
  dotnet sln add ./PrimeService/PrimeService.csproj
  ```

* Crie o projeto *PrimeService.Tests* executando o seguinte comando:

  ```dotnetcli
  dotnet new xunit -o PrimeService.Tests
  ```

* O comando anterior:
  * Cria o projeto *PrimeService.Tests* no diretório *PrimeService.Tests.* O projeto de teste usa [xUnit](https://xunit.github.io/) como biblioteca de testes.
  * Configura o corredor de teste `<PackageReference />`adicionando os seguintes elementos ao arquivo do projeto:
    * "Microsoft.NET.Test.Sdk"
    * "xunit"
    * "xunit.runner.visualstudio"

* Adicione o projeto de teste ao arquivo da solução executando o seguinte comando:

  ```dotnetcli
  dotnet sln add ./PrimeService.Tests/PrimeService.Tests.csproj
  ```

* Adicione `PrimeService` a biblioteca de classes como uma dependência ao projeto *PrimeService.Tests:*

  ```dotnetcli
  dotnet add ./PrimeService.Tests/PrimeService.Tests.csproj reference ./PrimeService/PrimeService.csproj  
  ```

<a name="create-test-cmd"></a>

### <a name="commands-to-create-the-solution"></a>Comandos para criar a solução

Esta seção resume todos os comandos da seção anterior. Pule esta seção se você tiver concluído as etapas na seção anterior.

Os comandos a seguir criam a solução de teste em uma máquina windows. Para macOS e Unix, atualize `ren` o `ren` comando para a versão do Sistema Operacional para renomear um arquivo:

```dotnetcli
dotnet new sln -o unit-testing-using-dotnet-test
cd unit-testing-using-dotnet-test
dotnet new classlib -o PrimeService
ren .\PrimeService\Class1.cs PrimeService.cs
dotnet sln add ./PrimeService/PrimeService.csproj
dotnet new xunit -o PrimeService.Tests
dotnet add ./PrimeService.Tests/PrimeService.Tests.csproj reference ./PrimeService/PrimeService.csproj
dotnet sln add ./PrimeService.Tests/PrimeService.Tests.csproj
```

Siga as instruções de "Substituir o código em *PrimeService.cs* com o seguinte código" na seção anterior.

## <a name="create-a-test"></a>Crie um teste

Uma abordagem popular no desenvolvimento baseado em teste (TDD) é escrever um teste antes de implementar o código de destino. Este tutorial usa a abordagem TDD. O `IsPrime` método é calável, mas não implementado. Uma chamada `IsPrime` de teste para falhar. Com TDD, um teste é escrito que é conhecido por falhar. O código de destino é atualizado para fazer o teste passar. Você continua repetindo essa abordagem, escrevendo um teste de falha e atualizando o código de destino para passar.

Atualize o projeto *PrimeService.Tests:*

* Exclua *PrimeService.Tests/UnitTest1.cs*.
* Crie um arquivo *PrimeService.Tests/PrimeService_IsPrimeShould.cs.*
* Substitua o código em *PrimeService_IsPrimeShould.cs* com o seguinte código:

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
        public void IsPrime_InputIs1_ReturnFalse()
        {
            var result = _primeService.IsPrime(1);

            Assert.False(result, "1 should not be prime");
        }
    }
}
```

O `[Fact]` atributo declara um método de teste que é executado pelo corredor de teste. A partir da pasta *PrimeService.Tests,* execute `dotnet test`. O comando [de teste dotnet](../tools/dotnet-test.md) constrói ambos os projetos e executa os testes. O corredor de teste xUnit contém o ponto de entrada do programa para executar os testes. `dotnet test`inicia o corredor de teste usando o projeto de teste da unidade.

O teste `IsPrime` falha porque não foi implementado. Usando a abordagem TDD, escreva apenas código suficiente para que este teste passe. Atualize `IsPrime` com o seguinte código:

```csharp
public bool IsPrime(int candidate)
{
    if (candidate == 1)
    {
        return false;
    }
    throw new NotImplementedException("Not fully implemented.");
}
```

Execute `dotnet test`. O teste é aprovado.

### <a name="add-more-tests"></a>Adicione mais testes

Adicione testes de número primo para 0 e -1. Você pode copiar o teste anterior e alterar o seguinte código para usar 0 e -1:

```csharp
var result = _primeService.IsPrime(1);

Assert.False(result, "1 should not be prime");
```

Copiar o código do teste quando apenas um parâmetro muda resulta em duplicação de código e inchaço do teste. Os seguintes atributos xUnit permitem escrever um conjunto de testes semelhantes:

- O `[Theory]` representa um pacote de testes que executa o mesmo código, mas têm diferentes argumentos de entrada.

- O atributo `[InlineData]` especifica valores para essas entradas.

Em vez de criar novos testes, aplique os atributos xUnit anteriores para criar uma única teoria. Substitua o código a seguir:

```csharp
[Fact]
public void IsPrime_InputIs1_ReturnFalse()
{
    var result = _primeService.IsPrime(1);

    Assert.False(result, "1 should not be prime");
}
```

pelo código a seguir:

[!code-csharp[Sample_TestCode](../../../samples/snippets/core/testing/unit-testing-using-dotnet-test/csharp/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

No código `[Theory]` anterior, `[InlineData]` e habilite testar vários valores menores que dois. Dois é o menor número primo.

Run, `dotnet test`dois dos testes falham. Para fazer com que todos `IsPrime` os testes passem, atualize o método com o seguinte código:

```csharp
public bool IsPrime(int candidate)
{
    if (candidate < 2)
    {
        return false;
    }
    throw new NotImplementedException("Not fully implemented.");
}
```

Seguindo a abordagem TDD, adicione mais testes de falha e atualize o código de destino. Veja a [versão finalizada dos testes](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs) e a [implementação completa da biblioteca](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs).

O `IsPrime` método completo não é um algoritmo eficiente para testar a primalidade.

### <a name="additional-resources"></a>Recursos adicionais

- [Site oficial do xUnit.net](https://xunit.github.io)
- [Lógica do controlador de teste no ASP.NET Core](/aspnet/core/mvc/controllers/testing)
- [`dotnet add reference`](../tools/dotnet-add-reference.md)
