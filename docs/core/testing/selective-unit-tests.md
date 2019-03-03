---
title: Executar testes de unidade seletivos
description: Como usar uma expressão de filtro para executar testes de unidade seletivos com o comando de teste do dotnet no .NET Core.
author: smadala
ms.date: 03/22/2017
ms.custom: seodec18
ms.openlocfilehash: 6160a8b9184d031fcc06356b5b489ee24b765e84
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57201411"
---
# <a name="running-selective-unit-tests"></a><span data-ttu-id="af5a6-103">Executar testes de unidade seletivos</span><span class="sxs-lookup"><span data-stu-id="af5a6-103">Running selective unit tests</span></span>

<span data-ttu-id="af5a6-104">Com o comando `dotnet test` no .NET Core, use uma expressão de filtro para executar testes seletivos.</span><span class="sxs-lookup"><span data-stu-id="af5a6-104">With the `dotnet test` command in .NET Core, you can use a filter expression to run selective tests.</span></span> <span data-ttu-id="af5a6-105">Este artigo demonstra como filtrar os testes que são executados.</span><span class="sxs-lookup"><span data-stu-id="af5a6-105">This article demonstrates how to filter which test are run.</span></span> <span data-ttu-id="af5a6-106">Os exemplos a seguir usam `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="af5a6-106">The following examples use `dotnet test`.</span></span> <span data-ttu-id="af5a6-107">Se você estiver usando `vstest.console.exe`, substitua `--filter` por `--testcasefilter:`.</span><span class="sxs-lookup"><span data-stu-id="af5a6-107">If you're using `vstest.console.exe`, replace `--filter` with `--testcasefilter:`.</span></span>

## <a name="mstest"></a><span data-ttu-id="af5a6-108">MSTest</span><span class="sxs-lookup"><span data-stu-id="af5a6-108">MSTest</span></span>

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

| <span data-ttu-id="af5a6-109">Expressão</span><span class="sxs-lookup"><span data-stu-id="af5a6-109">Expression</span></span> | <span data-ttu-id="af5a6-110">Resultado</span><span class="sxs-lookup"><span data-stu-id="af5a6-110">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="af5a6-111">Executa testes cujo `FullyQualifiedName` contém `Method`.</span><span class="sxs-lookup"><span data-stu-id="af5a6-111">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="af5a6-112">Disponível em `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="af5a6-112">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="af5a6-113">Executa testes cujo nome contém `TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="af5a6-113">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTest1` | <span data-ttu-id="af5a6-114">Executa testes que estão na classe `MSTestNamespace.UnitTest1`.</span><span class="sxs-lookup"><span data-stu-id="af5a6-114">Runs tests which are in class `MSTestNamespace.UnitTest1`.</span></span><br><span data-ttu-id="af5a6-115">**Observação:** O valor `ClassName` deve ter um namespace; portanto, `ClassName=UnitTest1` não funcionará.</span><span class="sxs-lookup"><span data-stu-id="af5a6-115">**Note:** The `ClassName` value should have a namespace, so `ClassName=UnitTest1` won't work.</span></span> |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="af5a6-116">Executa todos os testes, exceto `MSTestNamespace.UnitTest1.TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="af5a6-116">Runs all tests except `MSTestNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="af5a6-117">Executa testes que são anotados com `[TestCategory("CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="af5a6-117">Runs tests which are annotated with `[TestCategory("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="af5a6-118">Executa testes que são anotados com `[Priority(2)]`.</span><span class="sxs-lookup"><span data-stu-id="af5a6-118">Runs tests which are annotated with `[Priority(2)]`.</span></span><br>

<span data-ttu-id="af5a6-119">**Usar operadores condicionais | e &amp;**</span><span class="sxs-lookup"><span data-stu-id="af5a6-119">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="af5a6-120">Expressão</span><span class="sxs-lookup"><span data-stu-id="af5a6-120">Expression</span></span> | <span data-ttu-id="af5a6-121">Resultado</span><span class="sxs-lookup"><span data-stu-id="af5a6-121">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="af5a6-122">Executa testes que têm `UnitTest1` em `FullyQualifiedName` **, ou**  `TestCategory` é `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="af5a6-122">Runs tests which have `UnitTest1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | <span data-ttu-id="af5a6-123">Executa testes que têm `UnitTest1` em `FullyQualifiedName` **, e**  `TestCategory` é `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="af5a6-123">Runs tests which have `UnitTest1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="af5a6-124">Executa testes que têm `FullyQualifiedName` contendo `UnitTest1` **, e**  `TestCategory` é `CategoryA` **ou** `Priority` é 1.</span><span class="sxs-lookup"><span data-stu-id="af5a6-124">Runs tests which have either `FullyQualifiedName` containing `UnitTest1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="xunit"></a><span data-ttu-id="af5a6-125">xUnit</span><span class="sxs-lookup"><span data-stu-id="af5a6-125">xUnit</span></span>

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

| <span data-ttu-id="af5a6-126">Expressão</span><span class="sxs-lookup"><span data-stu-id="af5a6-126">Expression</span></span> | <span data-ttu-id="af5a6-127">Resultado</span><span class="sxs-lookup"><span data-stu-id="af5a6-127">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="af5a6-128">Executa somente um teste, `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="af5a6-128">Runs only one test, `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="af5a6-129">Executa todos os testes, exceto `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="af5a6-129">Runs all tests except `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter DisplayName~TestClass1` | <span data-ttu-id="af5a6-130">Executa testes cujo nome de exibição contém `TestClass1`.</span><span class="sxs-lookup"><span data-stu-id="af5a6-130">Runs tests whose display name contains `TestClass1`.</span></span> |

<span data-ttu-id="af5a6-131">No exemplo de código, as características definidas com chaves `Category` e `Priority` podem ser usadas para filtragem.</span><span class="sxs-lookup"><span data-stu-id="af5a6-131">In the code example, the defined traits with keys `Category` and `Priority` can be used for filtering.</span></span>

| <span data-ttu-id="af5a6-132">Expressão</span><span class="sxs-lookup"><span data-stu-id="af5a6-132">Expression</span></span> | <span data-ttu-id="af5a6-133">Resultado</span><span class="sxs-lookup"><span data-stu-id="af5a6-133">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter XUnit` | <span data-ttu-id="af5a6-134">Executa testes cujo `FullyQualifiedName` contém `XUnit`.</span><span class="sxs-lookup"><span data-stu-id="af5a6-134">Runs tests whose `FullyQualifiedName` contains `XUnit`.</span></span>  <span data-ttu-id="af5a6-135">Disponível em `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="af5a6-135">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Category=CategoryA` | <span data-ttu-id="af5a6-136">Executa testes que têm `[Trait("Category", "CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="af5a6-136">Runs tests which have `[Trait("Category", "CategoryA")]`.</span></span> |

<span data-ttu-id="af5a6-137">**Usar operadores condicionais | e &amp;**</span><span class="sxs-lookup"><span data-stu-id="af5a6-137">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="af5a6-138">Expressão</span><span class="sxs-lookup"><span data-stu-id="af5a6-138">Expression</span></span> | <span data-ttu-id="af5a6-139">Resultado</span><span class="sxs-lookup"><span data-stu-id="af5a6-139">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=CategoryA"</code> | <span data-ttu-id="af5a6-140">Executa testes que têm `TestClass1` em `FullyQualifiedName` **, ou**  `Category` é `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="af5a6-140">Runs tests which has `TestClass1` in `FullyQualifiedName` **or** `Category` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=CategoryA"` | <span data-ttu-id="af5a6-141">Executa testes que têm `TestClass1` em `FullyQualifiedName` **, e**  `Category` é `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="af5a6-141">Runs tests which has `TestClass1` in `FullyQualifiedName` **and** `Category` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="af5a6-142">Executa testes que têm `FullyQualifiedName` contendo `TestClass1` **, e**  `Category` é `CategoryA` **ou** `Priority` é 1.</span><span class="sxs-lookup"><span data-stu-id="af5a6-142">Runs tests which have either `FullyQualifiedName` containing `TestClass1` **and** `Category` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="nunit"></a><span data-ttu-id="af5a6-143">NUnit</span><span class="sxs-lookup"><span data-stu-id="af5a6-143">NUnit</span></span>

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

| <span data-ttu-id="af5a6-144">Expressão</span><span class="sxs-lookup"><span data-stu-id="af5a6-144">Expression</span></span> | <span data-ttu-id="af5a6-145">Resultado</span><span class="sxs-lookup"><span data-stu-id="af5a6-145">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="af5a6-146">Executa testes cujo `FullyQualifiedName` contém `Method`.</span><span class="sxs-lookup"><span data-stu-id="af5a6-146">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="af5a6-147">Disponível em `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="af5a6-147">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="af5a6-148">Executa testes cujo nome contém `TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="af5a6-148">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter FullyQualifiedName~NUnitNamespace.UnitTest1` | <span data-ttu-id="af5a6-149">Executa testes que estão na classe `NUnitNamespace.UnitTest1`.</span><span class="sxs-lookup"><span data-stu-id="af5a6-149">Runs tests which are in class `NUnitNamespace.UnitTest1`.</span></span><br>
| `dotnet test --filter FullyQualifiedName!=NUnitNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="af5a6-150">Executa todos os testes, exceto `NUnitNamespace.UnitTest1.TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="af5a6-150">Runs all tests except `NUnitNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="af5a6-151">Executa testes que são anotados com `[Category("CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="af5a6-151">Runs tests which are annotated with `[Category("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="af5a6-152">Executa testes que são anotados com `[Priority(2)]`.</span><span class="sxs-lookup"><span data-stu-id="af5a6-152">Runs tests which are annotated with `[Priority(2)]`.</span></span><br>

<span data-ttu-id="af5a6-153">**Usar operadores condicionais | e &amp;**</span><span class="sxs-lookup"><span data-stu-id="af5a6-153">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="af5a6-154">Expressão</span><span class="sxs-lookup"><span data-stu-id="af5a6-154">Expression</span></span> | <span data-ttu-id="af5a6-155">Resultado</span><span class="sxs-lookup"><span data-stu-id="af5a6-155">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="af5a6-156">Executa testes que têm `UnitTest1` em `FullyQualifiedName` **, ou**  `TestCategory` é `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="af5a6-156">Runs tests which have `UnitTest1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | <span data-ttu-id="af5a6-157">Executa testes que têm `UnitTest1` em `FullyQualifiedName` **, e**  `TestCategory` é `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="af5a6-157">Runs tests which have `UnitTest1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="af5a6-158">Executa testes que têm `FullyQualifiedName` contendo `UnitTest1` **, e**  `TestCategory` é `CategoryA` **ou** `Priority` é 1.</span><span class="sxs-lookup"><span data-stu-id="af5a6-158">Runs tests which have either `FullyQualifiedName` containing `UnitTest1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |
