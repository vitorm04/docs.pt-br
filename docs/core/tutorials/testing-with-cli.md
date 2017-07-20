---
title: Organizando e testando projetos com a linha de comando do .NET Core | Microsoft Docs
description: Este tutorial explica como organizar e testar projetos do .NET Core por meio da linha de comando.
keywords: .NET, .NET Core, teste de unidade, .NET CLI, xUnit
author: cartermp
ms.author: mairaw
ms.date: 05/16/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 52ff1be3-d92e-4477-9c84-8c1771e87ab5
ms.translationtype: Human Translation
ms.sourcegitcommit: 6edd52bc56a03138fe16048fa06cad00a2af4847
ms.openlocfilehash: 1e6e987777678ade860f108aed05bba926a6d4fd
ms.contentlocale: pt-br
ms.lasthandoff: 05/16/2017

---

# <a name="organizing-and-testing-projects-with-the-net-core-command-line"></a>Organizando e testando projetos com a linha de comando do .NET Core

Este tutorial segue a [Introdução ao .NET Core no Windows/Linux/macOS usando a linha de comando](using-with-xplat-cli.md), levando você além da criação de um simples aplicativo de console para desenvolver aplicativos avançados e bem organizados. Depois de mostrar como usar pastas para organizar seu código, este tutorial mostra como estender um aplicativo de console com a estrutura de teste [xUnit](https://xunit.github.io/).

## <a name="using-folders-to-organize-code"></a>Usar pastas para organizar o código

Se você quiser introduzir novos tipos em um aplicativo de console, poderá fazer isso adicionando arquivos que contêm os tipos para o aplicativo. Por exemplo, se você adicionar arquivos contendo os tipos `AccountInformation` e `MonthlyReportRecords` ao seu projeto, a estrutura do arquivo de projeto será simples e fácil de navegar:

```
/MyProject
|__AccountInformation.cs
|__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

No entanto, isso funciona bem apenas quando o projeto é relativamente pequeno. Você pode imaginar o que acontecerá se adicionar 20 tipos ao projeto? O projeto definitivamente não será fácil navegar e manter com tantos arquivos dividindo o diretório raiz do projeto.

Para organizar o projeto, crie uma nova pasta e nomeie-a como *Modelos* para armazenar os arquivos do tipo. Coloque os arquivos de tipo na pasta *Modelos*:

```
/MyProject
|__/Models
   |__AccountInformation.cs
   |__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

Projetos que agrupam arquivos em pastas de forma lógica são fáceis de navegar e manter. Na próxima seção, você criará um exemplo mais complexo com pastas e testes de unidade.

## <a name="organizing-and-testing-using-the-newtypes-pets-sample"></a>Organizando e testando usando o Exemplo Pets de NewTypes

### <a name="building-the-sample"></a>Compilando o exemplo

Para as etapas a seguir, você pode acompanhar usando o [NewTypes Pets Sample](https://github.com/dotnet/docs/tree/master/samples/core/console-apps/NewTypesMsBuild) (Exemplo Pets de NewTypes) ou criar seus próprios arquivos e pastas. Os tipos são organizados logicamente em uma estrutura de pastas que permite a adição de mais tipos posteriormente e os testes também são posicionados logicamente nas pastas, permitindo a adição de mais testes posteriormente.

Esse exemplo contém dois tipos, `Dog` e `Cat`, e faz com que eles implementem uma interface comum, `IPet`. Para o projeto `NewTypes`, sua meta é organizar os tipos relacionados a animais de estimação em uma pasta *Pets*. Se outro conjunto de tipos for adicionado posteriormente, *WildAnimals* por exemplo, ele será colocado na pasta *NewTypes* junto com a pasta *Pets*. A pasta *WildAnimals* pode conter tipos de animais que não são animais de estimação, como os tipos `Squirrel` e `Rabbit`. Dessa forma, conforme os tipos são adicionados, o projeto continua bem organizado. 

Crie a seguinte estrutura de pasta com o conteúdo do arquivo indicado:

```
/NewTypes
|__/src
   |__/NewTypes
      |__/Pets
         |__Dog.cs
         |__Cat.cs
         |__IPet.cs
      |__Program.cs
      |__NewTypes.csproj
```

*IPet.cs*:

[!code-csharp[Interface IPet](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Pets/IPet.cs)]

*Dog.cs*:

[!code-csharp[Classe Dog](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Pets/Dog.cs)]

*Cat.cs*:

[!code-csharp[Classe Cat](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Pets/Cat.cs)]

*Program.cs*:

[!code-csharp[Main](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Program.cs)]

*NewTypes.csproj*:

[!code-xml[csproj NewTypes](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/NewTypes.csproj)]

Execute os seguintes comandos:

```console
dotnet restore
dotnet run
```

Obtenha a seguinte saída:

```console
Woof!
Meow!
```

Exercício opcional: você pode adicionar um novo tipo de animal de estimação, como um `Bird`, estendendo esse projeto. Faça com que o método `TalkToOwner` de pássaro dê um `Tweet!` para o proprietário. Execute o aplicativo novamente. A saída incluirá `Tweet!`

### <a name="testing-the-sample"></a>Testando o exemplo

O projeto `NewTypes` está em funcionamento e você o organizou mantendo os tipos relacionados a animais de estimação em uma pasta. Em seguida, crie seu projeto de teste e comece a escrever testes com a estrutura de teste [xUnit](https://xunit.github.io/). O teste de unidade permite que você verifique automaticamente o comportamento dos seus tipos de animais de estimação para confirmar se eles estão funcionando corretamente.

Crie uma pasta *test* com a pasta *NewTypesTests* nela. Em um prompt de comando da pasta *NewTypesTests*, execute `dotnet new xunit`. Isso gera dois arquivos: *NewTypesTests.csproj* e *UnitTest1.cs*.

No momento, o projeto de teste não pode testar os tipos no `NewTypes` e requer uma referência de projeto para o projeto `NewTypes`. Para adicionar uma referência de projeto, use o comando [`dotnet add reference`](../tools/dotnet-add-reference.md):

```
dotnet add reference ../../src/NewTypes/NewTypes.csproj
```

Você também tem a opção de adicionar manualmente a referência de projeto adicionando um nó `<ItemGroup>` ao arquivo *NewTypesTests.csproj*:

```xml
<ItemGroup>
  <ProjectReference Include="../../src/NewTypes/NewTypes.csproj" />
</ItemGroup>
```

*NewTypesTests.csproj*:

[!code-xml[csproj NewTypesTests](../../../samples/core/console-apps/NewTypesMsBuild/test/NewTypesTests/NewTypesTests.csproj)]

O arquivo *NewTypesTests.csproj* com o seguinte:

* Referência de pacote para `Microsoft.NET.Test.Sdk`, a infraestrutura de teste do .NET
* Referência de pacote para `xunit`, a estrutura de teste do xUnit
* Referência de pacote para `xunit.runner.visualstudio`, o executor de teste
* Referência de projeto para `NewTypes`, o código a ser testado

Altere o nome de *UnitTest1.cs* para *PetTests.cs* e substitua o código no arquivo pelo seguinte:

```csharp
using System;
using Xunit;
using Pets;

public class PetTests
{
    [Fact]
    public void DogTalkToOwnerReturnsWoof()
    {
        string expected = "Woof!";
        string actual = new Dog().TalkToOwner();
        
        Assert.NotEqual(expected, actual);
    }
    
    [Fact]
    public void CatTalkToOwnerReturnsMeow()
    {
        string expected = "Meow!";
        string actual = new Cat().TalkToOwner();
        
        Assert.NotEqual(expected, actual);
    }
}
```

Exercício opcional: se você adicionou um tipo `Bird` anteriormente que produz um `Tweet!` para o proprietário, adicione um método de teste ao arquivo *PetTests.cs*, `BirdTalkToOwnerReturnsTweet`, para verificar se o método `TalkToOwner` funciona corretamente para o tipo `Bird`.

> [!NOTE]
> Embora você espere que os valores `expected` e `actual` sejam iguais, as asserções inicias com as verificações `Assert.NotEqual` especificam que eles *não são iguais*. Sempre crie inicialmente os testes para falhar uma vez para verificar a lógica dos testes. Essa é uma etapa importante na metodologia TDD (design orientado a testes). Depois de confirmar que os testes falham, ajuste as asserções para permitir que eles sejam aprovados.

O código a seguir mostra a estrutura do projeto completo:

```
/NewTypes
|__/src
   |__/NewTypes
      |__/Pets
         |__Dog.cs
         |__Cat.cs
         |__IPet.cs
      |__Program.cs
      |__NewTypes.csproj
|__/test
   |__NewTypesTests
      |__PetTests.cs
      |__NewTypesTests.csproj
```

Inicie no diretório *test/NewTypesTests*. Restaure o projeto de teste com o comando [`dotnet restore`](../tools/dotnet-restore.md). Execute os testes com o comando [`dotnet test`](../tools/dotnet-test.md). Esse comando inicia o executor de teste especificado no arquivo de projeto.
 
Conforme o esperado, o teste falha e o console exibe a seguinte saída:
 
```
Test run for C:\NewTypesMsBuild\test\NewTypesTests\bin\Debug\netcoreapp1.1\NewTypesTests.dll(.NETCoreApp,Version=v1.1)
Microsoft (R) Test Execution Command Line Tool Version 15.0.0.0
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...
[xUnit.net 00:00:00.7271827]   Discovering: NewTypesTests
[xUnit.net 00:00:00.8258687]   Discovered:  NewTypesTests
[xUnit.net 00:00:00.8663545]   Starting:    NewTypesTests
[xUnit.net 00:00:01.0109236]     PetTests.CatTalkToOwnerReturnsMeow [FAIL]
[xUnit.net 00:00:01.0119107]       Assert.NotEqual() Failure
[xUnit.net 00:00:01.0120278]       Expected: Not "Meow!"
[xUnit.net 00:00:01.0120968]       Actual:   "Meow!"
[xUnit.net 00:00:01.0130500]       Stack Trace:
[xUnit.net 00:00:01.0141240]         C:\NewTypesMsBuild\test\NewTypesTests\PetTests.cs(22,0): at PetTests.CatTalkToOwnerReturnsMeow()
[xUnit.net 00:00:01.0272364]     PetTests.DogTalkToOwnerReturnsWoof [FAIL]
[xUnit.net 00:00:01.0273649]       Assert.NotEqual() Failure
[xUnit.net 00:00:01.0274166]       Expected: Not "Woof!"
[xUnit.net 00:00:01.0274690]       Actual:   "Woof!"
[xUnit.net 00:00:01.0275264]       Stack Trace:
[xUnit.net 00:00:01.0275960]         C:\NewTypesMsBuild\test\NewTypesTests\PetTests.cs(13,0): at PetTests.DogTalkToOwnerReturnsWoof()
[xUnit.net 00:00:01.0294509]   Finished:    NewTypesTests
Failed   PetTests.CatTalkToOwnerReturnsMeow
Error Message:
 Assert.NotEqual() Failure
Expected: Not "Meow!"
Actual:   "Meow!"
Stack Trace:
   at PetTests.CatTalkToOwnerReturnsMeow() in C:\NewTypesMsBuild\test\NewTypesTests\PetTests.cs:line 22
Failed   PetTests.DogTalkToOwnerReturnsWoof
Error Message:
 Assert.NotEqual() Failure
Expected: Not "Woof!"
Actual:   "Woof!"
Stack Trace:
   at PetTests.DogTalkToOwnerReturnsWoof() in C:\NewTypesMsBuild\test\NewTypesTests\PetTests.cs:line 13

Total tests: 2. Passed: 0. Failed: 2. Skipped: 0.
Test Run Failed.
Test execution time: 2.1371 Seconds
```

Altere as asserções de seus testes de `Assert.NotEqual` para `Assert.Equal`:

[!code-csharp[Classe PetTests](../../../samples/core/console-apps/NewTypesMsBuild/test/NewTypesTests/PetTests.cs)]

Execute novamente os testes com o comando `dotnet test` e obtenha a seguinte saída:

```
Microsoft (R) Test Execution Command Line Tool Version 15.0.0.0
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...
[xUnit.net 00:00:01.3882374]   Discovering: NewTypesTests
[xUnit.net 00:00:01.4767970]   Discovered:  NewTypesTests
[xUnit.net 00:00:01.5157667]   Starting:    NewTypesTests
[xUnit.net 00:00:01.6408870]   Finished:    NewTypesTests

Total tests: 2. Passed: 2. Failed: 0. Skipped: 0.
Test Run Successful.
Test execution time: 1.6634 Seconds
```

O teste é aprovado. Os métodos dos tipos de animais de estimação retornam os valores corretos ao conversar com o proprietário.

Você aprendeu técnicas para organizar e testar projetos usando xUnit. Prossiga com essas técnicas aplicando-as em seus próprios projetos. *Boa codificação!*
