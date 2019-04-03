---
title: 'Como: Elementos de classificação (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: c2c09279-6c8a-482e-8e71-b1453a815052
ms.openlocfilehash: b6f2e0056582e60066b2c0715a663022b72a6c9c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58841206"
---
# <a name="how-to-sort-elements-visual-basic"></a><span data-ttu-id="e039f-102">Como: Elementos de classificação (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e039f-102">How to: Sort Elements (Visual Basic)</span></span>
<span data-ttu-id="e039f-103">Este exemplo mostra como escrever uma consulta que classifica seus resultados.</span><span class="sxs-lookup"><span data-stu-id="e039f-103">This example shows how to write a query that sorts its results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e039f-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e039f-104">Example</span></span>  
 <span data-ttu-id="e039f-105">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: Dados numéricos (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="e039f-105">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
```vb  
Dim root As XElement = XElement.Load("Data.xml")  
Dim prices As IEnumerable(Of Decimal) = _  
    From el In root.<Data> _  
    Let price = Convert.ToDecimal(el.<Price>.Value) _  
    Order By (price) _  
    Select price  
For Each el As Decimal In prices  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="e039f-106">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="e039f-106">This code produces the following output:</span></span>  
  
```  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="example"></a><span data-ttu-id="e039f-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e039f-107">Example</span></span>  
 <span data-ttu-id="e039f-108">O exemplo a seguir mostra a mesma consulta para XML que está em um namespace.</span><span class="sxs-lookup"><span data-stu-id="e039f-108">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="e039f-109">Para obter mais informações, consulte [trabalhando com Namespaces XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="e039f-109">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="e039f-110">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: Dados numéricos em um namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="e039f-110">This example uses the following XML document: [Sample XML File: Numerical Data in a Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md).</span></span>  
  
```vb  
Imports <xmlns='http://www.adatum.com'>  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = XElement.Load("DataInNamespace.xml")  
        Dim prices As IEnumerable(Of Decimal) = _  
            From el In root.<Data> _  
            Let price = Convert.ToDecimal(el.<Price>.Value) _  
            Order By (price) _  
            Select price  
        For Each el As Decimal In prices  
            Console.WriteLine(el)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="e039f-111">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="e039f-111">This code produces the following output:</span></span>  
  
```  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="see-also"></a><span data-ttu-id="e039f-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e039f-112">See also</span></span>

- [<span data-ttu-id="e039f-113">Classificando Dados</span><span class="sxs-lookup"><span data-stu-id="e039f-113">Sorting Data</span></span>](../../../../visual-basic/programming-guide/concepts/linq/sorting-data.md)
- [<span data-ttu-id="e039f-114">Consultas básicas (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e039f-114">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
