---
title: 'Como: Recuperar o valor de um atributo (LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 5f4b3790-c83f-4eb3-a889-e3587edf3ca1
ms.openlocfilehash: d03b2b146ad2f6b796ba6589cf99d06aa429535d
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68710501"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-visual-basic"></a>Como: Recuperar o valor de um atributo (LINQ to XML) (Visual Basic)
Este tópico mostra como obter o valor de atributos. Há duas maneiras principais: Você pode converter um <xref:System.Xml.Linq.XAttribute> no tipo desejado; o operador de conversão explícita converte então o conteúdo do elemento ou do atributo no tipo especificado. Outra opção é usar a propriedade <xref:System.Xml.Linq.XAttribute.Value%2A>. No entanto, a conversão geralmente é a abordagem recomendada. Se você converter o atributo em um tipo anulável, o código será mais simples de criar ao recuperar o valor de um atributo que pode ou não existir. Para obter exemplos dessa técnica, confira [Como: Recupera o valor de um elemento (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md).  
  
## <a name="example"></a>Exemplo  
 Em Visual Basic, você pode usar a propriedade de atributo integrado para recuperar o valor de um atributo.  
  
```vb  
Dim root As XElement = <Root Attr="abcde"/>  
Console.WriteLine(root)  
Dim str As String = root.@Attr  
Console.WriteLine(str)  
```  
  
 Este exemplo gera a seguinte saída:  
  
```xml  
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
 O exemplo a seguir mostra como recuperar o valor de um atributo em que o atributo está em um namespace. Para obter mais informações, consulte [visão geral de namespaces (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).  
  
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

- [Eixos LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
