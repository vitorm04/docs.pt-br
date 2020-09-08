---
title: Como projetar um novo tipo-LINQ to XML
description: Sua consulta pode retornar um IEnumerable de um tipo diferente daqueles comuns. Este artigo mostra como em um exemplo.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 48145cf9-1e0b-4e73-bbfd-28fc04800dc4
ms.openlocfilehash: 15eabf37e23363894ec1ab72e6df6dbe1fd974db
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89551960"
---
# <a name="how-to-project-a-new-type-linq-to-xml"></a><span data-ttu-id="30bc6-104">Como projetar um novo tipo (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="30bc6-104">How to project a new type (LINQ to XML)</span></span>

<span data-ttu-id="30bc6-105">Outros exemplos nesta seção mostraram consultas que os resultados de retorno como <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> de `string`, e <xref:System.Collections.Generic.IEnumerable%601> de `int`.</span><span class="sxs-lookup"><span data-stu-id="30bc6-105">Other examples in this section have shown queries that return results as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> of `string`, and <xref:System.Collections.Generic.IEnumerable%601> of `int`.</span></span> <span data-ttu-id="30bc6-106">Esses são tipos de resultados comuns, mas não são apropriados para todos os cenários.</span><span class="sxs-lookup"><span data-stu-id="30bc6-106">These are common result types, but they're not appropriate for every scenario.</span></span> <span data-ttu-id="30bc6-107">Em muitos casos, você desejará que suas consultas retornem um <xref:System.Collections.Generic.IEnumerable%601> de algum outro tipo.</span><span class="sxs-lookup"><span data-stu-id="30bc6-107">In many cases, you'll want your queries to return an <xref:System.Collections.Generic.IEnumerable%601> of some other type.</span></span>

## <a name="example-define-a-new-type-and-have-the-select-statement-create-an-instance-of-the-type"></a><span data-ttu-id="30bc6-108">Exemplo: definir um novo tipo e fazer com que a `select` instrução crie uma instância do tipo</span><span class="sxs-lookup"><span data-stu-id="30bc6-108">Example: Define a new type and have the `select` statement create an instance of the type</span></span>

<span data-ttu-id="30bc6-109">Este exemplo mostra como instanciar objetos na cláusula `select` .</span><span class="sxs-lookup"><span data-stu-id="30bc6-109">This example shows how to instantiate objects in the `select` clause.</span></span> <span data-ttu-id="30bc6-110">O código primeiro invoca um construtor para definir uma nova classe e, em seguida, modifica a `select` instrução para que a expressão seja uma nova instância da nova classe.</span><span class="sxs-lookup"><span data-stu-id="30bc6-110">The code first invokes a constructor to define a new class, and then modifies the `select` statement so that the expression is a new instance of the new class.</span></span> <span data-ttu-id="30bc6-111">O exemplo usa arquivo XML de exemplo de documento XML [: ordem de compra típica](sample-xml-file-typical-purchase-order.md).</span><span class="sxs-lookup"><span data-stu-id="30bc6-111">The example uses XML document [Sample XML file: Typical purchase order](sample-xml-file-typical-purchase-order.md).</span></span>

```csharp
class NameQty
{
    public string name;
    public int qty;
    public NameQty(string n, int q)
    {
        name = n;
        qty = q;
    }
};

class Program {
    public static void Main()
    {
        XElement po = XElement.Load("PurchaseOrder.xml");

        IEnumerable<NameQty> nqList =
            from n in po.Descendants("Item")
            select new NameQty(
                    (string)n.Element("ProductName"),
                    (int)n.Element("Quantity")
                );

        foreach (NameQty n in nqList)
            Console.WriteLine(n.name + ":" + n.qty);
    }
}
```

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

<span data-ttu-id="30bc6-112">Este exemplo usa o <xref:System.Xml.Linq.XContainer.Element%2A> método que foi introduzido no artigo [como recuperar um único elemento filho](retrieve-single-child-element.md) .</span><span class="sxs-lookup"><span data-stu-id="30bc6-112">This example uses the <xref:System.Xml.Linq.XContainer.Element%2A> method that was introduced in the [How to retrieve a single child element](retrieve-single-child-element.md) article.</span></span> <span data-ttu-id="30bc6-113">Também usa conversões para recuperar os valores dos elementos que são retornados pelo método de <xref:System.Xml.Linq.XContainer.Element%2A> .</span><span class="sxs-lookup"><span data-stu-id="30bc6-113">It also uses casts to retrieve the values of the elements that are returned by the <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span>

<span data-ttu-id="30bc6-114">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="30bc6-114">This example produces the following output:</span></span>

```output
Lawnmower:1
Baby Monitor:2
```

## <a name="see-also"></a><span data-ttu-id="30bc6-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="30bc6-115">See also</span></span>

- [<span data-ttu-id="30bc6-116">Projeções e transformações (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="30bc6-116">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
