---
title: Materialização intermediária (C#)
description: Saiba como o uso de alguns operadores de consulta padrão pode causar a materialização de coleções em uma consulta e alterar drasticamente o perfil de memória e de desempenho do seu aplicativo.
ms.date: 07/20/2015
ms.assetid: 7922d38f-5044-41cf-8e17-7173d6553a5e
ms.openlocfilehash: 8dca4bb29886973762351049d06bcf5d3ba352db
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89551866"
---
# <a name="intermediate-materialization-c"></a><span data-ttu-id="c647c-103">Materialização intermediária (C#)</span><span class="sxs-lookup"><span data-stu-id="c647c-103">Intermediate materialization (C#)</span></span>

<span data-ttu-id="c647c-104">Se você não tiver cuidado, poderá, em algumas situações, alterar drasticamente o perfil de memória e desempenho do seu aplicativo, causando uma materialização prematura das coleções em suas consultas.</span><span class="sxs-lookup"><span data-stu-id="c647c-104">If you're not careful you can, in some situations, drastically alter the memory and performance profile of your application by causing premature materialization of collections in your queries.</span></span> <span data-ttu-id="c647c-105">Alguns operadores de consulta padrão faz com que o materialization de sua coleção de origem antes de produzir um único elemento.</span><span class="sxs-lookup"><span data-stu-id="c647c-105">Some standard query operators cause materialization of their source collection before yielding a single element.</span></span> <span data-ttu-id="c647c-106">Por exemplo, <xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType> primeiro itera através da coleção inteira de origem, então classe todos os itens, e então produz basicamente o primeiro item.</span><span class="sxs-lookup"><span data-stu-id="c647c-106">For example, <xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType> first iterates through its entire source collection, then sorts all items, and then finally yields the first item.</span></span> <span data-ttu-id="c647c-107">Isso significa que é caro obter o primeiro item de uma coleção ordenada; em seguida, cada item não é caro.</span><span class="sxs-lookup"><span data-stu-id="c647c-107">This means that it's expensive to get the first item of an ordered collection; each item thereafter isn't expensive.</span></span> <span data-ttu-id="c647c-108">Isso faz sentido: Seria impossível para esse operador de consulta de fazer outra maneira.</span><span class="sxs-lookup"><span data-stu-id="c647c-108">This makes sense: It would be impossible for that query operator to do otherwise.</span></span>

## <a name="example-add-a-method-that-calls-tolist-causing-materialization"></a><span data-ttu-id="c647c-109">Exemplo: adicionar um método que chama `ToList` , causando materialização</span><span class="sxs-lookup"><span data-stu-id="c647c-109">Example: Add a method that calls `ToList`, causing materialization</span></span>

<span data-ttu-id="c647c-110">Este exemplo altera o exemplo no [exemplo de consultas de cadeia (C#)](chain-queries-example.md): o `AppendString` método é alterado para chamar <xref:System.Linq.Enumerable.ToList%2A> antes de iterar pela origem, o que causa a materialização.</span><span class="sxs-lookup"><span data-stu-id="c647c-110">This example alters the example in [Chain queries example (C#)](chain-queries-example.md): the `AppendString` method is changed to call <xref:System.Linq.Enumerable.ToList%2A> before iterating through the source, which causes materialization.</span></span>

```csharp
public static class LocalExtensions
{
    public static IEnumerable<string>
      ConvertCollectionToUpperCase(this IEnumerable<string> source)
    {
        foreach (string str in source)
        {
            Console.WriteLine("ToUpper: source >{0}<", str);
            yield return str.ToUpper();
        }
    }

    public static IEnumerable<string>
      AppendString(this IEnumerable<string> source, string stringToAppend)
    {
        // the following statement materializes the source collection in a List<T>
        // before iterating through it
        foreach (string str in source.ToList())
        {
            Console.WriteLine("AppendString: source >{0}<", str);
            yield return str + stringToAppend;
        }
    }
}

class Program
{
    static void Main(string[] args)
    {
        string[] stringArray = { "abc", "def", "ghi" };

        IEnumerable<string> q1 =
            from s in stringArray.ConvertCollectionToUpperCase()
            select s;

        IEnumerable<string> q2 =
            from s in q1.AppendString("!!!")
            select s;

        foreach (string str in q2)
        {
            Console.WriteLine("Main: str >{0}<", str);
            Console.WriteLine();
        }
    }
}
```

 <span data-ttu-id="c647c-111">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="c647c-111">This example produces the following output:</span></span>

```output
ToUpper: source >abc<
ToUpper: source >def<
ToUpper: source >ghi<
AppendString: source >ABC<
Main: str >ABC!!!<

AppendString: source >DEF<
Main: str >DEF!!!<

AppendString: source >GHI<
Main: str >GHI!!!<
```

<span data-ttu-id="c647c-112">Nesse exemplo, você pode ver que a chamada a <xref:System.Linq.Enumerable.ToList%2A> faz com que `AppendString` enumerar sua fonte inteiro antes de como o primeiro item.</span><span class="sxs-lookup"><span data-stu-id="c647c-112">In this example, you can see that the call to <xref:System.Linq.Enumerable.ToList%2A> causes `AppendString` to enumerate its entire source before yielding the first item.</span></span> <span data-ttu-id="c647c-113">Se a origem foi uma matriz grande, essa alteraria significativamente o perfil de memória do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c647c-113">If the source were a large array, this would significantly alter the memory profile of the application.</span></span>

<span data-ttu-id="c647c-114">Os operadores de consulta padrão também podem ser encadeados, conforme mostrado no artigo final deste tutorial:</span><span class="sxs-lookup"><span data-stu-id="c647c-114">Standard query operators can also be chained together as shown in the final article in this tutorial:</span></span>

- [<span data-ttu-id="c647c-115">Operadores de consulta padrão de cadeia juntos (C#)</span><span class="sxs-lookup"><span data-stu-id="c647c-115">Chain standard query operators together (C#)</span></span>](chain-standard-query-operators-together.md)

## <a name="see-also"></a><span data-ttu-id="c647c-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="c647c-116">See also</span></span>

- [<span data-ttu-id="c647c-117">Execução retardada e avaliação lenta</span><span class="sxs-lookup"><span data-stu-id="c647c-117">Deferred execution and lazy evaluation</span></span>](deferred-execution-lazy-evaluation.md)
