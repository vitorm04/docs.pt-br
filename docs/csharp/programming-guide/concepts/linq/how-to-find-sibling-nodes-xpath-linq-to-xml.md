---
title: 'Como: Localizar nós irmãos (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: e2c73d10-a8ca-4e11-b5aa-d055de285874
ms.openlocfilehash: b71bf1123461e4b0c0db5024eac3330bcf666ecc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54646757"
---
# <a name="how-to-find-sibling-nodes-xpath-linq-to-xml-c"></a><span data-ttu-id="29aba-102">Como: Localizar nós irmãos (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="29aba-102">How to: Find Sibling Nodes (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="29aba-103">Você pode desejar localizar todos os seus irmãos de um nó que têm um nome específico.</span><span class="sxs-lookup"><span data-stu-id="29aba-103">You might want to find all siblings of a node that have a specific name.</span></span> <span data-ttu-id="29aba-104">A coleção resultante pode incluir o nó de contexto se o nó de contexto também tem o nome específico.</span><span class="sxs-lookup"><span data-stu-id="29aba-104">The resulting collection might include the context node if the context node also has the specific name.</span></span>  
  
 <span data-ttu-id="29aba-105">A expressão XPath é:</span><span class="sxs-lookup"><span data-stu-id="29aba-105">The XPath expression is:</span></span>  
  
 `../Book`  
  
## <a name="example"></a><span data-ttu-id="29aba-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="29aba-106">Example</span></span>  
 <span data-ttu-id="29aba-107">Este exemplo localiza primeiro um elemento de `Book` , e localiza em todos os elementos irmãos nomeados `Book`.</span><span class="sxs-lookup"><span data-stu-id="29aba-107">This example first finds a `Book` element, and then finds all sibling elements named `Book`.</span></span> <span data-ttu-id="29aba-108">A coleção resultante inclui o nó de contexto.</span><span class="sxs-lookup"><span data-stu-id="29aba-108">The resulting collection includes the context node.</span></span>  
  
 <span data-ttu-id="29aba-109">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: Livros (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="29aba-109">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>  
  
```csharp  
XDocument books = XDocument.Load("Books.xml");  
  
XElement book =   
    books  
    .Root  
    .Elements("Book")  
    .Skip(1)  
    .First();  
  
// LINQ to XML query  
IEnumerable<XElement> list1 =  
    book  
    .Parent  
    .Elements("Book");  
  
// XPath expression  
IEnumerable<XElement> list2 = book.XPathSelectElements("../Book");  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="29aba-110">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="29aba-110">This example produces the following output:</span></span>  
  
```  
Results are identical  
<Book id="bk101">  
  <Author>Garghentini, Davide</Author>  
  <Title>XML Developer's Guide</Title>  
  <Genre>Computer</Genre>  
  <Price>44.95</Price>  
  <PublishDate>2000-10-01</PublishDate>  
  <Description>An in-depth look at creating applications   
      with XML.</Description>  
</Book>  
<Book id="bk102">  
  <Author>Garcia, Debra</Author>  
  <Title>Midnight Rain</Title>  
  <Genre>Fantasy</Genre>  
  <Price>5.95</Price>  
  <PublishDate>2000-12-16</PublishDate>  
  <Description>A former architect battles corporate zombies,   
      an evil sorceress, and her own childhood to become queen   
      of the world.</Description>  
</Book>  
```  
  
## <a name="see-also"></a><span data-ttu-id="29aba-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="29aba-111">See also</span></span>

- [<span data-ttu-id="29aba-112">Usuários do LINQ to XML para XPath (C#)</span><span class="sxs-lookup"><span data-stu-id="29aba-112">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
