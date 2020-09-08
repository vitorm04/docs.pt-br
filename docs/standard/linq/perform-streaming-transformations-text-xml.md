---
title: Como executar transformações de streaming de texto em XML em C#-LINQ to XML
description: Você pode usar um método de extensão que libera uma linha por vez para transmitir um arquivo de texto para processamento. Essa técnica reduz os requisitos de memória em comparação com as técnicas que carregam todo o arquivo e depois o processam.
ms.date: 07/20/2015
dev_langs:
- csharp
ms.assetid: 9b3bd941-d0ff-4f2d-ae41-7c3b81d8fae6
ms.openlocfilehash: 8e0d710d7cbc6de8cc60721c211376a82b6c29fc
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552308"
---
# <a name="how-to-perform-streaming-transformations-of-text-to-xml-in-c-linq-to-xml"></a><span data-ttu-id="7a3dd-104">Como executar transformações de streaming de texto em XML em C# (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="7a3dd-104">How to perform streaming transformations of text to XML in C# (LINQ to XML)</span></span>

<span data-ttu-id="7a3dd-105">Você pode usar um método de extensão que libera uma linha por vez para transmitir um arquivo de texto para processamento.</span><span class="sxs-lookup"><span data-stu-id="7a3dd-105">You can use an extension method that releases a line at a time to stream a text file for processing.</span></span> <span data-ttu-id="7a3dd-106">Essa técnica reduz os requisitos de memória em comparação com as técnicas que carregam todo o arquivo e depois o processam.</span><span class="sxs-lookup"><span data-stu-id="7a3dd-106">This technique reduces memory requirements compared to techniques which load the entire file and then process it.</span></span>

<span data-ttu-id="7a3dd-107">O método de extensão pode fornecer a linha usando a `yield return` construção.</span><span class="sxs-lookup"><span data-stu-id="7a3dd-107">The extension method can provide the line using the `yield return` construct.</span></span> <span data-ttu-id="7a3dd-108">Uma consulta LINQ pode processar o fluxo de forma retardada de modo lento.</span><span class="sxs-lookup"><span data-stu-id="7a3dd-108">A LINQ query can process the stream in a lazy deferred fashion.</span></span> <span data-ttu-id="7a3dd-109">Se você usar <xref:System.Xml.Linq.XStreamingElement> o para transmitir a saída, poderá criar uma transformação do arquivo de texto para XML que usa uma quantidade mínima de memória, independentemente do tamanho do arquivo de texto de origem.</span><span class="sxs-lookup"><span data-stu-id="7a3dd-109">If you use <xref:System.Xml.Linq.XStreamingElement> to stream output, you can create a transformation from the text file to XML that uses a minimal amount of memory, regardless of the size of the source text file.</span></span>

> [!NOTE]
> <span data-ttu-id="7a3dd-110">A técnica é melhor aplicada em situações nas quais você pode processar todo o arquivo uma vez, levando em ordem as linhas do documento de origem.</span><span class="sxs-lookup"><span data-stu-id="7a3dd-110">The technique is best applied in situations in which you can process the entire file once, taking the lines in order from the source document.</span></span> <span data-ttu-id="7a3dd-111">O processamento do arquivo mais de uma vez ou a classificação antes do processamento reduz os benefícios de desempenho de uma técnica de streaming.</span><span class="sxs-lookup"><span data-stu-id="7a3dd-111">Processing the file more than once, or sorting before processing, reduces the performance benefits of a streaming technique.</span></span>

## <a name="example-use-an-extension-method-to-stream-text"></a><span data-ttu-id="7a3dd-112">Exemplo de uso de um método de extensão para transmitir texto</span><span class="sxs-lookup"><span data-stu-id="7a3dd-112">Example Use an extension method to stream text</span></span>

<span data-ttu-id="7a3dd-113">O exemplo usa o seguinte arquivo de texto, People.txt, como sua fonte:</span><span class="sxs-lookup"><span data-stu-id="7a3dd-113">The example uses the following text file, People.txt, as its source:</span></span>

```text
#This is a comment
1,Tai,Yee,Writer
2,Nikolay,Grachev,Programmer
3,David,Wright,Inventor
```

<span data-ttu-id="7a3dd-114">No código para o exemplo, o método de extensão `Lines` fornece o texto uma linha por vez:</span><span class="sxs-lookup"><span data-stu-id="7a3dd-114">In the code for the example, extension method `Lines` provides the text a line at a time:</span></span>

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

<span data-ttu-id="7a3dd-115">O exemplo produz a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="7a3dd-115">The example produces the following output:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="7a3dd-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="7a3dd-116">See also</span></span>

- <xref:System.Xml.Linq.XStreamingElement>
