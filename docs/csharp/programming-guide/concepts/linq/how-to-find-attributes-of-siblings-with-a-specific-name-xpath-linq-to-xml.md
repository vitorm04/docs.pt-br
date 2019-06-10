---
title: 'Como: Localizar atributos de irmãos com um nome específico (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: c3133d64-523f-422d-8838-73d36b945ca0
ms.openlocfilehash: 0c62ecb7660a012af556515ba5e7de330d5ab5e7
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66486794"
---
# <a name="how-to-find-attributes-of-siblings-with-a-specific-name-xpath-linq-to-xml-c"></a>Como: Localizar atributos de irmãos com um nome específico (XPath-LINQ to XML) (C#)
Este tópico mostra como localizar todos os atributos de seus irmãos o nó de contexto. Somente os atributos com um nome específico são retornados na coleção.  
  
 A expressão XPath é:  
  
 `../Book/@id`  
  
## <a name="example"></a>Exemplo  
 Este exemplo localiza primeiro um elemento de `Book` , e localiza em todos os elementos irmãos nomeados `Book`, e localiza em todos os atributos nomeados `id`. O resultado é uma coleção de atributos.  
  
 Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: Livros (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).  
  
```csharp  
XDocument books = XDocument.Load("Books.xml");  
  
XElement book =   
    books  
    .Root  
    .Element("Book");  
  
// LINQ to XML query  
IEnumerable<XAttribute> list1 =  
    from el in book.Parent.Elements("Book")  
    select el.Attribute("id");  
  
// XPath expression  
IEnumerable<XAttribute> list2 =  
  ((IEnumerable)book.XPathEvaluate("../Book/@id")).Cast<XAttribute>();  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XAttribute el in list1)  
    Console.WriteLine(el);  
```  
  
 Este exemplo gera a seguinte saída:  
  
```  
Results are identical  
id="bk101"  
id="bk102"  
```  
  