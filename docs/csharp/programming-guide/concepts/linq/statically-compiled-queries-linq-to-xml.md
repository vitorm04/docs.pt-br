---
title: Consultas estaticamente compiladas (LINQ to XML) (C#) | Microsoft Docs
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 3bf558fe-0705-479d-86d4-00188f5fcf9c
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 10e4df75be88dc5609e0ca15666042a0354824bc
ms.lasthandoff: 03/13/2017


---
# <a name="statically-compiled-queries-linq-to-xml-c"></a>Consultas estaticamente compiladas (LINQ to XML) (C#)
Um dos benefícios de desempenho mais importantes do LINQ to XML, em oposição ao <xref:System.Xml.XmlDocument>, é que as consultas no LINQ to XML são compiladas estatisticamente compiladas, ao passo que as consultas XPath devem ser interpretadas em tempo de execução. Esse recurso é interna a LINQ to XML, portanto você não precisa executar etapas adicionais para aproveitá-lo, mas é útil entender a diferença ao escolher entre as duas tecnologias. Este tópico explica a diferença.  
  
## <a name="statically-compiled-queries-vs-xpath"></a>Consultas estaticamente compilado contra. XPath  
 O exemplo a seguir mostra como obter os elementos descendentes com um nome especificado e, com um atributo com um valor especificado.  
  
 O seguinte é a expressão XPath equivalente:  
  
```  
//Address[@Type='Shipping']  
```  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    from el in po.Descendants("Address")  
    where (string)el.Attribute("Type") == "Shipping"  
    select el;  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 A expressão de consulta nesse exemplo é reescrita pelo compilador a sintaxe da consulta com base em método. O exemplo a seguir, que é escrito na sintaxe da consulta com base em método, gerenciar os mesmos resultados que anterior:  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    po  
    .Descendants("Address")  
    .Where(el => (string)el.Attribute("Type") == "Shipping");  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 O método <xref:System.Linq.Enumerable.Where%2A> é um método de extensão. Para obter mais informações, consulte [Métodos de extensão](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md). Como <xref:System.Linq.Enumerable.Where%2A> é um método de extensão, a consulta acima é compilada como se tivesse sido escrita da seguinte forma:  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    System.Linq.Enumerable.Where(  
        po.Descendants("Address"),  
        el => (string)el.Attribute("Type") == "Shipping");  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 Este exemplo gerencia exatamente os mesmos resultados que os dois exemplos anteriores. Isso ilustra o fato de que as consultas são compiladas efetivamente estaticamente associados em chamadas de método. Isso, combinado com a semântica de execução adiada de iteradores, melhora o desempenho. Para obter mais informações sobre a semântica de execução adiada dos iteradores, consulte [Execução adiada e avaliação lenta em LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).  
  
> [!NOTE]
>  Esses exemplos são representante de código que o compilador pode escrever. A implementação real pode diferir um pouco desses exemplos, mas o desempenho será o mesmo ou semelhante a esses exemplos.  
  
## <a name="executing-xpath-expressions-with-xmldocument"></a>Executando com expressões XPath XmlDocument  
 O exemplo a seguir usa <xref:System.Xml.XmlDocument> para executar os mesmos resultados que os exemplos anteriores:  
  
```csharp  
XmlReader reader = XmlReader.Create("PurchaseOrders.xml");  
XmlDocument doc = new XmlDocument();  
doc.Load(reader);  
XmlNodeList nl = doc.SelectNodes(".//Address[@Type='Shipping']");  
foreach (XmlNode n in nl)  
    Console.WriteLine(n.OuterXml);  
reader.Close();  
```  
  
 Esta consulta retorna a mesma saída que os exemplos que usam o LINQ to XML, a única diferença é que o LINQ to XML recua o XML impresso, enquanto o <xref:System.Xml.XmlDocument> não.  
  
 No entanto, a abordagem de <xref:System.Xml.XmlDocument> geralmente não tem um desempenho tão bom quanto o LINQ to XML porque o método <xref:System.Xml.XmlNode.SelectNodes%2A> precisa fazer o seguinte internamente sempre que é chamado:  
  
-   Analisa a cadeia de caracteres que contém a expressão XPath, quebrando a cadeia de caracteres em tokens.  
  
-   Valida os tokens para certificar-se de que a expressão XPath é válido.  
  
-   Converte a expressão em uma árvore de expressão interna.  
  
-   Itera através de nós, selecionando adequadamente os nós para o conjunto de resultados com base na avaliação da expressão.  
  
 Este é significativamente mais do que o trabalho feito pela consulta correspondente LINQ to XML. A diferença de desempenho específica varia para tipos diferentes de consultas, mas em geral as consultas LINQ to XML realizam menos trabalho e, portanto, têm um desempenho menor do que as expressões XPath de avaliação usando <xref:System.Xml.XmlDocument>.  
  
## <a name="see-also"></a>Consulte também  
 [Desempenho (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/performance-linq-to-xml.md)
