---
title: Operadores de consulta padrão de cadeia juntos (C#)-LINQ to XML
description: Saiba como encadear operadores de consulta juntos.
ms.date: 07/20/2015
dev_langs:
- csharp
ms.assetid: 66f2b0a9-2c23-4735-988e-bbc9dfb55c7b
ms.openlocfilehash: ed3ca44c853ebbeee690cb31232a13e35b383d1b
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89551847"
---
# <a name="chain-standard-query-operators-together-c-linq-to-xml"></a><span data-ttu-id="58b27-103">Operadores de consulta padrão de cadeia juntos (C#) (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="58b27-103">Chain standard query operators together (C#) (LINQ to XML)</span></span>

<span data-ttu-id="58b27-104">Os operadores de consulta padrão podem ser encadeados juntos.</span><span class="sxs-lookup"><span data-stu-id="58b27-104">The standard query operators can be chained together.</span></span> <span data-ttu-id="58b27-105">Por exemplo, você pode levantar o <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> operador (chamado pela `where` cláusula) e funciona de maneira lenta; ou seja, nenhum resultado intermediário é materializado por ele.</span><span class="sxs-lookup"><span data-stu-id="58b27-105">For example, you can interject the <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> operator (invoked by the `where` clause), and it operates in a lazy fashion; that is, no intermediate results are materialized by it.</span></span>

## <a name="example-interject-a-where-clause"></a><span data-ttu-id="58b27-106">Exemplo: levantar uma cláusula WHERE</span><span class="sxs-lookup"><span data-stu-id="58b27-106">Example: Interject a where clause</span></span>

<span data-ttu-id="58b27-107">Nesse exemplo, o método de <xref:System.Linq.Enumerable.Where%2A> é chamado antes de chamar `ConvertCollectionToUpperCase`.</span><span class="sxs-lookup"><span data-stu-id="58b27-107">In this example, the <xref:System.Linq.Enumerable.Where%2A> method is called before calling `ConvertCollectionToUpperCase`.</span></span> <span data-ttu-id="58b27-108">O método de <xref:System.Linq.Enumerable.Where%2A> opera quase exatamente a mesma maneira que os métodos lentos usados em exemplos anteriores neste tutorial, `ConvertCollectionToUpperCase` e `AppendString`.</span><span class="sxs-lookup"><span data-stu-id="58b27-108">The <xref:System.Linq.Enumerable.Where%2A> method operates in almost exactly the same way as the lazy methods used in previous examples in this tutorial, `ConvertCollectionToUpperCase` and `AppendString`.</span></span>

<span data-ttu-id="58b27-109">Uma diferença é que, nesse caso, o <xref:System.Linq.Enumerable.Where%2A> método itera por meio de sua coleção de origem, determina que o primeiro item não passa o predicado e, em seguida, obtém o próximo item, que passa.</span><span class="sxs-lookup"><span data-stu-id="58b27-109">One difference is that in this case, the <xref:System.Linq.Enumerable.Where%2A> method iterates through its source collection, determines that the first item doesn't pass the predicate, and then gets the next item, which does pass.</span></span> <span data-ttu-id="58b27-110">Produz no segundo item.</span><span class="sxs-lookup"><span data-stu-id="58b27-110">It then yields the second item.</span></span>

<span data-ttu-id="58b27-111">No entanto, a ideia básica é a mesma: as coleções intermediárias não são materializadas, a menos que tenham que ser.</span><span class="sxs-lookup"><span data-stu-id="58b27-111">However, the basic idea is the same: intermediate collections aren't materialized unless they have to be.</span></span>

<span data-ttu-id="58b27-112">Quando expressões de consulta são usadas, elas são convertidas em chamadas para os operadores de consulta padrão e os mesmos princípios se aplicam.</span><span class="sxs-lookup"><span data-stu-id="58b27-112">When query expressions are used, they're converted to calls to the standard query operators, and the same principles apply.</span></span>

<span data-ttu-id="58b27-113">Todos os exemplos nesta seção que estão vendo documentos do Office Open XML usam o mesmo princípio.</span><span class="sxs-lookup"><span data-stu-id="58b27-113">All of the examples in this section that are querying Office Open XML documents use the same principle.</span></span> <span data-ttu-id="58b27-114">A execução retardada e a avaliação lenta são alguns dos conceitos fundamentais que você deve entender para usar o LINQ e LINQ to XML, com eficiência.</span><span class="sxs-lookup"><span data-stu-id="58b27-114">Deferred execution and lazy evaluation are some of the fundamental concepts that you must understand to use LINQ, and LINQ to XML, effectively.</span></span>

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
        foreach (string str in source)
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
            where s.CompareTo("D") >= 0
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

<span data-ttu-id="58b27-115">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="58b27-115">This example produces the following output:</span></span>

```output
ToUpper: source >abc<
ToUpper: source >def<
AppendString: source >DEF<
Main: str >DEF!!!<

ToUpper: source >ghi<
AppendString: source >GHI<
Main: str >GHI!!!<
```

<span data-ttu-id="58b27-116">Este é o artigo final do tutorial [: encadeamento de consultas em conjunto (C#)](chain-queries-example.md) .</span><span class="sxs-lookup"><span data-stu-id="58b27-116">This is the final article in the [Tutorial: Chaining Queries Together (C#)](chain-queries-example.md) tutorial.</span></span>
