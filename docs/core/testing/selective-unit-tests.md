---
title: Executar testes de unidade seletivos | Microsoft Docs
description: "Mostra como usar uma expressão de filtro para executar testes de unidade seletivos com o comando de teste do dotnet."
keywords: .NET, .NET Core, teste de unidade, teste seletivo
author: smadala
ms.author: mairaw
ms.date: 03/22/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 13d01272-bbf8-456c-a97a-560001d1a7f2
ms.translationtype: Human Translation
ms.sourcegitcommit: ae036cfcad341ffc859336a7ab2a49feec145715
ms.openlocfilehash: aceb0dc92b6c355a2b36a541d59cf1cd3cf4d0d4
ms.contentlocale: pt-br
ms.lasthandoff: 05/18/2017

---

# <a name="running-selective-unit-tests"></a>Executar testes de unidade seletivos

Os exemplos a seguir usam `dotnet test`. Se você estiver usando `vstest.console.exe`, substitua `--filter ` por `--testcasefilter:`.

## <a name="mstest"></a>MSTest

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

| Expressão | Resultado |
| ---------- | ------ |
| `dotnet test --filter Method` | Executa testes cujo `FullyQualifiedName` contém `Method`. Disponível em `vstest 15.1+`. |
| `dotnet test --filter Name~TestMethod1` | Executa testes cujo nome contém `TestMethod1`. |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTestClass1` | Executa testes que estão na classe `MSTestNamespace.UnitTestClass1`.<br>**Observação:** o valor `ClassName` deve ter um namespace, portanto `ClassName=UnitTestClass1` não funcionará. |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTestClass1.TestMethod1` | Executa todos os testes, exceto `MSTestNamespace.UnitTestClass1.TestMethod1`. |
| `dotnet test --filter TestCategory=CategoryA` | Executa testes que são anotados com `[TestCategory("CategoryA")]`. |
| `dotnet test --filter Priority=3` | Executa testes que são anotados com `[Priority(3)]`.<br>**Observação:** `Priority~3` é um valor inválido, pois não é uma cadeia de caracteres. |

**Usar operadores condicionais | e &amp;**

| Expressão | Resultado |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTestClass1&#124;TestCategory=CategoryA"</code> | Executa testes que têm `UnitTestClass1` em `FullyQualifiedName` **, ou**  `TestCategory` é `CategoryA`. |
| `dotnet test --filter "FullyQualifiedName~UnitTestClass1&TestCategory=CategoryA"` | Executa testes que têm `UnitTestClass1` em `FullyQualifiedName` **, e**  `TestCategory` é `CategoryA`. |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTestClass1&TestCategory=CategoryA)&#124;Priority=1"</code> | Executa testes que têm `FullyQualifiedName` contendo `UnitTestClass1` **, e**  `TestCategory` é `CategoryA`  **ou**  `Priority` é 1. |

## <a name="xunit"></a>xUnit

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

| Expressão | Resultado |
| ---------- | ------ |
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | Executa somente um teste, `XUnitNamespace.TestClass1.Test1`. |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | Executa todos os testes, exceto `XUnitNamespace.TestClass1.Test1`. |
| `dotnet test --filter DisplayName~TestClass1` | Executa testes cujo nome de exibição contém `TestClass1`. |

No exemplo de código, as características definidas com chaves `Category` e `Priority` podem ser usadas para filtragem.

| Expressão | Resultado |
| ---------- | ------ |
| `dotnet test --filter XUnit` | Executa testes cujo `FullyQualifiedName` contém `XUnit`.  Disponível em `vstest 15.1+`. |
| `dotnet test --filter Category=bvt` | Executa testes que têm `[Trait("Category", "bvt")]`. |

**Usar operadores condicionais | e &amp;**

| Expressão | Resultado |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=Nightly"</code> | Executa testes que têm `TestClass1` em `FullyQualifiedName` **, ou**  `Category` é `Nightly`. |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=Nightly"` | Executa testes que têm `TestClass1` em `FullyQualifiedName` **, e**  `Category` é `Nightly`. |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=Nightly)&#124;Priority=1"</code> | Executa testes que têm `FullyQualifiedName` contendo `TestClass1` **, e**  `Category` é `CategoryA`  **ou**  `Priority` é 1. |

