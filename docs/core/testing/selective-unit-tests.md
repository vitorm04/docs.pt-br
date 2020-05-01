---
title: Executar testes de unidade seletivos
description: Como usar uma expressão de filtro para executar testes de unidade seletivos com o comando de teste do dotnet no .NET Core.
author: smadala
ms.date: 04/29/2020
ms.openlocfilehash: e66455b5ac012114c45d998fae11da7ee769fbe2
ms.sourcegitcommit: e09dbff13f0b21b569a101f3b3c5efa174aec204
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/01/2020
ms.locfileid: "82624911"
---
# <a name="running-selective-unit-tests"></a><span data-ttu-id="1bf24-103">Executar testes de unidade seletivos</span><span class="sxs-lookup"><span data-stu-id="1bf24-103">Running selective unit tests</span></span>

<span data-ttu-id="1bf24-104">Com o comando `dotnet test` no .NET Core, use uma expressão de filtro para executar testes seletivos.</span><span class="sxs-lookup"><span data-stu-id="1bf24-104">With the `dotnet test` command in .NET Core, you can use a filter expression to run selective tests.</span></span> <span data-ttu-id="1bf24-105">Este artigo demonstra como filtrar os testes que são executados.</span><span class="sxs-lookup"><span data-stu-id="1bf24-105">This article demonstrates how to filter which test are run.</span></span> <span data-ttu-id="1bf24-106">Os exemplos a seguir usam `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="1bf24-106">The following examples use `dotnet test`.</span></span> <span data-ttu-id="1bf24-107">Se você estiver usando `vstest.console.exe`, substitua `--filter` por `--testcasefilter:`.</span><span class="sxs-lookup"><span data-stu-id="1bf24-107">If you're using `vstest.console.exe`, replace `--filter` with `--testcasefilter:`.</span></span>

## <a name="character-escaping"></a><span data-ttu-id="1bf24-108">Escape de caractere</span><span class="sxs-lookup"><span data-stu-id="1bf24-108">Character escaping</span></span>

<span data-ttu-id="1bf24-109">O uso de filtros que incluem o ponto de exclamação ( `*nix` !) em requer `!` escape, pois é reservado.</span><span class="sxs-lookup"><span data-stu-id="1bf24-109">Using filters that include exclamation mark (!) on `*nix` requires escaping since `!` is reserved.</span></span> <span data-ttu-id="1bf24-110">Por exemplo, esse filtro ignorará todos os testes se o namespace contiver `dotnet test --filter FullyQualifiedName\!~IntegrationTests`IntegrationTests:.</span><span class="sxs-lookup"><span data-stu-id="1bf24-110">For example, this filter skips all tests if the namespace contains IntegrationTests: `dotnet test --filter FullyQualifiedName\!~IntegrationTests`.</span></span>
<span data-ttu-id="1bf24-111">Observe a barra invertida que precede o ponto de exclamação.</span><span class="sxs-lookup"><span data-stu-id="1bf24-111">Note the backslash that precedes the exclamation mark.</span></span>

<span data-ttu-id="1bf24-112">Para `FullyQualifiedName` valores que incluem uma vírgula para parâmetros de tipo genérico, escape a vírgula `%2C`com.</span><span class="sxs-lookup"><span data-stu-id="1bf24-112">For `FullyQualifiedName` values that include a comma for generic type parameters, escape the comma with `%2C`.</span></span> <span data-ttu-id="1bf24-113">Por exemplo: </span><span class="sxs-lookup"><span data-stu-id="1bf24-113">For example:</span></span>

```dotnetcli
dotnet test --filter "FullyQualifiedName=MyNamespace.MyTestsClass<ParameterType1%2CParameterType2>.MyTestMethod"
```

## <a name="mstest"></a><span data-ttu-id="1bf24-114">MSTest</span><span class="sxs-lookup"><span data-stu-id="1bf24-114">MSTest</span></span>

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

| <span data-ttu-id="1bf24-115">Expression</span><span class="sxs-lookup"><span data-stu-id="1bf24-115">Expression</span></span> | <span data-ttu-id="1bf24-116">Result</span><span class="sxs-lookup"><span data-stu-id="1bf24-116">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="1bf24-117">Executa testes cujo `FullyQualifiedName` contém `Method`.</span><span class="sxs-lookup"><span data-stu-id="1bf24-117">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="1bf24-118">Disponível em `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="1bf24-118">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="1bf24-119">Executa testes cujo nome contém `TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="1bf24-119">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTest1` | <span data-ttu-id="1bf24-120">Executa testes que estão na classe `MSTestNamespace.UnitTest1`.</span><span class="sxs-lookup"><span data-stu-id="1bf24-120">Runs tests which are in class `MSTestNamespace.UnitTest1`.</span></span><br><span data-ttu-id="1bf24-121">**Observação:** o valor `ClassName` deve ter um namespace, portanto `ClassName=UnitTest1` não funcionará.</span><span class="sxs-lookup"><span data-stu-id="1bf24-121">**Note:** The `ClassName` value should have a namespace, so `ClassName=UnitTest1` won't work.</span></span> |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="1bf24-122">Executa todos os testes, exceto `MSTestNamespace.UnitTest1.TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="1bf24-122">Runs all tests except `MSTestNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="1bf24-123">Executa testes que são anotados com `[TestCategory("CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="1bf24-123">Runs tests which are annotated with `[TestCategory("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="1bf24-124">Executa testes que são anotados com `[Priority(2)]`.</span><span class="sxs-lookup"><span data-stu-id="1bf24-124">Runs tests which are annotated with `[Priority(2)]`.</span></span><br>

<span data-ttu-id="1bf24-125">**Usar operadores condicionais | e &amp;**</span><span class="sxs-lookup"><span data-stu-id="1bf24-125">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="1bf24-126">Expression</span><span class="sxs-lookup"><span data-stu-id="1bf24-126">Expression</span></span> | <span data-ttu-id="1bf24-127">Result</span><span class="sxs-lookup"><span data-stu-id="1bf24-127">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="1bf24-128">Executa testes que têm `UnitTest1` em `FullyQualifiedName` \*\*, ou \*\* `TestCategory` é `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="1bf24-128">Runs tests which have `UnitTest1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | <span data-ttu-id="1bf24-129">Executa testes que têm `UnitTest1` em `FullyQualifiedName` \*\*, e \*\* `TestCategory` é `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="1bf24-129">Runs tests which have `UnitTest1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="1bf24-130">Executa testes que têm `FullyQualifiedName` contendo `UnitTest1` \*\*, e \*\* `TestCategory` é `CategoryA` \*\* ou \*\* `Priority` é 1.</span><span class="sxs-lookup"><span data-stu-id="1bf24-130">Runs tests which have either `FullyQualifiedName` containing `UnitTest1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="xunit"></a><span data-ttu-id="1bf24-131">xUnit</span><span class="sxs-lookup"><span data-stu-id="1bf24-131">xUnit</span></span>

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

| <span data-ttu-id="1bf24-132">Expression</span><span class="sxs-lookup"><span data-stu-id="1bf24-132">Expression</span></span> | <span data-ttu-id="1bf24-133">Result</span><span class="sxs-lookup"><span data-stu-id="1bf24-133">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="1bf24-134">Executa somente um teste, `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="1bf24-134">Runs only one test, `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="1bf24-135">Executa todos os testes, exceto `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="1bf24-135">Runs all tests except `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter DisplayName~TestClass1` | <span data-ttu-id="1bf24-136">Executa testes cujo nome de exibição contém `TestClass1`.</span><span class="sxs-lookup"><span data-stu-id="1bf24-136">Runs tests whose display name contains `TestClass1`.</span></span> |

<span data-ttu-id="1bf24-137">No exemplo de código, as características definidas com chaves `Category` e `Priority` podem ser usadas para filtragem.</span><span class="sxs-lookup"><span data-stu-id="1bf24-137">In the code example, the defined traits with keys `Category` and `Priority` can be used for filtering.</span></span>

| <span data-ttu-id="1bf24-138">Expression</span><span class="sxs-lookup"><span data-stu-id="1bf24-138">Expression</span></span> | <span data-ttu-id="1bf24-139">Result</span><span class="sxs-lookup"><span data-stu-id="1bf24-139">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter XUnit` | <span data-ttu-id="1bf24-140">Executa testes cujo `FullyQualifiedName` contém `XUnit`.</span><span class="sxs-lookup"><span data-stu-id="1bf24-140">Runs tests whose `FullyQualifiedName` contains `XUnit`.</span></span>  <span data-ttu-id="1bf24-141">Disponível em `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="1bf24-141">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Category=CategoryA` | <span data-ttu-id="1bf24-142">Executa testes que têm `[Trait("Category", "CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="1bf24-142">Runs tests which have `[Trait("Category", "CategoryA")]`.</span></span> |

<span data-ttu-id="1bf24-143">**Usar operadores condicionais | e &amp;**</span><span class="sxs-lookup"><span data-stu-id="1bf24-143">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="1bf24-144">Expression</span><span class="sxs-lookup"><span data-stu-id="1bf24-144">Expression</span></span> | <span data-ttu-id="1bf24-145">Result</span><span class="sxs-lookup"><span data-stu-id="1bf24-145">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=CategoryA"</code> | <span data-ttu-id="1bf24-146">Executa testes que têm `TestClass1` em `FullyQualifiedName` \*\*, ou \*\* `Category` é `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="1bf24-146">Runs tests which has `TestClass1` in `FullyQualifiedName` **or** `Category` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=CategoryA"` | <span data-ttu-id="1bf24-147">Executa testes que têm `TestClass1` em `FullyQualifiedName` \*\*, e \*\* `Category` é `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="1bf24-147">Runs tests which has `TestClass1` in `FullyQualifiedName` **and** `Category` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="1bf24-148">Executa testes que têm `FullyQualifiedName` contendo `TestClass1` \*\*, e \*\* `Category` é `CategoryA` \*\* ou \*\* `Priority` é 1.</span><span class="sxs-lookup"><span data-stu-id="1bf24-148">Runs tests which have either `FullyQualifiedName` containing `TestClass1` **and** `Category` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="nunit"></a><span data-ttu-id="1bf24-149">NUnit</span><span class="sxs-lookup"><span data-stu-id="1bf24-149">NUnit</span></span>

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

| <span data-ttu-id="1bf24-150">Expression</span><span class="sxs-lookup"><span data-stu-id="1bf24-150">Expression</span></span> | <span data-ttu-id="1bf24-151">Result</span><span class="sxs-lookup"><span data-stu-id="1bf24-151">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="1bf24-152">Executa testes cujo `FullyQualifiedName` contém `Method`.</span><span class="sxs-lookup"><span data-stu-id="1bf24-152">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="1bf24-153">Disponível em `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="1bf24-153">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="1bf24-154">Executa testes cujo nome contém `TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="1bf24-154">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter FullyQualifiedName~NUnitNamespace.UnitTest1` | <span data-ttu-id="1bf24-155">Executa testes que estão na classe `NUnitNamespace.UnitTest1`.</span><span class="sxs-lookup"><span data-stu-id="1bf24-155">Runs tests which are in class `NUnitNamespace.UnitTest1`.</span></span><br>
| `dotnet test --filter FullyQualifiedName!=NUnitNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="1bf24-156">Executa todos os testes, exceto `NUnitNamespace.UnitTest1.TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="1bf24-156">Runs all tests except `NUnitNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="1bf24-157">Executa testes que são anotados com `[Category("CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="1bf24-157">Runs tests which are annotated with `[Category("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="1bf24-158">Executa testes que são anotados com `[Priority(2)]`.</span><span class="sxs-lookup"><span data-stu-id="1bf24-158">Runs tests which are annotated with `[Priority(2)]`.</span></span><br>

<span data-ttu-id="1bf24-159">**Usar operadores condicionais | e &amp;**</span><span class="sxs-lookup"><span data-stu-id="1bf24-159">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="1bf24-160">Expression</span><span class="sxs-lookup"><span data-stu-id="1bf24-160">Expression</span></span> | <span data-ttu-id="1bf24-161">Result</span><span class="sxs-lookup"><span data-stu-id="1bf24-161">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="1bf24-162">Executa testes que têm `UnitTest1` em `FullyQualifiedName` \*\*, ou \*\* `TestCategory` é `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="1bf24-162">Runs tests which have `UnitTest1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | <span data-ttu-id="1bf24-163">Executa testes que têm `UnitTest1` em `FullyQualifiedName` \*\*, e \*\* `TestCategory` é `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="1bf24-163">Runs tests which have `UnitTest1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="1bf24-164">Executa testes que têm `FullyQualifiedName` contendo `UnitTest1` \*\*, e \*\* `TestCategory` é `CategoryA` \*\* ou \*\* `Priority` é 1.</span><span class="sxs-lookup"><span data-stu-id="1bf24-164">Runs tests which have either `FullyQualifiedName` containing `UnitTest1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |

<span data-ttu-id="1bf24-165">Para obter mais informações, consulte [filtro TestCase](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).</span><span class="sxs-lookup"><span data-stu-id="1bf24-165">For more information, see [TestCase filter](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).</span></span>
