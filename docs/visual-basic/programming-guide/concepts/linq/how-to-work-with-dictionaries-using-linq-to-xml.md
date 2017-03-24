---
title: "Como: trabalhar com dicionários usando LINQ to XML (Visual Basic) | Documentos do Microsoft"
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
ms.assetid: 6cb3f969-1986-414a-b850-87418712edea
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 3441e513012ba24419a3c5330cdb2f75f5ca394f
ms.lasthandoff: 03/13/2017


---
# <a name="how-to-work-with-dictionaries-using-linq-to-xml-visual-basic"></a>Como: trabalhar com dicionários usando LINQ to XML (Visual Basic)
É conveniente converter variedades de estruturas de dados para XML, e XML de volta para outras estruturas de dados. Este tópico mostra uma implementação específica dessa abordagem geral convertendo um <xref:System.Collections.Generic.Dictionary%602>para XML e vice-versa.</xref:System.Collections.Generic.Dictionary%602>  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa literais XML e uma consulta em uma expressão inserida. A consulta projetos novos <xref:System.Xml.Linq.XElement>objetos, que então se tornar o novo conteúdo para o `Root` <xref:System.Xml.Linq.XElement>objeto.</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XElement>  
  
```vb  
Dim dict As Dictionary(Of String, String) = New Dictionary(Of String, String)()  
dict.Add("Child1", "Value1")  
dict.Add("Child2", "Value2")  
dict.Add("Child3", "Value3")  
dict.Add("Child4", "Value4")  
Dim root As XElement = _  
    <Root>  
        <%= From keyValue In dict _  
            Select New XElement(keyValue.Key, keyValue.Value) %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 Esse código gera a seguinte saída:  
  
```xml  
  
          <Root>  
  <Child1>Value1</Child1>  
  <Child2>Value2</Child2>  
  <Child3>Value3</Child3>  
  <Child4>Value4</Child4>  
</Root>  
```  
  
## <a name="example"></a>Exemplo  
 O código a seguir cria um dicionário XML.  
  
```vb  
Dim root As XElement = _  
        <Root>  
            <Child1>Value1</Child1>  
            <Child2>Value2</Child2>  
            <Child3>Value3</Child3>  
            <Child4>Value4</Child4>  
        </Root>  
  
Dim dict As Dictionary(Of String, String) = New Dictionary(Of String, String)  
For Each el As XElement In root.Elements  
    dict.Add(el.Name.LocalName, el.Value)  
Next  
For Each str As String In dict.Keys  
    Console.WriteLine("{0}:{1}", str, dict(str))  
Next  
```  
  
 Esse código gera a seguinte saída:  
  
```  
Child1:Value1  
Child2:Value2  
Child3:Value3  
Child4:Value4  
```  
  
## <a name="see-also"></a>Consulte também  
 [Projeções e transformações (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
