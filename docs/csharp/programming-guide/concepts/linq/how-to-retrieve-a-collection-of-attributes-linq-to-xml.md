---
title: Como recuperar uma coleção de atributos (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: a49ee7a3-b2c2-4d49-9b5c-b7c6c41f4f13
ms.openlocfilehash: 73e548b100893652b63dfcc69669eabce655efa6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33317837"
---
# <a name="how-to-retrieve-a-collection-of-attributes-linq-to-xml-c"></a>Como recuperar uma coleção de atributos (LINQ to XML) (C#)
Este tópico apresenta o método de <xref:System.Xml.Linq.XElement.Attributes%2A> . Esse método recupera os atributos de um elemento.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como iterar através da coleção de atributos de um elemento.  
  
```csharp  
XElement val = new XElement("Value",  
    new XAttribute("ID", "1243"),  
    new XAttribute("Type", "int"),  
    new XAttribute("ConvertableTo", "double"),  
    "100");  
IEnumerable<XAttribute> listOfAttributes =  
    from att in val.Attributes()  
    select att;  
foreach (XAttribute a in listOfAttributes)  
    Console.WriteLine(a);  
```  
  
 Esse código gera a seguinte saída:  
  
```  
ID="1243"  
Type="int"  
ConvertableTo="double"  
```  
  
## <a name="see-also"></a>Consulte também  
 [Eixos do LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
