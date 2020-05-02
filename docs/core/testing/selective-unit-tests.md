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
# <a name="run-selective-unit-tests"></a>Executar testes de unidade seletivos

Com o comando `dotnet test` no .NET Core, use uma expressão de filtro para executar testes seletivos. Este artigo demonstra como filtrar quais testes são executados. Os exemplos a seguir usam `dotnet test`. Se você estiver usando `vstest.console.exe`, substitua `--filter` por `--testcasefilter:`.

## <a name="character-escaping"></a>Escape de caractere

O uso de filtros que incluem o ponto de exclamação ( `*nix` !) em requer `!` escape, pois é reservado. Por exemplo, esse filtro ignorará todos os testes se o namespace contiver `dotnet test --filter FullyQualifiedName\!~IntegrationTests`IntegrationTests:.
Observe a barra invertida que precede o ponto de exclamação.

Para `FullyQualifiedName` valores que incluem uma vírgula para parâmetros de tipo genérico, escape a vírgula `%2C`com. Por exemplo: 

```dotnetcli
dotnet test --filter "FullyQualifiedName=MyNamespace.MyTestsClass<ParameterType1%2CParameterType2>.MyTestMethod"
```

## <a name="mstest"></a>MSTest

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

| Expression | Result |
| ---------- | ------ |
| `dotnet test --filter Method` | Executa testes cujo `FullyQualifiedName` contém `Method`. Disponível em `vstest 15.1+`. |
| `dotnet test --filter Name~TestMethod1` | Executa testes cujo nome contém `TestMethod1`. |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTest1` | Executa testes que estão na classe `MSTestNamespace.UnitTest1`.<br>**Observação:** o valor `ClassName` deve ter um namespace, portanto `ClassName=UnitTest1` não funcionará. |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTest1.TestMethod1` | Executa todos os testes, exceto `MSTestNamespace.UnitTest1.TestMethod1`. |
| `dotnet test --filter TestCategory=CategoryA` | Executa testes que são anotados com `[TestCategory("CategoryA")]`. |
| `dotnet test --filter Priority=2` | Executa testes que são anotados com `[Priority(2)]`.<br>

**Usar operadores condicionais | e &amp;**

| Expression | Result |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | Executa testes que têm `UnitTest1` o `FullyQualifiedName` no **ou** `TestCategory` no `CategoryA`. |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | Executa testes que têm `UnitTest1` o `FullyQualifiedName` no **e** `TestCategory` é `CategoryA`. |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | Executa `FullyQualifiedName` testes que contêm `UnitTest1` **e** `TestCategory` são `CategoryA` **ou** `Priority` são 1. |

## <a name="xunit"></a>xUnit

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

| Expression | Result |
| ---------- | ------ |
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | Executa somente um teste, `XUnitNamespace.TestClass1.Test1`. |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | Executa todos os testes, exceto `XUnitNamespace.TestClass1.Test1`. |
| `dotnet test --filter DisplayName~TestClass1` | Executa testes cujo nome de exibição contém `TestClass1`. |

No exemplo de código, as características definidas com chaves `Category` e `Priority` podem ser usadas para filtragem.

| Expression | Result |
| ---------- | ------ |
| `dotnet test --filter XUnit` | Executa testes cujo `FullyQualifiedName` contém `XUnit`.  Disponível em `vstest 15.1+`. |
| `dotnet test --filter Category=CategoryA` | Executa testes que têm `[Trait("Category", "CategoryA")]`. |

**Usar operadores condicionais | e &amp;**

| Expression | Result |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=CategoryA"</code> | Executa testes que têm `TestClass1` o `FullyQualifiedName` no **ou** `Category` no `CategoryA`. |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=CategoryA"` | Executa testes que têm `TestClass1` o `FullyQualifiedName` no **e** `Category` é `CategoryA`. |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=CategoryA)&#124;Priority=1"</code> | Executa `FullyQualifiedName` testes que contêm `TestClass1` **e** `Category` são `CategoryA` **ou** `Priority` são 1. |

## <a name="nunit"></a>NUnit

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

| Expression | Result |
| ---------- | ------ |
| `dotnet test --filter Method` | Executa testes cujo `FullyQualifiedName` contém `Method`. Disponível em `vstest 15.1+`. |
| `dotnet test --filter Name~TestMethod1` | Executa testes cujo nome contém `TestMethod1`. |
| `dotnet test --filter FullyQualifiedName~NUnitNamespace.UnitTest1` | Executa testes que estão na classe `NUnitNamespace.UnitTest1`.<br>
| `dotnet test --filter FullyQualifiedName!=NUnitNamespace.UnitTest1.TestMethod1` | Executa todos os testes, exceto `NUnitNamespace.UnitTest1.TestMethod1`. |
| `dotnet test --filter TestCategory=CategoryA` | Executa testes que são anotados com `[Category("CategoryA")]`. |
| `dotnet test --filter Priority=2` | Executa testes que são anotados com `[Priority(2)]`.<br>

**Usar operadores condicionais | e &amp;**

| Expression | Result |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | Executa testes que têm `UnitTest1` o `FullyQualifiedName` no **ou** `TestCategory` no `CategoryA`. |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | Executa testes que têm `UnitTest1` o `FullyQualifiedName` no **e** `TestCategory` é `CategoryA`. |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | Executa `FullyQualifiedName` testes que contêm `UnitTest1` **e** `TestCategory` são `CategoryA` **ou** `Priority` são 1. |

Para obter mais informações, consulte [filtro TestCase](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).
