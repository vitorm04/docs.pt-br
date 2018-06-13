---
title: 'Como: escrever consultas com filtragem complexa (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: bf286ffc-7990-4b00-a4eb-ee3d70129950
ms.openlocfilehash: 500cd9cdc62252eff3addc26006c4ce815ae1b4d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33645857"
---
# <a name="how-to-write-queries-with-complex-filtering-visual-basic"></a><span data-ttu-id="9c372-102">Como: escrever consultas com filtragem complexa (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9c372-102">How to: Write Queries with Complex Filtering (Visual Basic)</span></span>
<span data-ttu-id="9c372-103">Muitas vezes, você deseja escrever consultas LINQ to XML com filtros complexos.</span><span class="sxs-lookup"><span data-stu-id="9c372-103">Sometimes you want to write LINQ to XML queries with complex filters.</span></span> <span data-ttu-id="9c372-104">Por exemplo, você pode ter que localizar todos os elementos que têm um elemento filho com um nome e um valor específicos.</span><span class="sxs-lookup"><span data-stu-id="9c372-104">For example, you might have to find all elements that have a child element with a particular name and value.</span></span> <span data-ttu-id="9c372-105">Este tópico dá um exemplo de como escrever uma consulta com filtragem complexa.</span><span class="sxs-lookup"><span data-stu-id="9c372-105">This topic gives an example of writing a query with complex filtering.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c372-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9c372-106">Example</span></span>  
 <span data-ttu-id="9c372-107">Este exemplo mostra como localizar todos os elementos `PurchaseOrder` que têm um elemento filho `Address` que têm um atributo `Type` igual a “Shipping” e um elemento filho `State` igual a “NY”.</span><span class="sxs-lookup"><span data-stu-id="9c372-107">This example shows how to find all `PurchaseOrder` elements that have a child `Address` element that has a `Type` attribute equal to "Shipping" and a child `State` element equal to "NY".</span></span> <span data-ttu-id="9c372-108">Ele usa uma consulta aninhada na cláusula `Where` e o operador `Any` retornará `True` se a coleção tiver elementos nele.</span><span class="sxs-lookup"><span data-stu-id="9c372-108">It uses a nested query in the `Where` clause, and the `Any` operator returns `True` if the collection has any elements in it.</span></span>  
  
 <span data-ttu-id="9c372-109">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: vários pedidos de compra (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="9c372-109">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="9c372-110">Para obter mais informações sobre o `Any` operador, consulte [operações de quantificador (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md).</span><span class="sxs-lookup"><span data-stu-id="9c372-110">For more information about the `Any` operator, see [Quantifier Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md).</span></span>  
  
```vb  
Dim root As XElement = XElement.Load("PurchaseOrders.xml")  
Dim purchaseOrders As IEnumerable(Of XElement) = _  
    From el In root.<PurchaseOrder> _  
    Where _  
        (From add In el.<Address> _  
        Where _  
             add.@Type = "Shipping" And _  
             add.<State>.Value = "NY" _  
        Select add) _  
    .Any() _  
    Select el  
For Each el As XElement In purchaseOrders  
    Console.WriteLine(el.@PurchaseOrderNumber)  
Next  
```  
  
 <span data-ttu-id="9c372-111">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="9c372-111">This code produces the following output:</span></span>  
  
```  
99505  
```  
  
## <a name="example"></a><span data-ttu-id="9c372-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9c372-112">Example</span></span>  
 <span data-ttu-id="9c372-113">O exemplo a seguir mostra a mesma consulta para XML que está em um namespace.</span><span class="sxs-lookup"><span data-stu-id="9c372-113">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="9c372-114">Para obter mais informações, consulte [trabalhando com Namespaces de XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="9c372-114">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="9c372-115">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: vários pedidos de compra em um namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="9c372-115">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders in a Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span></span>  
  
```vb  
Imports <xmlns:aw='http://www.adventure-works.com'>  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = XElement.Load("PurchaseOrdersInNamespace.xml")  
        Dim purchaseOrders As IEnumerable(Of XElement) = _  
            From el In root.<aw:PurchaseOrder> _  
            Where _  
                (From add In el.<aw:Address> _  
                Where _  
                     add.@aw:Type = "Shipping" And _  
                     add.<aw:State>.Value = "NY" _  
                Select add) _  
            .Any() _  
            Select el  
        For Each el As XElement In purchaseOrders  
            Console.WriteLine(el.@aw:PurchaseOrderNumber)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="9c372-116">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="9c372-116">This code produces the following output:</span></span>  
  
```  
99505  
```  
  
## <a name="see-also"></a><span data-ttu-id="9c372-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9c372-117">See Also</span></span>  
 <xref:System.Xml.Linq.XElement.Attribute%2A>  
 <xref:System.Xml.Linq.XContainer.Elements%2A>  
 [<span data-ttu-id="9c372-118">Consultas básicas (LINQ para XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9c372-118">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)  
 [<span data-ttu-id="9c372-119">Propriedade do Eixo Filho XML</span><span class="sxs-lookup"><span data-stu-id="9c372-119">XML Child Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)  
 [<span data-ttu-id="9c372-120">Propriedade de Eixo do Atributo XML</span><span class="sxs-lookup"><span data-stu-id="9c372-120">XML Attribute Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)  
 [<span data-ttu-id="9c372-121">Propriedade do Valor XML</span><span class="sxs-lookup"><span data-stu-id="9c372-121">XML Value Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)  
 [<span data-ttu-id="9c372-122">Operações de projeção (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9c372-122">Projection Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projection-operations.md)  
 [<span data-ttu-id="9c372-123">Operações de quantificador (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9c372-123">Quantifier Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md)
