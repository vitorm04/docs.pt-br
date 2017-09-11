---
title: "Encadeando operadores de consulta padrão juntos (C#)"
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
ms.assetid: 66f2b0a9-2c23-4735-988e-bbc9dfb55c7b
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 40c65c80c08caa310cb72a194534ad63fcea890a
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="chaining-standard-query-operators-together-c"></a><span data-ttu-id="1f2f5-102">Encadeando operadores de consulta padrão juntos (C#)</span><span class="sxs-lookup"><span data-stu-id="1f2f5-102">Chaining Standard Query Operators Together (C#)</span></span>
<span data-ttu-id="1f2f5-103">Este é o tópico final no tutorial do [Tutorial: encadear consultas juntas (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md).</span><span class="sxs-lookup"><span data-stu-id="1f2f5-103">This is the final topic in the [Tutorial: Chaining Queries Together (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md) tutorial.</span></span>  
  
 <span data-ttu-id="1f2f5-104">Os operadores de consulta padrão podem também ser encadeados juntos.</span><span class="sxs-lookup"><span data-stu-id="1f2f5-104">The standard query operators can also be chained together.</span></span> <span data-ttu-id="1f2f5-105">Por exemplo, você pode interject o operador de <xref:System.Linq.Enumerable.Where%2A?displayProperty=fullName> , e também funciona em uma forma lazy.</span><span class="sxs-lookup"><span data-stu-id="1f2f5-105">For example, you can interject the <xref:System.Linq.Enumerable.Where%2A?displayProperty=fullName> operator, and it also operates in a lazy fashion.</span></span> <span data-ttu-id="1f2f5-106">Resultados intermediária é materializado por ele.</span><span class="sxs-lookup"><span data-stu-id="1f2f5-106">No intermediate results are materialized by it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f2f5-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1f2f5-107">Example</span></span>  
 <span data-ttu-id="1f2f5-108">Nesse exemplo, o método de <xref:System.Linq.Enumerable.Where%2A> é chamado antes de chamar `ConvertCollectionToUpperCase`.</span><span class="sxs-lookup"><span data-stu-id="1f2f5-108">In this example, the <xref:System.Linq.Enumerable.Where%2A> method is called before calling `ConvertCollectionToUpperCase`.</span></span> <span data-ttu-id="1f2f5-109">O método de <xref:System.Linq.Enumerable.Where%2A> opera quase exatamente a mesma maneira que os métodos lentos usados em exemplos anteriores neste tutorial, `ConvertCollectionToUpperCase` e `AppendString`.</span><span class="sxs-lookup"><span data-stu-id="1f2f5-109">The <xref:System.Linq.Enumerable.Where%2A> method operates in almost exactly the same way as the lazy methods used in previous examples in this tutorial, `ConvertCollectionToUpperCase` and `AppendString`.</span></span>  
  
 <span data-ttu-id="1f2f5-110">Uma diferença é que nesse caso, o método de <xref:System.Linq.Enumerable.Where%2A> itera através da coleção fonte, determina que o primeiro item não passa o predicado e em seguida, o próximo item, que passa.</span><span class="sxs-lookup"><span data-stu-id="1f2f5-110">One difference is that in this case, the <xref:System.Linq.Enumerable.Where%2A> method iterates through its source collection, determines that the first item does not pass the predicate, and then gets the next item, which does pass.</span></span> <span data-ttu-id="1f2f5-111">Produz no segundo item.</span><span class="sxs-lookup"><span data-stu-id="1f2f5-111">It then yields the second item.</span></span>  
  
 <span data-ttu-id="1f2f5-112">Entretanto, a exibição básica é a mesma: As coleções intermediários não são materializadas a menos que têm que ser.</span><span class="sxs-lookup"><span data-stu-id="1f2f5-112">However, the basic idea is the same: Intermediate collections are not materialized unless they have to be.</span></span>  
  
 <span data-ttu-id="1f2f5-113">Quando as expressões de consulta são usadas, são convertidas para chamadas aos operadores de consulta padrão, e os mesmos princípios se aplicam.</span><span class="sxs-lookup"><span data-stu-id="1f2f5-113">When query expressions are used, they are converted to calls to the standard query operators, and the same principles apply.</span></span>  
  
 <span data-ttu-id="1f2f5-114">Todos os exemplos nesta seção que estão vendo documentos do Office Open XML usam o mesmo princípio.</span><span class="sxs-lookup"><span data-stu-id="1f2f5-114">All of the examples in this section that are querying Office Open XML documents use the same principle.</span></span> <span data-ttu-id="1f2f5-115">A execução adiada e a avaliação lazy são alguns conceitos fundamentais que você deve compreender para usar efetivamente LINQ (e LINQ to XML).</span><span class="sxs-lookup"><span data-stu-id="1f2f5-115">Deferred execution and lazy evaluation are some of the fundamental concepts that you must understand  to use LINQ (and LINQ to XML) effectively.</span></span>  
  
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
  
 <span data-ttu-id="1f2f5-116">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="1f2f5-116">This example produces the following output:</span></span>  
  
```  
ToUpper: source >abc<  
ToUpper: source >def<  
AppendString: source >DEF<  
Main: str >DEF!!!<  
  
ToUpper: source >ghi<  
AppendString: source >GHI<  
Main: str >GHI!!!<  
```  
  
## <a name="see-also"></a><span data-ttu-id="1f2f5-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1f2f5-117">See Also</span></span>  
 [<span data-ttu-id="1f2f5-118">Tutorial: encadear consultas juntas (C#)</span><span class="sxs-lookup"><span data-stu-id="1f2f5-118">Tutorial: Chaining Queries Together (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)

