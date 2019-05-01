---
title: 'Como: Recuperar uma coleção de atributos (LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: a07e9645-b45b-403b-b698-f652f904c7d2
ms.openlocfilehash: 2e99e561c1d479412c7c5cd2a19563446b872049
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051293"
---
# <a name="how-to-retrieve-a-collection-of-attributes-linq-to-xml-visual-basic"></a>Como: Recuperar uma coleção de atributos (LINQ to XML) (Visual Basic)
Este tópico apresenta o método de <xref:System.Xml.Linq.XElement.Attributes%2A> . Esse método recupera os atributos de um elemento.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como iterar através da coleção de atributos de um elemento.  
  
```vb  
Dim val = _  
    <Value ID="1243" Type="int" ConvertableTo="double">100</Value>  
Dim listOfAttributes As IEnumerable(Of XAttribute) = _  
    From att In val.Attributes() _  
    Select att  
For Each att As XAttribute In listOfAttributes  
    Console.WriteLine(att)  
Next  
```  
  
 Esse código gera a seguinte saída:  
  
```  
ID="1243"  
Type="int"  
ConvertableTo="double"  
```  
  
## <a name="see-also"></a>Consulte também

- [Eixos LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
