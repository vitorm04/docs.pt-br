---
title: 'Como: calcule valores intermediários (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 933a97b2-dfe7-4f4d-94ad-e6e20df84abd
ms.openlocfilehash: e3aa54c365e90a11ac8c31e0bf7d901c5a4a6b96
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33642470"
---
# <a name="how-to-calculate-intermediate-values-visual-basic"></a><span data-ttu-id="3b810-102">Como: calcule valores intermediários (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3b810-102">How to: Calculate Intermediate Values (Visual Basic)</span></span>
<span data-ttu-id="3b810-103">Este exemplo mostra como calcular valores intermediários que podem ser usados na classificação, filtragem, e em selecionar.</span><span class="sxs-lookup"><span data-stu-id="3b810-103">This example shows how to calculate intermediate values that can be used in sorting, filtering, and selecting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b810-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3b810-104">Example</span></span>  
 <span data-ttu-id="3b810-105">O exemplo a seguir utiliza a cláusula de `Let` .</span><span class="sxs-lookup"><span data-stu-id="3b810-105">The following example uses the `Let` clause.</span></span>  
  
 <span data-ttu-id="3b810-106">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: dados numéricos (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="3b810-106">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
```vb  
Dim root As XElement = XElement.Load("Data.xml")  
Dim extensions As IEnumerable(Of Decimal) = _  
    From el In root.<Data> _  
    Let extension = CDec(el.<Quantity>.Value) * CDec(el.<Price>.Value) _  
    Where extension > 25 _  
    Order By extension _  
    Select extension  
For Each ex As Decimal In extensions  
    Console.WriteLine(ex)  
Next  
```  
  
 <span data-ttu-id="3b810-107">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="3b810-107">This code produces the following output:</span></span>  
  
```  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
  
## <a name="example"></a><span data-ttu-id="3b810-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3b810-108">Example</span></span>  
 <span data-ttu-id="3b810-109">O exemplo a seguir mostra a mesma consulta para XML que está em um namespace.</span><span class="sxs-lookup"><span data-stu-id="3b810-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="3b810-110">Para obter mais informações, consulte [trabalhando com Namespaces de XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="3b810-110">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="3b810-111">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: dados numéricos em um namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="3b810-111">This example uses the following XML document: [Sample XML File: Numerical Data in a Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md).</span></span>  
  
```vb  
Imports <xmlns="http://www.adatum.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = XElement.Load("DataInNamespace.xml")  
        Dim extensions As IEnumerable(Of Decimal) = _  
            From el In root.<Data> _  
            Let extension = CDec(el.<Quantity>.Value) * CDec(el.<Price>.Value) _  
            Where extension > 25 _  
            Order By extension _  
            Select extension  
        For Each ex As Decimal In extensions  
            Console.WriteLine(ex)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="3b810-112">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="3b810-112">This code produces the following output:</span></span>  
  
```  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
  
## <a name="see-also"></a><span data-ttu-id="3b810-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3b810-113">See Also</span></span>  
 [<span data-ttu-id="3b810-114">Consultas básicas (LINQ para XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3b810-114">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
