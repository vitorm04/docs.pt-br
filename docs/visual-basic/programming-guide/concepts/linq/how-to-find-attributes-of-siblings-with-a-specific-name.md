---
title: 'Como: Localizar atributos de irmãos com um nome específico (XPath-LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 83b3ddca-830a-4b71-9756-9e4bdf907302
ms.openlocfilehash: ce97cbc4b8b1105e8431016a9c296c158cf0091c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54596183"
---
# <a name="how-to-find-attributes-of-siblings-with-a-specific-name-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="43094-102">Como: Localizar atributos de irmãos com um nome específico (XPath-LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="43094-102">How to: Find Attributes of Siblings with a Specific Name (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="43094-103">Este tópico mostra como localizar todos os atributos de seus irmãos o nó de contexto.</span><span class="sxs-lookup"><span data-stu-id="43094-103">This topic shows how to find all attributes of the siblings of the context node.</span></span> <span data-ttu-id="43094-104">Somente os atributos com um nome específico são retornados na coleção.</span><span class="sxs-lookup"><span data-stu-id="43094-104">Only attributes with a specific name are returned in the collection.</span></span>  
  
 <span data-ttu-id="43094-105">A expressão XPath é:</span><span class="sxs-lookup"><span data-stu-id="43094-105">The XPath expression is:</span></span>  
  
 `../Book/@id`  
  
## <a name="example"></a><span data-ttu-id="43094-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="43094-106">Example</span></span>  
 <span data-ttu-id="43094-107">Este exemplo localiza primeiro um elemento de `Book` , e localiza em todos os elementos irmãos nomeados `Book`, e localiza em todos os atributos nomeados `id`.</span><span class="sxs-lookup"><span data-stu-id="43094-107">This example first finds a `Book` element, and then finds all sibling elements named `Book`, and then finds all attributes named `id`.</span></span> <span data-ttu-id="43094-108">O resultado é uma coleção de atributos.</span><span class="sxs-lookup"><span data-stu-id="43094-108">The result is a collection of attributes.</span></span>  
  
 <span data-ttu-id="43094-109">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: Livros (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="43094-109">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>  
  
```vb  
Dim books as XDocument = XDocument.Load("Books.xml")  
Dim book As XElement = books.Root.<Book>(0)  
  
' LINQ to XML query  
Dim list1 As IEnumerable(Of XAttribute) = _  
    From el In book.Parent.<Book> _  
    Select el.Attribute("id")  
  
' XPath expression  
Dim list2 As IEnumerable(Of XAttribute) = DirectCast(book. _  
    XPathEvaluate("../Book/@id"), IEnumerable).Cast(Of XAttribute)()  
  
If list1.Count() = list2.Count() And _  
        (list1.Intersect(list2)).Count() = list1.Count() Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
  
For Each el As XAttribute In list1  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="43094-110">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="43094-110">This example produces the following output:</span></span>  
  
```  
Results are identical  
id="bk101"  
id="bk102"  
```  
  
## <a name="see-also"></a><span data-ttu-id="43094-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="43094-111">See also</span></span>
- [<span data-ttu-id="43094-112">LINQ to XML para os usuários do XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="43094-112">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
