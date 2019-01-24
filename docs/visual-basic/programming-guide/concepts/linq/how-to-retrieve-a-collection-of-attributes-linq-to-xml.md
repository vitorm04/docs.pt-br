---
title: 'Como: Recuperar uma coleção de atributos (LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: a07e9645-b45b-403b-b698-f652f904c7d2
ms.openlocfilehash: 691ec9edda6051ba1f598891dfb9331b85ceb278
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54716603"
---
# <a name="how-to-retrieve-a-collection-of-attributes-linq-to-xml-visual-basic"></a><span data-ttu-id="8c059-102">Como: Recuperar uma coleção de atributos (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8c059-102">How to: Retrieve a Collection of Attributes (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="8c059-103">Este tópico apresenta o método de <xref:System.Xml.Linq.XElement.Attributes%2A> .</span><span class="sxs-lookup"><span data-stu-id="8c059-103">This topic introduces the <xref:System.Xml.Linq.XElement.Attributes%2A> method.</span></span> <span data-ttu-id="8c059-104">Esse método recupera os atributos de um elemento.</span><span class="sxs-lookup"><span data-stu-id="8c059-104">This method retrieves the attributes of an element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8c059-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8c059-105">Example</span></span>  
 <span data-ttu-id="8c059-106">O exemplo a seguir mostra como iterar através da coleção de atributos de um elemento.</span><span class="sxs-lookup"><span data-stu-id="8c059-106">The following example shows how to iterate through the collection of attributes of an element.</span></span>  
  
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
  
 <span data-ttu-id="8c059-107">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="8c059-107">This code produces the following output:</span></span>  
  
```  
ID="1243"  
Type="int"  
ConvertableTo="double"  
```  
  
## <a name="see-also"></a><span data-ttu-id="8c059-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8c059-108">See also</span></span>
- [<span data-ttu-id="8c059-109">Eixos LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8c059-109">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
