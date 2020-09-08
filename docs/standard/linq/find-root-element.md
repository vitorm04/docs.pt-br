---
title: Como localizar o elemento raiz-LINQ to XML
description: Saiba como usar XPath e LINQ to XML, em C# e Visual Basic, para localizar o elemento raiz de um documento XML.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 4fd824e0-4d39-429b-b092-f6a5c046ee6c
ms.openlocfilehash: 16217960b84276bd3bb4c5cb6b38d7cb56d2b41e
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89551932"
---
# <a name="how-to-find-the-root-element-linq-to-xml"></a><span data-ttu-id="2d6e3-103">Como localizar o elemento raiz (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="2d6e3-103">How to find the root element (LINQ to XML)</span></span>

<span data-ttu-id="2d6e3-104">Este artigo fornece um exemplo que mostra como usar XPath e LINQ to XML, em C# e Visual Basic, para localizar o elemento raiz de um documento XML.</span><span class="sxs-lookup"><span data-stu-id="2d6e3-104">This article provides an example that shows how to use XPath and LINQ to XML, in C# and Visual Basic, to find the root element of an XML document.</span></span>

## <a name="example-find-the-root-element"></a><span data-ttu-id="2d6e3-105">Exemplo: localizar o elemento raiz</span><span class="sxs-lookup"><span data-stu-id="2d6e3-105">Example: Find the root element</span></span>

<span data-ttu-id="2d6e3-106">Este exemplo usa LINQ to XML consulta e XPath para localizar o elemento raiz no arquivo XML de exemplo de documento XML [: várias ordens de compra](sample-xml-file-multiple-purchase-orders.md).</span><span class="sxs-lookup"><span data-stu-id="2d6e3-106">This example uses LINQ to XML query and XPath to find the root element in XML document [Sample XML file: Multiple purchase orders](sample-xml-file-multiple-purchase-orders.md).</span></span> <span data-ttu-id="2d6e3-107">A expressão XPath é `/PurchaseOrders`.</span><span class="sxs-lookup"><span data-stu-id="2d6e3-107">The XPath expression is `/PurchaseOrders`.</span></span>

```csharp
XDocument po = XDocument.Load("PurchaseOrders.xml");

// LINQ to XML query
XElement el1 = po.Root;

// XPath expression
XElement el2 = po.XPathSelectElement("/PurchaseOrders");

if (el1 == el2)
    Console.WriteLine("Results are identical");
else
    Console.WriteLine("Results differ");
Console.WriteLine(el1.Name);
```

```vb
Dim po As XDocument = XDocument.Load("PurchaseOrders.xml")

' LINQ to XML query
Dim el1 As XElement = po.Root

' XPath expression
Dim el2 As XElement = po.XPathSelectElement("/PurchaseOrders")

If el1 Is el2 Then
    Console.WriteLine("Results are identical")
Else
    Console.WriteLine("Results differ")
End If
Console.WriteLine(el1.Name)
```

<span data-ttu-id="2d6e3-108">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="2d6e3-108">This example produces the following output:</span></span>

```output
Results are identical
PurchaseOrders
```

## <a name="see-also"></a><span data-ttu-id="2d6e3-109">Confira também</span><span class="sxs-lookup"><span data-stu-id="2d6e3-109">See also</span></span>

- [<span data-ttu-id="2d6e3-110">LINQ to XML para usuários do XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2d6e3-110">LINQ to XML for XPath Users (Visual Basic)</span></span>](/../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
