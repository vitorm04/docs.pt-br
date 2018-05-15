---
title: 'Como: localizar os atributos de seus irmãos com um nome específico (XPath-LINQ para XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 83b3ddca-830a-4b71-9756-9e4bdf907302
ms.openlocfilehash: 467a9a5f529111b45fccda79437ccc6538f1372a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-find-attributes-of-siblings-with-a-specific-name-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="b38fd-102">Como: localizar os atributos de seus irmãos com um nome específico (XPath-LINQ para XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b38fd-102">How to: Find Attributes of Siblings with a Specific Name (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="b38fd-103">Este tópico mostra como localizar todos os atributos de seus irmãos o nó de contexto.</span><span class="sxs-lookup"><span data-stu-id="b38fd-103">This topic shows how to find all attributes of the siblings of the context node.</span></span> <span data-ttu-id="b38fd-104">Somente os atributos com um nome específico são retornados na coleção.</span><span class="sxs-lookup"><span data-stu-id="b38fd-104">Only attributes with a specific name are returned in the collection.</span></span>  
  
 <span data-ttu-id="b38fd-105">A expressão XPath é:</span><span class="sxs-lookup"><span data-stu-id="b38fd-105">The XPath expression is:</span></span>  
  
 `../Book/@id`  
  
## <a name="example"></a><span data-ttu-id="b38fd-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b38fd-106">Example</span></span>  
 <span data-ttu-id="b38fd-107">Este exemplo localiza primeiro um elemento de `Book` , e localiza em todos os elementos irmãos nomeados `Book`, e localiza em todos os atributos nomeados `id`.</span><span class="sxs-lookup"><span data-stu-id="b38fd-107">This example first finds a `Book` element, and then finds all sibling elements named `Book`, and then finds all attributes named `id`.</span></span> <span data-ttu-id="b38fd-108">O resultado é uma coleção de atributos.</span><span class="sxs-lookup"><span data-stu-id="b38fd-108">The result is a collection of attributes.</span></span>  
  
 <span data-ttu-id="b38fd-109">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: livros (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="b38fd-109">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="b38fd-110">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="b38fd-110">This example produces the following output:</span></span>  
  
```  
Results are identical  
id="bk101"  
id="bk102"  
```  
  
## <a name="see-also"></a><span data-ttu-id="b38fd-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b38fd-111">See Also</span></span>  
 [<span data-ttu-id="b38fd-112">LINQ to XML para XPath usuários (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b38fd-112">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
