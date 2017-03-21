---
title: Consultando um XDocument vs. Consultando um XElement (Visual Basic) | Documentos do Microsoft
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
ms.assetid: 2d111f84-0ded-4cde-8d93-5440557a726d
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 29044cd118bfd8ecc12bddca722ee3656d455e0f
ms.lasthandoff: 03/13/2017


---
# <a name="querying-an-xdocument-vs-querying-an-xelement-visual-basic"></a>Consultando um XDocument vs. Consultando um XElement (Visual Basic)
Quando você carrega um documento via <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName>, você observará que você precisa escrever consultas ligeiramente diferente que quando você carrega via <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName>.</xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName> </xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName>  
  
## <a name="comparison-of-xdocumentload-and-xelementload"></a>Comparação de XDocument.Load e de XElement.Load  
 Quando você carrega um documento XML em um <xref:System.Xml.Linq.XElement>via <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName>, o <xref:System.Xml.Linq.XElement>na raiz do XML árvore contém o elemento raiz do documento carregado.</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName> </xref:System.Xml.Linq.XElement> No entanto, quando você carrega o mesmo documento XML em uma <xref:System.Xml.Linq.XDocument>via <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName>, a raiz da árvore é um <xref:System.Xml.Linq.XDocument>nó e o elemento raiz do documento carregado é o filho permitidos um <xref:System.Xml.Linq.XElement>nó de <xref:System.Xml.Linq.XDocument>.</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName> </xref:System.Xml.Linq.XDocument> Os eixos [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] operam em relação ao nó raiz.  
  
 Neste primeiro exemplo carrega uma árvore XML usando <xref:System.Xml.Linq.XElement.Load%2A>.</xref:System.Xml.Linq.XElement.Load%2A> Em seguida, ele consulta os elementos filho da raiz da árvore.  
  
```vb  
' Create a simple document and  write it to a file  
File.WriteAllText("Test.xml", "<Root>" + Environment.NewLine + _  
    "    <Child1>1</Child1>" + Environment.NewLine + _  
    "    <Child2>2</Child2>" + Environment.NewLine + _  
    "    <Child3>3</Child3>" + Environment.NewLine + _  
    "</Root>")  
  
Console.WriteLine("Querying tree loaded with XElement.Load")  
Console.WriteLine("----")  
Dim doc As XElement = XElement.Load("Test.xml")  
Dim childList As IEnumerable(Of XElement) = _  
        From el In doc.Elements() _  
        Select el  
For Each e As XElement In childList  
    Console.WriteLine(e)  
Next  
```  
  
 Como esperado, Este exemplo gera a seguinte saída:  
  
```  
Querying tree loaded with XElement.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
 O exemplo a seguir é o mesmo que a especificada acima, com exceção de que a árvore XML é carregada em um <xref:System.Xml.Linq.XDocument>em vez de <xref:System.Xml.Linq.XElement>.</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XDocument>  
  
```vb  
' Create a simple document and  write it to a file  
File.WriteAllText("Test.xml", "<Root>" + Environment.NewLine + _  
    "    <Child1>1</Child1>" + Environment.NewLine + _  
    "    <Child2>2</Child2>" + Environment.NewLine + _  
    "    <Child3>3</Child3>" + Environment.NewLine + _  
    "</Root>")  
  
Console.WriteLine("Querying tree loaded with XDocument.Load")  
Console.WriteLine("----")  
Dim doc As XDocument = XDocument.Load("Test.xml")  
Dim childList As IEnumerable(Of XElement) = _  
        From el In doc.Elements() _  
        Select el  
For Each e As XElement In childList  
    Console.WriteLine(e)  
Next  
```  
  
 Este exemplo gera a seguinte saída:  
  
```  
Querying tree loaded with XDocument.Load  
----  
<Root>  
  <Child1>1</Child1>  
  <Child2>2</Child2>  
  <Child3>3</Child3>  
</Root>  
```  
  
 Observe que a mesma consulta retornou o nó `Root` em vez dos três nós filho.  
  
 Uma abordagem para lidar com isso é usar o <xref:System.Xml.Linq.XDocument.Root%2A>propriedade antes de acessar os métodos de eixos, da seguinte maneira:</xref:System.Xml.Linq.XDocument.Root%2A>  
  
```vb  
' Create a simple document and  write it to a file  
File.WriteAllText("Test.xml", "<Root>" + Environment.NewLine + _  
    "    <Child1>1</Child1>" + Environment.NewLine + _  
    "    <Child2>2</Child2>" + Environment.NewLine + _  
    "    <Child3>3</Child3>" + Environment.NewLine + _  
    "</Root>")  
  
Console.WriteLine("Querying tree loaded with XDocument.Load")  
Console.WriteLine("----")  
Dim doc As XDocument = XDocument.Load("Test.xml")  
Dim childList As IEnumerable(Of XElement) = _  
        From el In doc.Root.Elements() _  
        Select el  
For Each e As XElement In childList  
    Console.WriteLine(e)  
Next  
```  
  
 Essa consulta agora executa da mesma forma que a consulta na árvore enraizada em <xref:System.Xml.Linq.XElement>.</xref:System.Xml.Linq.XElement> O exemplo produz a seguinte saída:  
  
```  
Querying tree loaded with XDocument.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Consultas básicas (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
