---
title: "Como executar transformações de streaming de texto para XML (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 9b3bd941-d0ff-4f2d-ae41-7c3b81d8fae6
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 03c5ed5ef66db311ade751b5aad21de70b78f063
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-perform-streaming-transformations-of-text-to-xml-c"></a>Como executar transformações de streaming de texto para XML (C#)
Uma abordagem para processar um arquivo de texto é escrever um método de extensão que passa o arquivo de texto uma linha em uma hora usando a compilação de `yield return` . Você então pode escrever uma consulta LINQ que processa o arquivo de texto em uma forma adiada lazy. Se você usar <xref:System.Xml.Linq.XStreamingElement> para passar saída, então você pode criar uma transformação de arquivo de texto para XML que usa uma quantidade mínima de memória, independentemente do tamanho do arquivo de texto de origem.  
  
 Há algumas restrições em relação às transformações de streaming. Uma transformação de streaming é aplicada melhor em situações onde você pode processar o arquivo inteiro uma vez, e se você pode processar linhas na ordem que ocorrem no documento de origem. Se você precisa processar o arquivo mais de uma vez, ou se você precisa classificar as linhas antes que você possa processar as, você perderá muitos benefícios de usar uma técnica de streaming.  
  
## <a name="example"></a>Exemplo  
 O seguinte arquivo de texto, People.txt, é a fonte para esse exemplo.  
  
```  
#This is a comment  
1,Tai,Yee,Writer  
2,Nikolay,Grachev,Programmer  
3,David,Wright,Inventor  
```  
  
 O código a seguir contém um método de extensão que passa as linhas do arquivo de texto em uma forma adiada.  
  
```csharp  
public static class StreamReaderSequence  
{  
    public static IEnumerable<string> Lines(this StreamReader source)  
    {  
        String line;  
  
        if (source == null)  
            throw new ArgumentNullException("source");  
        while ((line = source.ReadLine()) != null)  
        {  
            yield return line;  
        }  
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        StreamReader sr = new StreamReader("People.txt");  
        XStreamingElement xmlTree = new XStreamingElement("Root",  
            from line in sr.Lines()  
            let items = line.Split(',')  
            where !line.StartsWith("#")  
            select new XElement("Person",  
                       new XAttribute("ID", items[0]),  
                       new XElement("First", items[1]),  
                       new XElement("Last", items[2]),  
                       new XElement("Occupation", items[3])  
                   )  
        );  
        Console.WriteLine(xmlTree);  
        sr.Close();  
    }  
}  
```  
  
 Este exemplo gera a seguinte saída:  
  
```xml  
<Root>  
  <Person ID="1">  
    <First>Tai</First>  
    <Last>Yee</Last>  
    <Occupation>Writer</Occupation>  
  </Person>  
  <Person ID="2">  
    <First>Nikolay</First>  
    <Last>Grachev</Last>  
    <Occupation>Programmer</Occupation>  
  </Person>  
  <Person ID="3">  
    <First>David</First>  
    <Last>Wright</Last>  
    <Occupation>Inventor</Occupation>  
  </Person>  
</Root>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Xml.Linq.XStreamingElement>  
 [Técnicas avançadas de consulta (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
