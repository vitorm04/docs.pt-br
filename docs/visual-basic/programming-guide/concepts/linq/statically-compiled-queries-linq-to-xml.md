---
title: Consultas estaticamente compiladas (LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 3f4825c7-c3b0-48da-ba4e-8e97fb2a2f34
ms.openlocfilehash: ff708dd14d27b34be797f1630dabe27a56c5a219
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61908330"
---
# <a name="statically-compiled-queries-linq-to-xml-visual-basic"></a>Consultas estaticamente compiladas (LINQ to XML) (Visual Basic)
Um de desempenho mais importante beneficia LINQ to XML, diferentemente de <xref:System.Xml.XmlDocument>, é que as consultas em LINQ to XML são compiladas estaticamente, enquanto as consultas XPath devem ser interpretado em tempo de execução. Esse recurso é interna a LINQ to XML, portanto você não precisa executar etapas adicionais para aproveitá-lo, mas é útil entender a diferença ao escolher entre as duas tecnologias. Este tópico explica a diferença.  
  
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
  
 O método de <xref:System.Linq.Enumerable.Where%2A> é um método de extensão. Para obter mais informações, consulte [Métodos de extensão](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md). Porque <xref:System.Linq.Enumerable.Where%2A> é um método de extensão, a consulta anterior é criada como se ele foi gravado como segue:  
  
```vb  
Dim po = XDocument.Load("PurchaseOrders.xml")  
  
Dim list1 = Enumerable.Where(po.Descendants("Address"), Function(el) el.@Type = "Shipping")  
  
For Each el In list1  
    Console.WriteLine(el)  
Next  
```  
  
 Este exemplo gerencia exatamente os mesmos resultados que os dois exemplos anteriores. Isso ilustra o fato de que as consultas são compiladas efetivamente estaticamente associados em chamadas de método. Isso, combinado com a semântica de execução adiada de iteradores, melhora o desempenho. Para obter mais informações sobre a semântica de execução adiada de iteradores, consulte [a execução adiada e avaliação lenta em LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).  
  
> [!NOTE]
>  Esses exemplos são representante de código que o compilador pode escrever. A implementação real pode diferir um pouco desses exemplos, mas o desempenho será o mesmo ou semelhante a esses exemplos.  
  
## <a name="executing-xpath-expressions-with-xmldocument"></a>Executando com expressões XPath XmlDocument  
 O exemplo a seguir usa <xref:System.Xml.XmlDocument> para executar os mesmos resultados que os exemplos anteriores:  
  
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
  
 Esta consulta retorna as mesmas saída que os exemplos que usam LINQ to XML; a única diferença é que LINQ to XML recua XML impresso, enquanto <xref:System.Xml.XmlDocument> não.  
  
 No entanto, a abordagem de <xref:System.Xml.XmlDocument> geralmente não executa bem como LINQ to XML, porque o método de <xref:System.Xml.XmlNode.SelectNodes%2A> deve fazer o seguinte internamente todas as vezes nele é chamado:  
  
- Analisa a cadeia de caracteres que contém a expressão XPath, quebrando a cadeia de caracteres em tokens.  
  
- Valida os tokens para certificar-se de que a expressão XPath é válido.  
  
- Converte a expressão em uma árvore de expressão interna.  
  
- Itera através de nós, selecionando adequadamente os nós para o conjunto de resultados com base na avaliação da expressão.  
  
 Este é significativamente mais do que o trabalho feito pela consulta correspondente LINQ to XML. A diferença desempenho específico variam para tipos diferentes de consultas, mas em geral LINQ to XML consultas menos trabalho e, portanto, executam melhor do que as expressões XPath de avaliação usando <xref:System.Xml.XmlDocument>.  
  
## <a name="see-also"></a>Consulte também

- [Desempenho (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
