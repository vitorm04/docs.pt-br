---
title: 'Como: Localizar nós irmãos (XPath-LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 73082738-2113-4438-8545-98d5df0927cb
ms.openlocfilehash: dad211c9c3716f760d28e4a18a61c885fc4dd58f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61780387"
---
# <a name="how-to-find-sibling-nodes-xpath-linq-to-xml-visual-basic"></a>Como: Localizar nós irmãos (XPath-LINQ to XML) (Visual Basic)
Você pode desejar localizar todos os seus irmãos de um nó que têm um nome específico. A coleção resultante pode incluir o nó de contexto se o nó de contexto também tem o nome específico.  
  
 A expressão XPath é:  
  
 `../Book`  
  
## <a name="example"></a>Exemplo  
 Este exemplo localiza primeiro um elemento de `Book` , e localiza em todos os elementos irmãos nomeados `Book`. A coleção resultante inclui o nó de contexto.  
  
 Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: Livros (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).  
  
```vb  
Dim books As XDocument = XDocument.Load("Books.xml")  
Dim book As XElement = books.Root.<Book>.Skip(1).First()  
  
' LINQ to XML query  
Dim list1 As IEnumerable(Of XElement) = book.Parent.<Book>  
  
' XPath expression  
Dim list2 As IEnumerable(Of XElement) = book.XPathSelectElements("../Book")  
  
If list1.Count() = list2.Count() And _  
        list1.Intersect(list2).Count() = list1.Count() Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
For Each el As XElement In list1  
    Console.WriteLine(el)  
Next  
```  
  
 Este exemplo gera a seguinte saída:  
  
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
  
## <a name="see-also"></a>Consulte também

- [LINQ to XML para os usuários do XPath (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
