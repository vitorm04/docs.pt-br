---
title: "Como: recuperar um único atributo (LINQ to XML) (Visual Basic) | Documentos do Microsoft"
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
ms.assetid: 11b938d7-c011-4048-900e-8b9183c41c94
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 35f477ead2bdcfdf78781459f93a755dbc89e5cc
ms.lasthandoff: 03/13/2017


---
# <a name="how-to-retrieve-a-single-attribute-linq-to-xml-visual-basic"></a>Como: recuperar um único atributo (LINQ to XML) (Visual Basic)
Este tópico explica como recuperar um único atributo de um elemento, dado o nome do atributo. Isso é útil para gravar as expressões de consulta onde você deseja localizar um elemento que possui um atributo específico.  
  
 O <xref:System.Xml.Linq.XElement.Attribute%2A>método o <xref:System.Xml.Linq.XElement>classe retorna o <xref:System.Xml.Linq.XAttribute>com o nome especificado.</xref:System.Xml.Linq.XAttribute> </xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XElement.Attribute%2A>  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o <xref:System.Xml.Linq.XElement.Attribute%2A>método.</xref:System.Xml.Linq.XElement.Attribute%2A>  
  
```vb  
Dim cust As XElement = <PhoneNumbers>  
                           <Phone type="home">555-555-5555</Phone>  
                           <Phone type="work">555-555-6666</Phone>  
                       </PhoneNumbers>  
Dim elList = From el In cust...<Phone>  
For Each e As XElement In elList  
    Console.WriteLine(e.@type)  
Next  
```  
  
 Este exemplo localiza os descendentes na árvore chamada `Phone`, e localiza o atributo chamado `type`.  
  
 Esse código gera a seguinte saída:  
  
```  
home  
work  
```  
  
## <a name="example"></a>Exemplo  
 Se você quiser recuperar o valor do atributo, você pode convertê-lo, exatamente como você faz para com <xref:System.Xml.Linq.XElement>objetos.</xref:System.Xml.Linq.XElement> O exemplo a seguir demonstra isso.  
  
```vb  
Dim cust As XElement = <PhoneNumbers>  
                           <Phone type="home">555-555-5555</Phone>  
                           <Phone type="work">555-555-6666</Phone>  
                       </PhoneNumbers>  
Dim elList As IEnumerable(Of XElement) = _  
    From el In cust...<Phone> _  
    Select el  
For Each el As XElement In elList  
    Console.WriteLine(el.@type)  
Next  
```  
  
 Esse código gera a seguinte saída:  
  
```  
home  
work  
```  
  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]provides explicit cast operators for the <xref:System.Xml.Linq.XAttribute> class to `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, and `GUID?`.</xref:System.Xml.Linq.XAttribute>  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra o mesmo código para um atributo que está em um namespace. Para obter mais informações, consulte [trabalhar com Namespaces XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim cust As XElement = _  
            <aw:PhoneNumbers>  
                <aw:Phone aw:type="home">555-555-5555</aw:Phone>  
                <aw:Phone aw:type="work">555-555-6666</aw:Phone>  
            </aw:PhoneNumbers>  
        Dim elList As IEnumerable(Of XElement) = _  
            From el In cust...<aw:Phone> _  
            Select el  
        For Each el As XElement In elList  
            Console.WriteLine(el.@aw:type)  
        Next  
    End Sub  
End Module  
```  
  
 Esse código gera a seguinte saída:  
  
```  
home  
work  
```  
  
## <a name="see-also"></a>Consulte também  
 [Eixos LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
