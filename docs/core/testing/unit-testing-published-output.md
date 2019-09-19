---
title: Testar a saída publicada com dotnet vstest
description: Saiba como executar testes em bibliotecas publicadas, em vez de no código-fonte, com o comando dotnet vstest.
author: kendrahavens
ms.author: kehavens
ms.date: 10/18/2017
ms.custom: seodec18
ms.openlocfilehash: 93b2e1a433b5d5b9694257d4d12e47d9107f4cd7
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117026"
---
# <a name="test-published-output-with-dotnet-vstest"></a>Testar a saída publicada com dotnet vstest

Você pode executar testes na saída já publicada usando o comando `dotnet vstest`. Isso funcionará em testes xUnit, MSTest e NUnit. Basta localizar o arquivo DLL que fazia parte de sua saída publicada e execute:

```dotnetcli
dotnet vstest <MyPublishedTests>.dll
```

Em que `<MyPublishedTests>` é o nome do projeto de teste publicado.

## <a name="example"></a>Exemplo

Os comandos abaixo demonstram a execução dos testes em uma DLL publicada.

```dotnetcli
dotnet new mstest -o MyProject.Tests
cd MyProject.Tests
dotnet publish -o out
dotnet vstest out/MyProject.Tests.dll
```

> [!NOTE]
> Observação: Se o aplicativo for direcionado a uma estrutura diferente de `netcoreapp`, você ainda poderá executar o comando `dotnet vstest` passando a estrutura de destino com um sinalizador de estrutura. Por exemplo, `dotnet vstest <MyPublishedTests>.dll  --Framework:".NETFramework,Version=v4.6"`. No Visual Studio 2017 Atualização 5, a estrutura desejada é detectada automaticamente.

## <a name="see-also"></a>Consulte também

- [Teste de unidade com dotnet test e xUnit](unit-testing-with-dotnet-test.md)
- [Teste de unidade com dotnet test e NUnit](unit-testing-with-nunit.md)
- [Teste de unidade com dotnet test e MSTest](unit-testing-with-mstest.md)
