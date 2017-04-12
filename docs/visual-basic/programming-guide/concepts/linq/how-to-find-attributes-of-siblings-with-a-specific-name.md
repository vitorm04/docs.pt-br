---
title: "Como: localizar os atributos de irmãos com um nome específico (XPath-LINQ para XML) (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 83b3ddca-830a-4b71-9756-9e4bdf907302
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 879aa75ed8e8c74b2840c54058cc034d1f6cccc6
ms.lasthandoff: 03/13/2017


---
# <a name="how-to-find-attributes-of-siblings-with-a-specific-name-xpath-linq-to-xml-visual-basic"></a>Como: localizar os atributos de irmãos com um nome específico (XPath-LINQ para XML) (Visual Basic)
Este tópico mostra como localizar todos os atributos de seus irmãos o nó de contexto. Somente os atributos com um nome específico são retornados na coleção.  
  
 A expressão XPath é:  
  
 `../Book/@id`  
  
## <a name="example"></a>Exemplo  
 Este exemplo localiza primeiro um elemento de `Book` , e localiza em todos os elementos irmãos nomeados `Book`, e localiza em todos os atributos nomeados `id`. O resultado é uma coleção de atributos.  
  
 Este exemplo usa o seguinte documento XML: [arquivo XML de exemplo: livros (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).  
  
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
  
```  
Results are identical  
id="bk101"  
id="bk102"  
```  
  
## <a name="see-also"></a>Consulte também  
 [LINQ to XML para XPath usuários (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
