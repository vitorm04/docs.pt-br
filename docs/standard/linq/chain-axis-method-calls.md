---
title: Como encadear chamadas de método de eixo-LINQ to XML
description: Saiba como usar os métodos XContainer. Elements e Extensions. Elements para localizar todos os elementos de um nome especificado em uma determinada profundidade na árvore.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 067e6da2-ee32-486d-803c-e611b328e39a
ms.openlocfilehash: 23d3b5a3dacbc56a570a92178cb8e28482907ca1
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552018"
---
# <a name="how-to-chain-axis-method-calls-linq-to-xml"></a><span data-ttu-id="397ad-103">Como encadear chamadas de método do eixo (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="397ad-103">How to chain axis method calls (LINQ to XML)</span></span>

<span data-ttu-id="397ad-104">Um padrão comum que você usar em seu código é chamar um método do eixo, então chama um dos eixos do método de extensão.</span><span class="sxs-lookup"><span data-stu-id="397ad-104">A common pattern that you will use in your code is to call an axis method, then call one of the extension method axes.</span></span>

<span data-ttu-id="397ad-105">Há dois eixos com o nome de `Elements` que retornam uma coleção de elementos: o método de <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> e o método de <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="397ad-105">There are two axes with the name of `Elements` that return a collection of elements: the <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> method and the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="397ad-106">Você pode combinar esses dois eixos para localizar todos os elementos de um nome especificado em uma determinada profundidade na árvore.</span><span class="sxs-lookup"><span data-stu-id="397ad-106">You can combine these two axes to find all elements of a specified name at a given depth in the tree.</span></span>

## <a name="example-retrieve-all-name-elements"></a><span data-ttu-id="397ad-107">Exemplo: recuperar todos os elementos de nome</span><span class="sxs-lookup"><span data-stu-id="397ad-107">Example: Retrieve all name elements</span></span>

<span data-ttu-id="397ad-108">Este exemplo usa <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> e <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> para recuperar todos os elementos em todos os elementos `Name` `Address` de todos os elementos `PurchaseOrder` .</span><span class="sxs-lookup"><span data-stu-id="397ad-108">This example uses <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> and <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> to retrieve all `Name` elements in all `Address` elements in all `PurchaseOrder` elements.</span></span>

<span data-ttu-id="397ad-109">Este exemplo usa arquivo XML de exemplo de documento XML [: várias ordens de compra](sample-xml-file-multiple-purchase-orders.md).</span><span class="sxs-lookup"><span data-stu-id="397ad-109">This example uses XML document [Sample XML file: Multiple purchase orders](sample-xml-file-multiple-purchase-orders.md).</span></span>

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

```vb
Dim purchaseOrders As XElement = XElement.Load("PurchaseOrders.xml")
Dim names As IEnumerable(Of XElement) = _
    From el In purchaseOrders.<PurchaseOrder>.<Address>.<Name> _
    Select el
For Each e As XElement In names
    Console.WriteLine(e)
Next
```

<span data-ttu-id="397ad-110">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="397ad-110">This example produces the following output:</span></span>

```xml
<Name>Ellen Adams</Name>
<Name>Tai Yee</Name>
<Name>Cristian Osorio</Name>
<Name>Cristian Osorio</Name>
<Name>Jessica Arnold</Name>
<Name>Jessica Arnold</Name>
```

<span data-ttu-id="397ad-111">Isto funciona porque uma das implementações do eixo de `Elements` é como um método de extensão em <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="397ad-111">This works because one of the implementations of the `Elements` axis is as an extension method on <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XContainer>.</span></span> <span data-ttu-id="397ad-112"><xref:System.Xml.Linq.XElement> deriva de <xref:System.Xml.Linq.XContainer>, então você pode chamar o método de <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> nos resultados de uma chamada para o método de <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="397ad-112"><xref:System.Xml.Linq.XElement> derives from <xref:System.Xml.Linq.XContainer>, so you can call the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> method on the results of a call to the <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> method.</span></span>

## <a name="example-retrieve-all-elements-at-a-particular-depth"></a><span data-ttu-id="397ad-113">Exemplo: recuperar todos os elementos em uma determinada profundidade</span><span class="sxs-lookup"><span data-stu-id="397ad-113">Example: Retrieve all elements at a particular depth</span></span>

<span data-ttu-id="397ad-114">Às vezes, você deseja recuperar todos os elementos em uma profundidade de elemento específica quando pode não haver ancestrais intermediários.</span><span class="sxs-lookup"><span data-stu-id="397ad-114">Sometimes you want to retrieve all elements at a particular element depth when there may not be intervening ancestors.</span></span> <span data-ttu-id="397ad-115">Por exemplo, no documento a seguir, você pode desejar recuperar todos os `ConfigParameter` elementos que são filhos do `Customer` elemento, mas não o `ConfigParameter` que é um filho do `Root` elemento.</span><span class="sxs-lookup"><span data-stu-id="397ad-115">For example, in the following document, you might want to retrieve all the `ConfigParameter` elements that are children of the `Customer` element, but not the `ConfigParameter` that's a child of the `Root` element.</span></span>

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

 <span data-ttu-id="397ad-116">Para fazer isso, você pode usar o eixo de <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> , como segue:</span><span class="sxs-lookup"><span data-stu-id="397ad-116">To do this, you can use the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> axis, as follows:</span></span>

```csharp
XElement root = XElement.Load("Irregular.xml");
IEnumerable<XElement> configParameters =
    root.Elements("Customer").Elements("Config").
    Elements("ConfigParameter");
foreach (XElement cp in configParameters)
    Console.WriteLine(cp);
```

```vb
Dim root As XElement = XElement.Load("Irregular.xml")
Dim configParameters As IEnumerable(Of XElement) = _
    root.<Customer>.<Config>.<ConfigParameter>
For Each cp As XElement In configParameters
    Console.WriteLine(cp)
Next
```

<span data-ttu-id="397ad-117">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="397ad-117">This example produces the following output:</span></span>

```xml
<ConfigParameter>FirstConfigParameter</ConfigParameter>
<ConfigParameter>SecondConfigParameter</ConfigParameter>
```

## <a name="example-retrieve-elements-for-xml-thats-in-a-namespace"></a><span data-ttu-id="397ad-118">Exemplo: recuperar elementos de XML que estão em um namespace</span><span class="sxs-lookup"><span data-stu-id="397ad-118">Example: Retrieve elements for XML that's in a namespace</span></span>

<span data-ttu-id="397ad-119">O exemplo a seguir mostra a mesma técnica para XML que está em um namespace.</span><span class="sxs-lookup"><span data-stu-id="397ad-119">The following example shows the same technique for XML that's in a namespace.</span></span> <span data-ttu-id="397ad-120">Para obter mais informações, consulte [visão geral de namespaces](namespaces-overview.md).</span><span class="sxs-lookup"><span data-stu-id="397ad-120">For more information, see [Namespaces overview](namespaces-overview.md).</span></span>

<span data-ttu-id="397ad-121">Este exemplo usa arquivo XML de exemplo de documento XML [: várias ordens de compra em um namespace](sample-xml-file-multiple-purchase-orders-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="397ad-121">This example uses XML document [Sample XML file: Multiple purchase orders in a namespace](sample-xml-file-multiple-purchase-orders-namespace.md).</span></span>

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

```vb
Imports <xmlns:aw="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim purchaseOrders As XElement = XElement.Load("PurchaseOrdersInNamespace.xml")
        Dim names As IEnumerable(Of XElement) = _
            From el In purchaseOrders.<aw:PurchaseOrder>.<aw:Address>.<aw:Name> _
            Select el
        For Each e As XElement In names
            Console.WriteLine(e)
        Next
    End Sub
End Module
```

<span data-ttu-id="397ad-122">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="397ad-122">This example produces the following output:</span></span>

```xml
<aw:Name xmlns:aw="http://www.adventure-works.com">Ellen Adams</aw:Name>
<aw:Name xmlns:aw="http://www.adventure-works.com">Tai Yee</aw:Name>
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>
```

## <a name="see-also"></a><span data-ttu-id="397ad-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="397ad-123">See also</span></span>

- [<span data-ttu-id="397ad-124">Visão geral dos eixos de LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="397ad-124">LINQ to XML axes overview</span></span>](linq-xml-axes-overview.md)
