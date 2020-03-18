---
title: Como encontrar um elemento com um atributo específico (C#)
ms.date: 07/20/2015
ms.assetid: b92591aa-3cfb-490e-99f6-da8de335e362
ms.openlocfilehash: 106885b8658c493caab3101e6b4ce921589076eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141155"
---
# <a name="how-to-find-an-element-with-a-specific-attribute-c"></a><span data-ttu-id="95c86-102">Como encontrar um elemento com um atributo específico (C#)</span><span class="sxs-lookup"><span data-stu-id="95c86-102">How to find an element with a specific attribute (C#)</span></span>
<span data-ttu-id="95c86-103">Este tópico mostra como localizar um elemento que tem um atributo que tem um valor específico.</span><span class="sxs-lookup"><span data-stu-id="95c86-103">This topic shows how to find an element that has an attribute that has a specific value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="95c86-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="95c86-104">Example</span></span>  
 <span data-ttu-id="95c86-105">O exemplo mostra como localizar o elemento `Address` que tem um atributo `Type` com um valor de “faturamento”.</span><span class="sxs-lookup"><span data-stu-id="95c86-105">The example shows how to find the `Address` element that has a `Type` attribute with a value of "Billing".</span></span>  
  
 <span data-ttu-id="95c86-106">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: ordem de compra típica (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="95c86-106">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("PurchaseOrder.xml");  
IEnumerable<XElement> address =  
    from el in root.Elements("Address")  
    where (string)el.Attribute("Type") == "Billing"  
    select el;  
foreach (XElement el in address)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="95c86-107">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="95c86-107">This code produces the following output:</span></span>  
  
```xml  
<Address Type="Billing">  
  <Name>Tai Yee</Name>  
  <Street>8 Oak Avenue</Street>  
  <City>Old Town</City>  
  <State>PA</State>  
  <Zip>95819</Zip>  
  <Country>USA</Country>  
</Address>  
```  
  
## <a name="example"></a><span data-ttu-id="95c86-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="95c86-108">Example</span></span>  
 <span data-ttu-id="95c86-109">O exemplo a seguir mostra a mesma consulta para XML que está em um namespace.</span><span class="sxs-lookup"><span data-stu-id="95c86-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="95c86-110">Para obter mais informações, consulte [Visão geral de namespaces (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="95c86-110">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="95c86-111">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: ordem de compra típica em um namespace](./sample-xml-file-typical-purchase-order-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="95c86-111">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](./sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("PurchaseOrderInNamespace.xml");  
XNamespace aw = "http://www.adventure-works.com";  
IEnumerable<XElement> address =  
    from el in root.Elements(aw + "Address")  
    where (string)el.Attribute(aw + "Type") == "Billing"  
    select el;  
foreach (XElement el in address)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="95c86-112">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="95c86-112">This code produces the following output:</span></span>  
  
```xml  
<aw:Address aw:Type="Billing" xmlns:aw="http://www.adventure-works.com">  
  <aw:Name>Tai Yee</aw:Name>  
  <aw:Street>8 Oak Avenue</aw:Street>  
  <aw:City>Old Town</aw:City>  
  <aw:State>PA</aw:State>  
  <aw:Zip>95819</aw:Zip>  
  <aw:Country>USA</aw:Country>  
</aw:Address>  
```  
  
## <a name="see-also"></a><span data-ttu-id="95c86-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="95c86-113">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [<span data-ttu-id="95c86-114">Visão geral de operadores de consulta padrão (C#)</span><span class="sxs-lookup"><span data-stu-id="95c86-114">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="95c86-115">Operações de projeção (C#)</span><span class="sxs-lookup"><span data-stu-id="95c86-115">Projection Operations (C#)</span></span>](./projection-operations.md)
