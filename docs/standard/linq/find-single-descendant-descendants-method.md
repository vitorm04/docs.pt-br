---
title: Como localizar um único descendente usando o método descendentes-LINQ to XML
description: Use o método de eixo XContainer. Descendants para localizar um único elemento descendente nomeado exclusivamente.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 6f735be9-0293-4680-8007-ca9d96bfebed
ms.openlocfilehash: 9065309822bfb7c46da556fcf9b3a3b48df16302
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89551930"
---
# <a name="how-to-find-a-single-descendant-using-the-descendants-method-linq-to-xml"></a><span data-ttu-id="59f4a-103">Como localizar um único descendente usando o método descendentes (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="59f4a-103">How to find a single descendant using the Descendants method (LINQ to XML)</span></span>

<span data-ttu-id="59f4a-104">Você pode usar o <xref:System.Xml.Linq.XContainer.Descendants%2A> método Axis para localizar um único elemento descendant nomeado exclusivamente.</span><span class="sxs-lookup"><span data-stu-id="59f4a-104">You can use the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis method to find a single uniquely-named descendant element.</span></span> <span data-ttu-id="59f4a-105">Essa técnica é especialmente útil quando você deseja encontrar um descendente específico com um nome específico e pode ser mais rápido e fácil de usar do que navegar na árvore XML.</span><span class="sxs-lookup"><span data-stu-id="59f4a-105">This technique is especially useful when you want to find a particular descendant with a specific name, and may be faster and easier to use than navigating the XML tree.</span></span>

## <a name="example-use-xcontainerdescendants-to-find-a-single-uniquely-named-descendant-element"></a><span data-ttu-id="59f4a-106">Exemplo: Use XContainer. Descendants para localizar um único elemento descendente nomeado exclusivamente</span><span class="sxs-lookup"><span data-stu-id="59f4a-106">Example: Use XContainer.Descendants to find a single uniquely-named descendant element</span></span>

<span data-ttu-id="59f4a-107">Este exemplo usa o operador padrão de consulta <xref:System.Linq.Enumerable.First%2A>.</span><span class="sxs-lookup"><span data-stu-id="59f4a-107">This example uses the <xref:System.Linq.Enumerable.First%2A> standard query operator.</span></span>

```csharp
XElement root = XElement.Parse(@"<Root>
  <Child1>
    <GrandChild1>GC1 Value</GrandChild1>
  </Child1>
  <Child2>
    <GrandChild2>GC2 Value</GrandChild2>
  </Child2>
  <Child3>
    <GrandChild3>GC3 Value</GrandChild3>
  </Child3>
  <Child4>
    <GrandChild4>GC4 Value</GrandChild4>
  </Child4>
</Root>");
string grandChild3 = (string)
    (from el in root.Descendants("GrandChild3")
    select el).First();
Console.WriteLine(grandChild3);
```

```vb
Dim root As XElement = _
    <Root>
        <Child1>
            <GrandChild1>GC1 Value</GrandChild1>
        </Child1>
        <Child2>
            <GrandChild2>GC2 Value</GrandChild2>
        </Child2>
        <Child3>
            <GrandChild3>GC3 Value</GrandChild3>
        </Child3>
        <Child4>
            <GrandChild4>GC4 Value</GrandChild4>
        </Child4>
    </Root>
Dim grandChild3 As String = _
    (From el In root...<GrandChild3> _
    Select el).First()
Console.WriteLine(grandChild3)
```

<span data-ttu-id="59f4a-108">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="59f4a-108">This example produces the following output:</span></span>

```output
GC3 Value
```

## <a name="example-find-when-the-xml-is-in-a-namespace"></a><span data-ttu-id="59f4a-109">Exemplo: localizar quando o XML está em um namespace</span><span class="sxs-lookup"><span data-stu-id="59f4a-109">Example: Find when the XML is in a namespace</span></span>

<span data-ttu-id="59f4a-110">O exemplo a seguir faz o mesmo que o anterior, mas para XML que está em um namespace.</span><span class="sxs-lookup"><span data-stu-id="59f4a-110">The following example does the same as the previous one, but for XML that's  in a namespace.</span></span> <span data-ttu-id="59f4a-111">Para obter mais informações, consulte [visão geral de namespaces](namespaces-overview.md).</span><span class="sxs-lookup"><span data-stu-id="59f4a-111">For more information, see [Namespaces overview](namespaces-overview.md).</span></span>

```csharp
XElement root = XElement.Parse(@"<aw:Root xmlns:aw='http://www.adventure-works.com'>
  <aw:Child1>
    <aw:GrandChild1>GC1 Value</aw:GrandChild1>
  </aw:Child1>
  <aw:Child2>
    <aw:GrandChild2>GC2 Value</aw:GrandChild2>
  </aw:Child2>
  <aw:Child3>
    <aw:GrandChild3>GC3 Value</aw:GrandChild3>
  </aw:Child3>
  <aw:Child4>
    <aw:GrandChild4>GC4 Value</aw:GrandChild4>
  </aw:Child4>
</aw:Root>");
XNamespace aw = "http://www.adventure-works.com";
string grandChild3 = (string)
    (from el in root.Descendants(aw + "GrandChild3")
     select el).First();
Console.WriteLine(grandChild3);
```

```vb
Imports <xmlns:aw='http://www.adventure-works.com'>

Module Module1
    Sub Main()
        Dim root As XElement = _
            <aw:Root>
                <aw:Child1>
                    <aw:GrandChild1>GC1 Value</aw:GrandChild1>
                </aw:Child1>
                <aw:Child2>
                    <aw:GrandChild2>GC2 Value</aw:GrandChild2>
                </aw:Child2>
                <aw:Child3>
                    <aw:GrandChild3>GC3 Value</aw:GrandChild3>
                </aw:Child3>
                <aw:Child4>
                    <aw:GrandChild4>GC4 Value</aw:GrandChild4>
                </aw:Child4>
            </aw:Root>
        Dim grandChild3 As String = _
            (From el In root...<aw:GrandChild3> _
            Select el).First()
        Console.WriteLine(grandChild3)
    End Sub
End Module
```

<span data-ttu-id="59f4a-112">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="59f4a-112">This example produces the following output:</span></span>

```output
GC3 Value
```
