---
title: 'Como: Localizar anterior irmãos (XPath-LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 59055718-d0a7-4db3-8901-18dd33587703
ms.openlocfilehash: 4584a84df0e25b451a440c33e17c14cd78fc78bf
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58833003"
---
# <a name="how-to-find-preceding-siblings-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="dd0b7-102">Como: Localizar anterior irmãos (XPath-LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dd0b7-102">How to: Find Preceding Siblings (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="dd0b7-103">Este tópico compara o eixo `preceding-sibling` de XPath ao eixo <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> filho do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dd0b7-103">This topic compares the XPath `preceding-sibling` axis to the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] child <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> axis.</span></span>  
  
 <span data-ttu-id="dd0b7-104">A expressão XPath é:</span><span class="sxs-lookup"><span data-stu-id="dd0b7-104">The XPath expression is:</span></span>  
  
 `preceding-sibling::*`  
  
 <span data-ttu-id="dd0b7-105">Observe que os resultados de ambos <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> e <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> estão na ordem de documento.</span><span class="sxs-lookup"><span data-stu-id="dd0b7-105">Note that the results of both <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> and <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> are in document order.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd0b7-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="dd0b7-106">Example</span></span>  
 <span data-ttu-id="dd0b7-107">O exemplo a seguir localiza o elemento de `FullAddress` , e então recuperar os elementos anteriores usando o eixo de `preceding-sibling` .</span><span class="sxs-lookup"><span data-stu-id="dd0b7-107">The following example finds the `FullAddress` element, and then retrieves the previous elements using the `preceding-sibling` axis.</span></span>  
  
 <span data-ttu-id="dd0b7-108">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: Clientes e ordens (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="dd0b7-108">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span></span>  
  
```vb  
Dim co As XElement = XElement.Load("CustomersOrders.xml")  
Dim add As XElement = co.<Customers>.<Customer>. _  
        <FullAddress>.FirstOrDefault  
  
' LINQ to XML query  
Dim list1 As IEnumerable(Of XElement) = add.ElementsBeforeSelf()  
  
' XPath expression  
Dim list2 As IEnumerable(Of XElement) = add.XPathSelectElements("preceding-sibling::*")  
  
If list1.Count() = list2.Count() And _  
        list1.Intersect(list2).Count() = list1.Count() Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
For Each el As XElement In list2  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="dd0b7-109">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="dd0b7-109">This example produces the following output:</span></span>  
  
```  
Results are identical  
<CompanyName>Great Lakes Food Market</CompanyName>  
<ContactName>Howard Snyder</ContactName>  
<ContactTitle>Marketing Manager</ContactTitle>  
<Phone>(503) 555-7555</Phone>  
```  
  
## <a name="see-also"></a><span data-ttu-id="dd0b7-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dd0b7-110">See also</span></span>

- [<span data-ttu-id="dd0b7-111">LINQ to XML para os usuários do XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dd0b7-111">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
