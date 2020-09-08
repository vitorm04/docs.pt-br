---
title: Exemplo de execução adiada-LINQ to XML
description: Saiba como a execução retardada e a avaliação lenta afetam a execução de suas consultas de LINQ to XML.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 50f4fbac-81fe-4f26-aedf-506e21419b19
ms.openlocfilehash: 59784db895211aecbd263b5ee050734ecd16fa4b
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552012"
---
# <a name="deferred-execution-example-linq-to-xml"></a><span data-ttu-id="bf075-103">Exemplo de execução adiada (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="bf075-103">Deferred execution example (LINQ to XML)</span></span>

<span data-ttu-id="bf075-104">Este artigo mostra como a execução retardada e a avaliação lenta afetam a execução de suas consultas de LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="bf075-104">This article shows how deferred execution and lazy evaluation affect the execution of your LINQ to XML queries.</span></span>

## <a name="example-use-the-yield-return-construct-in-an-extension-method-to-defer-execution"></a><span data-ttu-id="bf075-105">Exemplo: usar a `yield return` construção em um método de extensão para adiar a execução</span><span class="sxs-lookup"><span data-stu-id="bf075-105">Example: Use the `yield return` construct in an extension method to defer execution</span></span>

<span data-ttu-id="bf075-106">O exemplo a seguir mostra a ordem de execução para usar um método de extensão que use a execução adiada.</span><span class="sxs-lookup"><span data-stu-id="bf075-106">The following example shows the order of execution when using an extension method that uses deferred execution.</span></span> <span data-ttu-id="bf075-107">O exemplo declara uma matriz de três cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="bf075-107">The example declares an array of three strings.</span></span> <span data-ttu-id="bf075-108">Em itera através da coleção retornada por `ConvertCollectionToUpperCase`.</span><span class="sxs-lookup"><span data-stu-id="bf075-108">It then iterates through the collection returned by `ConvertCollectionToUpperCase`.</span></span>

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

```vb
Imports System.Runtime.CompilerServices

Module Module1

    <Extension()>
    Private Iterator Function ConvertCollectionToUpperCase(
    ByVal source As IEnumerable(Of String)) _
    As IEnumerable(Of String)
        For Each str As String In source
            Console.WriteLine("ToUpper: source {0}", str)
            Yield str.ToUpper()
        Next
    End Function

    Sub Main()
        Dim stringArray = New String() {"abc", "def", "ghi"}

        Dim q = From str In stringArray.ConvertCollectionToUpperCase()
                Select str

        For Each Str As String In q
            Console.WriteLine("Main: str {0}", Str)
        Next
    End Sub

End Module
```

<span data-ttu-id="bf075-109">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="bf075-109">This example produces the following output:</span></span>

```output
ToUpper: source abc
Main: str ABC
ToUpper: source def
Main: str DEF
ToUpper: source ghi
Main: str GHI
```

<span data-ttu-id="bf075-110">Observe que para iterar através da coleção retornada por `ConvertCollectionToUpperCase`, cada item é recuperado de matriz de cadeias de caracteres de origem e convertido para maiúsculas antes que o próximo item é recuperado de matriz de cadeias de caracteres de origem.</span><span class="sxs-lookup"><span data-stu-id="bf075-110">Notice that when iterating through the collection returned by `ConvertCollectionToUpperCase`, each item is retrieved from the source string array and converted to uppercase before the next item is retrieved from the source string array.</span></span>

<span data-ttu-id="bf075-111">Você pode ver que toda a matriz de cadeias de caracteres não é convertida em maiúsculas antes que cada item na coleção retornada seja processado no `foreach` loop em `Main` .</span><span class="sxs-lookup"><span data-stu-id="bf075-111">You can see that the entire array of strings isn't converted to uppercase before each item in the returned collection is processed in the `foreach` loop in `Main`.</span></span>

## <a name="see-also"></a><span data-ttu-id="bf075-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="bf075-112">See also</span></span>

- [<span data-ttu-id="bf075-113">Execução retardada e avaliação lenta</span><span class="sxs-lookup"><span data-stu-id="bf075-113">Deferred execution and lazy evaluation</span></span>](deferred-execution-lazy-evaluation.md)
- [<span data-ttu-id="bf075-114">Tutorial: encadear consultas juntas (C#)</span><span class="sxs-lookup"><span data-stu-id="bf075-114">Tutorial: Chain queries together (C#)</span></span>](chain-queries-example.md)
