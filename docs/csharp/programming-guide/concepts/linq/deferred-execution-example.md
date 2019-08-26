---
title: Exemplo de execução adiada (C#)
ms.date: 07/20/2015
ms.assetid: 50f4fbac-81fe-4f26-aedf-506e21419b19
ms.openlocfilehash: a934645d0d7ad807e1524031ca3f023f7b11c5b4
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69594549"
---
# <a name="deferred-execution-example-c"></a><span data-ttu-id="a27ce-102">Exemplo de execução adiada (C#)</span><span class="sxs-lookup"><span data-stu-id="a27ce-102">Deferred Execution Example (C#)</span></span>
<span data-ttu-id="a27ce-103">Este tópico mostra como execução adiada e a avaliação lazy afetam a execução das consultas LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="a27ce-103">This topic shows how deferred execution and lazy evaluation affect the execution of your LINQ to XML queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a27ce-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a27ce-104">Example</span></span>  
 <span data-ttu-id="a27ce-105">O exemplo a seguir mostra a ordem de execução para usar um método de extensão que use a execução adiada.</span><span class="sxs-lookup"><span data-stu-id="a27ce-105">The following example shows the order of execution when using an extension method that uses deferred execution.</span></span> <span data-ttu-id="a27ce-106">O exemplo declara uma matriz de três cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="a27ce-106">The example declares an array of three strings.</span></span> <span data-ttu-id="a27ce-107">Em itera através da coleção retornada por `ConvertCollectionToUpperCase`.</span><span class="sxs-lookup"><span data-stu-id="a27ce-107">It then iterates through the collection returned by `ConvertCollectionToUpperCase`.</span></span>  
  
```csharp  
public static class LocalExtensions  
{  
    public static IEnumerable<string>  
      ConvertCollectionToUpperCase(this IEnumerable<string> source)  
    {  
        foreach (string str in source)  
        {  
            Console.WriteLine("ToUpper: source {0}", str);  
            yield return str.ToUpper();  
        }  
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        string[] stringArray = { "abc", "def", "ghi" };  
  
        var q = from str in stringArray.ConvertCollectionToUpperCase()  
                select str;  
  
        foreach (string str in q)  
            Console.WriteLine("Main: str {0}", str);  
    }  
}  
```  
  
 <span data-ttu-id="a27ce-108">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="a27ce-108">This example produces the following output:</span></span>  
  
```  
ToUpper: source abc  
Main: str ABC  
ToUpper: source def  
Main: str DEF  
ToUpper: source ghi  
Main: str GHI  
```  
  
 <span data-ttu-id="a27ce-109">Observe que para iterar através da coleção retornada por `ConvertCollectionToUpperCase`, cada item é recuperado de matriz de cadeias de caracteres de origem e convertido para maiúsculas antes que o próximo item é recuperado de matriz de cadeias de caracteres de origem.</span><span class="sxs-lookup"><span data-stu-id="a27ce-109">Notice that when iterating through the collection returned by `ConvertCollectionToUpperCase`, each item is retrieved from the source string array and converted to uppercase before the next item is retrieved from the source string array.</span></span>  
  
 <span data-ttu-id="a27ce-110">Você pode ver que a matriz inteira de cadeias de caracteres não é convertida para maiúsculas antes que cada item na coleção retornada é processado no loop de `foreach` em `Main`.</span><span class="sxs-lookup"><span data-stu-id="a27ce-110">You can see that the entire array of strings is not converted to uppercase before each item in the returned collection is processed in the `foreach` loop in `Main`.</span></span>  
  
 <span data-ttu-id="a27ce-111">O próximo tópico neste tutorial mostra o encadeamento consultas em conjunto:</span><span class="sxs-lookup"><span data-stu-id="a27ce-111">The next topic in this tutorial illustrates chaining queries together:</span></span>  
  
- [<span data-ttu-id="a27ce-112">Exemplo de encadeamento de consultas (C#)</span><span class="sxs-lookup"><span data-stu-id="a27ce-112">Chaining Queries Example (C#)</span></span>](./chaining-queries-example.md)  
  
## <a name="see-also"></a><span data-ttu-id="a27ce-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a27ce-113">See also</span></span>

- [<span data-ttu-id="a27ce-114">Tutorial: Encadeando consultas (C#)</span><span class="sxs-lookup"><span data-stu-id="a27ce-114">Tutorial: Chaining Queries Together (C#)</span></span>](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
