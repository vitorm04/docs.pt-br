---
title: 'Como: recuperar o valor de um atributo (LINQ to XML) (Visual Basic) | Documentos do Microsoft'
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
ms.assetid: 5f4b3790-c83f-4eb3-a889-e3587edf3ca1
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: a1661b1ea00eb7e377fc4d8a57ba27a558052b46
ms.lasthandoff: 03/13/2017


---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-visual-basic"></a>Como: recuperar o valor de um atributo (LINQ to XML) (Visual Basic)
Este tópico mostra como obter o valor de atributos. Há duas maneiras principais: você pode converter um <xref:System.Xml.Linq.XAttribute>para o tipo desejado; o operador de conversão explícita converte o conteúdo do elemento ou atributo para o tipo especificado.</xref:System.Xml.Linq.XAttribute> Como alternativa, você pode usar o <xref:System.Xml.Linq.XAttribute.Value%2A>propriedade.</xref:System.Xml.Linq.XAttribute.Value%2A> No entanto, a conversão geralmente é a abordagem recomendada. Se você converter o atributo em um tipo anulável, o código será mais simples de criar ao recuperar o valor de um atributo que pode ou não existir. Para obter exemplos dessa técnica, consulte [como: recuperar o valor de um elemento (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md).  
  
## <a name="example"></a>Exemplo  
 Em Visual Basic, você pode usar a propriedade de atributo integrado para recuperar o valor de um atributo.  
  
```vb  
Dim root As XElement = <Root Attr="abcde"/>  
Console.WriteLine(root)  
Dim str As String = root.@Attr  
Console.WriteLine(str)  
```  
  
 Este exemplo gera a seguinte saída:  
  
```  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a>Exemplo  
 Em Visual Basic, você pode usar a propriedade de atributo integrado para definir o valor de um atributo. Além disso, se você usar a propriedade de atributo integrado para definir o valor de um atributo que não existe, o atributo será criado.  
  
```vb  
Dim root As XElement = <Root Att1="content"/>  
root.@Att1 = "new content"  
root.@Att2 = "new attribute"  
Console.WriteLine(root)  
```  
  
 Este exemplo gera a seguinte saída:  
  
```xml  
<Root Att1="new content" Att2="new attribute" />  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como recuperar o valor de um atributo em que o atributo está em um namespace. Para obter mais informações, consulte [trabalhar com Namespaces XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <aw:Root aw:Attr="abcde"/>  
        Dim str As String = root.@aw:Attr  
        Console.WriteLine(str)  
    End Sub  
End Module  
```  
  
 Este exemplo gera a seguinte saída:  
  
```  
abcde  
```  
  
## <a name="see-also"></a>Consulte também  
 [Eixos LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
