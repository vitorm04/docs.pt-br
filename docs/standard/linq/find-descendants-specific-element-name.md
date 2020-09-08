---
title: Como localizar descendentes com um nome de elemento específico-LINQ to XML
description: Para localizar todos os descendentes que têm um nome específico, é mais fácil usar XContainer. Descendants do que iterar em todos os descendentes.
ms.date: 07/20/2015
ms.assetid: f684da20-bee9-47f5-9607-7e3fd7e67470
ms.openlocfilehash: 68d5ed3379e11872458ce98421e62e3cd53c1ab5
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89551836"
---
# <a name="how-to-find-descendants-with-a-specific-element-name-linq-to-xml"></a><span data-ttu-id="618a4-103">Como localizar descendentes com um nome de elemento específico (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="618a4-103">How to find descendants with a specific element name (LINQ to XML)</span></span>

<span data-ttu-id="618a4-104">Às vezes, você deseja localizar todos os descendentes com um nome específico.</span><span class="sxs-lookup"><span data-stu-id="618a4-104">Sometimes you want to find all descendants with a specific name.</span></span> <span data-ttu-id="618a4-105">Você poderia escrever código para iterar por todos os descendentes, mas é mais fácil usar o <xref:System.Xml.Linq.XContainer.Descendants%2A> eixo.</span><span class="sxs-lookup"><span data-stu-id="618a4-105">You could write code to iterate through all of the descendants, but it's easier to use the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis.</span></span>

## <a name="example-find-descendants-with-a-specific-element-name"></a><span data-ttu-id="618a4-106">Exemplo: localizar descendentes com um nome de elemento específico</span><span class="sxs-lookup"><span data-stu-id="618a4-106">Example: Find descendants with a specific element name</span></span>

<span data-ttu-id="618a4-107">O exemplo a seguir mostra como localizar descendentes com um nome de elemento específico.</span><span class="sxs-lookup"><span data-stu-id="618a4-107">The following example shows how to find descendants with a specific element name.</span></span>

```csharp
XElement root = XElement.Parse(@"<root>
  <para>
    <r>
      <t>Some text </t>
    </r>
    <n>
      <r>
        <t>that's broken up into </t>
      </r>
    </n>
    <n>
      <r>
        <t>multiple segments.</t>
      </r>
    </n>
  </para>
</root>");
IEnumerable<string> textSegs =
    from seg in root.Descendants("t")
    select (string)seg;

string str = textSegs.Aggregate(new StringBuilder(),
    (sb, i) => sb.Append(i),
    sp => sp.ToString()
);

Console.WriteLine(str);
```

```vb
Dim root As XElement = _
    <root>
        <para>
            <r>
                <t>Some text </t>
            </r>
            <n>
                <r>
                    <t>that's broken up into </t>
                </r>
            </n>
            <n>
                <r>
                    <t>multiple segments.</t>
                </r>
            </n>
        </para>
    </root>

Dim textSegs As IEnumerable(Of String) = _
    From seg In root...<t> _
    Select seg.Value

Dim str As String = textSegs.Aggregate( _
    New StringBuilder, _
    Function(sb, i) sb.Append(i), _
    Function(sb) sb.ToString)

Console.WriteLine(str)
```

<span data-ttu-id="618a4-108">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="618a4-108">This example produces the following output:</span></span>

```output
Some text that's broken up into multiple segments.

## Example: Find when the XML is in a namespace

The following example shows the same query for XML that's in a namespace. For more information, see [Namespaces overview](namespaces-overview.md).

```csharp
XElement root = XElement.Parse(@"<root xmlns='http://www.adatum.com'>
  <para>
    <r>
      <t>Some text </t>
    </r>
    <n>
      <r>
        <t>that's broken up into </t>
      </r>
    </n>
    <n>
      <r>
        <t>multiple segments.</t>
      </r>
    </n>
  </para>
</root>");
XNamespace ad = "http://www.adatum.com";
IEnumerable<string> textSegs =
    from seg in root.Descendants(ad + "t")
    select (string)seg;

string str = textSegs.Aggregate(new StringBuilder(),
    (sb, i) => sb.Append(i),
    sp => sp.ToString()
);

Console.WriteLine(str);
```

```vb
Imports <xmlns='http://www.adatum.com'>

Module Module1
    Sub Main()
        Dim root As XElement = _
            <root>
                <para>
                    <r>
                        <t>Some text </t>
                    </r>
                    <n>
                        <r>
                            <t>that's broken up into </t>
                        </r>
                    </n>
                    <n>
                        <r>
                            <t>multiple segments.</t>
                        </r>
                    </n>
                </para>
            </root>

        Dim textSegs As IEnumerable(Of String) = _
            From seg In root...<t> _
            Select seg.Value

        Dim str As String = textSegs.Aggregate( _
            New StringBuilder, _
            Function(sb, i) sb.Append(i), _
            Function(sb) sb.ToString)

        Console.WriteLine(str)
    End Sub
End Module
```

<span data-ttu-id="618a4-109">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="618a4-109">This example produces the following output:</span></span>

```output
Some text that's broken up into multiple segments.
```

## <a name="see-also"></a><span data-ttu-id="618a4-110">Confira também</span><span class="sxs-lookup"><span data-stu-id="618a4-110">See also</span></span>

- <xref:System.Xml.Linq.XContainer.Descendants%2A>
