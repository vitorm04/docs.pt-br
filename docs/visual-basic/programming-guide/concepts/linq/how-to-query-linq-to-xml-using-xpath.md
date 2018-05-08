---
title: 'Como: consulte LINQ to XML usando XPath (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: e1f69a20-1efa-452d-9089-c472fa84b3d5
ms.openlocfilehash: d8f23bd8417c3f59377e5e677b08e403ecc1122d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-query-linq-to-xml-using-xpath-visual-basic"></a>Como: consulte LINQ to XML usando XPath (Visual Basic)
Este tópico apresenta os métodos de extensão que permitem ver uma árvore XML usando o XPath. Para obter informações detalhadas sobre como usar esses métodos de extensão, consulte <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.  
  
 A menos que você tenha um motivo específico para muito consulte o XPath em uso, como o uso extensivo de código herdado, usando o XPath com LINQ to XML não é recomendada. Consultas de XPath não são executadas tão bem quanto consultas de [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria uma árvore XML pequena e usa <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> para selecionar um conjunto de elementos.  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <Child1>1</Child1>  
        <Child1>2</Child1>  
        <Child1>3</Child1>  
        <Child2>4</Child2>  
        <Child2>5</Child2>  
        <Child2>6</Child2>  
    </Root>  
  
Dim list As IEnumerable(Of XElement) = root.XPathSelectElements("./Child2")  
For Each el As XElement In list  
    Console.WriteLine(el)  
Next  
```  
  
 Este exemplo gera a seguinte saída:  
  
```xml  
<Child2>4</Child2>  
<Child2>5</Child2>  
<Child2>6</Child2>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Técnicas avançadas de consulta (LINQ para XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
