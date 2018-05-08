---
title: 'Como: localizar um elemento com um elemento filho específico (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: b0d0a463-6a85-46c3-8453-ad25b0ecf93c
ms.openlocfilehash: 9ebc7fd826e2245cea661b2441fa9989b0aee8b8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-find-an-element-with-a-specific-child-element-visual-basic"></a>Como: localizar um elemento com um elemento filho específico (Visual Basic)
Este tópico mostra como localizar determinado elemento que tem um elemento filho com um valor específico.  
  
## <a name="example"></a>Exemplo  
 O exemplo localiza o elemento `Test` que possui um elemento filho `CommandLine` com o valor "Examp2.EXE".  
  
 Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: configuração de teste (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-test-configuration-linq-to-xml.md).  
  
```vb  
Dim root As XElement = XElement.Load("TestConfig.xml")  
Dim tests As IEnumerable(Of XElement) = _  
    From el In root.<Test> _  
    Where el.<CommandLine>.Value = "Examp2.EXE" _  
    Select el  
For Each el as XElement In tests  
    Console.WriteLine(el.@TestId)  
Next  
```  
  
 Esse código gera a seguinte saída:  
  
```  
0002  
0006  
```  
  
 Observe que este exemplo usa o [propriedade de eixo filho XML](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md), o [propriedade de eixo de atributo XML](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)e o [propriedade de valor XML](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra a mesma consulta para XML que está em um namespace. Para obter mais informações, consulte [trabalhando com Namespaces de XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
 Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: configuração de teste em um namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-test-configuration-in-a-namespace.md).  
  
```vb  
Imports <xmlns='http://www.adatum.com'>  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = XElement.Load("TestConfigInNamespace.xml")  
        Dim tests As IEnumerable(Of XElement) = _  
            From el In root.<Test> _  
            Where el.<CommandLine>.Value = "Examp2.EXE" _  
            Select el  
        For Each el As XElement In tests  
            Console.WriteLine(el.@TestId)  
        Next  
    End Sub  
End Module  
```  
  
 Esse código gera a seguinte saída:  
  
```  
0002  
0006  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Xml.Linq.XElement.Attribute%2A>  
 <xref:System.Xml.Linq.XContainer.Elements%2A>  
 [Consultas básicas (LINQ para XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)  
 [Visão geral de operadores de consulta padrão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [Operações de projeção (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projection-operations.md)
