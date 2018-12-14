---
title: Executar testes de unidade seletivos – .NET Core
description: Como usar uma expressão de filtro para executar testes de unidade seletivos com o comando de teste do dotnet no .NET Core.
author: smadala
ms.author: mairaw
ms.date: 03/22/2017
ms.custom: seodec18
ms.openlocfilehash: 3c24fb8cc5024399ae523801373b0fd8eff85f45
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53151740"
---
# <a name="running-selective-unit-tests"></a><span data-ttu-id="e7e7c-103">Executar testes de unidade seletivos</span><span class="sxs-lookup"><span data-stu-id="e7e7c-103">Running selective unit tests</span></span>

<span data-ttu-id="e7e7c-104">Os exemplos a seguir usam `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="e7e7c-104">The following examples use `dotnet test`.</span></span> <span data-ttu-id="e7e7c-105">Se você estiver usando `vstest.console.exe`, substitua `--filter ` por `--testcasefilter:`.</span><span class="sxs-lookup"><span data-stu-id="e7e7c-105">If you're using `vstest.console.exe`, replace `--filter ` with `--testcasefilter:`.</span></span>

## <a name="mstest"></a><span data-ttu-id="e7e7c-106">MSTest</span><span class="sxs-lookup"><span data-stu-id="e7e7c-106">MSTest</span></span>

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

| <span data-ttu-id="e7e7c-107">Expressão</span><span class="sxs-lookup"><span data-stu-id="e7e7c-107">Expression</span></span> | <span data-ttu-id="e7e7c-108">Resultado</span><span class="sxs-lookup"><span data-stu-id="e7e7c-108">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="e7e7c-109">Executa testes cujo `FullyQualifiedName` contém `Method`.</span><span class="sxs-lookup"><span data-stu-id="e7e7c-109">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="e7e7c-110">Disponível em `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="e7e7c-110">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="e7e7c-111">Executa testes cujo nome contém `TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="e7e7c-111">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTest1` | <span data-ttu-id="e7e7c-112">Executa testes que estão na classe `MSTestNamespace.UnitTest1`.</span><span class="sxs-lookup"><span data-stu-id="e7e7c-112">Runs tests which are in class `MSTestNamespace.UnitTest1`.</span></span><br><span data-ttu-id="e7e7c-113">**Observação:** o valor `ClassName` deve ter um namespace, portanto `ClassName=UnitTest1` não funcionará.</span><span class="sxs-lookup"><span data-stu-id="e7e7c-113">**Note:** The `ClassName` value should have a namespace, so `ClassName=UnitTest1` won't work.</span></span> |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="e7e7c-114">Executa todos os testes, exceto `MSTestNamespace.UnitTest1.TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="e7e7c-114">Runs all tests except `MSTestNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="e7e7c-115">Executa testes que são anotados com `[TestCategory("CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="e7e7c-115">Runs tests which are annotated with `[TestCategory("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="e7e7c-116">Executa testes que são anotados com `[Priority(2)]`.</span><span class="sxs-lookup"><span data-stu-id="e7e7c-116">Runs tests which are annotated with `[Priority(2)]`.</span></span><br>

<span data-ttu-id="e7e7c-117">**Usar operadores condicionais | e &amp;**</span><span class="sxs-lookup"><span data-stu-id="e7e7c-117">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="e7e7c-118">Expressão</span><span class="sxs-lookup"><span data-stu-id="e7e7c-118">Expression</span></span> | <span data-ttu-id="e7e7c-119">Resultado</span><span class="sxs-lookup"><span data-stu-id="e7e7c-119">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="e7e7c-120">Executa testes que têm `UnitTest1` em `FullyQualifiedName` **, ou**  `TestCategory` é `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="e7e7c-120">Runs tests which have `UnitTest1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | <span data-ttu-id="e7e7c-121">Executa testes que têm `UnitTest1` em `FullyQualifiedName` **, e**  `TestCategory` é `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="e7e7c-121">Runs tests which have `UnitTest1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="e7e7c-122">Executa testes que têm `FullyQualifiedName` contendo `UnitTest1` **, e**  `TestCategory` é `CategoryA` **ou** `Priority` é 1.</span><span class="sxs-lookup"><span data-stu-id="e7e7c-122">Runs tests which have either `FullyQualifiedName` containing `UnitTest1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="xunit"></a><span data-ttu-id="e7e7c-123">xUnit</span><span class="sxs-lookup"><span data-stu-id="e7e7c-123">xUnit</span></span>

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

| <span data-ttu-id="e7e7c-124">Expressão</span><span class="sxs-lookup"><span data-stu-id="e7e7c-124">Expression</span></span> | <span data-ttu-id="e7e7c-125">Resultado</span><span class="sxs-lookup"><span data-stu-id="e7e7c-125">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="e7e7c-126">Executa somente um teste, `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="e7e7c-126">Runs only one test, `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="e7e7c-127">Executa todos os testes, exceto `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="e7e7c-127">Runs all tests except `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter DisplayName~TestClass1` | <span data-ttu-id="e7e7c-128">Executa testes cujo nome de exibição contém `TestClass1`.</span><span class="sxs-lookup"><span data-stu-id="e7e7c-128">Runs tests whose display name contains `TestClass1`.</span></span> |

<span data-ttu-id="e7e7c-129">No exemplo de código, as características definidas com chaves `Category` e `Priority` podem ser usadas para filtragem.</span><span class="sxs-lookup"><span data-stu-id="e7e7c-129">In the code example, the defined traits with keys `Category` and `Priority` can be used for filtering.</span></span>

| <span data-ttu-id="e7e7c-130">Expressão</span><span class="sxs-lookup"><span data-stu-id="e7e7c-130">Expression</span></span> | <span data-ttu-id="e7e7c-131">Resultado</span><span class="sxs-lookup"><span data-stu-id="e7e7c-131">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter XUnit` | <span data-ttu-id="e7e7c-132">Executa testes cujo `FullyQualifiedName` contém `XUnit`.</span><span class="sxs-lookup"><span data-stu-id="e7e7c-132">Runs tests whose `FullyQualifiedName` contains `XUnit`.</span></span>  <span data-ttu-id="e7e7c-133">Disponível em `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="e7e7c-133">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Category=CategoryA` | <span data-ttu-id="e7e7c-134">Executa testes que têm `[Trait("Category", "CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="e7e7c-134">Runs tests which have `[Trait("Category", "CategoryA")]`.</span></span> |

<span data-ttu-id="e7e7c-135">**Usar operadores condicionais | e &amp;**</span><span class="sxs-lookup"><span data-stu-id="e7e7c-135">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="e7e7c-136">Expressão</span><span class="sxs-lookup"><span data-stu-id="e7e7c-136">Expression</span></span> | <span data-ttu-id="e7e7c-137">Resultado</span><span class="sxs-lookup"><span data-stu-id="e7e7c-137">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=CategoryA"</code> | <span data-ttu-id="e7e7c-138">Executa testes que têm `TestClass1` em `FullyQualifiedName` **, ou**  `Category` é `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="e7e7c-138">Runs tests which has `TestClass1` in `FullyQualifiedName` **or** `Category` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=CategoryA"` | <span data-ttu-id="e7e7c-139">Executa testes que têm `TestClass1` em `FullyQualifiedName` **, e**  `Category` é `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="e7e7c-139">Runs tests which has `TestClass1` in `FullyQualifiedName` **and** `Category` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="e7e7c-140">Executa testes que têm `FullyQualifiedName` contendo `TestClass1` **, e**  `Category` é `CategoryA` **ou** `Priority` é 1.</span><span class="sxs-lookup"><span data-stu-id="e7e7c-140">Runs tests which have either `FullyQualifiedName` containing `TestClass1` **and** `Category` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="nunit"></a><span data-ttu-id="e7e7c-141">NUnit</span><span class="sxs-lookup"><span data-stu-id="e7e7c-141">NUnit</span></span>

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

| <span data-ttu-id="e7e7c-142">Expressão</span><span class="sxs-lookup"><span data-stu-id="e7e7c-142">Expression</span></span> | <span data-ttu-id="e7e7c-143">Resultado</span><span class="sxs-lookup"><span data-stu-id="e7e7c-143">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="e7e7c-144">Executa testes cujo `FullyQualifiedName` contém `Method`.</span><span class="sxs-lookup"><span data-stu-id="e7e7c-144">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="e7e7c-145">Disponível em `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="e7e7c-145">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="e7e7c-146">Executa testes cujo nome contém `TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="e7e7c-146">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter FullyQualifiedName~NUnitNamespace.UnitTest1` | <span data-ttu-id="e7e7c-147">Executa testes que estão na classe `NUnitNamespace.UnitTest1`.</span><span class="sxs-lookup"><span data-stu-id="e7e7c-147">Runs tests which are in class `NUnitNamespace.UnitTest1`.</span></span><br>
| `dotnet test --filter FullyQualifiedName!=NUnitNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="e7e7c-148">Executa todos os testes, exceto `NUnitNamespace.UnitTest1.TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="e7e7c-148">Runs all tests except `NUnitNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="e7e7c-149">Executa testes que são anotados com `[Category("CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="e7e7c-149">Runs tests which are annotated with `[Category("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="e7e7c-150">Executa testes que são anotados com `[Priority(2)]`.</span><span class="sxs-lookup"><span data-stu-id="e7e7c-150">Runs tests which are annotated with `[Priority(2)]`.</span></span><br>

<span data-ttu-id="e7e7c-151">**Usar operadores condicionais | e &amp;**</span><span class="sxs-lookup"><span data-stu-id="e7e7c-151">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="e7e7c-152">Expressão</span><span class="sxs-lookup"><span data-stu-id="e7e7c-152">Expression</span></span> | <span data-ttu-id="e7e7c-153">Resultado</span><span class="sxs-lookup"><span data-stu-id="e7e7c-153">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="e7e7c-154">Executa testes que têm `UnitTest1` em `FullyQualifiedName` **, ou**  `TestCategory` é `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="e7e7c-154">Runs tests which have `UnitTest1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | <span data-ttu-id="e7e7c-155">Executa testes que têm `UnitTest1` em `FullyQualifiedName` **, e**  `TestCategory` é `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="e7e7c-155">Runs tests which have `UnitTest1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="e7e7c-156">Executa testes que têm `FullyQualifiedName` contendo `UnitTest1` **, e**  `TestCategory` é `CategoryA` **ou** `Priority` é 1.</span><span class="sxs-lookup"><span data-stu-id="e7e7c-156">Runs tests which have either `FullyQualifiedName` containing `UnitTest1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |
