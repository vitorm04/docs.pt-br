---
title: 'Como: escrever uma consulta que encontra elementos com base no contexto (Visual Basic) | Documentos do Microsoft'
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
ms.assetid: 0b085290-ddc1-4126-aaa0-e4c95a3d9a09
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: c26a6f0debd165a925bf45e2ac5063e1afff693f
ms.lasthandoff: 03/13/2017


---
# <a name="how-to-write-a-query-that-finds-elements-based-on-context-visual-basic"></a>Como: escrever uma consulta que encontra elementos com base no contexto (Visual Basic)
Muitas vezes você pode ter que escrever uma consulta que seleciona elementos com base no contexto. Você pode querer filtrar com base nos elementos irmãos precedentes ou seguintes. Você pode querer filtrar com base nos elementos filhos ou ancestrais.  
  
 Você pode fazer isso escrevendo uma consulta e usando os resultados da consulta na cláusula `where`. Se você primeiro tiver que testar com zero e, em seguida, testar o valor, é mais conveniente fazer a consulta em uma cláusula `let` e usar os resultados na cláusula `where`.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir seleciona todos os elementos `p` que são imediatamente seguidos por um elemento `ul`.  
  
```vb  
Dim doc As XElement = _  
    <Root>  
        <p id='1'/>  
        <ul>abc</ul>  
        <Child>  
            <p id='2'/>  
            <notul/>  
            <p id='3'/>  
            <ul>def</ul>  
            <p id='4'/>  
        </Child>  
        <Child>  
            <p id='5'/>  
            <notul/>  
            <p id='6'/>  
            <ul>abc</ul>  
            <p id='7'/>  
        </Child>  
    </Root>  
  
Dim items As IEnumerable(Of XElement) = _  
    From e In doc...<p> _  
    Let z = e.ElementsAfterSelf().FirstOrDefault() _  
    Where z IsNot Nothing AndAlso z.Name.LocalName = "ul" _  
    Select e  
  
For Each e As XElement In items  
    Console.WriteLine("id = {0}", e.@<id>)  
Next  
  
```  
  
 Esse código gera a seguinte saída:  
  
```  
id = 1  
id = 3  
id = 6  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra a mesma consulta para XML que está em um namespace. Para obter mais informações, consulte [trabalhar com Namespaces XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
```vb  
Imports <xmlns='http://www.adatum.com'>  
  
Module Module1  
    Sub Main()  
        Dim doc As XElement = _  
            <Root>  
                <p id='1'/>  
                <ul>abc</ul>  
                <Child>  
                    <p id='2'/>  
                    <notul/>  
                    <p id='3'/>  
                    <ul>def</ul>  
                    <p id='4'/>  
                </Child>  
                <Child>  
                    <p id='5'/>  
                    <notul/>  
                    <p id='6'/>  
                    <ul>abc</ul>  
                    <p id='7'/>  
                </Child>  
            </Root>  
  
        Dim items As IEnumerable(Of XElement) = _  
            From e In doc...<p> _  
            Let z = e.ElementsAfterSelf().FirstOrDefault() _  
            Where z IsNot Nothing AndAlso z.Name = GetXmlNamespace().GetName("ul") _  
            Select e  
  
        For Each e As XElement In items  
            Console.WriteLine("id = {0}", e.@<id>)  
        Next  
    End Sub  
End Module  
```  
  
 Esse código gera a seguinte saída:  
  
```  
id = 1  
id = 3  
id = 6  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Xml.Linq.XElement.Parse%2A></xref:System.Xml.Linq.XElement.Parse%2A>   
 <xref:System.Xml.Linq.XContainer.Descendants%2A></xref:System.Xml.Linq.XContainer.Descendants%2A>   
 <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A></xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>   
 <xref:System.Linq.Enumerable.FirstOrDefault%2A></xref:System.Linq.Enumerable.FirstOrDefault%2A>   
 [Consultas básicas (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
