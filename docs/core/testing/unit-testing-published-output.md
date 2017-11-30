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
# <a name="test-published-output-with-dotnet-vstest"></a><span data-ttu-id="943fc-103">Teste de saída publicada com vstest dotnet</span><span class="sxs-lookup"><span data-stu-id="943fc-103">Test published output with dotnet vstest</span></span>

<span data-ttu-id="943fc-104">Você pode executar testes na saída já publicada usando o `dotnet vstest` comando.</span><span class="sxs-lookup"><span data-stu-id="943fc-104">You can run tests on already published output by using the `dotnet vstest` command.</span></span> <span data-ttu-id="943fc-105">Isso funcionará em xUnit MSTest e NUnit testes.</span><span class="sxs-lookup"><span data-stu-id="943fc-105">This will work on xUnit, MSTest, and NUnit tests.</span></span> <span data-ttu-id="943fc-106">Basta localizar o arquivo DLL que fazia parte de sua saída publicada e execute:</span><span class="sxs-lookup"><span data-stu-id="943fc-106">Simply locate the DLL file that was part of your published output and run:</span></span>
```
dotnet vstest <MyPublishedTests>.dll
```
<span data-ttu-id="943fc-107">onde `<MyPublishedTests>` é o nome do seu projeto de teste publicada.</span><span class="sxs-lookup"><span data-stu-id="943fc-107">where `<MyPublishedTests>` is the name of your published test project.</span></span>

### <a name="example-of-running-tests-on-a-published-dll"></a><span data-ttu-id="943fc-108">Exemplo de execução de testes em uma DLL publicada</span><span class="sxs-lookup"><span data-stu-id="943fc-108">Example of running tests on a published DLL</span></span>

```
dotnet new mstest -o MyProject.Tests
cd MyProject.Tests
dotnet publish -o out
dotnet vstest out/MyProject.Tests.dll
```

> [!NOTE] <span data-ttu-id="943fc-109">Observação: Se seu aplicativo tem como destino uma estrutura diferente de `netcoreapp` você ainda pode executar o `dotnet vstest` comando, passando o framework de destino com um sinalizador de framework.</span><span class="sxs-lookup"><span data-stu-id="943fc-109">Note: If your app is targeting a framework other than `netcoreapp` you can still run the `dotnet vstest` command by passing in the targeted framework with a framework flag.</span></span> <span data-ttu-id="943fc-110">Por exemplo, `dotnet vstest <MyPublishedTests>.dll  --Framework:".NETFramework,Version=v4.6"`.</span><span class="sxs-lookup"><span data-stu-id="943fc-110">For example, `dotnet vstest <MyPublishedTests>.dll  --Framework:".NETFramework,Version=v4.6"`.</span></span> <span data-ttu-id="943fc-111">No Visual Studio 2017 atualização 5 a estrutura desejada é detectada automaticamente.</span><span class="sxs-lookup"><span data-stu-id="943fc-111">In Visual Studio 2017 Update 5 the desired framework is automatically detected.</span></span>

### <a name="related-topics"></a><span data-ttu-id="943fc-112">Tópicos relacionados</span><span class="sxs-lookup"><span data-stu-id="943fc-112">Related topics</span></span>
- [<span data-ttu-id="943fc-113">Teste de unidade com teste dotnet e xUnit</span><span class="sxs-lookup"><span data-stu-id="943fc-113">Unit Testing with dotnet test and xUnit</span></span>](unit-testing-with-dotnet-test.md)
- [<span data-ttu-id="943fc-114">Teste de unidade com teste dotnet e MSTest</span><span class="sxs-lookup"><span data-stu-id="943fc-114">Unit Testing with dotnet test and MSTest</span></span>](unit-testing-with-mstest.md)
