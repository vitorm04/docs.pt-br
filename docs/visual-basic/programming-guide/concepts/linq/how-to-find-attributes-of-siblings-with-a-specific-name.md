---
title: 'Como: Atributos de localização de seus irmãos com um nome específico (XPath- LINQ para XML)'
ms.date: 07/20/2015
ms.assetid: 83b3ddca-830a-4b71-9756-9e4bdf907302
ms.openlocfilehash: ea4492dbbe9dc8e32c675e1a938cda0d10321b7a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343672"
---
# <a name="how-to-find-attributes-of-siblings-with-a-specific-name-xpath-linq-to-xml-visual-basic"></a>Como localizar atributos de irmãos com um nome específico (XPath-LINQ to XML) (Visual Basic)
Este tópico mostra como localizar todos os atributos de seus irmãos o nó de contexto. Somente os atributos com um nome específico são retornados na coleção.  
  
 A expressão XPath é:  
  
 `../Book/@id`  
  
## <a name="example"></a>Exemplo  
 Este exemplo localiza primeiro um elemento de `Book` , e localiza em todos os elementos irmãos nomeados `Book`, e localiza em todos os atributos nomeados `id`. O resultado é uma coleção de atributos.  
  
 Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: livros (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).  
  
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
  
 Este exemplo gera a seguinte saída:  
  
```console  
Results are identical  
id="bk101"  
id="bk102"  
```  
  
## <a name="see-also"></a>Consulte também

- [LINQ to XML para usuários do XPath (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
