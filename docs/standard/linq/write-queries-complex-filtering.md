---
title: Como escrever consultas com filtragem complexa-LINQ to XML
description: Muitas vezes, você deseja escrever consultas LINQ to XML com filtros complexos. Por exemplo, você pode ter que localizar todos os elementos que têm um elemento filho com um nome e um valor específicos.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 4065d901-cf89-4e47-8bf9-abb65acfb003
ms.openlocfilehash: c5e7f812364e7e96e3a4b8f5515d07a3524ec979
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552317"
---
# <a name="how-to-write-queries-with-complex-filtering-linq-to-xml"></a><span data-ttu-id="a804b-104">Como escrever consultas com filtragem complexa (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="a804b-104">How to write queries with complex filtering (LINQ to XML)</span></span>

<span data-ttu-id="a804b-105">Muitas vezes, você deseja escrever consultas LINQ to XML com filtros complexos.</span><span class="sxs-lookup"><span data-stu-id="a804b-105">Sometimes you want to write LINQ to XML queries with complex filters.</span></span> <span data-ttu-id="a804b-106">Por exemplo, você pode ter que localizar todos os elementos que têm um elemento filho com um nome e um valor específicos.</span><span class="sxs-lookup"><span data-stu-id="a804b-106">For example, you might have to find all elements that have a child element with a particular name and value.</span></span> <span data-ttu-id="a804b-107">Este artigo fornece um exemplo de como escrever uma consulta com filtragem complexa.</span><span class="sxs-lookup"><span data-stu-id="a804b-107">This article gives an example of writing a query with complex filtering.</span></span>

## <a name="example-find-with-a-nested-query-in-the-where-clause"></a><span data-ttu-id="a804b-108">Exemplo: localizar com uma consulta aninhada na `Where` cláusula</span><span class="sxs-lookup"><span data-stu-id="a804b-108">Example: Find with a nested query in the `Where` clause</span></span>

<span data-ttu-id="a804b-109">Este exemplo mostra como localizar todos os `PurchaseOrder` elementos que têm:</span><span class="sxs-lookup"><span data-stu-id="a804b-109">This example shows how to find all `PurchaseOrder` elements that have:</span></span>

- <span data-ttu-id="a804b-110">Um `Address` elemento filho cujo `Type` atributo é igual a "Shipping".</span><span class="sxs-lookup"><span data-stu-id="a804b-110">A child `Address` element whose `Type` attribute equals "Shipping".</span></span>
- <span data-ttu-id="a804b-111">Um `State` elemento filho que é igual a "NY".</span><span class="sxs-lookup"><span data-stu-id="a804b-111">A child `State` element that equals "NY".</span></span>

<span data-ttu-id="a804b-112">Ele usa uma consulta aninhada na cláusula `Where` e o operador `Any` retornará `true` se a coleção tiver elementos nele.</span><span class="sxs-lookup"><span data-stu-id="a804b-112">It uses a nested query in the `Where` clause, and the `Any` operator returns `true` if the collection has any elements in it.</span></span> <span data-ttu-id="a804b-113">O exemplo usa arquivo XML de exemplo de documento XML [: várias ordens de compra](sample-xml-file-multiple-purchase-orders.md).</span><span class="sxs-lookup"><span data-stu-id="a804b-113">The example uses XML document [Sample XML file: Multiple purchase orders](sample-xml-file-multiple-purchase-orders.md).</span></span>

<span data-ttu-id="a804b-114">Para obter mais informações sobre o `Any` operador, consulte [operações do quantificador (C#)](../../../docs/csharp/programming-guide/concepts/linq/quantifier-operations.md) e [operações do quantificador (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md).</span><span class="sxs-lookup"><span data-stu-id="a804b-114">For more information about the `Any` operator, see [Quantifier Operations (C#)](../../../docs/csharp/programming-guide/concepts/linq/quantifier-operations.md) and [Quantifier Operations (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md).</span></span>

```csharp
XElement root = XElement.Load("PurchaseOrders.xml");
IEnumerable<XElement> purchaseOrders =
    from el in root.Elements("PurchaseOrder")
    where
        (from add in el.Elements("Address")
        where
            (string)add.Attribute("Type") == "Shipping" &&
            (string)add.Element("State") == "NY"
        select add)
        .Any()
    select el;
foreach (XElement el in purchaseOrders)
    Console.WriteLine((string)el.Attribute("PurchaseOrderNumber"));
```

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

<span data-ttu-id="a804b-115">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="a804b-115">This example produces the following output:</span></span>

```output
99505
```

## <a name="example-find-in-xml-thats-in-a-namespace"></a><span data-ttu-id="a804b-116">Exemplo: Localizar em XML que está em um namespace</span><span class="sxs-lookup"><span data-stu-id="a804b-116">Example: Find in XML that's in a namespace</span></span>

<span data-ttu-id="a804b-117">O exemplo a seguir mostra a mesma consulta como acima, mas para XML que está em um namespace.</span><span class="sxs-lookup"><span data-stu-id="a804b-117">The following example shows the same query as above, but for XML that's in a namespace.</span></span> <span data-ttu-id="a804b-118">Para obter mais informações, consulte [visão geral de namespaces](namespaces-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a804b-118">For more information, see [Namespaces overview](namespaces-overview.md).</span></span>

<span data-ttu-id="a804b-119">Este exemplo usa arquivo XML de exemplo de documento XML [: várias ordens de compra em um namespace](sample-xml-file-multiple-purchase-orders-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="a804b-119">This example uses XML document [Sample XML file: Multiple purchase orders in a namespace](sample-xml-file-multiple-purchase-orders-namespace.md).</span></span>

```csharp
XElement root = XElement.Load("PurchaseOrdersInNamespace.xml");
XNamespace aw = "http://www.adventure-works.com";
IEnumerable<XElement> purchaseOrders =
    from el in root.Elements(aw + "PurchaseOrder")
    where
        (from add in el.Elements(aw + "Address")
         where
             (string)add.Attribute(aw + "Type") == "Shipping" &&
             (string)add.Element(aw + "State") == "NY"
         select add)
        .Any()
    select el;
foreach (XElement el in purchaseOrders)
    Console.WriteLine((string)el.Attribute(aw + "PurchaseOrderNumber"));
```

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

<span data-ttu-id="a804b-120">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="a804b-120">This example produces the following output:</span></span>

```output
99505
```

## <a name="see-also"></a><span data-ttu-id="a804b-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="a804b-121">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [<span data-ttu-id="a804b-122">Operações de projeção (C#)</span><span class="sxs-lookup"><span data-stu-id="a804b-122">Projection Operations (C#)</span></span>](../../csharp/programming-guide/concepts/linq/projection-operations.md)
- [<span data-ttu-id="a804b-123">Operações de quantificador (C#)</span><span class="sxs-lookup"><span data-stu-id="a804b-123">Quantifier Operations (C#)</span></span>](../../csharp/programming-guide/concepts/linq/quantifier-operations.md)
- [<span data-ttu-id="a804b-124">Propriedade do eixo filho XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a804b-124">XML Child Axis Property (Visual Basic)</span></span>](../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)
- [<span data-ttu-id="a804b-125">Propriedade de eixo do atributo XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a804b-125">XML Attribute Axis Property (Visual Basic)</span></span>](../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)
- [<span data-ttu-id="a804b-126">Propriedade do valor XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a804b-126">XML Value Property (Visual Basic)</span></span>](../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [<span data-ttu-id="a804b-127">Operações de projeção (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a804b-127">Projection Operations (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/projection-operations.md)
- [<span data-ttu-id="a804b-128">Operações do quantificador (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a804b-128">Quantifier Operations (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md)
