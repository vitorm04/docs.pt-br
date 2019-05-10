---
title: 'Como: Filtrar em nomes de elemento (LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: b1437b4a-48aa-4546-834a-d6d3ab015fe1
ms.openlocfilehash: 18b1fff128c648d04f0b1217214d3c055674e5f6
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64614904"
---
# <a name="how-to-filter-on-element-names-linq-to-xml-visual-basic"></a><span data-ttu-id="61b6c-102">Como: Filtrar em nomes de elemento (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="61b6c-102">How to: Filter on Element Names (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="61b6c-103">Quando você chamar um dos métodos que <xref:System.Collections.Generic.IEnumerable%601> de retorno de <xref:System.Xml.Linq.XElement>, você pode filtrar no nome do elemento.</span><span class="sxs-lookup"><span data-stu-id="61b6c-103">When you call one of the methods that return <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, you can filter on the element name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="61b6c-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="61b6c-104">Example</span></span>  
 <span data-ttu-id="61b6c-105">Este exemplo retorna uma coleção de descendentes que é filtrada para conter somente descendentes com o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="61b6c-105">This example retrieves a collection of descendants that is filtered to contain only descendants with the specified name.</span></span>  
  
 <span data-ttu-id="61b6c-106">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: Ordem de compra típica (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="61b6c-106">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span></span>  
  
```vb  
Dim po As XElement = XElement.Load("PurchaseOrder.xml")  
Dim items As IEnumerable(Of XElement) = _  
    From el In po...<ProductName> _  
    Select el  
For Each prdName As XElement In items  
    Console.WriteLine(prdName.Name.ToString & ":" & prdName.Value)  
Next  
```  
  
 <span data-ttu-id="61b6c-107">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="61b6c-107">This code produces the following output:</span></span>  
  
```  
ProductName:Lawnmower  
ProductName:Baby Monitor  
```  
  
 <span data-ttu-id="61b6c-108">Os outros métodos que <xref:System.Collections.Generic.IEnumerable%601> de retorno de coleções de <xref:System.Xml.Linq.XElement> segue o mesmo padrão.</span><span class="sxs-lookup"><span data-stu-id="61b6c-108">The other methods that return <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement> collections follow the same pattern.</span></span> <span data-ttu-id="61b6c-109">Suas assinaturas são semelhantes a <xref:System.Xml.Linq.XContainer.Elements%2A> e a <xref:System.Xml.Linq.XContainer.Descendants%2A>.</span><span class="sxs-lookup"><span data-stu-id="61b6c-109">Their signatures are similar to <xref:System.Xml.Linq.XContainer.Elements%2A> and <xref:System.Xml.Linq.XContainer.Descendants%2A>.</span></span> <span data-ttu-id="61b6c-110">O seguinte é a lista completa dos métodos semelhantes que tenham assinaturas de método:</span><span class="sxs-lookup"><span data-stu-id="61b6c-110">The following is the complete list of methods that have similar method signatures:</span></span>  
  
- <xref:System.Xml.Linq.XNode.Ancestors%2A>  
  
- <xref:System.Xml.Linq.XContainer.Descendants%2A>  
  
- <xref:System.Xml.Linq.XContainer.Elements%2A>  
  
- <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>  
  
- <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>  
  
- <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>  
  
- <xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A>  
  
## <a name="example"></a><span data-ttu-id="61b6c-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="61b6c-111">Example</span></span>  
 <span data-ttu-id="61b6c-112">O exemplo a seguir mostra a mesma consulta para XML que está em um namespace.</span><span class="sxs-lookup"><span data-stu-id="61b6c-112">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="61b6c-113">Para obter mais informações, consulte [trabalhando com Namespaces XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="61b6c-113">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="61b6c-114">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: Ordem de compra típica em um namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="61b6c-114">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim po As XElement = XElement.Load("PurchaseOrderInNamespace.xml")  
        Dim items As IEnumerable(Of XElement) = _  
            From el In po...<aw:ProductName> _  
            Select el  
        For Each prdName As XElement In items  
            Console.WriteLine(prdName.Name.ToString & ":" & prdName.Value)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="61b6c-115">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="61b6c-115">This code produces the following output:</span></span>  
  
```  
{http://www.adventure-works.com}ProductName:Lawnmower  
{http://www.adventure-works.com}ProductName:Baby Monitor  
```  
  
## <a name="see-also"></a><span data-ttu-id="61b6c-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="61b6c-116">See also</span></span>

- [<span data-ttu-id="61b6c-117">Eixos LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="61b6c-117">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
