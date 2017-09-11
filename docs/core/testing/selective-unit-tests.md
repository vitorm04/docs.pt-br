---
title: Executar testes de unidade seletivos
description: "Mostra como usar uma expressão de filtro para executar testes de unidade seletivos com o comando de teste do dotnet."
keywords: .NET, .NET Core, teste de unidade, teste seletivo
author: smadala
ms.author: mairaw
ms.date: 03/22/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 13d01272-bbf8-456c-a97a-560001d1a7f2
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: af832d04d2cba530a93710a90701ab119a66deef
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---

# <a name="running-selective-unit-tests"></a><span data-ttu-id="8a350-104">Executar testes de unidade seletivos</span><span class="sxs-lookup"><span data-stu-id="8a350-104">Running selective unit tests</span></span>

<span data-ttu-id="8a350-105">Os exemplos a seguir usam `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="8a350-105">The following examples use `dotnet test`.</span></span> <span data-ttu-id="8a350-106">Se você estiver usando `vstest.console.exe`, substitua `--filter ` por `--testcasefilter:`.</span><span class="sxs-lookup"><span data-stu-id="8a350-106">If you're using `vstest.console.exe`, replace `--filter ` with `--testcasefilter:`.</span></span>

## <a name="mstest"></a><span data-ttu-id="8a350-107">MSTest</span><span class="sxs-lookup"><span data-stu-id="8a350-107">MSTest</span></span>

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

| <span data-ttu-id="8a350-108">Expressão</span><span class="sxs-lookup"><span data-stu-id="8a350-108">Expression</span></span> | <span data-ttu-id="8a350-109">Resultado</span><span class="sxs-lookup"><span data-stu-id="8a350-109">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="8a350-110">Executa testes cujo `FullyQualifiedName` contém `Method`.</span><span class="sxs-lookup"><span data-stu-id="8a350-110">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="8a350-111">Disponível em `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="8a350-111">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="8a350-112">Executa testes cujo nome contém `TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="8a350-112">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTestClass1` | <span data-ttu-id="8a350-113">Executa testes que estão na classe `MSTestNamespace.UnitTestClass1`.</span><span class="sxs-lookup"><span data-stu-id="8a350-113">Runs tests which are in class `MSTestNamespace.UnitTestClass1`.</span></span><br><span data-ttu-id="8a350-114">**Observação:** o valor `ClassName` deve ter um namespace, portanto `ClassName=UnitTestClass1` não funcionará.</span><span class="sxs-lookup"><span data-stu-id="8a350-114">**Note:** The `ClassName` value should have a namespace, so `ClassName=UnitTestClass1` won't work.</span></span> |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTestClass1.TestMethod1` | <span data-ttu-id="8a350-115">Executa todos os testes, exceto `MSTestNamespace.UnitTestClass1.TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="8a350-115">Runs all tests except `MSTestNamespace.UnitTestClass1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="8a350-116">Executa testes que são anotados com `[TestCategory("CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="8a350-116">Runs tests which are annotated with `[TestCategory("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=3` | <span data-ttu-id="8a350-117">Executa testes que são anotados com `[Priority(3)]`.</span><span class="sxs-lookup"><span data-stu-id="8a350-117">Runs tests which are annotated with `[Priority(3)]`.</span></span><br><span data-ttu-id="8a350-118">**Observação:** `Priority~3` é um valor inválido, pois não é uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="8a350-118">**Note:** `Priority~3` is an invalid value, as it isn't a string.</span></span> |

<span data-ttu-id="8a350-119">**Usar operadores condicionais | e &amp;**</span><span class="sxs-lookup"><span data-stu-id="8a350-119">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="8a350-120">Expressão</span><span class="sxs-lookup"><span data-stu-id="8a350-120">Expression</span></span> | <span data-ttu-id="8a350-121">Resultado</span><span class="sxs-lookup"><span data-stu-id="8a350-121">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTestClass1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="8a350-122">Executa testes que têm `UnitTestClass1` em `FullyQualifiedName` **, ou**  `TestCategory` é `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="8a350-122">Runs tests which have `UnitTestClass1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTestClass1&TestCategory=CategoryA"` | <span data-ttu-id="8a350-123">Executa testes que têm `UnitTestClass1` em `FullyQualifiedName` **, e**  `TestCategory` é `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="8a350-123">Runs tests which have `UnitTestClass1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTestClass1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="8a350-124">Executa testes que têm `FullyQualifiedName` contendo `UnitTestClass1` **, e**  `TestCategory` é `CategoryA`  **ou**  `Priority` é 1.</span><span class="sxs-lookup"><span data-stu-id="8a350-124">Runs tests which have either `FullyQualifiedName` containing `UnitTestClass1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="xunit"></a><span data-ttu-id="8a350-125">xUnit</span><span class="sxs-lookup"><span data-stu-id="8a350-125">xUnit</span></span>

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

| <span data-ttu-id="8a350-126">Expressão</span><span class="sxs-lookup"><span data-stu-id="8a350-126">Expression</span></span> | <span data-ttu-id="8a350-127">Resultado</span><span class="sxs-lookup"><span data-stu-id="8a350-127">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="8a350-128">Executa somente um teste, `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="8a350-128">Runs only one test, `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="8a350-129">Executa todos os testes, exceto `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="8a350-129">Runs all tests except `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter DisplayName~TestClass1` | <span data-ttu-id="8a350-130">Executa testes cujo nome de exibição contém `TestClass1`.</span><span class="sxs-lookup"><span data-stu-id="8a350-130">Runs tests whose display name contains `TestClass1`.</span></span> |

<span data-ttu-id="8a350-131">No exemplo de código, as características definidas com chaves `Category` e `Priority` podem ser usadas para filtragem.</span><span class="sxs-lookup"><span data-stu-id="8a350-131">In the code example, the defined traits with keys `Category` and `Priority` can be used for filtering.</span></span>

| <span data-ttu-id="8a350-132">Expressão</span><span class="sxs-lookup"><span data-stu-id="8a350-132">Expression</span></span> | <span data-ttu-id="8a350-133">Resultado</span><span class="sxs-lookup"><span data-stu-id="8a350-133">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter XUnit` | <span data-ttu-id="8a350-134">Executa testes cujo `FullyQualifiedName` contém `XUnit`.</span><span class="sxs-lookup"><span data-stu-id="8a350-134">Runs tests whose `FullyQualifiedName` contains `XUnit`.</span></span>  <span data-ttu-id="8a350-135">Disponível em `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="8a350-135">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Category=bvt` | <span data-ttu-id="8a350-136">Executa testes que têm `[Trait("Category", "bvt")]`.</span><span class="sxs-lookup"><span data-stu-id="8a350-136">Runs tests which have `[Trait("Category", "bvt")]`.</span></span> |

<span data-ttu-id="8a350-137">**Usar operadores condicionais | e &amp;**</span><span class="sxs-lookup"><span data-stu-id="8a350-137">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="8a350-138">Expressão</span><span class="sxs-lookup"><span data-stu-id="8a350-138">Expression</span></span> | <span data-ttu-id="8a350-139">Resultado</span><span class="sxs-lookup"><span data-stu-id="8a350-139">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=Nightly"</code> | <span data-ttu-id="8a350-140">Executa testes que têm `TestClass1` em `FullyQualifiedName` **, ou**  `Category` é `Nightly`.</span><span class="sxs-lookup"><span data-stu-id="8a350-140">Runs tests which has `TestClass1` in `FullyQualifiedName` **or** `Category` is `Nightly`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=Nightly"` | <span data-ttu-id="8a350-141">Executa testes que têm `TestClass1` em `FullyQualifiedName` **, e**  `Category` é `Nightly`.</span><span class="sxs-lookup"><span data-stu-id="8a350-141">Runs tests which has `TestClass1` in `FullyQualifiedName` **and** `Category` is `Nightly`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=Nightly)&#124;Priority=1"</code> | <span data-ttu-id="8a350-142">Executa testes que têm `FullyQualifiedName` contendo `TestClass1` **, e**  `Category` é `CategoryA`  **ou**  `Priority` é 1.</span><span class="sxs-lookup"><span data-stu-id="8a350-142">Runs tests which have either `FullyQualifiedName` containing `TestClass1` **and** `Category` is `CategoryA` **or** `Priority` is 1.</span></span> |

