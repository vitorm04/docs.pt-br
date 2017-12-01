---
title: "Teste de saída publicada com vstest dotnet"
description: "Saiba como executar testes na saída publicada com o comando de vstest dotnet."
author: kendrahavens
ms.author: kehavens
ms.date: 10/18/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 3965e4ca-75b8-4969-b3af-ca993c397a15
ms.openlocfilehash: 217787d41a9da6000941ded6caaa4f44d124644b
ms.sourcegitcommit: 8a4f8e6a7f1341764abcd188a332cc28d1e2d8ec
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/24/2017
---
# <a name="test-published-output-with-dotnet-vstest"></a>Teste de saída publicada com vstest dotnet

Você pode executar testes na saída já publicada usando o `dotnet vstest` comando. Isso funcionará em xUnit MSTest e NUnit testes. Basta localizar o arquivo DLL que fazia parte de sua saída publicada e execute:
```
dotnet vstest <MyPublishedTests>.dll
```
onde `<MyPublishedTests>` é o nome do seu projeto de teste publicada.

### <a name="example-of-running-tests-on-a-published-dll"></a>Exemplo de execução de testes em uma DLL publicada

```
dotnet new mstest -o MyProject.Tests
cd MyProject.Tests
dotnet publish -o out
dotnet vstest out/MyProject.Tests.dll
```

> [!NOTE] Observação: Se seu aplicativo tem como destino uma estrutura diferente de `netcoreapp` você ainda pode executar o `dotnet vstest` comando, passando o framework de destino com um sinalizador de framework. Por exemplo, `dotnet vstest <MyPublishedTests>.dll  --Framework:".NETFramework,Version=v4.6"`. No Visual Studio 2017 atualização 5 a estrutura desejada é detectada automaticamente.

### <a name="related-topics"></a>Tópicos relacionados
- [Teste de unidade com teste dotnet e xUnit](unit-testing-with-dotnet-test.md)
- [Teste de unidade com teste dotnet e MSTest](unit-testing-with-mstest.md)
