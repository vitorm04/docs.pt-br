---
title: Como encadear chamadas de método de eixo (LINQ to XMLC#) ()
ms.date: 07/20/2015
ms.assetid: 067e6da2-ee32-486d-803c-e611b328e39a
ms.openlocfilehash: ccfbf516a7fddbef357bfb0072288e250768616b
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141437"
---
# <a name="how-to-chain-axis-method-calls-linq-to-xml-c"></a><span data-ttu-id="d4cad-102">Como encadear chamadas de método de eixo (LINQ to XMLC#) ()</span><span class="sxs-lookup"><span data-stu-id="d4cad-102">How to chain axis method calls (LINQ to XML) (C#)</span></span>
<span data-ttu-id="d4cad-103">Um padrão comum que você usar em seu código é chamar um método do eixo, então chama um dos eixos do método de extensão.</span><span class="sxs-lookup"><span data-stu-id="d4cad-103">A common pattern that you will use in your code is to call an axis method, then call one of the extension method axes.</span></span>  
  
 <span data-ttu-id="d4cad-104">Há dois eixos com o nome de `Elements` que retornam uma coleção de elementos: o método de <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> e o método de <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="d4cad-104">There are two axes with the name of `Elements` that return a collection of elements: the <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> method and the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="d4cad-105">Você pode combinar esses dois eixos para localizar todos os elementos de um nome especificado em uma determinada profundidade na árvore.</span><span class="sxs-lookup"><span data-stu-id="d4cad-105">You can combine these two axes to find all elements of a specified name at a given depth in the tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d4cad-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d4cad-106">Example</span></span>  
 <span data-ttu-id="d4cad-107">Este exemplo usa <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> e <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> para localizar todos os elementos de `Name` em todos os elementos de `Address` em todos os elementos de `PurchaseOrder` .</span><span class="sxs-lookup"><span data-stu-id="d4cad-107">This example uses <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> and <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> to find all `Name` elements in all `Address` elements in all `PurchaseOrder` elements.</span></span>  
  
 <span data-ttu-id="d4cad-108">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: vários pedidos de compra (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="d4cad-108">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
```csharp  
XElement purchaseOrders = XElement.Load("PurchaseOrders.xml");  
IEnumerable<XElement> names =  
    from el in purchaseOrders  
        .Elements("PurchaseOrder")  
        .Elements("Address")  
        .Elements("Name")  
    select el;  
foreach (XElement e in names)  
    Console.WriteLine(e);  
```  
  
 <span data-ttu-id="d4cad-109">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="d4cad-109">This example produces the following output:</span></span>  
  
```xml  
<Name>Ellen Adams</Name>  
<Name>Tai Yee</Name>  
<Name>Cristian Osorio</Name>  
<Name>Cristian Osorio</Name>  
<Name>Jessica Arnold</Name>  
<Name>Jessica Arnold</Name>  
```  
  
 <span data-ttu-id="d4cad-110">Isto funciona porque uma das implementações do eixo de `Elements` é como um método de extensão em <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="d4cad-110">This works because one of the implementations of the `Elements` axis is as an extension method on <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XContainer>.</span></span> <span data-ttu-id="d4cad-111"><xref:System.Xml.Linq.XElement> deriva de <xref:System.Xml.Linq.XContainer>, então você pode chamar o método de <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> nos resultados de uma chamada para o método de <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="d4cad-111"><xref:System.Xml.Linq.XElement> derives from <xref:System.Xml.Linq.XContainer>, so you can call the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> method on the results of a call to the <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d4cad-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d4cad-112">Example</span></span>  
 <span data-ttu-id="d4cad-113">Às vezes você deseja recuperar todos os elementos em uma profundidade específico do elemento quando pode ou não pode haver ancestrais interveniente.</span><span class="sxs-lookup"><span data-stu-id="d4cad-113">Sometimes you want to retrieve all elements at a particular element depth when there might or might not be intervening ancestors.</span></span> <span data-ttu-id="d4cad-114">Por exemplo, o seguinte documento, você pode desejar recuperar todos os elementos de `ConfigParameter` que são filhos do elemento de `Customer` , mas não `ConfigParameter` que é um filho do elemento de `Root` .</span><span class="sxs-lookup"><span data-stu-id="d4cad-114">For example, in the following document, you might want to retrieve all the `ConfigParameter` elements that are children of the `Customer` element, but not the `ConfigParameter` that is a child of the `Root` element.</span></span>  
  
```xml  
<Root>  
  <ConfigParameter>RootConfigParameter</ConfigParameter>  
  <Customer>  
    <Name>Frank</Name>  
    <Config>  
      <ConfigParameter>FirstConfigParameter</ConfigParameter>  
    </Config>  
  </Customer>  
  <Customer>  
    <Name>Bob</Name>  
    <!--This customer doesn't have a Config element-->  
  </Customer>  
  <Customer>  
    <Name>Bill</Name>  
    <Config>  
      <ConfigParameter>SecondConfigParameter</ConfigParameter>  
    </Config>  
  </Customer>  
</Root>  
```  
  
 <span data-ttu-id="d4cad-115">Para fazer isso, você pode usar o eixo de <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> , como segue:</span><span class="sxs-lookup"><span data-stu-id="d4cad-115">To do this, you can use the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> axis, as follows:</span></span>  
  
```csharp  
XElement root = XElement.Load("Irregular.xml");  
IEnumerable<XElement> configParameters =   
    root.Elements("Customer").Elements("Config").  
    Elements("ConfigParameter");  
foreach (XElement cp in configParameters)  
    Console.WriteLine(cp);  
```  
  
 <span data-ttu-id="d4cad-116">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="d4cad-116">This example produces the following output:</span></span>  
  
```xml  
<ConfigParameter>FirstConfigParameter</ConfigParameter>  
<ConfigParameter>SecondConfigParameter</ConfigParameter>  
```  
  
## <a name="example"></a><span data-ttu-id="d4cad-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d4cad-117">Example</span></span>  
 <span data-ttu-id="d4cad-118">O exemplo a seguir mostra a mesma técnica para XML que é em um namespace.</span><span class="sxs-lookup"><span data-stu-id="d4cad-118">The following example shows the same technique for XML that is in a namespace.</span></span> <span data-ttu-id="d4cad-119">Para obter mais informações, consulte [Visão geral de namespaces (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="d4cad-119">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="d4cad-120">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: vários pedidos de compra em um namespace](./sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="d4cad-120">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders in a Namespace](./sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement purchaseOrders = XElement.Load("PurchaseOrdersInNamespace.xml");  
IEnumerable<XElement> names =  
    from el in purchaseOrders  
        .Elements(aw + "PurchaseOrder")  
        .Elements(aw + "Address")  
        .Elements(aw + "Name")  
    select el;  
foreach (XElement e in names)  
    Console.WriteLine(e);  
```  
  
 <span data-ttu-id="d4cad-121">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="d4cad-121">This example produces the following output:</span></span>  
  
```xml  
<aw:Name xmlns:aw="http://www.adventure-works.com">Ellen Adams</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Tai Yee</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d4cad-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d4cad-122">See also</span></span>

- [<span data-ttu-id="d4cad-123">Eixos do LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="d4cad-123">LINQ to XML Axes (C#)</span></span>](linq-to-xml-axes-overview.md)
