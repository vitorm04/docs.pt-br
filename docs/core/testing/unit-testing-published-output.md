---
title: Testar a saída publicada com dotnet vstest
description: Saiba como executar testes em bibliotecas publicadas, em vez de no código-fonte, com o comando dotnet vstest.
author: kendrahavens
ms.author: kehavens
ms.date: 10/18/2017
ms.openlocfilehash: 7618d37782de3a16f1963380bbb56945fb73e8eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714261"
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
> Nota: Se o aplicativo tiver `netcoreapp`como alvo uma `dotnet vstest` estrutura diferente, você ainda pode executar o comando passando no framework alvo com uma bandeira de quadro. Por exemplo, `dotnet vstest <MyPublishedTests>.dll --Framework:".NETFramework,Version=v4.6"`. No Visual Studio 2017 Update 5 e posterior, a estrutura desejada é detectada automaticamente.

## <a name="see-also"></a>Confira também

- [Teste unitário com teste dotnet e xUnit](unit-testing-with-dotnet-test.md)
- [Teste de unidade com dotnet test e NUnit](unit-testing-with-nunit.md)
- [Teste de unidade com teste dotnet e MSTest](unit-testing-with-mstest.md)
