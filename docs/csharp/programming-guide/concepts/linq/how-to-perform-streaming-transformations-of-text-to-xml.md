---
title: 'Como: Executar transformações de streaming de texto para XML (C#)'
ms.date: 07/20/2015
ms.assetid: 9b3bd941-d0ff-4f2d-ae41-7c3b81d8fae6
ms.openlocfilehash: 906150483f7f76b4429ea390d083e9f18696ac9e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54555876"
---
# <a name="how-to-perform-streaming-transformations-of-text-to-xml-c"></a><span data-ttu-id="9dc45-102">Como: Executar transformações de streaming de texto para XML (C#)</span><span class="sxs-lookup"><span data-stu-id="9dc45-102">How to: Perform Streaming Transformations of Text to XML (C#)</span></span>
<span data-ttu-id="9dc45-103">Uma abordagem para processar um arquivo de texto é escrever um método de extensão que passa o arquivo de texto uma linha em uma hora usando a compilação de `yield return` .</span><span class="sxs-lookup"><span data-stu-id="9dc45-103">One approach to processing a text file is to write an extension method that streams the text file a line at a time using the `yield return` construct.</span></span> <span data-ttu-id="9dc45-104">Você então pode escrever uma consulta LINQ que processa o arquivo de texto em uma forma adiada lazy.</span><span class="sxs-lookup"><span data-stu-id="9dc45-104">You then can write a LINQ query that processes the text file in a lazy deferred fashion.</span></span> <span data-ttu-id="9dc45-105">Se você usar <xref:System.Xml.Linq.XStreamingElement> para passar saída, então você pode criar uma transformação de arquivo de texto para XML que usa uma quantidade mínima de memória, independentemente do tamanho do arquivo de texto de origem.</span><span class="sxs-lookup"><span data-stu-id="9dc45-105">If you then use <xref:System.Xml.Linq.XStreamingElement> to stream output, you then can create a transformation from the text file to XML that uses a minimal amount of memory, regardless of the size of the source text file.</span></span>  
  
 <span data-ttu-id="9dc45-106">Há algumas restrições em relação às transformações de streaming.</span><span class="sxs-lookup"><span data-stu-id="9dc45-106">There are some caveats regarding streaming transformations.</span></span> <span data-ttu-id="9dc45-107">Uma transformação de streaming é aplicada melhor em situações onde você pode processar o arquivo inteiro uma vez, e se você pode processar linhas na ordem que ocorrem no documento de origem.</span><span class="sxs-lookup"><span data-stu-id="9dc45-107">A streaming transformation is best applied in situations where you can process the entire file once, and if you can process the lines in the order that they occur in the source document.</span></span> <span data-ttu-id="9dc45-108">Se você precisa processar o arquivo mais de uma vez, ou se você precisa classificar as linhas antes que você possa processar as, você perderá muitos benefícios de usar uma técnica de streaming.</span><span class="sxs-lookup"><span data-stu-id="9dc45-108">If you have to process the file more than once, or if you have to sort the lines before you can process them, you will lose many of the benefits of using a streaming technique.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9dc45-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9dc45-109">Example</span></span>  
 <span data-ttu-id="9dc45-110">O seguinte arquivo de texto, People.txt, é a fonte para esse exemplo.</span><span class="sxs-lookup"><span data-stu-id="9dc45-110">The following text file, People.txt, is the source for this example.</span></span>  
  
```  
#This is a comment  
1,Tai,Yee,Writer  
2,Nikolay,Grachev,Programmer  
3,David,Wright,Inventor  
```  
  
 <span data-ttu-id="9dc45-111">O código a seguir contém um método de extensão que passa as linhas do arquivo de texto em uma forma adiada.</span><span class="sxs-lookup"><span data-stu-id="9dc45-111">The following code contains an extension method that streams the lines of the text file in a deferred fashion.</span></span>  
  
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
  
 <span data-ttu-id="9dc45-112">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="9dc45-112">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9dc45-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9dc45-113">See also</span></span>

- <xref:System.Xml.Linq.XStreamingElement>
- [<span data-ttu-id="9dc45-114">Técnicas avançadas de consulta (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="9dc45-114">Advanced Query Techniques (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
