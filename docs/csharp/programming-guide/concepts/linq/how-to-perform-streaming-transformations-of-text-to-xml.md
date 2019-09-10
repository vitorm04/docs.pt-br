---
title: 'Como: Executar transformações de streaming de texto para XML (C#)'
ms.date: 07/20/2015
ms.assetid: 9b3bd941-d0ff-4f2d-ae41-7c3b81d8fae6
ms.openlocfilehash: 6dc48a7342bbeedb79e8e7f4a9270899be336f91
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70851031"
---
# <a name="how-to-perform-streaming-transformations-of-text-to-xml-c"></a>Como: Executar transformações de streaming de texto para XML (C#)

Uma abordagem para processar um arquivo de texto é escrever um método de extensão que passa o arquivo de texto uma linha em uma hora usando a compilação de `yield return` . Você então pode escrever uma consulta LINQ que processa o arquivo de texto em uma forma adiada lazy. Se você usar <xref:System.Xml.Linq.XStreamingElement> para passar saída, então você pode criar uma transformação de arquivo de texto para XML que usa uma quantidade mínima de memória, independentemente do tamanho do arquivo de texto de origem.

 Há algumas restrições em relação às transformações de streaming. Uma transformação de streaming é aplicada melhor em situações onde você pode processar o arquivo inteiro uma vez, e se você pode processar linhas na ordem que ocorrem no documento de origem. Se você precisa processar o arquivo mais de uma vez, ou se você precisa classificar as linhas antes que você possa processar as, você perderá muitos benefícios de usar uma técnica de streaming.

## <a name="example"></a>Exemplo

 O seguinte arquivo de texto, People.txt, é a fonte para esse exemplo.

```text
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
        if (source == null)
            throw new ArgumentNullException(nameof(source));

        string line;
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
        var sr = new StreamReader("People.txt");
        var xmlTree = new XStreamingElement("Root",
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

- <xref:System.Xml.Linq.XStreamingElement>
