---
title: Testar a saída publicada com dotnet vstest
description: Saiba como executar testes na saída publicada com o comando dotnet vstest.
author: kendrahavens
ms.author: kehavens
ms.date: 10/18/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.workload:
- dotnetcore
ms.openlocfilehash: 2f750a8bb0907069691c4a4491beeb4b1733df29
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="test-published-output-with-dotnet-vstest"></a>Testar a saída publicada com dotnet vstest

Você pode executar testes na saída já publicada usando o comando `dotnet vstest`. Isso funcionará em testes xUnit, MSTest e NUnit. Basta localizar o arquivo DLL que fazia parte de sua saída publicada e execute:

```
dotnet vstest <MyPublishedTests>.dll
```

em que `<MyPublishedTests>` é o nome de seu projeto de teste publicado.

## <a name="example-of-running-tests-on-a-published-dll"></a>Exemplo de execução de testes em uma DLL publicada

```
dotnet new mstest -o MyProject.Tests
cd MyProject.Tests
dotnet publish -o out
dotnet vstest out/MyProject.Tests.dll
```

> [!NOTE]
> Observação: se o seu aplicativo for direcionado a uma estrutura diferente de `netcoreapp`, ainda será possível executar o comando `dotnet vstest`, passando a estrutura de destino com um sinalizador de estrutura. Por exemplo, `dotnet vstest <MyPublishedTests>.dll  --Framework:".NETFramework,Version=v4.6"`. No Visual Studio 2017 Atualização 5, a estrutura desejada é detectada automaticamente.

## <a name="see-also"></a>Consulte também
 [Teste de unidade com dotnet test e xUnit](unit-testing-with-dotnet-test.md)  
 [Teste de unidade com dotnet test e MSTest](unit-testing-with-mstest.md)  
