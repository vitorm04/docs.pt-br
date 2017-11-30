---
title: 'Como: projeta um novo tipo (LINQ para XML) (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8cfb24f5-89b2-4cfb-b85d-e7963f8f1845
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 73b677e45be1d457d54de01331c93f60348e6bfd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-project-a-new-type-linq-to-xml-visual-basic"></a><span data-ttu-id="9a9c6-102">Como: projeta um novo tipo (LINQ para XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9a9c6-102">How to: Project a New Type (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="9a9c6-103">Outros exemplos nesta seção mostraram consultas que os resultados de retorno como <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> de `string`, e <xref:System.Collections.Generic.IEnumerable%601> de `int`.</span><span class="sxs-lookup"><span data-stu-id="9a9c6-103">Other examples in this section have shown queries that return results as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> of `string`, and <xref:System.Collections.Generic.IEnumerable%601> of `int`.</span></span> <span data-ttu-id="9a9c6-104">Esses são tipos comuns de resultado, mas não são adequados para cada cenário.</span><span class="sxs-lookup"><span data-stu-id="9a9c6-104">These are common result types, but they are not appropriate for every scenario.</span></span> <span data-ttu-id="9a9c6-105">Em muitos casos você desejará suas consultas para retornar <xref:System.Collections.Generic.IEnumerable%601> de qualquer outro tipo.</span><span class="sxs-lookup"><span data-stu-id="9a9c6-105">In many cases you will want your queries to return an <xref:System.Collections.Generic.IEnumerable%601> of some other type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a9c6-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9a9c6-106">Example</span></span>  
 <span data-ttu-id="9a9c6-107">Este exemplo mostra como instanciar objetos na cláusula `Select` .</span><span class="sxs-lookup"><span data-stu-id="9a9c6-107">This example shows how to instantiate objects in the `Select` clause.</span></span> <span data-ttu-id="9a9c6-108">O código define primeiro uma nova classe com um construtor, e altera a declaração de `Select` de modo que a expressão é uma nova instância da nova classe.</span><span class="sxs-lookup"><span data-stu-id="9a9c6-108">The code first defines a new class with a constructor, and then modifies the `Select` statement so that the expression is a new instance of the new class.</span></span>  
  
 <span data-ttu-id="9a9c6-109">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: ordem de compra típica (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="9a9c6-109">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span></span>  
  
```vb  
Public Class NameQty  
    Public name As String  
    Public qty As Integer  
    Public Sub New(ByVal n As String, ByVal q As Integer)  
        name = n  
        qty = q  
    End Sub  
End Class  
  
Public Class Program  
    Shared Sub Main()  
        Dim po As XElement = XElement.Load("PurchaseOrder.xml")  
  
        Dim nqList As IEnumerable(Of NameQty) = _  
            From n In po...<Item> _  
            Select New NameQty( _  
                n.<ProductName>.Value, CInt(n.<Quantity>.Value))  
  
        For Each n As NameQty In nqList  
            Console.WriteLine(n.name & ":" & n.qty)  
        Next  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="9a9c6-110">Este exemplo usa o `M:System.Xml.Linq.XElement.Element` método foi introduzido no tópico [como: recuperar um único elemento filho (LINQ para XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-single-child-element-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="9a9c6-110">This example uses the `M:System.Xml.Linq.XElement.Element` method that was introduced in the topic [How to: Retrieve a Single Child Element (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-single-child-element-linq-to-xml.md).</span></span> <span data-ttu-id="9a9c6-111">Também usa conversões para recuperar os valores dos elementos que são retornados pelo método de `M:System.Xml.Linq.XElement.Element` .</span><span class="sxs-lookup"><span data-stu-id="9a9c6-111">It also uses casts to retrieve the values of the elements that are returned by the `M:System.Xml.Linq.XElement.Element` method.</span></span>  
  
 <span data-ttu-id="9a9c6-112">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="9a9c6-112">This example produces the following output:</span></span>  
  
```  
Lawnmower:1  
Baby Monitor:2  
```  
  
## <a name="see-also"></a><span data-ttu-id="9a9c6-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9a9c6-113">See Also</span></span>  
 [<span data-ttu-id="9a9c6-114">Projeções e transformações (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9a9c6-114">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
