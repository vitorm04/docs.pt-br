---
title: Como localizar o elemento raiz (XPath-LINQ to XML) (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 4fd824e0-4d39-429b-b092-f6a5c046ee6c
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 22512cc4d85dd8d7a901b53dd6e888046b077af0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-find-the-root-element-xpath-linq-to-xml-c"></a><span data-ttu-id="cd242-102">Como localizar o elemento raiz (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="cd242-102">How to: Find the Root Element (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="cd242-103">Este tópico mostra como obter o elemento raiz com XPath e [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cd242-103">This topic shows how to get the root element with XPath and [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="cd242-104">A expressão XPath é:</span><span class="sxs-lookup"><span data-stu-id="cd242-104">The XPath expression is:</span></span>  
  
 `/PurchaseOrders`  
  
## <a name="example"></a><span data-ttu-id="cd242-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cd242-105">Example</span></span>  
 <span data-ttu-id="cd242-106">Este exemplo localiza o elemento raiz.</span><span class="sxs-lookup"><span data-stu-id="cd242-106">This example finds the root element.</span></span>  
  
 <span data-ttu-id="cd242-107">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: vários pedidos de compra (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="cd242-107">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="cd242-108">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="cd242-108">This example produces the following output:</span></span>  
  
```  
Results are identical  
PurchaseOrders  
```  
  
## <a name="see-also"></a><span data-ttu-id="cd242-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cd242-109">See Also</span></span>  
 [<span data-ttu-id="cd242-110">Usuários do LINQ to XML para XPath (C#)</span><span class="sxs-lookup"><span data-stu-id="cd242-110">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
