---
title: Atomizados de XName e XNamespace objeto (LINQ to XML) (Visual Basic) | Documentos do Microsoft
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
ms.assetid: 21ee7585-7df9-40b4-8c76-a12bb5f29bb3
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: b08f3116f5acb404cf2c33072ec31fbaada4e7cb
ms.lasthandoff: 03/13/2017


---
# <a name="atomized-xname-and-xnamespace-objects-linq-to-xml-visual-basic"></a>Atomizados de XName e XNamespace objeto (LINQ to XML) (Visual Basic)
<xref:System.Xml.Linq.XName>e <xref:System.Xml.Linq.XNamespace>são objetos *atomizado*; ou seja, se tiverem o mesmo nome qualificado, eles se referem ao mesmo objeto.</xref:System.Xml.Linq.XNamespace></xref:System.Xml.Linq.XName> Este benefícios de desempenho das para consultas: Quando você compara dois nomes atomizados para igualdade, o linguagem intermediária subjacente só precisa determinar se o ponto de duas referências para o mesmo objeto. O código subjacente não tem que fazer as comparações de cadeias de caracteres, que poderiam demoradas.  
  
## <a name="atomization-semantics"></a>Semântica de atomização  
 Atomização significa que, se dois <xref:System.Xml.Linq.XName>objetos têm o mesmo nome local e eles estão no mesmo namespace, compartilham a mesma instância.</xref:System.Xml.Linq.XName> Da mesma forma, se dois <xref:System.Xml.Linq.XNamespace>objetos têm o mesmo URI de namespace, compartilham a mesma instância.</xref:System.Xml.Linq.XNamespace>  
  
 Para que uma classe permite objetos atomizados, o construtor para a classe deve ser particular, não público. Isso ocorre porque se foi o construtor público, você pode criar um objeto não atomizado. O <xref:System.Xml.Linq.XName>e <xref:System.Xml.Linq.XNamespace>classes implementam um operador de conversão implícita para converter uma cadeia de caracteres em um <xref:System.Xml.Linq.XName>ou <xref:System.Xml.Linq.XNamespace>.</xref:System.Xml.Linq.XNamespace> </xref:System.Xml.Linq.XName> </xref:System.Xml.Linq.XNamespace> </xref:System.Xml.Linq.XName> Isso é como você obtém uma instância desses objetos. Você não pode obter uma instância usando um construtor, porque o construtor é inacessível.  
  
 <xref:System.Xml.Linq.XName>e <xref:System.Xml.Linq.XNamespace>também implementam os operadores de igualdade e desigualdade, para determinar se dois objetos que estão sendo comparados são referências à mesma instância.</xref:System.Xml.Linq.XNamespace></xref:System.Xml.Linq.XName>  
  
## <a name="example"></a>Exemplo  
 O código a seguir cria alguns <xref:System.Xml.Linq.XElement>objetos e demonstra que os nomes idênticos compartilham a mesma instância.</xref:System.Xml.Linq.XElement>  
  
```vb  
Dim r1 As New XElement("Root", "data1")  
Dim r2 As XElement = XElement.Parse("<Root>data2</Root>")  
  
If DirectCast(r1.Name, Object) = DirectCast(r2.Name, Object) Then  
    Console.WriteLine("r1 and r2 have names that refer to the same instance.")  
Else  
    Console.WriteLine("Different")  
End If  
  
Dim n As XName = "Root"  
  
If DirectCast(n, Object) = DirectCast(r1.Name, Object) Then  
    Console.WriteLine("The name of r1 and the name in 'n' refer to the same instance.")  
Else  
    Console.WriteLine("Different")  
End If  
  
```  
  
 Este exemplo gera a seguinte saída:  
  
```  
r1 and r2 have names that refer to the same instance.  
The name of r1 and the name in 'n' refer to the same instance.  
```  
  
 Como mencionado anteriormente, o benefício de objetos atomizados é que, quando você usar um dos métodos de eixo que levam um <xref:System.Xml.Linq.XName>como um parâmetro, o método do eixo só precisa determinar que dois nomes referenciam a mesma instância para selecionar os elementos desejados.</xref:System.Xml.Linq.XName>  
  
 O exemplo a seguir passa um <xref:System.Xml.Linq.XName>para o <xref:System.Xml.Linq.XContainer.Descendants%2A>chamada de método, que tem um melhor desempenho devido ao padrão de atomização.</xref:System.Xml.Linq.XContainer.Descendants%2A> </xref:System.Xml.Linq.XName>  
  
```vb  
Dim root As New XElement("Root", New XElement("C1", 1), New XElement("Z1", New XElement("C1", 2), New XElement("C1", 1)))  
  
Dim query = From e In root.Descendants("C1") Where CInt(e) = 1e  
  
For Each z As var In query  
    Console.WriteLine(z)  
Next  
```  
  
 Este exemplo gera a seguinte saída:  
  
```  
<C1>1</C1>  
<C1>1</C1>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Desempenho (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
