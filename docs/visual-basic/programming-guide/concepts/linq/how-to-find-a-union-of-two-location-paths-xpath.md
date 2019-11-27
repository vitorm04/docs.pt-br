---
title: 'Como: Localizar uma união de dois caminhos de local (XPath- LINQ para XML)'
ms.date: 07/20/2015
ms.assetid: c82c09b4-cb0a-47ec-8cc3-a124144c2788
ms.openlocfilehash: db9ba3f66bfa8643738203ec05a106bab4193fda
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352981"
---
# <a name="how-to-find-a-union-of-two-location-paths-xpath-linq-to-xml-visual-basic"></a>Como localizar uma União de dois caminhos de local (XPath-LINQ to XML) (Visual Basic)
O XPath permite que você localize a união de resultados de dois caminhos de local XPath.  
  
 A expressão XPath é:  
  
 `//Category|//Price`  
  
 Você pode obter os mesmos resultados usando o operador padrão de consulta de <xref:System.Linq.Enumerable.Concat%2A> .  
  
## <a name="example"></a>Exemplo  
 Este exemplo localiza os elementos de `Category` e todos os elementos de `Price` , e os concatena em uma única coleção. Observe que a consulta de [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] chama <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> para ordenar os resultados. Os resultados da avaliação de expressão XPath são também em ordem do documento.  
  
 Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: dados numéricos (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).  
  
```vb  
Dim data As XDocument = XDocument.Load("Data.xml")  
  
' LINQ to XML query  
Dim list1 As IEnumerable(Of XElement) = _  
    data...<Category>.Concat(data...<Price>).InDocumentOrder()  
  
' XPath expression  
Dim list2 As IEnumerable(Of XElement) = _  
    data.XPathSelectElements("//Category|//Price")  
  
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
  
```console
Results are identical  
<Category>A</Category>  
<Price>24.50</Price>  
<Category>B</Category>  
<Price>89.99</Price>  
<Category>A</Category>  
<Price>4.95</Price>  
<Category>A</Category>  
<Price>66.00</Price>  
<Category>B</Category>  
<Price>.99</Price>  
<Category>A</Category>  
<Price>29.00</Price>  
<Category>B</Category>  
<Price>6.99</Price>  
```  
  
## <a name="see-also"></a>Consulte também

- [LINQ to XML para usuários do XPath (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
