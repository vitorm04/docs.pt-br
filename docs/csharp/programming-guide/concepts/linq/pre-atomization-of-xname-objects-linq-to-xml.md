---
title: "Pré-atomização de objetos XName (LINQ to XML) (C#)"
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
ms.assetid: e84fbbe7-f072-4771-bfbb-059d18e1ad15
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: bc71a1a5b6d8fe038a9eefaff1649df0ea81aa02
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="pre-atomization-of-xname-objects-linq-to-xml-c"></a>Pré-atomização de objetos XName (LINQ to XML) (C#)
Uma maneira para melhorar o desempenho em LINQ to XML é pré-compilação atomizar objetos de <xref:System.Xml.Linq.XName> . a pré-compilação atomização significa que você atribuir uma cadeia de caracteres a um objeto de <xref:System.Xml.Linq.XName> antes de criar a árvore XML usando os construtores de classes de <xref:System.Xml.Linq.XElement> e de <xref:System.Xml.Linq.XAttribute> . Em seguida, em vez de passar uma cadeia de caracteres para o construtor, que usaria a conversão implícita de cadeia de caracteres a <xref:System.Xml.Linq.XName>, você passa o objeto inicializado de <xref:System.Xml.Linq.XName> .  
  
 Isso melhora o desempenho quando você cria uma grande árvore XML em que os nomes específicos são repetidos. Para fazer isso, você declarar e inicializar objetos de <xref:System.Xml.Linq.XName> antes que você construa a árvore XML e em seguida, usar objetos de <xref:System.Xml.Linq.XName> em vez de especificar cadeias de caracteres para nomes de elementos e atributos. Essa técnica pode produzir ganhos significativos de desempenho se você estiver criando um grande número de elementos ou atributos () com o mesmo nome.  
  
 Você deve testar a pré-compilação atomização com seu cenário para decidir se você usar o.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra isso.  
  
```csharp  
XName Root = "Root";  
XName Data = "Data";  
XName ID = "ID";  
  
XElement root = new XElement(Root,  
    new XElement(Data,  
        new XAttribute(ID, "1"),  
        "4,100,000"),  
    new XElement(Data,  
        new XAttribute(ID, "2"),  
        "3,700,000"),  
    new XElement(Data,  
        new XAttribute(ID, "3"),  
        "1,150,000")  
);  
  
Console.WriteLine(root);  
```  
  
 Este exemplo gera a seguinte saída:  
  
```xml  
<Root>  
  <Data ID="1">4,100,000</Data>  
  <Data ID="2">3,700,000</Data>  
  <Data ID="3">1,150,000</Data>  
</Root>  
```  
  
 O exemplo a seguir mostra a mesma técnica onde o documento XML é em um namespace:  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XName Root = aw + "Root";  
XName Data = aw + "Data";  
XName ID = "ID";  
  
XElement root = new XElement(Root,  
    new XAttribute(XNamespace.Xmlns + "aw", aw),  
    new XElement(Data,  
        new XAttribute(ID, "1"),  
        "4,100,000"),  
    new XElement(Data,  
        new XAttribute(ID, "2"),  
        "3,700,000"),  
    new XElement(Data,  
        new XAttribute(ID, "3"),  
        "1,150,000")  
);  
  
Console.WriteLine(root);  
```  
  
 Este exemplo gera a seguinte saída:  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Data ID="1">4,100,000</aw:Data>  
  <aw:Data ID="2">3,700,000</aw:Data>  
  <aw:Data ID="3">1,150,000</aw:Data>  
</aw:Root>  
```  
  
 O exemplo a seguir é mais semelhante ao que você provavelmente encontrará no mundo real. Nesse exemplo, o conteúdo do elemento é fornecido por uma consulta:  
  
```csharp  
XName Root = "Root";  
XName Data = "Data";  
XName ID = "ID";  
  
DateTime t1 = DateTime.Now;  
XElement root = new XElement(Root,  
    from i in System.Linq.Enumerable.Range(1, 100000)  
    select new XElement(Data,  
        new XAttribute(ID, i),  
        i * 5)  
);  
DateTime t2 = DateTime.Now;  
  
Console.WriteLine("Time to construct:{0}", t2 - t1);  
```  
  
 O exemplo anterior executa melhor do que o exemplo, em que os nomes não são atomizados passos:  
  
```csharp  
DateTime t1 = DateTime.Now;  
XElement root = new XElement("Root",  
    from i in System.Linq.Enumerable.Range(1, 100000)  
    select new XElement("Data",  
        new XAttribute("ID", i),  
        i * 5)  
);  
DateTime t2 = DateTime.Now;  
  
Console.WriteLine("Time to construct:{0}", t2 - t1);  
```  
  
## <a name="see-also"></a>Consulte também  
 [Desempenho (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/performance-linq-to-xml.md)   
 [Objetos XName e XNamespace atomizados (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/atomized-xname-and-xnamespace-objects-linq-to-xml.md)

