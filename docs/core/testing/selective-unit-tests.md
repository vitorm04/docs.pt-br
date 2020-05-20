---
title: Executar testes de unidade seletivos
description: Como usar uma expressão de filtro para executar testes de unidade seletivos com o comando de teste do dotnet no .NET Core.
author: smadala
ms.date: 05/18/2020
zone_pivot_groups: unit-testing-framework-set-one
ms.openlocfilehash: 6a6bbb0687742d1e3288d64fb88f6825dc678e28
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702984"
---
# <a name="run-selective-unit-tests"></a><span data-ttu-id="8d367-103">Executar testes de unidade seletivos</span><span class="sxs-lookup"><span data-stu-id="8d367-103">Run selective unit tests</span></span>

<span data-ttu-id="8d367-104">Com o [`dotnet test`](../tools/dotnet-test.md) comando no .NET Core, você pode usar uma expressão de filtro para executar testes seletivos.</span><span class="sxs-lookup"><span data-stu-id="8d367-104">With the [`dotnet test`](../tools/dotnet-test.md) command in .NET Core, you can use a filter expression to run selective tests.</span></span> <span data-ttu-id="8d367-105">Este artigo demonstra como filtrar quais testes são executados.</span><span class="sxs-lookup"><span data-stu-id="8d367-105">This article demonstrates how to filter which tests are run.</span></span> <span data-ttu-id="8d367-106">Os exemplos a seguir usam `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="8d367-106">The following examples use `dotnet test`.</span></span> <span data-ttu-id="8d367-107">Se você estiver usando `vstest.console.exe`, substitua `--filter` por `--testcasefilter:`.</span><span class="sxs-lookup"><span data-stu-id="8d367-107">If you're using `vstest.console.exe`, replace `--filter` with `--testcasefilter:`.</span></span>

## <a name="character-escaping"></a><span data-ttu-id="8d367-108">Escape de caractere</span><span class="sxs-lookup"><span data-stu-id="8d367-108">Character escaping</span></span>

<span data-ttu-id="8d367-109">O uso de filtros que incluem o ponto `!` de exclamação em `*nix` requer escape, pois `!` é reservado.</span><span class="sxs-lookup"><span data-stu-id="8d367-109">Using filters that include exclamation mark `!` on `*nix` requires escaping since `!` is reserved.</span></span> <span data-ttu-id="8d367-110">Por exemplo, esse filtro ignorará todos os testes se o namespace contiver IntegrationTests:</span><span class="sxs-lookup"><span data-stu-id="8d367-110">For example, this filter skips all tests if the namespace contains IntegrationTests:</span></span>

```dotnetcli
dotnet test --filter FullyQualifiedName\!~IntegrationTests
```

> [!IMPORTANT]
> <span data-ttu-id="8d367-111">A barra invertida precede o ponto de exclamação para indicar que é um caractere de escape `\!` .</span><span class="sxs-lookup"><span data-stu-id="8d367-111">The backslash precedes the exclamation mark to indicate it is an escaped character `\!`.</span></span>

<span data-ttu-id="8d367-112">Para `FullyQualifiedName` valores que incluem uma vírgula para parâmetros de tipo genérico, escape a vírgula com `%2C` .</span><span class="sxs-lookup"><span data-stu-id="8d367-112">For `FullyQualifiedName` values that include a comma for generic type parameters, escape the comma with `%2C`.</span></span> <span data-ttu-id="8d367-113">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="8d367-113">For example:</span></span>

```dotnetcli
dotnet test --filter "FullyQualifiedName=MyNamespace.MyTestsClass<ParameterType1%2CParameterType2>.MyTestMethod"
```

:::zone pivot="mstest"

```csharp
using Microsoft.VisualStudio.TestTools.UnitTesting;

namespace MSTestNamespace
{
    [TestClass]
    public class UnitTest1
    {
        [TestMethod, Priority(1), TestCategory("CategoryA")]
        public void TestMethod1()
        {
        }

        [TestMethod, Priority(2)]
        public void TestMethod2()
        {
        }
    }
}
```

| <span data-ttu-id="8d367-114">Expression</span><span class="sxs-lookup"><span data-stu-id="8d367-114">Expression</span></span> | <span data-ttu-id="8d367-115">Result</span><span class="sxs-lookup"><span data-stu-id="8d367-115">Result</span></span> |
|--|--|
| `dotnet test --filter Method` | <span data-ttu-id="8d367-116">Executa testes cujo <xref:System.Reflection.Module.FullyQualifiedName> contém `Method`.</span><span class="sxs-lookup"><span data-stu-id="8d367-116">Runs tests whose <xref:System.Reflection.Module.FullyQualifiedName> contains `Method`.</span></span> <span data-ttu-id="8d367-117">Disponível em `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="8d367-117">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="8d367-118">Executa testes cujo nome contém `TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="8d367-118">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTest1` | <span data-ttu-id="8d367-119">Executa testes que estão na classe `MSTestNamespace.UnitTest1` .</span><span class="sxs-lookup"><span data-stu-id="8d367-119">Runs tests that are in class `MSTestNamespace.UnitTest1`.</span></span><br><span data-ttu-id="8d367-120">**Observação:** o valor `ClassName` deve ter um namespace, portanto `ClassName=UnitTest1` não funcionará.</span><span class="sxs-lookup"><span data-stu-id="8d367-120">**Note:** The `ClassName` value should have a namespace, so `ClassName=UnitTest1` won't work.</span></span> |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="8d367-121">Executa todos os testes, exceto `MSTestNamespace.UnitTest1.TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="8d367-121">Runs all tests except `MSTestNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="8d367-122">Executa testes que são anotados com `[TestCategory("CategoryA")]` .</span><span class="sxs-lookup"><span data-stu-id="8d367-122">Runs tests that are annotated with `[TestCategory("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="8d367-123">Executa testes que são anotados com `[Priority(2)]` .</span><span class="sxs-lookup"><span data-stu-id="8d367-123">Runs tests that are annotated with `[Priority(2)]`.</span></span> |

<span data-ttu-id="8d367-124">Exemplos que usam os operadores condicionais `|` e `&` :</span><span class="sxs-lookup"><span data-stu-id="8d367-124">Examples using the conditional operators `|` and `&`:</span></span>

<span data-ttu-id="8d367-125">Executar testes que têm `UnitTest1` no ou no <xref:System.Reflection.Module.FullyQualifiedName> **or** <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute> `"CategoryA"` .</span><span class="sxs-lookup"><span data-stu-id="8d367-125">To run tests that have `UnitTest1` in their <xref:System.Reflection.Module.FullyQualifiedName> **or** <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute> is `"CategoryA"`.</span></span>

```dotnetcli
dotnet test --filter "FullyQualifiedName~UnitTest1|TestCategory=CategoryA"
```

<span data-ttu-id="8d367-126">Executar testes que têm `UnitTest1` em seu <xref:System.Reflection.Module.FullyQualifiedName> **e** ter um <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute> de `"CategoryA"` .</span><span class="sxs-lookup"><span data-stu-id="8d367-126">To run tests that have `UnitTest1` in their <xref:System.Reflection.Module.FullyQualifiedName> **and** have a <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute> of `"CategoryA"`.</span></span>

```dotnetcli
dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"
```

<span data-ttu-id="8d367-127">Para executar testes que <xref:System.Reflection.Module.FullyQualifiedName> contêm `UnitTest1` **e** têm um <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute> `"CategoryA"` **ou** têm uma <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute> prioridade de `1` .</span><span class="sxs-lookup"><span data-stu-id="8d367-127">To run tests that have either <xref:System.Reflection.Module.FullyQualifiedName> containing `UnitTest1` **and** have a <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute> of `"CategoryA"` **or** have a <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute> with a priority of `1`.</span></span>

```dotnetcli
dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)|Priority=1"
```

:::zone-end
:::zone pivot="xunit"

```csharp
using Xunit;

namespace XUnitNamespace
{
    public class TestClass1
    {
        [Fact, Trait("Priority", "1"), Trait("Category", "CategoryA")]
        public void Test1()
        {
        }

        [Fact, Trait("Priority", "2")]
        public void Test2()
        {
        }
    }
}
```

| <span data-ttu-id="8d367-128">Expression</span><span class="sxs-lookup"><span data-stu-id="8d367-128">Expression</span></span> | <span data-ttu-id="8d367-129">Result</span><span class="sxs-lookup"><span data-stu-id="8d367-129">Result</span></span> |
|--|--|
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="8d367-130">Executa somente um teste, `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="8d367-130">Runs only one test, `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="8d367-131">Executa todos os testes, exceto `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="8d367-131">Runs all tests except `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter DisplayName~TestClass1` | <span data-ttu-id="8d367-132">Executa testes cujo nome de exibição contém `TestClass1`.</span><span class="sxs-lookup"><span data-stu-id="8d367-132">Runs tests whose display name contains `TestClass1`.</span></span> |

<span data-ttu-id="8d367-133">No exemplo de código, as características definidas com chaves `"Category"` e `"Priority"` podem ser usadas para filtragem.</span><span class="sxs-lookup"><span data-stu-id="8d367-133">In the code example, the defined traits with keys `"Category"` and `"Priority"` can be used for filtering.</span></span>

| <span data-ttu-id="8d367-134">Expression</span><span class="sxs-lookup"><span data-stu-id="8d367-134">Expression</span></span> | <span data-ttu-id="8d367-135">Result</span><span class="sxs-lookup"><span data-stu-id="8d367-135">Result</span></span> |
|--|--|
| `dotnet test --filter XUnit` | <span data-ttu-id="8d367-136">Executa testes cujo <xref:System.Reflection.Module.FullyQualifiedName> contém `XUnit`.</span><span class="sxs-lookup"><span data-stu-id="8d367-136">Runs tests whose <xref:System.Reflection.Module.FullyQualifiedName> contains `XUnit`.</span></span>  <span data-ttu-id="8d367-137">Disponível em `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="8d367-137">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Category=CategoryA` | <span data-ttu-id="8d367-138">Executa testes que têm `[Trait("Category", "CategoryA")]` .</span><span class="sxs-lookup"><span data-stu-id="8d367-138">Runs tests that have `[Trait("Category", "CategoryA")]`.</span></span> |

<span data-ttu-id="8d367-139">Exemplos que usam os operadores condicionais `|` e `&` :</span><span class="sxs-lookup"><span data-stu-id="8d367-139">Examples using the conditional operators `|` and `&`:</span></span>

<span data-ttu-id="8d367-140">Executar testes que têm `TestClass1` em seu <xref:System.Reflection.Module.FullyQualifiedName> **ou** têm um `Trait` com uma chave `"Category"` e valor de `"CategoryA"` .</span><span class="sxs-lookup"><span data-stu-id="8d367-140">To run tests that have `TestClass1` in their <xref:System.Reflection.Module.FullyQualifiedName> **or** have a `Trait` with a key of `"Category"` and value of `"CategoryA"`.</span></span>

```dotnetcli
dotnet test --filter "FullyQualifiedName~TestClass1|Category=CategoryA"
```

<span data-ttu-id="8d367-141">Executar testes que têm `TestClass1` em seu <xref:System.Reflection.Module.FullyQualifiedName> **e** ter um `Trait` com uma chave `"Category"` e valor de `"CategoryA"` .</span><span class="sxs-lookup"><span data-stu-id="8d367-141">To run tests that have `TestClass1` in their <xref:System.Reflection.Module.FullyQualifiedName> **and** have a `Trait` with a key of `"Category"` and value of `"CategoryA"`.</span></span>

```dotnetcli
dotnet test --filter "FullyQualifiedName~TestClass1&Category=CategoryA"
```

<span data-ttu-id="8d367-142">Para executar testes que <xref:System.Reflection.Module.FullyQualifiedName> contêm `TestClass1` **e** têm um `Trait` com uma chave `"Category"` e um valor de `"CategoryA"` **ou** têm um `Trait` com uma chave `"Priority"` e valor de `1` .</span><span class="sxs-lookup"><span data-stu-id="8d367-142">To run tests that have either <xref:System.Reflection.Module.FullyQualifiedName> containing `TestClass1` **and** have a `Trait` with a key of `"Category"` and value of `"CategoryA"` **or** have a `Trait` with a key of `"Priority"` and value of `1`.</span></span>

```dotnetcli
dotnet test --filter "(FullyQualifiedName~TestClass1&Category=CategoryA)|Priority=1"
```

:::zone-end
:::zone pivot="nunit"

```csharp
using NUnit.Framework;

namespace NUnitNamespace
{
    public class UnitTest1
    {
        [Test, Property("Priority", 1), Category("CategoryA")]
        public void TestMethod1()
        {
        }

        [Test, Property("Priority", 2)]
        public void TestMethod2()
        {
        }
    }
}
```

| <span data-ttu-id="8d367-143">Expression</span><span class="sxs-lookup"><span data-stu-id="8d367-143">Expression</span></span> | <span data-ttu-id="8d367-144">Result</span><span class="sxs-lookup"><span data-stu-id="8d367-144">Result</span></span> |
|--|--|
| `dotnet test --filter Method` | <span data-ttu-id="8d367-145">Executa testes cujo <xref:System.Reflection.Module.FullyQualifiedName> contém `Method`.</span><span class="sxs-lookup"><span data-stu-id="8d367-145">Runs tests whose <xref:System.Reflection.Module.FullyQualifiedName> contains `Method`.</span></span> <span data-ttu-id="8d367-146">Disponível em `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="8d367-146">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="8d367-147">Executa testes cujo nome contém `TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="8d367-147">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter FullyQualifiedName~NUnitNamespace.UnitTest1` | <span data-ttu-id="8d367-148">Executa testes que estão na classe `NUnitNamespace.UnitTest1` .</span><span class="sxs-lookup"><span data-stu-id="8d367-148">Runs tests that are in class `NUnitNamespace.UnitTest1`.</span></span> |
| `dotnet test --filter FullyQualifiedName!=NUnitNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="8d367-149">Executa todos os testes, exceto `NUnitNamespace.UnitTest1.TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="8d367-149">Runs all tests except `NUnitNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="8d367-150">Executa testes que são anotados com `[Category("CategoryA")]` .</span><span class="sxs-lookup"><span data-stu-id="8d367-150">Runs tests that are annotated with `[Category("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="8d367-151">Executa testes que são anotados com `[Priority(2)]` .</span><span class="sxs-lookup"><span data-stu-id="8d367-151">Runs tests that are annotated with `[Priority(2)]`.</span></span> |

<span data-ttu-id="8d367-152">Exemplos que usam os operadores condicionais `|` e `&` :</span><span class="sxs-lookup"><span data-stu-id="8d367-152">Examples using the conditional operators `|` and `&`:</span></span>

<span data-ttu-id="8d367-153">Para executar testes que têm `UnitTest1` em seu <xref:System.Reflection.Module.FullyQualifiedName> **ou** têm um `Category` de `"CategoryA"` .</span><span class="sxs-lookup"><span data-stu-id="8d367-153">To run tests that have `UnitTest1` in their <xref:System.Reflection.Module.FullyQualifiedName> **or** have a `Category` of `"CategoryA"`.</span></span>

```dotnetcli
dotnet test --filter "FullyQualifiedName~UnitTest1|TestCategory=CategoryA"
```

<span data-ttu-id="8d367-154">Executar testes que têm `UnitTest1` em seu <xref:System.Reflection.Module.FullyQualifiedName> **e** ter um `Category` de `"CategoryA"` .</span><span class="sxs-lookup"><span data-stu-id="8d367-154">To run tests that have `UnitTest1` in their <xref:System.Reflection.Module.FullyQualifiedName> **and** have a `Category` of `"CategoryA"`.</span></span>

```dotnetcli
dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"
```

<span data-ttu-id="8d367-155">Para executar testes que têm um <xref:System.Reflection.Module.FullyQualifiedName> contendo `UnitTest1` **e** têm um `Category` `"CategoryA"` **ou** têm um `Property` com `"Priority"` `1` .</span><span class="sxs-lookup"><span data-stu-id="8d367-155">To run tests that have either a <xref:System.Reflection.Module.FullyQualifiedName> containing `UnitTest1` **and** have a `Category` of `"CategoryA"` **or** have a `Property` with a `"Priority"` of `1`.</span></span>

```dotnetcli
dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)|Priority=1"
```

<span data-ttu-id="8d367-156">Para obter mais informações, consulte [filtro TestCase](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).</span><span class="sxs-lookup"><span data-stu-id="8d367-156">For more information, see [TestCase filter](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).</span></span>

:::zone-end

## <a name="see-also"></a><span data-ttu-id="8d367-157">Confira também</span><span class="sxs-lookup"><span data-stu-id="8d367-157">See also</span></span>

- [<span data-ttu-id="8d367-158">dotnet test</span><span class="sxs-lookup"><span data-stu-id="8d367-158">dotnet test</span></span>](../tools/dotnet-test.md)
- [<span data-ttu-id="8d367-159">teste dotnet – filtro</span><span class="sxs-lookup"><span data-stu-id="8d367-159">dotnet test --filter</span></span>](../tools/dotnet-test.md#filter-option-details)

## <a name="next-steps"></a><span data-ttu-id="8d367-160">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="8d367-160">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8d367-161">Ordenar testes de unidade</span><span class="sxs-lookup"><span data-stu-id="8d367-161">Order unit tests</span></span>](order-unit-tests.md)
