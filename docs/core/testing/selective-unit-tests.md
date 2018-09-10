---
title: Executar testes de unidade seletivos
description: Mostra como usar uma expressão de filtro para executar testes de unidade seletivos com o comando de teste do dotnet.
author: smadala
ms.author: mairaw
ms.date: 03/22/2017
ms.openlocfilehash: 428e31014f5d8d487deb7c4b4317ebcef13c294d
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43517214"
---
# <a name="running-selective-unit-tests"></a><span data-ttu-id="283e5-103">Executar testes de unidade seletivos</span><span class="sxs-lookup"><span data-stu-id="283e5-103">Running selective unit tests</span></span>

<span data-ttu-id="283e5-104">Os exemplos a seguir usam `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="283e5-104">The following examples use `dotnet test`.</span></span> <span data-ttu-id="283e5-105">Se você estiver usando `vstest.console.exe`, substitua `--filter ` por `--testcasefilter:`.</span><span class="sxs-lookup"><span data-stu-id="283e5-105">If you're using `vstest.console.exe`, replace `--filter ` with `--testcasefilter:`.</span></span>

## <a name="mstest"></a><span data-ttu-id="283e5-106">MSTest</span><span class="sxs-lookup"><span data-stu-id="283e5-106">MSTest</span></span>

```csharp
using Microsoft.VisualStudio.TestTools.UnitTesting;

namespace MSTestNamespace
{
    [TestClass]
    public class UnitTest1
    {
        [TestCategory("CategoryA")]
        [Priority(1)]
        [TestMethod]
        public void TestMethod1()
        {
        }

        [Priority(2)]
        [TestMethod]
        public void TestMethod2()
        {
        }
    }
}
```

| <span data-ttu-id="283e5-107">Expressão</span><span class="sxs-lookup"><span data-stu-id="283e5-107">Expression</span></span> | <span data-ttu-id="283e5-108">Resultado</span><span class="sxs-lookup"><span data-stu-id="283e5-108">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="283e5-109">Executa testes cujo `FullyQualifiedName` contém `Method`.</span><span class="sxs-lookup"><span data-stu-id="283e5-109">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="283e5-110">Disponível em `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="283e5-110">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="283e5-111">Executa testes cujo nome contém `TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="283e5-111">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTest1` | <span data-ttu-id="283e5-112">Executa testes que estão na classe `MSTestNamespace.UnitTest1`.</span><span class="sxs-lookup"><span data-stu-id="283e5-112">Runs tests which are in class `MSTestNamespace.UnitTest1`.</span></span><br><span data-ttu-id="283e5-113">**Observação:** o valor `ClassName` deve ter um namespace, portanto `ClassName=UnitTest1` não funcionará.</span><span class="sxs-lookup"><span data-stu-id="283e5-113">**Note:** The `ClassName` value should have a namespace, so `ClassName=UnitTest1` won't work.</span></span> |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="283e5-114">Executa todos os testes, exceto `MSTestNamespace.UnitTest1.TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="283e5-114">Runs all tests except `MSTestNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="283e5-115">Executa testes que são anotados com `[TestCategory("CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="283e5-115">Runs tests which are annotated with `[TestCategory("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="283e5-116">Executa testes que são anotados com `[Priority(2)]`.</span><span class="sxs-lookup"><span data-stu-id="283e5-116">Runs tests which are annotated with `[Priority(2)]`.</span></span><br>

<span data-ttu-id="283e5-117">**Usar operadores condicionais | e &amp;**</span><span class="sxs-lookup"><span data-stu-id="283e5-117">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="283e5-118">Expressão</span><span class="sxs-lookup"><span data-stu-id="283e5-118">Expression</span></span> | <span data-ttu-id="283e5-119">Resultado</span><span class="sxs-lookup"><span data-stu-id="283e5-119">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="283e5-120">Executa testes que têm `UnitTest1` em `FullyQualifiedName` **, ou**  `TestCategory` é `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="283e5-120">Runs tests which have `UnitTest1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | <span data-ttu-id="283e5-121">Executa testes que têm `UnitTest1` em `FullyQualifiedName` **, e**  `TestCategory` é `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="283e5-121">Runs tests which have `UnitTest1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="283e5-122">Executa testes que têm `FullyQualifiedName` contendo `UnitTest1` **, e**  `TestCategory` é `CategoryA` **ou** `Priority` é 1.</span><span class="sxs-lookup"><span data-stu-id="283e5-122">Runs tests which have either `FullyQualifiedName` containing `UnitTest1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="xunit"></a><span data-ttu-id="283e5-123">xUnit</span><span class="sxs-lookup"><span data-stu-id="283e5-123">xUnit</span></span>

```csharp
using Xunit;

namespace XUnitNamespace
{
    public class TestClass1
    {
        [Trait("Category", "CategoryA")]
        [Trait("Priority", "1")]
        [Fact]
        public void Test1()
        {
        }

        [Trait("Priority", "2")]
        [Fact]
        public void Test2()
        {
        }
    }
}
```

| <span data-ttu-id="283e5-124">Expressão</span><span class="sxs-lookup"><span data-stu-id="283e5-124">Expression</span></span> | <span data-ttu-id="283e5-125">Resultado</span><span class="sxs-lookup"><span data-stu-id="283e5-125">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="283e5-126">Executa somente um teste, `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="283e5-126">Runs only one test, `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="283e5-127">Executa todos os testes, exceto `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="283e5-127">Runs all tests except `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter DisplayName~TestClass1` | <span data-ttu-id="283e5-128">Executa testes cujo nome de exibição contém `TestClass1`.</span><span class="sxs-lookup"><span data-stu-id="283e5-128">Runs tests whose display name contains `TestClass1`.</span></span> |

<span data-ttu-id="283e5-129">No exemplo de código, as características definidas com chaves `Category` e `Priority` podem ser usadas para filtragem.</span><span class="sxs-lookup"><span data-stu-id="283e5-129">In the code example, the defined traits with keys `Category` and `Priority` can be used for filtering.</span></span>

| <span data-ttu-id="283e5-130">Expressão</span><span class="sxs-lookup"><span data-stu-id="283e5-130">Expression</span></span> | <span data-ttu-id="283e5-131">Resultado</span><span class="sxs-lookup"><span data-stu-id="283e5-131">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter XUnit` | <span data-ttu-id="283e5-132">Executa testes cujo `FullyQualifiedName` contém `XUnit`.</span><span class="sxs-lookup"><span data-stu-id="283e5-132">Runs tests whose `FullyQualifiedName` contains `XUnit`.</span></span>  <span data-ttu-id="283e5-133">Disponível em `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="283e5-133">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Category=CategoryA` | <span data-ttu-id="283e5-134">Executa testes que têm `[Trait("Category", "CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="283e5-134">Runs tests which have `[Trait("Category", "CategoryA")]`.</span></span> |

<span data-ttu-id="283e5-135">**Usar operadores condicionais | e &amp;**</span><span class="sxs-lookup"><span data-stu-id="283e5-135">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="283e5-136">Expressão</span><span class="sxs-lookup"><span data-stu-id="283e5-136">Expression</span></span> | <span data-ttu-id="283e5-137">Resultado</span><span class="sxs-lookup"><span data-stu-id="283e5-137">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=CategoryA"</code> | <span data-ttu-id="283e5-138">Executa testes que têm `TestClass1` em `FullyQualifiedName` **, ou**  `Category` é `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="283e5-138">Runs tests which has `TestClass1` in `FullyQualifiedName` **or** `Category` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=CategoryA"` | <span data-ttu-id="283e5-139">Executa testes que têm `TestClass1` em `FullyQualifiedName` **, e**  `Category` é `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="283e5-139">Runs tests which has `TestClass1` in `FullyQualifiedName` **and** `Category` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="283e5-140">Executa testes que têm `FullyQualifiedName` contendo `TestClass1` **, e**  `Category` é `CategoryA` **ou** `Priority` é 1.</span><span class="sxs-lookup"><span data-stu-id="283e5-140">Runs tests which have either `FullyQualifiedName` containing `TestClass1` **and** `Category` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="nunit"></a><span data-ttu-id="283e5-141">NUnit</span><span class="sxs-lookup"><span data-stu-id="283e5-141">NUnit</span></span>

```csharp
using NUnit.Framework;

namespace NUnitNamespace
{
    public class UnitTest1
    {
        [Category("CategoryA")]
        [Property("Priority", 1)]
        [Test]
        public void TestMethod1()
        {
        }

        [Property("Priority", 2)]
        [Test]
        public void TestMethod2()
        {
        }
    }
}
```

| <span data-ttu-id="283e5-142">Expressão</span><span class="sxs-lookup"><span data-stu-id="283e5-142">Expression</span></span> | <span data-ttu-id="283e5-143">Resultado</span><span class="sxs-lookup"><span data-stu-id="283e5-143">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="283e5-144">Executa testes cujo `FullyQualifiedName` contém `Method`.</span><span class="sxs-lookup"><span data-stu-id="283e5-144">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="283e5-145">Disponível em `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="283e5-145">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="283e5-146">Executa testes cujo nome contém `TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="283e5-146">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter FullyQualifiedName~NUnitNamespace.UnitTest1` | <span data-ttu-id="283e5-147">Executa testes que estão na classe `NUnitNamespace.UnitTest1`.</span><span class="sxs-lookup"><span data-stu-id="283e5-147">Runs tests which are in class `NUnitNamespace.UnitTest1`.</span></span><br>
| `dotnet test --filter FullyQualifiedName!=NUnitNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="283e5-148">Executa todos os testes, exceto `NUnitNamespace.UnitTest1.TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="283e5-148">Runs all tests except `NUnitNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="283e5-149">Executa testes que são anotados com `[Category("CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="283e5-149">Runs tests which are annotated with `[Category("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="283e5-150">Executa testes que são anotados com `[Priority(2)]`.</span><span class="sxs-lookup"><span data-stu-id="283e5-150">Runs tests which are annotated with `[Priority(2)]`.</span></span><br>

<span data-ttu-id="283e5-151">**Usar operadores condicionais | e &amp;**</span><span class="sxs-lookup"><span data-stu-id="283e5-151">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="283e5-152">Expressão</span><span class="sxs-lookup"><span data-stu-id="283e5-152">Expression</span></span> | <span data-ttu-id="283e5-153">Resultado</span><span class="sxs-lookup"><span data-stu-id="283e5-153">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="283e5-154">Executa testes que têm `UnitTest1` em `FullyQualifiedName` **, ou**  `TestCategory` é `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="283e5-154">Runs tests which have `UnitTest1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | <span data-ttu-id="283e5-155">Executa testes que têm `UnitTest1` em `FullyQualifiedName` **, e**  `TestCategory` é `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="283e5-155">Runs tests which have `UnitTest1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="283e5-156">Executa testes que têm `FullyQualifiedName` contendo `UnitTest1` **, e**  `TestCategory` é `CategoryA` **ou** `Priority` é 1.</span><span class="sxs-lookup"><span data-stu-id="283e5-156">Runs tests which have either `FullyQualifiedName` containing `UnitTest1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |
