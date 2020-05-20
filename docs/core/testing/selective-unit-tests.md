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
# <a name="run-selective-unit-tests"></a>Executar testes de unidade seletivos

Com o [`dotnet test`](../tools/dotnet-test.md) comando no .NET Core, você pode usar uma expressão de filtro para executar testes seletivos. Este artigo demonstra como filtrar quais testes são executados. Os exemplos a seguir usam `dotnet test`. Se você estiver usando `vstest.console.exe`, substitua `--filter` por `--testcasefilter:`.

## <a name="character-escaping"></a>Escape de caractere

O uso de filtros que incluem o ponto `!` de exclamação em `*nix` requer escape, pois `!` é reservado. Por exemplo, esse filtro ignorará todos os testes se o namespace contiver IntegrationTests:

```dotnetcli
dotnet test --filter FullyQualifiedName\!~IntegrationTests
```

> [!IMPORTANT]
> A barra invertida precede o ponto de exclamação para indicar que é um caractere de escape `\!` .

Para `FullyQualifiedName` valores que incluem uma vírgula para parâmetros de tipo genérico, escape a vírgula com `%2C` . Por exemplo:

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

| Expression | Result |
|--|--|
| `dotnet test --filter Method` | Executa testes cujo <xref:System.Reflection.Module.FullyQualifiedName> contém `Method`. Disponível em `vstest 15.1+`. |
| `dotnet test --filter Name~TestMethod1` | Executa testes cujo nome contém `TestMethod1`. |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTest1` | Executa testes que estão na classe `MSTestNamespace.UnitTest1` .<br>**Observação:** o valor `ClassName` deve ter um namespace, portanto `ClassName=UnitTest1` não funcionará. |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTest1.TestMethod1` | Executa todos os testes, exceto `MSTestNamespace.UnitTest1.TestMethod1`. |
| `dotnet test --filter TestCategory=CategoryA` | Executa testes que são anotados com `[TestCategory("CategoryA")]` . |
| `dotnet test --filter Priority=2` | Executa testes que são anotados com `[Priority(2)]` . |

Exemplos que usam os operadores condicionais `|` e `&` :

Executar testes que têm `UnitTest1` no ou no <xref:System.Reflection.Module.FullyQualifiedName> **or** <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute> `"CategoryA"` .

```dotnetcli
dotnet test --filter "FullyQualifiedName~UnitTest1|TestCategory=CategoryA"
```

Executar testes que têm `UnitTest1` em seu <xref:System.Reflection.Module.FullyQualifiedName> **e** ter um <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute> de `"CategoryA"` .

```dotnetcli
dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"
```

Para executar testes que <xref:System.Reflection.Module.FullyQualifiedName> contêm `UnitTest1` **e** têm um <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute> `"CategoryA"` **ou** têm uma <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute> prioridade de `1` .

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

| Expression | Result |
|--|--|
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | Executa somente um teste, `XUnitNamespace.TestClass1.Test1`. |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | Executa todos os testes, exceto `XUnitNamespace.TestClass1.Test1`. |
| `dotnet test --filter DisplayName~TestClass1` | Executa testes cujo nome de exibição contém `TestClass1`. |

No exemplo de código, as características definidas com chaves `"Category"` e `"Priority"` podem ser usadas para filtragem.

| Expression | Result |
|--|--|
| `dotnet test --filter XUnit` | Executa testes cujo <xref:System.Reflection.Module.FullyQualifiedName> contém `XUnit`.  Disponível em `vstest 15.1+`. |
| `dotnet test --filter Category=CategoryA` | Executa testes que têm `[Trait("Category", "CategoryA")]` . |

Exemplos que usam os operadores condicionais `|` e `&` :

Executar testes que têm `TestClass1` em seu <xref:System.Reflection.Module.FullyQualifiedName> **ou** têm um `Trait` com uma chave `"Category"` e valor de `"CategoryA"` .

```dotnetcli
dotnet test --filter "FullyQualifiedName~TestClass1|Category=CategoryA"
```

Executar testes que têm `TestClass1` em seu <xref:System.Reflection.Module.FullyQualifiedName> **e** ter um `Trait` com uma chave `"Category"` e valor de `"CategoryA"` .

```dotnetcli
dotnet test --filter "FullyQualifiedName~TestClass1&Category=CategoryA"
```

Para executar testes que <xref:System.Reflection.Module.FullyQualifiedName> contêm `TestClass1` **e** têm um `Trait` com uma chave `"Category"` e um valor de `"CategoryA"` **ou** têm um `Trait` com uma chave `"Priority"` e valor de `1` .

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

| Expression | Result |
|--|--|
| `dotnet test --filter Method` | Executa testes cujo <xref:System.Reflection.Module.FullyQualifiedName> contém `Method`. Disponível em `vstest 15.1+`. |
| `dotnet test --filter Name~TestMethod1` | Executa testes cujo nome contém `TestMethod1`. |
| `dotnet test --filter FullyQualifiedName~NUnitNamespace.UnitTest1` | Executa testes que estão na classe `NUnitNamespace.UnitTest1` . |
| `dotnet test --filter FullyQualifiedName!=NUnitNamespace.UnitTest1.TestMethod1` | Executa todos os testes, exceto `NUnitNamespace.UnitTest1.TestMethod1`. |
| `dotnet test --filter TestCategory=CategoryA` | Executa testes que são anotados com `[Category("CategoryA")]` . |
| `dotnet test --filter Priority=2` | Executa testes que são anotados com `[Priority(2)]` . |

Exemplos que usam os operadores condicionais `|` e `&` :

Para executar testes que têm `UnitTest1` em seu <xref:System.Reflection.Module.FullyQualifiedName> **ou** têm um `Category` de `"CategoryA"` .

```dotnetcli
dotnet test --filter "FullyQualifiedName~UnitTest1|TestCategory=CategoryA"
```

Executar testes que têm `UnitTest1` em seu <xref:System.Reflection.Module.FullyQualifiedName> **e** ter um `Category` de `"CategoryA"` .

```dotnetcli
dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"
```

Para executar testes que têm um <xref:System.Reflection.Module.FullyQualifiedName> contendo `UnitTest1` **e** têm um `Category` `"CategoryA"` **ou** têm um `Property` com `"Priority"` `1` .

```dotnetcli
dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)|Priority=1"
```

Para obter mais informações, consulte [filtro TestCase](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).

:::zone-end

## <a name="see-also"></a>Confira também

- [dotnet test](../tools/dotnet-test.md)
- [teste dotnet – filtro](../tools/dotnet-test.md#filter-option-details)

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Ordenar testes de unidade](order-unit-tests.md)
