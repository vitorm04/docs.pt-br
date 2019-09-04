---
title: 'Como: Escrever consultas com filtragem complexa (C#)'
ms.date: 07/20/2015
ms.assetid: 4065d901-cf89-4e47-8bf9-abb65acfb003
ms.openlocfilehash: 7759a02c1b9ef0ae0c1af4bfb2600543b21cdf0f
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253182"
---
# <a name="how-to-write-queries-with-complex-filtering-c"></a><span data-ttu-id="b1b99-102">Como: Escrever consultas com filtragem complexa (C#)</span><span class="sxs-lookup"><span data-stu-id="b1b99-102">How to: Write Queries with Complex Filtering (C#)</span></span>
<span data-ttu-id="b1b99-103">Muitas vezes, você deseja escrever consultas LINQ to XML com filtros complexos.</span><span class="sxs-lookup"><span data-stu-id="b1b99-103">Sometimes you want to write LINQ to XML queries with complex filters.</span></span> <span data-ttu-id="b1b99-104">Por exemplo, você pode ter que localizar todos os elementos que têm um elemento filho com um nome e um valor específicos.</span><span class="sxs-lookup"><span data-stu-id="b1b99-104">For example, you might have to find all elements that have a child element with a particular name and value.</span></span> <span data-ttu-id="b1b99-105">Este tópico dá um exemplo de como escrever uma consulta com filtragem complexa.</span><span class="sxs-lookup"><span data-stu-id="b1b99-105">This topic gives an example of writing a query with complex filtering.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1b99-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b1b99-106">Example</span></span>  
 <span data-ttu-id="b1b99-107">Este exemplo mostra como localizar todos os elementos `PurchaseOrder` que têm um elemento filho `Address` que têm um atributo `Type` igual a “Shipping” e um elemento filho `State` igual a “NY”.</span><span class="sxs-lookup"><span data-stu-id="b1b99-107">This example shows how to find all `PurchaseOrder` elements that have a child `Address` element that has a `Type` attribute equal to "Shipping" and a child `State` element equal to "NY".</span></span> <span data-ttu-id="b1b99-108">Ele usa uma consulta aninhada na cláusula `Where` e o operador `Any` retornará `true` se a coleção tiver elementos nele.</span><span class="sxs-lookup"><span data-stu-id="b1b99-108">It uses a nested query in the `Where` clause, and the `Any` operator returns `true` if the collection has any elements in it.</span></span> <span data-ttu-id="b1b99-109">Para obter informações sobre como usar a sintaxe de consulta baseada em método, consulte [Sintaxe de consulta e sintaxe de método em LINQ](./query-syntax-and-method-syntax-in-linq.md).</span><span class="sxs-lookup"><span data-stu-id="b1b99-109">For information about using method-based query syntax, see [Query Syntax and Method Syntax in LINQ](./query-syntax-and-method-syntax-in-linq.md).</span></span>  
  
 <span data-ttu-id="b1b99-110">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: Várias ordens de compra (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="b1b99-110">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="b1b99-111">Para obter mais informações sobre o operador `Any`, consulte [Operações de quantificador (C#)](./quantifier-operations.md).</span><span class="sxs-lookup"><span data-stu-id="b1b99-111">For more information about the `Any` operator, see [Quantifier Operations (C#)](./quantifier-operations.md).</span></span>  
  
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
  
 <span data-ttu-id="b1b99-112">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="b1b99-112">This code produces the following output:</span></span>  
  
```output  
99505  
```  
  
## <a name="example"></a><span data-ttu-id="b1b99-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b1b99-113">Example</span></span>  
 <span data-ttu-id="b1b99-114">O exemplo a seguir mostra a mesma consulta para XML que está em um namespace.</span><span class="sxs-lookup"><span data-stu-id="b1b99-114">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="b1b99-115">Para obter mais informações, consulte [Visão geral de namespaces (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="b1b99-115">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="b1b99-116">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: Várias ordens de compra em um namespace](./sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="b1b99-116">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders in a Namespace](./sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="b1b99-117">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="b1b99-117">This code produces the following output:</span></span>  
  
```output  
99505  
```  
  
## <a name="see-also"></a><span data-ttu-id="b1b99-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b1b99-118">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [<span data-ttu-id="b1b99-119">Operações de projeção (C#)</span><span class="sxs-lookup"><span data-stu-id="b1b99-119">Projection Operations (C#)</span></span>](./projection-operations.md)
- [<span data-ttu-id="b1b99-120">Operações de quantificador (C#)</span><span class="sxs-lookup"><span data-stu-id="b1b99-120">Quantifier Operations (C#)</span></span>](./quantifier-operations.md)
