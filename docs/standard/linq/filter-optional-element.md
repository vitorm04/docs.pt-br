---
title: Como filtrar em um elemento opcional-LINQ to XML
description: Você pode escrever uma pesquisa de um elemento filho de tal forma que a pesquisa não dispare uma exceção quando o elemento não existir.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: f99e2f93-fca5-403f-8a0c-770761d4905a
ms.openlocfilehash: 0d6aa3319efb42b467782c8f09947bdae9657ab5
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89551849"
---
# <a name="how-to-filter-on-an-optional-element-linq-to-xml"></a><span data-ttu-id="6bbd0-103">Como filtrar em um elemento opcional (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="6bbd0-103">How to filter on an optional element (LINQ to XML)</span></span>

<span data-ttu-id="6bbd0-104">Às vezes, você deseja filtrar um elemento, mesmo que você não tenha certeza de que ele existe no documento XML.</span><span class="sxs-lookup"><span data-stu-id="6bbd0-104">Sometimes you want to filter for an element even though you're not sure it exists in your XML document.</span></span> <span data-ttu-id="6bbd0-105">Você pode escrever sua pesquisa para que, mesmo que o elemento específico não tenha o elemento filho, você não dispare uma exceção de referência nula filtrando para ela.</span><span class="sxs-lookup"><span data-stu-id="6bbd0-105">You can write your search so that, even if the particular element doesn't have the child element, you don't trigger a null reference exception by filtering for it.</span></span>

## <a name="example-search-that-doesnt-trigger-an-exception-when-the-target-element-doesnt-exist"></a><span data-ttu-id="6bbd0-106">Exemplo: Pesquisar que não dispara uma exceção quando o elemento de destino não existe</span><span class="sxs-lookup"><span data-stu-id="6bbd0-106">Example: Search that doesn't trigger an exception when the target element doesn't exist</span></span>

<span data-ttu-id="6bbd0-107">No exemplo a seguir, o `Child5` elemento não tem um `Type` elemento filho, mas a consulta ainda é executada corretamente.</span><span class="sxs-lookup"><span data-stu-id="6bbd0-107">In the following example, the `Child5` element doesn't have a `Type` child element, but the query still executes correctly.</span></span> <span data-ttu-id="6bbd0-108">O exemplo usa o <xref:System.Xml.Linq.Extensions.Elements%2A> método de extensão.</span><span class="sxs-lookup"><span data-stu-id="6bbd0-108">The example uses the <xref:System.Xml.Linq.Extensions.Elements%2A> extension method.</span></span>

```csharp
XElement root = XElement.Parse(@"<Root>
  <Child1>
    <Text>Child One Text</Text>
    <Type Value=""Yes""/>
  </Child1>
  <Child2>
    <Text>Child Two Text</Text>
    <Type Value=""Yes""/>
  </Child2>
  <Child3>
    <Text>Child Three Text</Text>
    <Type Value=""No""/>
  </Child3>
  <Child4>
    <Text>Child Four Text</Text>
    <Type Value=""Yes""/>
  </Child4>
  <Child5>
    <Text>Child Five Text</Text>
  </Child5>
</Root>");
var cList =
    from typeElement in root.Elements().Elements("Type")
    where (string)typeElement.Attribute("Value") == "Yes"
    select (string)typeElement.Parent.Element("Text");
foreach(string str in cList)
    Console.WriteLine(str);
```

```vb
Dim root As XElement = _
    <Root>
        <Child1>
            <Text>Child One Text</Text>
            <Type Value="Yes"/>
        </Child1>
        <Child2>
            <Text>Child Two Text</Text>
            <Type Value="Yes"/>
        </Child2>
        <Child3>
            <Text>Child Three Text</Text>
            <Type Value="No"/>
        </Child3>
        <Child4>
            <Text>Child Four Text</Text>
            <Type Value="Yes"/>
        </Child4>
        <Child5>
            <Text>Child Five Text</Text>
        </Child5>
    </Root>
Dim cList As IEnumerable(Of String) = _
    From typeElement In root.Elements().<Type> _
    Where typeElement.@Value = "Yes" _
    Select typeElement.Parent.<Text>.Value
Dim str As String
For Each str In cList
    Console.WriteLine(str)
Next
```

<span data-ttu-id="6bbd0-109">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="6bbd0-109">This example produces the following output:</span></span>

```output
Child One Text
Child Two Text
Child Four Text
```

## <a name="example-same-search-but-for-xml-in-a-namespace"></a><span data-ttu-id="6bbd0-110">Exemplo: a mesma pesquisa, mas para XML em um namespace</span><span class="sxs-lookup"><span data-stu-id="6bbd0-110">Example: Same search but for XML in a namespace</span></span>

<span data-ttu-id="6bbd0-111">O exemplo a seguir é a mesma consulta, mas para XML que está em um namespace.</span><span class="sxs-lookup"><span data-stu-id="6bbd0-111">The following example is the same query but for XML that's in a namespace.</span></span> <span data-ttu-id="6bbd0-112">Para obter mais informações, consulte [visão geral de namespaces](namespaces-overview.md).</span><span class="sxs-lookup"><span data-stu-id="6bbd0-112">For more information, see [Namespaces overview](namespaces-overview.md).</span></span>

```csharp
XElement root = XElement.Parse(@"<Root xmlns='http://www.adatum.com'>
  <Child1>
    <Text>Child One Text</Text>
    <Type Value=""Yes""/>
  </Child1>
  <Child2>
    <Text>Child Two Text</Text>
    <Type Value=""Yes""/>
  </Child2>
  <Child3>
    <Text>Child Three Text</Text>
    <Type Value=""No""/>
  </Child3>
  <Child4>
    <Text>Child Four Text</Text>
    <Type Value=""Yes""/>
  </Child4>
  <Child5>
    <Text>Child Five Text</Text>
  </Child5>
</Root>");
XNamespace ad = "http://www.adatum.com";
var cList =
    from typeElement in root.Elements().Elements(ad + "Type")
    where (string)typeElement.Attribute("Value") == "Yes"
    select (string)typeElement.Parent.Element(ad + "Text");
foreach (string str in cList)
    Console.WriteLine(str);
```

```vb
Imports <xmlns='http://www.adatum.com'>

Module Module1
    Sub Main()
        Dim root As XElement = _
            <Root>
                <Child1>
                    <Text>Child One Text</Text>
                    <Type Value="Yes"/>
                </Child1>
                <Child2>
                    <Text>Child Two Text</Text>
                    <Type Value="Yes"/>
                </Child2>
                <Child3>
                    <Text>Child Three Text</Text>
                    <Type Value="No"/>
                </Child3>
                <Child4>
                    <Text>Child Four Text</Text>
                    <Type Value="Yes"/>
                </Child4>
                <Child5>
                    <Text>Child Five Text</Text>
                </Child5>
            </Root>
        Dim cList As IEnumerable(Of String) = _
            From typeElement In root.Elements().<Type> _
            Where typeElement.@Value = "Yes" _
            Select typeElement.Parent.<Text>.Value
        Dim str As String
        For Each str In cList
            Console.WriteLine(str)
        Next
    End Sub
End Module
```

<span data-ttu-id="6bbd0-113">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="6bbd0-113">This example produces the following output:</span></span>

```output
Child One Text
Child Two Text
Child Four Text
```

## <a name="see-also"></a><span data-ttu-id="6bbd0-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="6bbd0-114">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType>
- [<span data-ttu-id="6bbd0-115">Visão geral de operadores de consulta padrão (C#)</span><span class="sxs-lookup"><span data-stu-id="6bbd0-115">Standard Query Operators Overview (C#)</span></span>](../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="6bbd0-116">Operações de projeção (C#)</span><span class="sxs-lookup"><span data-stu-id="6bbd0-116">Projection Operations (C#)</span></span>](../../csharp/programming-guide/concepts/linq/projection-operations.md)
- [<span data-ttu-id="6bbd0-117">Consultas básicas (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6bbd0-117">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
- [<span data-ttu-id="6bbd0-118">Propriedade do eixo filho XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6bbd0-118">XML Child Axis Property (Visual Basic)</span></span>](../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)
- [<span data-ttu-id="6bbd0-119">Propriedade de eixo do atributo XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6bbd0-119">XML Attribute Axis Property (Visual Basic)</span></span>](../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)
- [<span data-ttu-id="6bbd0-120">Propriedade do Valor XML</span><span class="sxs-lookup"><span data-stu-id="6bbd0-120">XML Value Property</span></span>](../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [<span data-ttu-id="6bbd0-121">Visão geral de operadores de consulta padrão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6bbd0-121">Standard Query Operators Overview (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="6bbd0-122">Operações de projeção (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6bbd0-122">Projection Operations (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/projection-operations.md)
