---
title: 'Como: localizar descendentes com um nome de elemento específico (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 78915518-0d25-4051-ab55-929779989510
ms.openlocfilehash: c6f702c121f6a8b9aa5750b4c5ff70c00e681b82
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33643135"
---
# <a name="how-to-find-descendants-with-a-specific-element-name-visual-basic"></a><span data-ttu-id="a9625-102">Como: localizar descendentes com um nome de elemento específico (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a9625-102">How to: Find Descendants with a Specific Element Name (Visual Basic)</span></span>
<span data-ttu-id="a9625-103">Às vezes, você deseja localizar todos os descendentes com um nome específico.</span><span class="sxs-lookup"><span data-stu-id="a9625-103">Sometimes you want to find all descendants with a particular name.</span></span> <span data-ttu-id="a9625-104">Você poderia escrever um código para iterar por todos os descendentes, mas é mais fácil usar o eixo <xref:System.Xml.Linq.XContainer.Descendants%2A>.</span><span class="sxs-lookup"><span data-stu-id="a9625-104">You could write code to iterate through all of the descendants, but it is easier to use the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a9625-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a9625-105">Example</span></span>  
 <span data-ttu-id="a9625-106">O exemplo a seguir mostra como localizar os descendentes com base no nome do elemento.</span><span class="sxs-lookup"><span data-stu-id="a9625-106">The following example shows how to find descendants based on the element name.</span></span>  
  
```vb  
Dim root As XElement = _  
    <root>  
        <para>  
            <r>  
                <t>Some text </t>  
            </r>  
            <n>  
                <r>  
                    <t>that is broken up into </t>  
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
  
 <span data-ttu-id="a9625-107">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="a9625-107">This code produces the following output:</span></span>  
  
```  
Some text that is broken up into multiple segments.  
```  
  
## <a name="example"></a><span data-ttu-id="a9625-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a9625-108">Example</span></span>  
 <span data-ttu-id="a9625-109">O exemplo a seguir mostra a mesma consulta para XML que está em um namespace.</span><span class="sxs-lookup"><span data-stu-id="a9625-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="a9625-110">Para obter mais informações, consulte [trabalhando com Namespaces de XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="a9625-110">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
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
                            <t>that is broken up into </t>  
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
  
 <span data-ttu-id="a9625-111">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="a9625-111">This code produces the following output:</span></span>  
  
```  
Some text that is broken up into multiple segments.  
```  
  
## <a name="see-also"></a><span data-ttu-id="a9625-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a9625-112">See Also</span></span>  
 <xref:System.Xml.Linq.XContainer.Descendants%2A>  
 [<span data-ttu-id="a9625-113">Consultas básicas (LINQ para XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a9625-113">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
