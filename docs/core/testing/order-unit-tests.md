---
title: Solicitar testes de unidade
description: Saiba como solicitar testes de unidade com o .NET Core.
author: IEvangelist
ms.date: 05/18/2020
zone_pivot_groups: unit-testing-framework-set-one
ms.openlocfilehash: 3400ae440a828054624d67c14807ee72783e466a
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989261"
---
# <a name="order-unit-tests"></a><span data-ttu-id="92520-103">Solicitar testes de unidade</span><span class="sxs-lookup"><span data-stu-id="92520-103">Order unit tests</span></span>

<span data-ttu-id="92520-104">Ocasionalmente, talvez você queira que os testes de unidade sejam executados em uma ordem específica.</span><span class="sxs-lookup"><span data-stu-id="92520-104">Occasionally, you may want to have unit tests run in a specific order.</span></span> <span data-ttu-id="92520-105">O ideal é que a ordem em que os testes de unidade sejam executados _não_ seja importante, e é uma [prática recomendada](unit-testing-best-practices.md) evitar a ordenação de testes de unidade.</span><span class="sxs-lookup"><span data-stu-id="92520-105">Ideally, the order in which unit tests run should _not_ matter, and it is [best practice](unit-testing-best-practices.md) to avoid ordering unit tests.</span></span> <span data-ttu-id="92520-106">Independentemente disso, pode ser necessário fazer isso.</span><span class="sxs-lookup"><span data-stu-id="92520-106">Regardless, there may be a need to do so.</span></span> <span data-ttu-id="92520-107">Nesse caso, este artigo demonstra como ordenar execuções de teste.</span><span class="sxs-lookup"><span data-stu-id="92520-107">In that case, this article demonstrates how to order test runs.</span></span>

<span data-ttu-id="92520-108">Se você preferir procurar o código-fonte, consulte o repositório solicitar exemplo de [testes de unidade do .NET Core](/samples/dotnet/samples/order-unit-tests-cs) .</span><span class="sxs-lookup"><span data-stu-id="92520-108">If you prefer to browse the source code, see the [order .NET Core unit tests](/samples/dotnet/samples/order-unit-tests-cs) sample repository.</span></span>

> [!TIP]
> <span data-ttu-id="92520-109">Além dos recursos de pedidos descritos neste artigo, considere a [criação de listas de reprodução personalizadas com o Visual Studio](/visualstudio/test/run-unit-tests-with-test-explorer?view=vs-2019#create-custom-playlists) como alternativa.</span><span class="sxs-lookup"><span data-stu-id="92520-109">In addition to the ordering capabilities outlined in this article, consider [creating custom playlists with Visual Studio](/visualstudio/test/run-unit-tests-with-test-explorer?view=vs-2019#create-custom-playlists) as an alternative.</span></span>

:::zone pivot="mstest"

## <a name="order-alphabetically"></a><span data-ttu-id="92520-110">Ordem alfabética</span><span class="sxs-lookup"><span data-stu-id="92520-110">Order alphabetically</span></span>

<span data-ttu-id="92520-111">Com MSTest, os testes são ordenados automaticamente pelo seu nome de teste.</span><span class="sxs-lookup"><span data-stu-id="92520-111">With MSTest, tests are automatically ordered by their test name.</span></span>

> [!NOTE]
> <span data-ttu-id="92520-112">Um teste chamado `Test14` será executado antes `Test2` mesmo que o número `2` seja menor que `14` .</span><span class="sxs-lookup"><span data-stu-id="92520-112">A test named `Test14` will run before `Test2` even though the number  `2` is less than `14`.</span></span> <span data-ttu-id="92520-113">Isso ocorre porque, o nome do teste Order usa o nome de texto do teste.</span><span class="sxs-lookup"><span data-stu-id="92520-113">This is because, test name ordering uses the text name of the test.</span></span>

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/MSTest.Project/ByAlphabeticalOrder.cs":::

:::zone-end
:::zone pivot="xunit"

<span data-ttu-id="92520-114">A estrutura de teste do xUnit permite mais granularidade e controle da ordem de execução de teste.</span><span class="sxs-lookup"><span data-stu-id="92520-114">The xUnit test framework allows for more granularity and control of test run order.</span></span> <span data-ttu-id="92520-115">Você implementa as `ITestCaseOrderer` `ITestCollectionOrderer` interfaces e para controlar a ordem dos casos de teste para uma classe ou coleções de teste.</span><span class="sxs-lookup"><span data-stu-id="92520-115">You implement the `ITestCaseOrderer` and `ITestCollectionOrderer` interfaces to control the order of test cases for a class, or test collections.</span></span>

## <a name="order-by-test-case-alphabetically"></a><span data-ttu-id="92520-116">Ordenar por caso de teste em ordem alfabética</span><span class="sxs-lookup"><span data-stu-id="92520-116">Order by test case alphabetically</span></span>

<span data-ttu-id="92520-117">Para ordenar os casos de teste pelo nome do método, você implementa o `ITestCaseOrderer` e fornece um mecanismo de ordenação.</span><span class="sxs-lookup"><span data-stu-id="92520-117">To order test cases by their method name, you implement the `ITestCaseOrderer` and provide an ordering mechanism.</span></span>

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/XUnit.TestProject/Orderers/AlphabeticalOrderer.cs":::

<span data-ttu-id="92520-118">Em seguida, em uma classe de teste, defina a ordem do caso de teste com o `TestCaseOrdererAttribute` .</span><span class="sxs-lookup"><span data-stu-id="92520-118">Then in a test class you set the test case order with the `TestCaseOrdererAttribute`.</span></span>

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/XUnit.TestProject/ByAlphabeticalOrder.cs":::

## <a name="order-by-collection-alphabetically"></a><span data-ttu-id="92520-119">Ordenar por coleção em ordem alfabética</span><span class="sxs-lookup"><span data-stu-id="92520-119">Order by collection alphabetically</span></span>

<span data-ttu-id="92520-120">Para solicitar coleções de teste por seu nome de exibição, você implementa o `ITestCollectionOrderer` e fornece um mecanismo de ordenação.</span><span class="sxs-lookup"><span data-stu-id="92520-120">To order test collections by their display name, you implement the `ITestCollectionOrderer` and provide an ordering mechanism.</span></span>

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/XUnit.TestProject/Orderers/DisplayNameOrderer.cs":::

<span data-ttu-id="92520-121">Como as coleções de testes podem ser executadas em paralelo, você deve desabilitar explicitamente a paralelização de teste das coleções com o `CollectionBehaviorAttribute` .</span><span class="sxs-lookup"><span data-stu-id="92520-121">Since test collections potentially run in parallel, you must explicitly disable test parallelization of the collections with the `CollectionBehaviorAttribute`.</span></span> <span data-ttu-id="92520-122">Em seguida, especifique a implementação para o `TestCollectionOrdererAttribute` .</span><span class="sxs-lookup"><span data-stu-id="92520-122">Then specify the implementation to the `TestCollectionOrdererAttribute`.</span></span>

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/XUnit.TestProject/ByDisplayName.cs":::

## <a name="order-by-custom-attribute"></a><span data-ttu-id="92520-123">Ordenar por atributo personalizado</span><span class="sxs-lookup"><span data-stu-id="92520-123">Order by custom attribute</span></span>

<span data-ttu-id="92520-124">Para solicitar testes de xUnit com atributos personalizados, primeiro você precisa de um atributo para confiar.</span><span class="sxs-lookup"><span data-stu-id="92520-124">To order xUnit tests with custom attributes, you first need an attribute to rely on.</span></span> <span data-ttu-id="92520-125">Defina uma das `TestPriorityAttribute` seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="92520-125">Define a `TestPriorityAttribute` as follows:</span></span>

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/XUnit.TestProject/Attributes/TestPriorityAttribute.cs":::

<span data-ttu-id="92520-126">Em seguida, considere a `PriorityOrderer` implementação da interface a seguir `ITestCaseOrderer` .</span><span class="sxs-lookup"><span data-stu-id="92520-126">Next, consider the following `PriorityOrderer` implementation of the `ITestCaseOrderer` interface.</span></span>

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/XUnit.TestProject/Orderers/PriorityOrderer.cs":::

<span data-ttu-id="92520-127">Em seguida, em uma classe de teste, defina o pedido de caso de teste com o `TestCaseOrdererAttribute` para `PriorityOrderer` .</span><span class="sxs-lookup"><span data-stu-id="92520-127">Then in a test class you set the test case order with the `TestCaseOrdererAttribute` to the `PriorityOrderer`.</span></span>

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/XUnit.TestProject/ByPriorityOrder.cs":::

:::zone-end
:::zone pivot="nunit"

## <a name="order-by-priority"></a><span data-ttu-id="92520-128">Ordenar por prioridade</span><span class="sxs-lookup"><span data-stu-id="92520-128">Order by priority</span></span>

<span data-ttu-id="92520-129">Para ordenar os testes explicitamente, o NUnit fornece um [`OrderAttribute`](https://github.com/nunit/docs/wiki/Order-Attribute) .</span><span class="sxs-lookup"><span data-stu-id="92520-129">To order tests explicitly, NUnit provides an [`OrderAttribute`](https://github.com/nunit/docs/wiki/Order-Attribute).</span></span> <span data-ttu-id="92520-130">Os testes com este atributo são iniciados antes dos testes sem.</span><span class="sxs-lookup"><span data-stu-id="92520-130">Tests with this attribute are started before tests without.</span></span> <span data-ttu-id="92520-131">O valor do pedido é usado para determinar a ordem de execução dos testes de unidade.</span><span class="sxs-lookup"><span data-stu-id="92520-131">The order value is used to determined the order to run the unit tests.</span></span>

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/NUnit.TestProject/ByOrder.cs":::

:::zone-end

## <a name="next-steps"></a><span data-ttu-id="92520-132">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="92520-132">Next Steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="92520-133">Cobertura de código de teste de unidade</span><span class="sxs-lookup"><span data-stu-id="92520-133">Unit test code coverage</span></span>](unit-testing-code-coverage.md)
