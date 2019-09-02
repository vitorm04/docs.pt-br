---
title: Testar a saída publicada com dotnet vstest
description: Saiba como executar testes em bibliotecas publicadas, em vez de no código-fonte, com o comando dotnet vstest.
author: kendrahavens
ms.author: kehavens
ms.date: 10/18/2017
ms.custom: seodec18
ms.openlocfilehash: 9ac03053bc762d0176e087545871ca8a145cd41e
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70168288"
---
# <a name="test-published-output-with-dotnet-vstest"></a><span data-ttu-id="138d4-103">Testar a saída publicada com dotnet vstest</span><span class="sxs-lookup"><span data-stu-id="138d4-103">Test published output with dotnet vstest</span></span>

<span data-ttu-id="138d4-104">Você pode executar testes na saída já publicada usando o comando `dotnet vstest`.</span><span class="sxs-lookup"><span data-stu-id="138d4-104">You can run tests on already published output by using the `dotnet vstest` command.</span></span> <span data-ttu-id="138d4-105">Isso funcionará em testes xUnit, MSTest e NUnit.</span><span class="sxs-lookup"><span data-stu-id="138d4-105">This will work on xUnit, MSTest, and NUnit tests.</span></span> <span data-ttu-id="138d4-106">Basta localizar o arquivo DLL que fazia parte de sua saída publicada e execute:</span><span class="sxs-lookup"><span data-stu-id="138d4-106">Simply locate the DLL file that was part of your published output and run:</span></span>

```console
dotnet vstest <MyPublishedTests>.dll
```

<span data-ttu-id="138d4-107">Em que `<MyPublishedTests>` é o nome do projeto de teste publicado.</span><span class="sxs-lookup"><span data-stu-id="138d4-107">Where `<MyPublishedTests>` is the name of your published test project.</span></span>

## <a name="example"></a><span data-ttu-id="138d4-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="138d4-108">Example</span></span>

<span data-ttu-id="138d4-109">Os comandos abaixo demonstram a execução dos testes em uma DLL publicada.</span><span class="sxs-lookup"><span data-stu-id="138d4-109">The commands below demonstrate running tests on a published DLL.</span></span>

```console
dotnet new mstest -o MyProject.Tests
cd MyProject.Tests
dotnet publish -o out
dotnet vstest out/MyProject.Tests.dll
```

> [!NOTE]
> <span data-ttu-id="138d4-110">Observação: Se o aplicativo for direcionado a uma estrutura diferente de `netcoreapp`, você ainda poderá executar o comando `dotnet vstest` passando a estrutura de destino com um sinalizador de estrutura.</span><span class="sxs-lookup"><span data-stu-id="138d4-110">Note: If your app is targeting a framework other than `netcoreapp` you can still run the `dotnet vstest` command by passing in the targeted framework with a framework flag.</span></span> <span data-ttu-id="138d4-111">Por exemplo, `dotnet vstest <MyPublishedTests>.dll  --Framework:".NETFramework,Version=v4.6"`.</span><span class="sxs-lookup"><span data-stu-id="138d4-111">For example, `dotnet vstest <MyPublishedTests>.dll  --Framework:".NETFramework,Version=v4.6"`.</span></span> <span data-ttu-id="138d4-112">No Visual Studio 2017 Atualização 5, a estrutura desejada é detectada automaticamente.</span><span class="sxs-lookup"><span data-stu-id="138d4-112">In Visual Studio 2017 Update 5 the desired framework is automatically detected.</span></span>

## <a name="see-also"></a><span data-ttu-id="138d4-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="138d4-113">See also</span></span>

- [<span data-ttu-id="138d4-114">Teste de unidade com dotnet test e xUnit</span><span class="sxs-lookup"><span data-stu-id="138d4-114">Unit Testing with dotnet test and xUnit</span></span>](unit-testing-with-dotnet-test.md)
- [<span data-ttu-id="138d4-115">Teste de unidade com dotnet test e NUnit</span><span class="sxs-lookup"><span data-stu-id="138d4-115">Unit Testing with dotnet test and NUnit</span></span>](unit-testing-with-nunit.md)
- [<span data-ttu-id="138d4-116">Teste de unidade com dotnet test e MSTest</span><span class="sxs-lookup"><span data-stu-id="138d4-116">Unit Testing with dotnet test and MSTest</span></span>](unit-testing-with-mstest.md)
