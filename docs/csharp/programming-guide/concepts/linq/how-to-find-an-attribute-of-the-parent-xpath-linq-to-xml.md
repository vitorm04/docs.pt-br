---
title: Como localizar um atributo do pai (XPath-LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: dbef9d89-a5c4-431f-80cc-7a2ebf323f86
ms.openlocfilehash: 6f796bfb8f8b0051af4e31f6e82a503dbfbbc334
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33318793"
---
# <a name="how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml-c"></a><span data-ttu-id="e2dca-102">Como localizar um atributo do pai (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="e2dca-102">How to: Find an Attribute of the Parent (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="e2dca-103">Este tópico mostra como navegar para o elemento pai e localizar um atributo deles.</span><span class="sxs-lookup"><span data-stu-id="e2dca-103">This topic shows how to navigate to the parent element and find an attribute of it.</span></span>  
  
 <span data-ttu-id="e2dca-104">A expressão XPath é:</span><span class="sxs-lookup"><span data-stu-id="e2dca-104">The XPath expression is:</span></span>  
  
 `../@id`  
  
## <a name="example"></a><span data-ttu-id="e2dca-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e2dca-105">Example</span></span>  
 <span data-ttu-id="e2dca-106">Este exemplo localiza primeiro um elemento de `Author` .</span><span class="sxs-lookup"><span data-stu-id="e2dca-106">This example first finds an `Author` element.</span></span> <span data-ttu-id="e2dca-107">Localiza no atributo de `id` de elemento pai.</span><span class="sxs-lookup"><span data-stu-id="e2dca-107">It then finds the `id` attribute of the parent element.</span></span>  
  
 <span data-ttu-id="e2dca-108">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: livros (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="e2dca-108">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>  
  
```csharp  
XDocument books = XDocument.Load("Books.xml");  
  
XElement author =   
    books  
    .Root  
    .Element("Book")  
    .Element("Author");  
  
// LINQ to XML query  
XAttribute att1 =  
    author  
    .Parent  
    .Attribute("id");  
  
// XPath expression  
XAttribute att2 = ((IEnumerable)author.XPathEvaluate("../@id")).Cast<XAttribute>().First();  
  
if (att1 == att2)  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
Console.WriteLine(att1);  
```  
  
 <span data-ttu-id="e2dca-109">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="e2dca-109">This example produces the following output:</span></span>  
  
```  
Results are identical  
id="bk101"  
```  
  
## <a name="see-also"></a><span data-ttu-id="e2dca-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e2dca-110">See Also</span></span>  
 [<span data-ttu-id="e2dca-111">Usuários do LINQ to XML para XPath (C#)</span><span class="sxs-lookup"><span data-stu-id="e2dca-111">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
