---
title: Como recuperar uma coleção de atributos (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: a49ee7a3-b2c2-4d49-9b5c-b7c6c41f4f13
ms.openlocfilehash: e872d0fefa5ea3c25208bf5deab42b59b5b7d5b0
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43526927"
---
# <a name="how-to-retrieve-a-collection-of-attributes-linq-to-xml-c"></a><span data-ttu-id="5da51-102">Como recuperar uma coleção de atributos (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="5da51-102">How to: Retrieve a Collection of Attributes (LINQ to XML) (C#)</span></span>
<span data-ttu-id="5da51-103">Este tópico apresenta o método de <xref:System.Xml.Linq.XElement.Attributes%2A> .</span><span class="sxs-lookup"><span data-stu-id="5da51-103">This topic introduces the <xref:System.Xml.Linq.XElement.Attributes%2A> method.</span></span> <span data-ttu-id="5da51-104">Esse método recupera os atributos de um elemento.</span><span class="sxs-lookup"><span data-stu-id="5da51-104">This method retrieves the attributes of an element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5da51-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5da51-105">Example</span></span>  
 <span data-ttu-id="5da51-106">O exemplo a seguir mostra como iterar através da coleção de atributos de um elemento.</span><span class="sxs-lookup"><span data-stu-id="5da51-106">The following example shows how to iterate through the collection of attributes of an element.</span></span>  
  
```csharp  
XElement val = new XElement("Value",  
    new XAttribute("ID", "1243"),  
    new XAttribute("Type", "int"),  
    new XAttribute("ConvertableTo", "double"),  
    "100");  
IEnumerable<XAttribute> listOfAttributes =  
    from att in val.Attributes()  
    select att;  
foreach (XAttribute a in listOfAttributes)  
    Console.WriteLine(a);  
```  
  
 <span data-ttu-id="5da51-107">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="5da51-107">This code produces the following output:</span></span>  
  
```  
ID="1243"  
Type="int"  
ConvertableTo="double"  
```  
  
## <a name="see-also"></a><span data-ttu-id="5da51-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5da51-108">See Also</span></span>

- [<span data-ttu-id="5da51-109">Eixos do LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="5da51-109">LINQ to XML Axes (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
