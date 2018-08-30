---
title: Testar a saída publicada com dotnet vstest
description: Saiba como executar testes na saída publicada com o comando dotnet vstest.
author: kendrahavens
ms.author: kehavens
ms.date: 10/18/2017
ms.openlocfilehash: e99000996f5dfa9f9d4f9b823e36ecbe325da835
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/26/2018
ms.locfileid: "42936020"
---
# <a name="test-published-output-with-dotnet-vstest"></a><span data-ttu-id="f9d7e-103">Testar a saída publicada com dotnet vstest</span><span class="sxs-lookup"><span data-stu-id="f9d7e-103">Test published output with dotnet vstest</span></span>

<span data-ttu-id="f9d7e-104">Você pode executar testes na saída já publicada usando o comando `dotnet vstest`.</span><span class="sxs-lookup"><span data-stu-id="f9d7e-104">You can run tests on already published output by using the `dotnet vstest` command.</span></span> <span data-ttu-id="f9d7e-105">Isso funcionará em testes xUnit, MSTest e NUnit.</span><span class="sxs-lookup"><span data-stu-id="f9d7e-105">This will work on xUnit, MSTest, and NUnit tests.</span></span> <span data-ttu-id="f9d7e-106">Basta localizar o arquivo DLL que fazia parte de sua saída publicada e execute:</span><span class="sxs-lookup"><span data-stu-id="f9d7e-106">Simply locate the DLL file that was part of your published output and run:</span></span>

```
dotnet vstest <MyPublishedTests>.dll
```

<span data-ttu-id="f9d7e-107">em que `<MyPublishedTests>` é o nome de seu projeto de teste publicado.</span><span class="sxs-lookup"><span data-stu-id="f9d7e-107">where `<MyPublishedTests>` is the name of your published test project.</span></span>

## <a name="example-of-running-tests-on-a-published-dll"></a><span data-ttu-id="f9d7e-108">Exemplo de execução de testes em uma DLL publicada</span><span class="sxs-lookup"><span data-stu-id="f9d7e-108">Example of running tests on a published DLL</span></span>

```
dotnet new mstest -o MyProject.Tests
cd MyProject.Tests
dotnet publish -o out
dotnet vstest out/MyProject.Tests.dll
```

> [!NOTE]
> <span data-ttu-id="f9d7e-109">Observação: se o seu aplicativo for direcionado a uma estrutura diferente de `netcoreapp`, ainda será possível executar o comando `dotnet vstest`, passando a estrutura de destino com um sinalizador de estrutura.</span><span class="sxs-lookup"><span data-stu-id="f9d7e-109">Note: If your app is targeting a framework other than `netcoreapp` you can still run the `dotnet vstest` command by passing in the targeted framework with a framework flag.</span></span> <span data-ttu-id="f9d7e-110">Por exemplo, `dotnet vstest <MyPublishedTests>.dll  --Framework:".NETFramework,Version=v4.6"`.</span><span class="sxs-lookup"><span data-stu-id="f9d7e-110">For example, `dotnet vstest <MyPublishedTests>.dll  --Framework:".NETFramework,Version=v4.6"`.</span></span> <span data-ttu-id="f9d7e-111">No Visual Studio 2017 Atualização 5, a estrutura desejada é detectada automaticamente.</span><span class="sxs-lookup"><span data-stu-id="f9d7e-111">In Visual Studio 2017 Update 5 the desired framework is automatically detected.</span></span>

## <a name="see-also"></a><span data-ttu-id="f9d7e-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f9d7e-112">See also</span></span>
- [<span data-ttu-id="f9d7e-113">Teste de unidade com dotnet test e xUnit</span><span class="sxs-lookup"><span data-stu-id="f9d7e-113">Unit Testing with dotnet test and xUnit</span></span>](unit-testing-with-dotnet-test.md)
- [<span data-ttu-id="f9d7e-114">Teste de unidade com dotnet test e NUnit</span><span class="sxs-lookup"><span data-stu-id="f9d7e-114">Unit Testing with dotnet test and NUnit</span></span>](unit-testing-with-nunit.md)
- [<span data-ttu-id="f9d7e-115">Teste de unidade com dotnet test e MSTest</span><span class="sxs-lookup"><span data-stu-id="f9d7e-115">Unit Testing with dotnet test and MSTest</span></span>](unit-testing-with-mstest.md)
