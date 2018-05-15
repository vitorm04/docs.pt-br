---
title: 'Como: recuperar uma coleção de atributos (LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: a07e9645-b45b-403b-b698-f652f904c7d2
ms.openlocfilehash: fdb7f236339de242a887f3040e33b8d24eb114f4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-retrieve-a-collection-of-attributes-linq-to-xml-visual-basic"></a><span data-ttu-id="c4a12-102">Como: recuperar uma coleção de atributos (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c4a12-102">How to: Retrieve a Collection of Attributes (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="c4a12-103">Este tópico apresenta o método de <xref:System.Xml.Linq.XElement.Attributes%2A> .</span><span class="sxs-lookup"><span data-stu-id="c4a12-103">This topic introduces the <xref:System.Xml.Linq.XElement.Attributes%2A> method.</span></span> <span data-ttu-id="c4a12-104">Esse método recupera os atributos de um elemento.</span><span class="sxs-lookup"><span data-stu-id="c4a12-104">This method retrieves the attributes of an element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4a12-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c4a12-105">Example</span></span>  
 <span data-ttu-id="c4a12-106">O exemplo a seguir mostra como iterar através da coleção de atributos de um elemento.</span><span class="sxs-lookup"><span data-stu-id="c4a12-106">The following example shows how to iterate through the collection of attributes of an element.</span></span>  
  
```vb  
Dim val = _  
    <Value ID="1243" Type="int" ConvertableTo="double">100</Value>  
Dim listOfAttributes As IEnumerable(Of XAttribute) = _  
    From att In val.Attributes() _  
    Select att  
For Each att As XAttribute In listOfAttributes  
    Console.WriteLine(att)  
Next  
```  
  
 <span data-ttu-id="c4a12-107">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="c4a12-107">This code produces the following output:</span></span>  
  
```  
ID="1243"  
Type="int"  
ConvertableTo="double"  
```  
  
## <a name="see-also"></a><span data-ttu-id="c4a12-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c4a12-108">See Also</span></span>  
 [<span data-ttu-id="c4a12-109">Eixos LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c4a12-109">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
