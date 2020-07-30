---
title: Como escrever consultas com filtragem complexa (C#)
description: Saiba como escrever LINQ to XML consultas com filtros complexos. Consulte exemplos de código e exiba recursos adicionais.
ms.date: 07/20/2015
ms.assetid: 4065d901-cf89-4e47-8bf9-abb65acfb003
ms.openlocfilehash: 5d2c1aafc210b35d4d6b1f1b2d74b11966d90c80
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303420"
---
# <a name="how-to-write-queries-with-complex-filtering-c"></a><span data-ttu-id="83b01-104">Como escrever consultas com filtragem complexa (C#)</span><span class="sxs-lookup"><span data-stu-id="83b01-104">How to write queries with complex filtering (C#)</span></span>
<span data-ttu-id="83b01-105">Muitas vezes, você deseja escrever consultas LINQ to XML com filtros complexos.</span><span class="sxs-lookup"><span data-stu-id="83b01-105">Sometimes you want to write LINQ to XML queries with complex filters.</span></span> <span data-ttu-id="83b01-106">Por exemplo, você pode ter que localizar todos os elementos que têm um elemento filho com um nome e um valor específicos.</span><span class="sxs-lookup"><span data-stu-id="83b01-106">For example, you might have to find all elements that have a child element with a particular name and value.</span></span> <span data-ttu-id="83b01-107">Este tópico dá um exemplo de como escrever uma consulta com filtragem complexa.</span><span class="sxs-lookup"><span data-stu-id="83b01-107">This topic gives an example of writing a query with complex filtering.</span></span>  
  
## <a name="example"></a><span data-ttu-id="83b01-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="83b01-108">Example</span></span>  
 <span data-ttu-id="83b01-109">Este exemplo mostra como localizar todos os elementos `PurchaseOrder` que têm um elemento filho `Address` que têm um atributo `Type` igual a “Shipping” e um elemento filho `State` igual a “NY”.</span><span class="sxs-lookup"><span data-stu-id="83b01-109">This example shows how to find all `PurchaseOrder` elements that have a child `Address` element that has a `Type` attribute equal to "Shipping" and a child `State` element equal to "NY".</span></span> <span data-ttu-id="83b01-110">Ele usa uma consulta aninhada na cláusula `Where` e o operador `Any` retornará `true` se a coleção tiver elementos nele.</span><span class="sxs-lookup"><span data-stu-id="83b01-110">It uses a nested query in the `Where` clause, and the `Any` operator returns `true` if the collection has any elements in it.</span></span> <span data-ttu-id="83b01-111">Para obter informações sobre como usar a sintaxe de consulta baseada em método, consulte [Sintaxe de consulta e sintaxe de método em LINQ](./query-syntax-and-method-syntax-in-linq.md).</span><span class="sxs-lookup"><span data-stu-id="83b01-111">For information about using method-based query syntax, see [Query Syntax and Method Syntax in LINQ](./query-syntax-and-method-syntax-in-linq.md).</span></span>  
  
 <span data-ttu-id="83b01-112">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: vários pedidos de compra (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="83b01-112">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="83b01-113">Para obter mais informações sobre o operador `Any`, consulte [Operações de quantificador (C#)](./quantifier-operations.md).</span><span class="sxs-lookup"><span data-stu-id="83b01-113">For more information about the `Any` operator, see [Quantifier Operations (C#)](./quantifier-operations.md).</span></span>  
  
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
  
 <span data-ttu-id="83b01-114">Este código produz a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="83b01-114">This code produces the following output:</span></span>  
  
```output  
99505  
```  
  
## <a name="example"></a><span data-ttu-id="83b01-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="83b01-115">Example</span></span>  
 <span data-ttu-id="83b01-116">O exemplo a seguir mostra a mesma consulta para XML que está em um namespace.</span><span class="sxs-lookup"><span data-stu-id="83b01-116">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="83b01-117">Para obter mais informações, consulte [Visão geral de namespaces (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="83b01-117">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="83b01-118">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: vários pedidos de compra em um namespace](./sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="83b01-118">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders in a Namespace](./sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="83b01-119">Este código produz a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="83b01-119">This code produces the following output:</span></span>  
  
```output  
99505  
```  
  
## <a name="see-also"></a><span data-ttu-id="83b01-120">Veja também</span><span class="sxs-lookup"><span data-stu-id="83b01-120">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [<span data-ttu-id="83b01-121">Operações de projeção (C#)</span><span class="sxs-lookup"><span data-stu-id="83b01-121">Projection Operations (C#)</span></span>](./projection-operations.md)
- [<span data-ttu-id="83b01-122">Operações de quantificador (C#)</span><span class="sxs-lookup"><span data-stu-id="83b01-122">Quantifier Operations (C#)</span></span>](./quantifier-operations.md)
