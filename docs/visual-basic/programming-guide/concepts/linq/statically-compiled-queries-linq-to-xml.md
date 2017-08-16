---
title: Compilado estaticamente consultas (LINQ to XML) (Visual Basic) | Documentos do Microsoft
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
ms.assetid: 3f4825c7-c3b0-48da-ba4e-8e97fb2a2f34
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 2ea8e71acf861b93a21296c74254b3ca4d977d0a
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017


---
# <a name="statically-compiled-queries-linq-to-xml-visual-basic"></a>Compilado estaticamente consultas (LINQ to XML) (Visual Basic)
Um desempenho mais importante beneficia LINQ to XML, em vez de <xref:System.Xml.XmlDocument>, é que consultas no LINQ to XML são compiladas estaticamente, enquanto as consultas XPath devem ser interpretadas em tempo de execução.</xref:System.Xml.XmlDocument> Esse recurso é interna a LINQ to XML, portanto você não precisa executar etapas adicionais para aproveitá-lo, mas é útil entender a diferença ao escolher entre as duas tecnologias. Este tópico explica a diferença.  
  
## <a name="statically-compiled-queries-vs-xpath"></a>Consultas estaticamente compilado contra. XPath  
 O exemplo a seguir mostra como obter os elementos descendentes com um nome especificado e, com um atributo com um valor especificado.  
  
 O seguinte é a expressão XPath equivalente:  
  
```  
//Address[@Type='Shipping']  
```  
  
```vb  
Dim po = XDocument.Load("PurchaseOrders.xml")  
  
Dim list1 = From el In po.Descendants("Address")  
            Where el.@Type = "Shipping"  
  
For Each el In list1  
    Console.WriteLine(el)  
Next  
```  
  
 A expressão de consulta nesse exemplo é reescrita pelo compilador a sintaxe da consulta com base em método. O exemplo a seguir, que é escrito na sintaxe da consulta com base em método, gerenciar os mesmos resultados que anterior:  
  
```vb  
Dim po = XDocument.Load("PurchaseOrders.xml")  
  
Dim list1 As IEnumerable(Of XElement) = po.Descendants("Address").Where(Function(el) el.@Type = "Shipping")  
  
For Each el In list1  
    Console.WriteLine(el)  
Next   
```  
  
 O <xref:System.Linq.Enumerable.Where%2A>método é um método de extensão.</xref:System.Linq.Enumerable.Where%2A> Para obter mais informações, consulte [métodos de extensão](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md). Porque <xref:System.Linq.Enumerable.Where%2A>é um método de extensão, a consulta acima é compilada como se tivesse sido feita da seguinte maneira:</xref:System.Linq.Enumerable.Where%2A>  
  
```vb  
Dim po = XDocument.Load("PurchaseOrders.xml")  
  
Dim list1 = Enumerable.Where(po.Descendants("Address"), Function(el) el.@Type = "Shipping")  
  
For Each el In list1  
    Console.WriteLine(el)  
Next  
```  
  
 Este exemplo gerencia exatamente os mesmos resultados que os dois exemplos anteriores. Isso ilustra o fato de que as consultas são compiladas efetivamente estaticamente associados em chamadas de método. Isso, combinado com a semântica de execução adiada de iteradores, melhora o desempenho. Para obter mais informações sobre a semântica de execução adiada de iteradores, consulte [execução adiada e avaliação lenta em LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).  
  
> [!NOTE]
>  Esses exemplos são representante de código que o compilador pode escrever. A implementação real pode diferir um pouco desses exemplos, mas o desempenho será o mesmo ou semelhante a esses exemplos.  
  
## <a name="executing-xpath-expressions-with-xmldocument"></a>Executando com expressões XPath XmlDocument  
 O exemplo a seguir usa <xref:System.Xml.XmlDocument>para alcançar os mesmos resultados que os exemplos anteriores:</xref:System.Xml.XmlDocument>  
  
```vb  
Dim reader = Xml.XmlReader.Create("PurchaseOrders.xml")  
Dim doc As New Xml.XmlDocument()  
doc.Load(reader)  
Dim nl As Xml.XmlNodeList = doc.SelectNodes(".//Address[@Type='Shipping']")  
For Each n As Xml.XmlNode In nl  
    Console.WriteLine(n.OuterXml)  
Next  
reader.Close()  
```  
  
 Esta consulta retorna o mesmo resultado que os exemplos que usam LINQ para XML; a única diferença é que o LINQ to XML recua XML impresso, enquanto <xref:System.Xml.XmlDocument>não.</xref:System.Xml.XmlDocument>  
  
 No entanto, o <xref:System.Xml.XmlDocument>abordagem geralmente não executam bem como o LINQ to XML, porque o <xref:System.Xml.XmlNode.SelectNodes%2A>método deve fazer o seguinte internamente toda vez que ele é chamado:</xref:System.Xml.XmlNode.SelectNodes%2A> </xref:System.Xml.XmlDocument>  
  
-   Analisa a cadeia de caracteres que contém a expressão XPath, quebrando a cadeia de caracteres em tokens.  
  
-   Valida os tokens para certificar-se de que a expressão XPath é válido.  
  
-   Converte a expressão em uma árvore de expressão interna.  
  
-   Itera através de nós, selecionando adequadamente os nós para o conjunto de resultados com base na avaliação da expressão.  
  
 Este é significativamente mais do que o trabalho feito pela consulta correspondente LINQ to XML. A diferença de desempenho específico variam para diferentes tipos de consultas, mas em geral menos trabalho consultas LINQ to XML e, portanto, têm desempenho melhor, que avaliar expressões XPath usando <xref:System.Xml.XmlDocument>.</xref:System.Xml.XmlDocument>  
  
## <a name="see-also"></a>Consulte também  
 [Desempenho (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)

