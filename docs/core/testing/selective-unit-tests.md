---
title: Executar testes de unidade seletivos
description: Mostra como usar uma expressão de filtro para executar testes de unidade seletivos com o comando de teste do dotnet.
author: smadala
ms.author: mairaw
ms.date: 03/22/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: 77ac7ab5a46150bd3654d50e6686087c804b8440
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="running-selective-unit-tests"></a><span data-ttu-id="8521a-103">Executar testes de unidade seletivos</span><span class="sxs-lookup"><span data-stu-id="8521a-103">Running selective unit tests</span></span>

<span data-ttu-id="8521a-104">Os exemplos a seguir usam `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="8521a-104">The following examples use `dotnet test`.</span></span> <span data-ttu-id="8521a-105">Se você estiver usando `vstest.console.exe`, substitua `--filter ` por `--testcasefilter:`.</span><span class="sxs-lookup"><span data-stu-id="8521a-105">If you're using `vstest.console.exe`, replace `--filter ` with `--testcasefilter:`.</span></span>

## <a name="mstest"></a><span data-ttu-id="8521a-106">MSTest</span><span class="sxs-lookup"><span data-stu-id="8521a-106">MSTest</span></span>

```csharp
namespace MSTestNamespace
{
    using Microsoft.VisualStudio.TestTools.UnitTesting;

    [TestClass]
    public class UnitTestClass1
    {
        [Priority(2)]
        [TestMethod]
        public void TestMethod1()
        {
        }

        [TestCategory("CategoryA")]
        [Priority(3)]
        [TestMethod]
        public void TestMethod2()
        {
        }
    }
}
```

| <span data-ttu-id="8521a-107">Expressão</span><span class="sxs-lookup"><span data-stu-id="8521a-107">Expression</span></span> | <span data-ttu-id="8521a-108">Resultado</span><span class="sxs-lookup"><span data-stu-id="8521a-108">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="8521a-109">Executa testes cujo `FullyQualifiedName` contém `Method`.</span><span class="sxs-lookup"><span data-stu-id="8521a-109">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="8521a-110">Disponível em `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="8521a-110">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="8521a-111">Executa testes cujo nome contém `TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="8521a-111">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTestClass1` | <span data-ttu-id="8521a-112">Executa testes que estão na classe `MSTestNamespace.UnitTestClass1`.</span><span class="sxs-lookup"><span data-stu-id="8521a-112">Runs tests which are in class `MSTestNamespace.UnitTestClass1`.</span></span><br><span data-ttu-id="8521a-113">**Observação:** o valor `ClassName` deve ter um namespace, portanto `ClassName=UnitTestClass1` não funcionará.</span><span class="sxs-lookup"><span data-stu-id="8521a-113">**Note:** The `ClassName` value should have a namespace, so `ClassName=UnitTestClass1` won't work.</span></span> |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTestClass1.TestMethod1` | <span data-ttu-id="8521a-114">Executa todos os testes, exceto `MSTestNamespace.UnitTestClass1.TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="8521a-114">Runs all tests except `MSTestNamespace.UnitTestClass1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="8521a-115">Executa testes que são anotados com `[TestCategory("CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="8521a-115">Runs tests which are annotated with `[TestCategory("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=3` | <span data-ttu-id="8521a-116">Executa testes que são anotados com `[Priority(3)]`.</span><span class="sxs-lookup"><span data-stu-id="8521a-116">Runs tests which are annotated with `[Priority(3)]`.</span></span><br><span data-ttu-id="8521a-117">**Observação:** `Priority~3` é um valor inválido, pois não é uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="8521a-117">**Note:** `Priority~3` is an invalid value, as it isn't a string.</span></span> |

<span data-ttu-id="8521a-118">**Usar operadores condicionais | e &amp;**</span><span class="sxs-lookup"><span data-stu-id="8521a-118">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="8521a-119">Expressão</span><span class="sxs-lookup"><span data-stu-id="8521a-119">Expression</span></span> | <span data-ttu-id="8521a-120">Resultado</span><span class="sxs-lookup"><span data-stu-id="8521a-120">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTestClass1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="8521a-121">Executa testes que têm `UnitTestClass1` em `FullyQualifiedName` **, ou**  `TestCategory` é `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="8521a-121">Runs tests which have `UnitTestClass1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTestClass1&TestCategory=CategoryA"` | <span data-ttu-id="8521a-122">Executa testes que têm `UnitTestClass1` em `FullyQualifiedName` **, e**  `TestCategory` é `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="8521a-122">Runs tests which have `UnitTestClass1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTestClass1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="8521a-123">Executa testes que têm `FullyQualifiedName` contendo `UnitTestClass1` **, e**  `TestCategory` é `CategoryA` **ou** `Priority` é 1.</span><span class="sxs-lookup"><span data-stu-id="8521a-123">Runs tests which have either `FullyQualifiedName` containing `UnitTestClass1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="xunit"></a><span data-ttu-id="8521a-124">xUnit</span><span class="sxs-lookup"><span data-stu-id="8521a-124">xUnit</span></span>

```csharp
namespace XUnitNamespace
{
    public class TestClass1
    {
        [Trait("Category", "bvt")]
        [Trait("Priority", "1")]
        [Fact]
        public void foo()
        {
        }

        [Trait("Category", "Nightly")]
        [Trait("Priority", "2")]
        [Fact]
        public void bar()
        {
        }
    }
}
```

| <span data-ttu-id="8521a-125">Expressão</span><span class="sxs-lookup"><span data-stu-id="8521a-125">Expression</span></span> | <span data-ttu-id="8521a-126">Resultado</span><span class="sxs-lookup"><span data-stu-id="8521a-126">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="8521a-127">Executa somente um teste, `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="8521a-127">Runs only one test, `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="8521a-128">Executa todos os testes, exceto `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="8521a-128">Runs all tests except `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter DisplayName~TestClass1` | <span data-ttu-id="8521a-129">Executa testes cujo nome de exibição contém `TestClass1`.</span><span class="sxs-lookup"><span data-stu-id="8521a-129">Runs tests whose display name contains `TestClass1`.</span></span> |

<span data-ttu-id="8521a-130">No exemplo de código, as características definidas com chaves `Category` e `Priority` podem ser usadas para filtragem.</span><span class="sxs-lookup"><span data-stu-id="8521a-130">In the code example, the defined traits with keys `Category` and `Priority` can be used for filtering.</span></span>

| <span data-ttu-id="8521a-131">Expressão</span><span class="sxs-lookup"><span data-stu-id="8521a-131">Expression</span></span> | <span data-ttu-id="8521a-132">Resultado</span><span class="sxs-lookup"><span data-stu-id="8521a-132">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter XUnit` | <span data-ttu-id="8521a-133">Executa testes cujo `FullyQualifiedName` contém `XUnit`.</span><span class="sxs-lookup"><span data-stu-id="8521a-133">Runs tests whose `FullyQualifiedName` contains `XUnit`.</span></span>  <span data-ttu-id="8521a-134">Disponível em `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="8521a-134">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Category=bvt` | <span data-ttu-id="8521a-135">Executa testes que têm `[Trait("Category", "bvt")]`.</span><span class="sxs-lookup"><span data-stu-id="8521a-135">Runs tests which have `[Trait("Category", "bvt")]`.</span></span> |

<span data-ttu-id="8521a-136">**Usar operadores condicionais | e &amp;**</span><span class="sxs-lookup"><span data-stu-id="8521a-136">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="8521a-137">Expressão</span><span class="sxs-lookup"><span data-stu-id="8521a-137">Expression</span></span> | <span data-ttu-id="8521a-138">Resultado</span><span class="sxs-lookup"><span data-stu-id="8521a-138">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=Nightly"</code> | <span data-ttu-id="8521a-139">Executa testes que têm `TestClass1` em `FullyQualifiedName` **, ou**  `Category` é `Nightly`.</span><span class="sxs-lookup"><span data-stu-id="8521a-139">Runs tests which has `TestClass1` in `FullyQualifiedName` **or** `Category` is `Nightly`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=Nightly"` | <span data-ttu-id="8521a-140">Executa testes que têm `TestClass1` em `FullyQualifiedName` **, e**  `Category` é `Nightly`.</span><span class="sxs-lookup"><span data-stu-id="8521a-140">Runs tests which has `TestClass1` in `FullyQualifiedName` **and** `Category` is `Nightly`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=Nightly)&#124;Priority=1"</code> | <span data-ttu-id="8521a-141">Executa testes que têm `FullyQualifiedName` contendo `TestClass1` **, e**  `Category` é `CategoryA` **ou** `Priority` é 1.</span><span class="sxs-lookup"><span data-stu-id="8521a-141">Runs tests which have either `FullyQualifiedName` containing `TestClass1` **and** `Category` is `CategoryA` **or** `Priority` is 1.</span></span> |
