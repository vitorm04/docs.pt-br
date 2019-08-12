---
title: 'Como: Localizar um elemento com um atributo específico (C#)'
ms.date: 07/20/2015
ms.assetid: b92591aa-3cfb-490e-99f6-da8de335e362
ms.openlocfilehash: 0362ded5984ff797a1ced93076679b7b975b998c
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68709950"
---
# <a name="how-to-find-an-element-with-a-specific-attribute-c"></a><span data-ttu-id="7e9cc-102">Como: Localizar um elemento com um atributo específico (C#)</span><span class="sxs-lookup"><span data-stu-id="7e9cc-102">How to: Find an Element with a Specific Attribute (C#)</span></span>
<span data-ttu-id="7e9cc-103">Este tópico mostra como localizar um elemento que tem um atributo que tem um valor específico.</span><span class="sxs-lookup"><span data-stu-id="7e9cc-103">This topic shows how to find an element that has an attribute that has a specific value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7e9cc-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7e9cc-104">Example</span></span>  
 <span data-ttu-id="7e9cc-105">O exemplo mostra como localizar o elemento `Address` que tem um atributo `Type` com um valor de “faturamento”.</span><span class="sxs-lookup"><span data-stu-id="7e9cc-105">The example shows how to find the `Address` element that has a `Type` attribute with a value of "Billing".</span></span>  
  
 <span data-ttu-id="7e9cc-106">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: Ordem de compra típica (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="7e9cc-106">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("PurchaseOrder.xml");  
IEnumerable<XElement> address =  
    from el in root.Elements("Address")  
    where (string)el.Attribute("Type") == "Billing"  
    select el;  
foreach (XElement el in address)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="7e9cc-107">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="7e9cc-107">This code produces the following output:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="7e9cc-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7e9cc-108">Example</span></span>  
 <span data-ttu-id="7e9cc-109">O exemplo a seguir mostra a mesma consulta para XML que está em um namespace.</span><span class="sxs-lookup"><span data-stu-id="7e9cc-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="7e9cc-110">Para obter mais informações, consulte [Visão geral de namespaces (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="7e9cc-110">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="7e9cc-111">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: Ordem de compra típica em um namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="7e9cc-111">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="7e9cc-112">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="7e9cc-112">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7e9cc-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7e9cc-113">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [<span data-ttu-id="7e9cc-114">Visão geral de operadores de consulta padrão (C#)</span><span class="sxs-lookup"><span data-stu-id="7e9cc-114">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="7e9cc-115">Operações de projeção (C#)</span><span class="sxs-lookup"><span data-stu-id="7e9cc-115">Projection Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projection-operations.md)
