---
title: Testar a saída publicada com dotnet vstest
description: Saiba como executar testes na saída publicada com o comando dotnet vstest.
author: kendrahavens
ms.author: kehavens
ms.date: 10/18/2017
ms.openlocfilehash: e99000996f5dfa9f9d4f9b823e36ecbe325da835
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43404709"
---
# <a name="test-published-output-with-dotnet-vstest"></a><span data-ttu-id="1ef9a-103">Testar a saída publicada com dotnet vstest</span><span class="sxs-lookup"><span data-stu-id="1ef9a-103">Test published output with dotnet vstest</span></span>

<span data-ttu-id="1ef9a-104">Você pode executar testes na saída já publicada usando o comando `dotnet vstest`.</span><span class="sxs-lookup"><span data-stu-id="1ef9a-104">You can run tests on already published output by using the `dotnet vstest` command.</span></span> <span data-ttu-id="1ef9a-105">Isso funcionará em testes xUnit, MSTest e NUnit.</span><span class="sxs-lookup"><span data-stu-id="1ef9a-105">This will work on xUnit, MSTest, and NUnit tests.</span></span> <span data-ttu-id="1ef9a-106">Basta localizar o arquivo DLL que fazia parte de sua saída publicada e execute:</span><span class="sxs-lookup"><span data-stu-id="1ef9a-106">Simply locate the DLL file that was part of your published output and run:</span></span>

```
dotnet vstest <MyPublishedTests>.dll
```

<span data-ttu-id="1ef9a-107">em que `<MyPublishedTests>` é o nome de seu projeto de teste publicado.</span><span class="sxs-lookup"><span data-stu-id="1ef9a-107">where `<MyPublishedTests>` is the name of your published test project.</span></span>

## <a name="example-of-running-tests-on-a-published-dll"></a><span data-ttu-id="1ef9a-108">Exemplo de execução de testes em uma DLL publicada</span><span class="sxs-lookup"><span data-stu-id="1ef9a-108">Example of running tests on a published DLL</span></span>

```
dotnet new mstest -o MyProject.Tests
cd MyProject.Tests
dotnet publish -o out
dotnet vstest out/MyProject.Tests.dll
```

> [!NOTE]
> <span data-ttu-id="1ef9a-109">Observação: se o seu aplicativo for direcionado a uma estrutura diferente de `netcoreapp`, ainda será possível executar o comando `dotnet vstest`, passando a estrutura de destino com um sinalizador de estrutura.</span><span class="sxs-lookup"><span data-stu-id="1ef9a-109">Note: If your app is targeting a framework other than `netcoreapp` you can still run the `dotnet vstest` command by passing in the targeted framework with a framework flag.</span></span> <span data-ttu-id="1ef9a-110">Por exemplo, `dotnet vstest <MyPublishedTests>.dll  --Framework:".NETFramework,Version=v4.6"`.</span><span class="sxs-lookup"><span data-stu-id="1ef9a-110">For example, `dotnet vstest <MyPublishedTests>.dll  --Framework:".NETFramework,Version=v4.6"`.</span></span> <span data-ttu-id="1ef9a-111">No Visual Studio 2017 Atualização 5, a estrutura desejada é detectada automaticamente.</span><span class="sxs-lookup"><span data-stu-id="1ef9a-111">In Visual Studio 2017 Update 5 the desired framework is automatically detected.</span></span>

## <a name="see-also"></a><span data-ttu-id="1ef9a-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1ef9a-112">See also</span></span>
- [<span data-ttu-id="1ef9a-113">Teste de unidade com dotnet test e xUnit</span><span class="sxs-lookup"><span data-stu-id="1ef9a-113">Unit Testing with dotnet test and xUnit</span></span>](unit-testing-with-dotnet-test.md)
- [<span data-ttu-id="1ef9a-114">Teste de unidade com dotnet test e NUnit</span><span class="sxs-lookup"><span data-stu-id="1ef9a-114">Unit Testing with dotnet test and NUnit</span></span>](unit-testing-with-nunit.md)
- [<span data-ttu-id="1ef9a-115">Teste de unidade com dotnet test e MSTest</span><span class="sxs-lookup"><span data-stu-id="1ef9a-115">Unit Testing with dotnet test and MSTest</span></span>](unit-testing-with-mstest.md)
