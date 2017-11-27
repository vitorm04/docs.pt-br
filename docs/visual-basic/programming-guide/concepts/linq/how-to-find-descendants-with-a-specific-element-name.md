---
title: "Como: localizar descendentes com um nome de elemento específico (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 78915518-0d25-4051-ab55-929779989510
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 076a2d6707cf0f09945030cfe75814c195cdd6cd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-find-descendants-with-a-specific-element-name-visual-basic"></a><span data-ttu-id="709c1-102">Como: localizar descendentes com um nome de elemento específico (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="709c1-102">How to: Find Descendants with a Specific Element Name (Visual Basic)</span></span>
<span data-ttu-id="709c1-103">Às vezes, você deseja localizar todos os descendentes com um nome específico.</span><span class="sxs-lookup"><span data-stu-id="709c1-103">Sometimes you want to find all descendants with a particular name.</span></span> <span data-ttu-id="709c1-104">Você poderia escrever um código para iterar por todos os descendentes, mas é mais fácil usar o eixo <xref:System.Xml.Linq.XContainer.Descendants%2A>.</span><span class="sxs-lookup"><span data-stu-id="709c1-104">You could write code to iterate through all of the descendants, but it is easier to use the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis.</span></span>  
  
## <a name="example"></a><span data-ttu-id="709c1-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="709c1-105">Example</span></span>  
 <span data-ttu-id="709c1-106">O exemplo a seguir mostra como localizar os descendentes com base no nome do elemento.</span><span class="sxs-lookup"><span data-stu-id="709c1-106">The following example shows how to find descendants based on the element name.</span></span>  
  
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
  
 <span data-ttu-id="709c1-107">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="709c1-107">This code produces the following output:</span></span>  
  
```  
Some text that is broken up into multiple segments.  
```  
  
## <a name="example"></a><span data-ttu-id="709c1-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="709c1-108">Example</span></span>  
 <span data-ttu-id="709c1-109">O exemplo a seguir mostra a mesma consulta para XML que está em um namespace.</span><span class="sxs-lookup"><span data-stu-id="709c1-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="709c1-110">Para obter mais informações, consulte [trabalhando com Namespaces de XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="709c1-110">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
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
  
 <span data-ttu-id="709c1-111">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="709c1-111">This code produces the following output:</span></span>  
  
```  
Some text that is broken up into multiple segments.  
```  
  
## <a name="see-also"></a><span data-ttu-id="709c1-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="709c1-112">See Also</span></span>  
 <xref:System.Xml.Linq.XContainer.Descendants%2A>  
 [<span data-ttu-id="709c1-113">Consultas básicas (LINQ para XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="709c1-113">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
