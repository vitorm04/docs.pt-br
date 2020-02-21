---
title: Executar testes de unidade seletivos
description: Como usar uma expressão de filtro para executar testes de unidade seletivos com o comando de teste do dotnet no .NET Core.
author: smadala
ms.date: 03/22/2017
ms.openlocfilehash: b9156300587215e68c01c609e298dbc1a2c53d11
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543502"
---
# <a name="running-selective-unit-tests"></a><span data-ttu-id="340c8-103">Executar testes de unidade seletivos</span><span class="sxs-lookup"><span data-stu-id="340c8-103">Running selective unit tests</span></span>

<span data-ttu-id="340c8-104">Com o comando `dotnet test` no .NET Core, use uma expressão de filtro para executar testes seletivos.</span><span class="sxs-lookup"><span data-stu-id="340c8-104">With the `dotnet test` command in .NET Core, you can use a filter expression to run selective tests.</span></span> <span data-ttu-id="340c8-105">Este artigo demonstra como filtrar os testes que são executados.</span><span class="sxs-lookup"><span data-stu-id="340c8-105">This article demonstrates how to filter which test are run.</span></span> <span data-ttu-id="340c8-106">Os exemplos a seguir usam `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="340c8-106">The following examples use `dotnet test`.</span></span> <span data-ttu-id="340c8-107">Se você estiver usando `vstest.console.exe`, substitua `--filter` por `--testcasefilter:`.</span><span class="sxs-lookup"><span data-stu-id="340c8-107">If you're using `vstest.console.exe`, replace `--filter` with `--testcasefilter:`.</span></span>

> [!NOTE]
> <span data-ttu-id="340c8-108">O uso de filtros que incluem o ponto de exclamação (!) em `*nix` requer saída, uma vez que `!` é reservado.</span><span class="sxs-lookup"><span data-stu-id="340c8-108">Using filters that include exclamation mark (!) on `*nix` requires escaping since `!` is reserved.</span></span> <span data-ttu-id="340c8-109">Por exemplo, esse filtro ignorará todos os testes se o namespace contiver IntegrationTests: `dotnet test --filter FullyQualifiedName\!~IntegrationTests`.</span><span class="sxs-lookup"><span data-stu-id="340c8-109">For example, this filter skips all tests if the namespace contains IntegrationTests: `dotnet test --filter FullyQualifiedName\!~IntegrationTests`.</span></span>
> <span data-ttu-id="340c8-110">Observe a barra invertida que precede o ponto de exclamação.</span><span class="sxs-lookup"><span data-stu-id="340c8-110">Note the backslash that precedes the exclamation mark.</span></span>

## <a name="mstest"></a><span data-ttu-id="340c8-111">MSTest</span><span class="sxs-lookup"><span data-stu-id="340c8-111">MSTest</span></span>

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

| <span data-ttu-id="340c8-112">Expression</span><span class="sxs-lookup"><span data-stu-id="340c8-112">Expression</span></span> | <span data-ttu-id="340c8-113">Result</span><span class="sxs-lookup"><span data-stu-id="340c8-113">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="340c8-114">Executa testes cujo `FullyQualifiedName` contém `Method`.</span><span class="sxs-lookup"><span data-stu-id="340c8-114">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="340c8-115">Disponível em `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="340c8-115">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="340c8-116">Executa testes cujo nome contém `TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="340c8-116">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTest1` | <span data-ttu-id="340c8-117">Executa testes que estão na classe `MSTestNamespace.UnitTest1`.</span><span class="sxs-lookup"><span data-stu-id="340c8-117">Runs tests which are in class `MSTestNamespace.UnitTest1`.</span></span><br><span data-ttu-id="340c8-118">**Observação:** o valor `ClassName` deve ter um namespace, portanto `ClassName=UnitTest1` não funcionará.</span><span class="sxs-lookup"><span data-stu-id="340c8-118">**Note:** The `ClassName` value should have a namespace, so `ClassName=UnitTest1` won't work.</span></span> |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="340c8-119">Executa todos os testes, exceto `MSTestNamespace.UnitTest1.TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="340c8-119">Runs all tests except `MSTestNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="340c8-120">Executa testes que são anotados com `[TestCategory("CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="340c8-120">Runs tests which are annotated with `[TestCategory("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="340c8-121">Executa testes que são anotados com `[Priority(2)]`.</span><span class="sxs-lookup"><span data-stu-id="340c8-121">Runs tests which are annotated with `[Priority(2)]`.</span></span><br>

<span data-ttu-id="340c8-122">**Usar operadores condicionais | e &amp;**</span><span class="sxs-lookup"><span data-stu-id="340c8-122">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="340c8-123">Expression</span><span class="sxs-lookup"><span data-stu-id="340c8-123">Expression</span></span> | <span data-ttu-id="340c8-124">Result</span><span class="sxs-lookup"><span data-stu-id="340c8-124">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="340c8-125">Executa testes que têm `UnitTest1` em `FullyQualifiedName` **ou** `TestCategory` é `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="340c8-125">Runs tests which have `UnitTest1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | <span data-ttu-id="340c8-126">Executa testes que têm `UnitTest1` em `FullyQualifiedName` **e** `TestCategory` é `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="340c8-126">Runs tests which have `UnitTest1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="340c8-127">Executa testes que têm um `FullyQualifiedName` contendo `UnitTest1` **e** `TestCategory` é `CategoryA` **ou** `Priority` é 1.</span><span class="sxs-lookup"><span data-stu-id="340c8-127">Runs tests which have either `FullyQualifiedName` containing `UnitTest1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="xunit"></a><span data-ttu-id="340c8-128">xUnit</span><span class="sxs-lookup"><span data-stu-id="340c8-128">xUnit</span></span>

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

| <span data-ttu-id="340c8-129">Expression</span><span class="sxs-lookup"><span data-stu-id="340c8-129">Expression</span></span> | <span data-ttu-id="340c8-130">Result</span><span class="sxs-lookup"><span data-stu-id="340c8-130">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="340c8-131">Executa somente um teste, `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="340c8-131">Runs only one test, `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="340c8-132">Executa todos os testes, exceto `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="340c8-132">Runs all tests except `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter DisplayName~TestClass1` | <span data-ttu-id="340c8-133">Executa testes cujo nome de exibição contém `TestClass1`.</span><span class="sxs-lookup"><span data-stu-id="340c8-133">Runs tests whose display name contains `TestClass1`.</span></span> |

<span data-ttu-id="340c8-134">No exemplo de código, as características definidas com chaves `Category` e `Priority` podem ser usadas para filtragem.</span><span class="sxs-lookup"><span data-stu-id="340c8-134">In the code example, the defined traits with keys `Category` and `Priority` can be used for filtering.</span></span>

| <span data-ttu-id="340c8-135">Expression</span><span class="sxs-lookup"><span data-stu-id="340c8-135">Expression</span></span> | <span data-ttu-id="340c8-136">Result</span><span class="sxs-lookup"><span data-stu-id="340c8-136">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter XUnit` | <span data-ttu-id="340c8-137">Executa testes cujo `FullyQualifiedName` contém `XUnit`.</span><span class="sxs-lookup"><span data-stu-id="340c8-137">Runs tests whose `FullyQualifiedName` contains `XUnit`.</span></span>  <span data-ttu-id="340c8-138">Disponível em `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="340c8-138">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Category=CategoryA` | <span data-ttu-id="340c8-139">Executa testes que têm `[Trait("Category", "CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="340c8-139">Runs tests which have `[Trait("Category", "CategoryA")]`.</span></span> |

<span data-ttu-id="340c8-140">**Usar operadores condicionais | e &amp;**</span><span class="sxs-lookup"><span data-stu-id="340c8-140">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="340c8-141">Expression</span><span class="sxs-lookup"><span data-stu-id="340c8-141">Expression</span></span> | <span data-ttu-id="340c8-142">Result</span><span class="sxs-lookup"><span data-stu-id="340c8-142">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=CategoryA"</code> | <span data-ttu-id="340c8-143">Executa testes que têm `TestClass1` em `FullyQualifiedName` **ou** `Category` é `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="340c8-143">Runs tests which has `TestClass1` in `FullyQualifiedName` **or** `Category` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=CategoryA"` | <span data-ttu-id="340c8-144">Executa testes que têm `TestClass1` em `FullyQualifiedName` **e** `Category` é `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="340c8-144">Runs tests which has `TestClass1` in `FullyQualifiedName` **and** `Category` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="340c8-145">Executa testes que têm um `FullyQualifiedName` contendo `TestClass1` **e** `Category` é `CategoryA` **ou** `Priority` é 1.</span><span class="sxs-lookup"><span data-stu-id="340c8-145">Runs tests which have either `FullyQualifiedName` containing `TestClass1` **and** `Category` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="nunit"></a><span data-ttu-id="340c8-146">NUnit</span><span class="sxs-lookup"><span data-stu-id="340c8-146">NUnit</span></span>

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

| <span data-ttu-id="340c8-147">Expression</span><span class="sxs-lookup"><span data-stu-id="340c8-147">Expression</span></span> | <span data-ttu-id="340c8-148">Result</span><span class="sxs-lookup"><span data-stu-id="340c8-148">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="340c8-149">Executa testes cujo `FullyQualifiedName` contém `Method`.</span><span class="sxs-lookup"><span data-stu-id="340c8-149">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="340c8-150">Disponível em `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="340c8-150">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="340c8-151">Executa testes cujo nome contém `TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="340c8-151">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter FullyQualifiedName~NUnitNamespace.UnitTest1` | <span data-ttu-id="340c8-152">Executa testes que estão na classe `NUnitNamespace.UnitTest1`.</span><span class="sxs-lookup"><span data-stu-id="340c8-152">Runs tests which are in class `NUnitNamespace.UnitTest1`.</span></span><br>
| `dotnet test --filter FullyQualifiedName!=NUnitNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="340c8-153">Executa todos os testes, exceto `NUnitNamespace.UnitTest1.TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="340c8-153">Runs all tests except `NUnitNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="340c8-154">Executa testes que são anotados com `[Category("CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="340c8-154">Runs tests which are annotated with `[Category("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="340c8-155">Executa testes que são anotados com `[Priority(2)]`.</span><span class="sxs-lookup"><span data-stu-id="340c8-155">Runs tests which are annotated with `[Priority(2)]`.</span></span><br>

<span data-ttu-id="340c8-156">**Usar operadores condicionais | e &amp;**</span><span class="sxs-lookup"><span data-stu-id="340c8-156">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="340c8-157">Expression</span><span class="sxs-lookup"><span data-stu-id="340c8-157">Expression</span></span> | <span data-ttu-id="340c8-158">Result</span><span class="sxs-lookup"><span data-stu-id="340c8-158">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="340c8-159">Executa testes que têm `UnitTest1` em `FullyQualifiedName` **ou** `TestCategory` é `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="340c8-159">Runs tests which have `UnitTest1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | <span data-ttu-id="340c8-160">Executa testes que têm `UnitTest1` em `FullyQualifiedName` **e** `TestCategory` é `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="340c8-160">Runs tests which have `UnitTest1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="340c8-161">Executa testes que têm um `FullyQualifiedName` contendo `UnitTest1` **e** `TestCategory` é `CategoryA` **ou** `Priority` é 1.</span><span class="sxs-lookup"><span data-stu-id="340c8-161">Runs tests which have either `FullyQualifiedName` containing `UnitTest1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |
