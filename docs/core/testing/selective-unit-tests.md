---
title: Executar testes de unidade seletivos
description: Como usar uma expressão de filtro para executar testes de unidade seletivos com o comando de teste do dotnet no .NET Core.
author: smadala
ms.date: 04/29/2020
ms.openlocfilehash: 50642126f3b470180ddd303ed4a2d2d90bfa5b8f
ms.sourcegitcommit: 7370aa8203b6036cea1520021b5511d0fd994574
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/02/2020
ms.locfileid: "82728188"
---
# <a name="run-selective-unit-tests"></a><span data-ttu-id="dad43-103">Executar testes de unidade seletivos</span><span class="sxs-lookup"><span data-stu-id="dad43-103">Run selective unit tests</span></span>

<span data-ttu-id="dad43-104">Com o comando `dotnet test` no .NET Core, use uma expressão de filtro para executar testes seletivos.</span><span class="sxs-lookup"><span data-stu-id="dad43-104">With the `dotnet test` command in .NET Core, you can use a filter expression to run selective tests.</span></span> <span data-ttu-id="dad43-105">Este artigo demonstra como filtrar quais testes são executados.</span><span class="sxs-lookup"><span data-stu-id="dad43-105">This article demonstrates how to filter which tests are run.</span></span> <span data-ttu-id="dad43-106">Os exemplos a seguir usam `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="dad43-106">The following examples use `dotnet test`.</span></span> <span data-ttu-id="dad43-107">Se você estiver usando `vstest.console.exe`, substitua `--filter` por `--testcasefilter:`.</span><span class="sxs-lookup"><span data-stu-id="dad43-107">If you're using `vstest.console.exe`, replace `--filter` with `--testcasefilter:`.</span></span>

## <a name="character-escaping"></a><span data-ttu-id="dad43-108">Escape de caractere</span><span class="sxs-lookup"><span data-stu-id="dad43-108">Character escaping</span></span>

<span data-ttu-id="dad43-109">O uso de filtros que incluem o ponto de exclamação ( `*nix` !) em requer `!` escape, pois é reservado.</span><span class="sxs-lookup"><span data-stu-id="dad43-109">Using filters that include exclamation mark (!) on `*nix` requires escaping since `!` is reserved.</span></span> <span data-ttu-id="dad43-110">Por exemplo, esse filtro ignorará todos os testes se o namespace contiver `dotnet test --filter FullyQualifiedName\!~IntegrationTests`IntegrationTests:.</span><span class="sxs-lookup"><span data-stu-id="dad43-110">For example, this filter skips all tests if the namespace contains IntegrationTests: `dotnet test --filter FullyQualifiedName\!~IntegrationTests`.</span></span>
<span data-ttu-id="dad43-111">Observe a barra invertida que precede o ponto de exclamação.</span><span class="sxs-lookup"><span data-stu-id="dad43-111">Note the backslash that precedes the exclamation mark.</span></span>

<span data-ttu-id="dad43-112">Para `FullyQualifiedName` valores que incluem uma vírgula para parâmetros de tipo genérico, escape a vírgula `%2C`com.</span><span class="sxs-lookup"><span data-stu-id="dad43-112">For `FullyQualifiedName` values that include a comma for generic type parameters, escape the comma with `%2C`.</span></span> <span data-ttu-id="dad43-113">Por exemplo: </span><span class="sxs-lookup"><span data-stu-id="dad43-113">For example:</span></span>

```dotnetcli
dotnet test --filter "FullyQualifiedName=MyNamespace.MyTestsClass<ParameterType1%2CParameterType2>.MyTestMethod"
```

## <a name="mstest"></a><span data-ttu-id="dad43-114">MSTest</span><span class="sxs-lookup"><span data-stu-id="dad43-114">MSTest</span></span>

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

| <span data-ttu-id="dad43-115">Expression</span><span class="sxs-lookup"><span data-stu-id="dad43-115">Expression</span></span> | <span data-ttu-id="dad43-116">Result</span><span class="sxs-lookup"><span data-stu-id="dad43-116">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="dad43-117">Executa testes cujo `FullyQualifiedName` contém `Method`.</span><span class="sxs-lookup"><span data-stu-id="dad43-117">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="dad43-118">Disponível em `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="dad43-118">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="dad43-119">Executa testes cujo nome contém `TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="dad43-119">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTest1` | <span data-ttu-id="dad43-120">Executa testes que estão na classe `MSTestNamespace.UnitTest1`.</span><span class="sxs-lookup"><span data-stu-id="dad43-120">Runs tests that are in class `MSTestNamespace.UnitTest1`.</span></span><br><span data-ttu-id="dad43-121">**Observação:** o valor `ClassName` deve ter um namespace, portanto `ClassName=UnitTest1` não funcionará.</span><span class="sxs-lookup"><span data-stu-id="dad43-121">**Note:** The `ClassName` value should have a namespace, so `ClassName=UnitTest1` won't work.</span></span> |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="dad43-122">Executa todos os testes, exceto `MSTestNamespace.UnitTest1.TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="dad43-122">Runs all tests except `MSTestNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="dad43-123">Executa testes que são anotados com `[TestCategory("CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="dad43-123">Runs tests that are annotated with `[TestCategory("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="dad43-124">Executa testes que são anotados com `[Priority(2)]`.</span><span class="sxs-lookup"><span data-stu-id="dad43-124">Runs tests that are annotated with `[Priority(2)]`.</span></span><br>

<span data-ttu-id="dad43-125">**Usar operadores condicionais | e &amp;**</span><span class="sxs-lookup"><span data-stu-id="dad43-125">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="dad43-126">Expression</span><span class="sxs-lookup"><span data-stu-id="dad43-126">Expression</span></span> | <span data-ttu-id="dad43-127">Result</span><span class="sxs-lookup"><span data-stu-id="dad43-127">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="dad43-128">Executa testes que têm `UnitTest1` o `FullyQualifiedName` no **ou** `TestCategory` no `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="dad43-128">Runs tests that have `UnitTest1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | <span data-ttu-id="dad43-129">Executa testes que têm `UnitTest1` o `FullyQualifiedName` no **e** `TestCategory` é `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="dad43-129">Runs tests that have `UnitTest1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="dad43-130">Executa `FullyQualifiedName` testes que contêm `UnitTest1` **e** `TestCategory` são `CategoryA` **ou** `Priority` são 1.</span><span class="sxs-lookup"><span data-stu-id="dad43-130">Runs tests that have either `FullyQualifiedName` containing `UnitTest1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="xunit"></a><span data-ttu-id="dad43-131">xUnit</span><span class="sxs-lookup"><span data-stu-id="dad43-131">xUnit</span></span>

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

| <span data-ttu-id="dad43-132">Expression</span><span class="sxs-lookup"><span data-stu-id="dad43-132">Expression</span></span> | <span data-ttu-id="dad43-133">Result</span><span class="sxs-lookup"><span data-stu-id="dad43-133">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="dad43-134">Executa somente um teste, `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="dad43-134">Runs only one test, `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="dad43-135">Executa todos os testes, exceto `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="dad43-135">Runs all tests except `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter DisplayName~TestClass1` | <span data-ttu-id="dad43-136">Executa testes cujo nome de exibição contém `TestClass1`.</span><span class="sxs-lookup"><span data-stu-id="dad43-136">Runs tests whose display name contains `TestClass1`.</span></span> |

<span data-ttu-id="dad43-137">No exemplo de código, as características definidas com chaves `Category` e `Priority` podem ser usadas para filtragem.</span><span class="sxs-lookup"><span data-stu-id="dad43-137">In the code example, the defined traits with keys `Category` and `Priority` can be used for filtering.</span></span>

| <span data-ttu-id="dad43-138">Expression</span><span class="sxs-lookup"><span data-stu-id="dad43-138">Expression</span></span> | <span data-ttu-id="dad43-139">Result</span><span class="sxs-lookup"><span data-stu-id="dad43-139">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter XUnit` | <span data-ttu-id="dad43-140">Executa testes cujo `FullyQualifiedName` contém `XUnit`.</span><span class="sxs-lookup"><span data-stu-id="dad43-140">Runs tests whose `FullyQualifiedName` contains `XUnit`.</span></span>  <span data-ttu-id="dad43-141">Disponível em `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="dad43-141">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Category=CategoryA` | <span data-ttu-id="dad43-142">Executa testes que têm `[Trait("Category", "CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="dad43-142">Runs tests that have `[Trait("Category", "CategoryA")]`.</span></span> |

<span data-ttu-id="dad43-143">**Usar operadores condicionais | e &amp;**</span><span class="sxs-lookup"><span data-stu-id="dad43-143">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="dad43-144">Expression</span><span class="sxs-lookup"><span data-stu-id="dad43-144">Expression</span></span> | <span data-ttu-id="dad43-145">Result</span><span class="sxs-lookup"><span data-stu-id="dad43-145">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=CategoryA"</code> | <span data-ttu-id="dad43-146">Executa testes que têm `TestClass1` o `FullyQualifiedName` no **ou** `Category` no `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="dad43-146">Runs tests that have `TestClass1` in `FullyQualifiedName` **or** `Category` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=CategoryA"` | <span data-ttu-id="dad43-147">Executa testes que têm `TestClass1` o `FullyQualifiedName` no **e** `Category` é `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="dad43-147">Runs tests that have `TestClass1` in `FullyQualifiedName` **and** `Category` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="dad43-148">Executa `FullyQualifiedName` testes que contêm `TestClass1` **e** `Category` são `CategoryA` **ou** `Priority` são 1.</span><span class="sxs-lookup"><span data-stu-id="dad43-148">Runs tests that have either `FullyQualifiedName` containing `TestClass1` **and** `Category` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="nunit"></a><span data-ttu-id="dad43-149">NUnit</span><span class="sxs-lookup"><span data-stu-id="dad43-149">NUnit</span></span>

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

| <span data-ttu-id="dad43-150">Expression</span><span class="sxs-lookup"><span data-stu-id="dad43-150">Expression</span></span> | <span data-ttu-id="dad43-151">Result</span><span class="sxs-lookup"><span data-stu-id="dad43-151">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="dad43-152">Executa testes cujo `FullyQualifiedName` contém `Method`.</span><span class="sxs-lookup"><span data-stu-id="dad43-152">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="dad43-153">Disponível em `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="dad43-153">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="dad43-154">Executa testes cujo nome contém `TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="dad43-154">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter FullyQualifiedName~NUnitNamespace.UnitTest1` | <span data-ttu-id="dad43-155">Executa testes que estão na classe `NUnitNamespace.UnitTest1`.</span><span class="sxs-lookup"><span data-stu-id="dad43-155">Runs tests that are in class `NUnitNamespace.UnitTest1`.</span></span><br>
| `dotnet test --filter FullyQualifiedName!=NUnitNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="dad43-156">Executa todos os testes, exceto `NUnitNamespace.UnitTest1.TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="dad43-156">Runs all tests except `NUnitNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="dad43-157">Executa testes que são anotados com `[Category("CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="dad43-157">Runs tests that are annotated with `[Category("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="dad43-158">Executa testes que são anotados com `[Priority(2)]`.</span><span class="sxs-lookup"><span data-stu-id="dad43-158">Runs tests that are annotated with `[Priority(2)]`.</span></span><br>

<span data-ttu-id="dad43-159">**Usar operadores condicionais | e &amp;**</span><span class="sxs-lookup"><span data-stu-id="dad43-159">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="dad43-160">Expression</span><span class="sxs-lookup"><span data-stu-id="dad43-160">Expression</span></span> | <span data-ttu-id="dad43-161">Result</span><span class="sxs-lookup"><span data-stu-id="dad43-161">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="dad43-162">Executa testes que têm `UnitTest1` o `FullyQualifiedName` no **ou** `TestCategory` no `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="dad43-162">Runs tests that have `UnitTest1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | <span data-ttu-id="dad43-163">Executa testes que têm `UnitTest1` o `FullyQualifiedName` no **e** `TestCategory` é `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="dad43-163">Runs tests that have `UnitTest1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="dad43-164">Executa `FullyQualifiedName` testes que contêm `UnitTest1` **e** `TestCategory` são `CategoryA` **ou** `Priority` são 1.</span><span class="sxs-lookup"><span data-stu-id="dad43-164">Runs tests that have either `FullyQualifiedName` containing `UnitTest1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |

<span data-ttu-id="dad43-165">Para obter mais informações, consulte [filtro TestCase](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).</span><span class="sxs-lookup"><span data-stu-id="dad43-165">For more information, see [TestCase filter](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).</span></span>
