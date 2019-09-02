---
title: Encadeando operadores de consulta padrão juntos (C#)
ms.date: 07/20/2015
ms.assetid: 66f2b0a9-2c23-4735-988e-bbc9dfb55c7b
ms.openlocfilehash: 37df654b2bfdcc135460e5ded2ceec1eca33b35a
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204210"
---
# <a name="chaining-standard-query-operators-together-c"></a><span data-ttu-id="debdd-102">Encadeando operadores de consulta padrão juntos (C#)</span><span class="sxs-lookup"><span data-stu-id="debdd-102">Chaining Standard Query Operators Together (C#)</span></span>
<span data-ttu-id="debdd-103">Este é o tópico final no [Tutorial: Encadeando consultas (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="debdd-103">This is the final topic in the [Tutorial: Chaining Queries Together (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md) tutorial.</span></span>  
  
 <span data-ttu-id="debdd-104">Os operadores de consulta padrão podem também ser encadeados juntos.</span><span class="sxs-lookup"><span data-stu-id="debdd-104">The standard query operators can also be chained together.</span></span> <span data-ttu-id="debdd-105">Por exemplo, você pode interject o operador de <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> , e também funciona em uma forma lazy.</span><span class="sxs-lookup"><span data-stu-id="debdd-105">For example, you can interject the <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> operator, and it also operates in a lazy fashion.</span></span> <span data-ttu-id="debdd-106">Resultados intermediária é materializado por ele.</span><span class="sxs-lookup"><span data-stu-id="debdd-106">No intermediate results are materialized by it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="debdd-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="debdd-107">Example</span></span>  
 <span data-ttu-id="debdd-108">Nesse exemplo, o método de <xref:System.Linq.Enumerable.Where%2A> é chamado antes de chamar `ConvertCollectionToUpperCase`.</span><span class="sxs-lookup"><span data-stu-id="debdd-108">In this example, the <xref:System.Linq.Enumerable.Where%2A> method is called before calling `ConvertCollectionToUpperCase`.</span></span> <span data-ttu-id="debdd-109">O método de <xref:System.Linq.Enumerable.Where%2A> opera quase exatamente a mesma maneira que os métodos lentos usados em exemplos anteriores neste tutorial, `ConvertCollectionToUpperCase` e `AppendString`.</span><span class="sxs-lookup"><span data-stu-id="debdd-109">The <xref:System.Linq.Enumerable.Where%2A> method operates in almost exactly the same way as the lazy methods used in previous examples in this tutorial, `ConvertCollectionToUpperCase` and `AppendString`.</span></span>  
  
 <span data-ttu-id="debdd-110">Uma diferença é que nesse caso, o método de <xref:System.Linq.Enumerable.Where%2A> itera através da coleção fonte, determina que o primeiro item não passa o predicado e em seguida, o próximo item, que passa.</span><span class="sxs-lookup"><span data-stu-id="debdd-110">One difference is that in this case, the <xref:System.Linq.Enumerable.Where%2A> method iterates through its source collection, determines that the first item does not pass the predicate, and then gets the next item, which does pass.</span></span> <span data-ttu-id="debdd-111">Produz no segundo item.</span><span class="sxs-lookup"><span data-stu-id="debdd-111">It then yields the second item.</span></span>  
  
 <span data-ttu-id="debdd-112">No entanto, a ideia básica é a mesma: As coleções intermediárias não são materializadas a menos que isso seja necessário.</span><span class="sxs-lookup"><span data-stu-id="debdd-112">However, the basic idea is the same: Intermediate collections are not materialized unless they have to be.</span></span>  
  
 <span data-ttu-id="debdd-113">Quando as expressões de consulta são usadas, são convertidas para chamadas aos operadores de consulta padrão, e os mesmos princípios se aplicam.</span><span class="sxs-lookup"><span data-stu-id="debdd-113">When query expressions are used, they are converted to calls to the standard query operators, and the same principles apply.</span></span>  
  
 <span data-ttu-id="debdd-114">Todos os exemplos nesta seção que estão vendo documentos do Office Open XML usam o mesmo princípio.</span><span class="sxs-lookup"><span data-stu-id="debdd-114">All of the examples in this section that are querying Office Open XML documents use the same principle.</span></span> <span data-ttu-id="debdd-115">A execução adiada e a avaliação lazy são alguns conceitos fundamentais que você deve compreender para usar efetivamente LINQ (e LINQ to XML).</span><span class="sxs-lookup"><span data-stu-id="debdd-115">Deferred execution and lazy evaluation are some of the fundamental concepts that you must understand  to use LINQ (and LINQ to XML) effectively.</span></span>  
  
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
  
 <span data-ttu-id="debdd-116">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="debdd-116">This example produces the following output:</span></span>  
  
```output  
ToUpper: source >abc<  
ToUpper: source >def<  
AppendString: source >DEF<  
Main: str >DEF!!!<  
  
ToUpper: source >ghi<  
AppendString: source >GHI<  
Main: str >GHI!!!<  
```  
