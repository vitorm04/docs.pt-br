---
title: Materialização intermediária (C#)
ms.date: 07/20/2015
ms.assetid: 7922d38f-5044-41cf-8e17-7173d6553a5e
ms.openlocfilehash: 56c4bb57a931362b3e14f6a8da917ae6907565d6
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43516537"
---
# <a name="intermediate-materialization-c"></a><span data-ttu-id="df51f-102">Materialização intermediária (C#)</span><span class="sxs-lookup"><span data-stu-id="df51f-102">Intermediate Materialization (C#)</span></span>
<span data-ttu-id="df51f-103">Se você não for cauteloso, em algumas situações dràstica você pode alterar a memória e o perfil de desempenho do seu aplicativo causando o materialization prematuro das coleções nas suas consultas.</span><span class="sxs-lookup"><span data-stu-id="df51f-103">If you are not careful, in some situations you can drastically alter the memory and performance profile of your application by causing premature materialization of collections in your queries.</span></span> <span data-ttu-id="df51f-104">Alguns operadores de consulta padrão faz com que o materialization de sua coleção de origem antes de produzir um único elemento.</span><span class="sxs-lookup"><span data-stu-id="df51f-104">Some standard query operators cause materialization of their source collection before yielding a single element.</span></span> <span data-ttu-id="df51f-105">Por exemplo, <xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType> primeiro itera através da coleção inteira de origem, então classe todos os itens, e então produz basicamente o primeiro item.</span><span class="sxs-lookup"><span data-stu-id="df51f-105">For example, <xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType> first iterates through its entire source collection, then sorts all items, and then finally yields the first item.</span></span> <span data-ttu-id="df51f-106">Isso significa que é grande obter o primeiro item de uma coleção ordenada; cada item não for depois disso caro.</span><span class="sxs-lookup"><span data-stu-id="df51f-106">This means that it is expensive to get the first item of an ordered collection; each item thereafter is not expensive.</span></span> <span data-ttu-id="df51f-107">Isso faz sentido: Seria impossível para esse operador de consulta de fazer outra maneira.</span><span class="sxs-lookup"><span data-stu-id="df51f-107">This makes sense: It would be impossible for that query operator to do otherwise.</span></span>  
  
## <a name="example"></a><span data-ttu-id="df51f-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="df51f-108">Example</span></span>  
 <span data-ttu-id="df51f-109">Este exemplo altera o exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="df51f-109">This example alters the previous example.</span></span> <span data-ttu-id="df51f-110">O método de `AppendString` chama <xref:System.Linq.Enumerable.ToList%2A> antes de fazer iterações pela origem.</span><span class="sxs-lookup"><span data-stu-id="df51f-110">The `AppendString` method calls <xref:System.Linq.Enumerable.ToList%2A> before iterating through the source.</span></span> <span data-ttu-id="df51f-111">Isso faz com que o materialization.</span><span class="sxs-lookup"><span data-stu-id="df51f-111">This causes materialization.</span></span>  
  
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
  
 <span data-ttu-id="df51f-112">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="df51f-112">This example produces the following output:</span></span>  
  
```  
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
  
 <span data-ttu-id="df51f-113">Nesse exemplo, você pode ver que a chamada a <xref:System.Linq.Enumerable.ToList%2A> faz com que `AppendString` enumerar sua fonte inteiro antes de como o primeiro item.</span><span class="sxs-lookup"><span data-stu-id="df51f-113">In this example, you can see that the call to <xref:System.Linq.Enumerable.ToList%2A> causes `AppendString` to enumerate its entire source before yielding the first item.</span></span> <span data-ttu-id="df51f-114">Se a origem foi uma matriz grande, essa alteraria significativamente o perfil de memória do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="df51f-114">If the source were a large array, this would significantly alter the memory profile of the application.</span></span>  
  
 <span data-ttu-id="df51f-115">Os operadores de consulta padrão podem também ser encadeados juntos.</span><span class="sxs-lookup"><span data-stu-id="df51f-115">Standard query operators can also be chained together.</span></span> <span data-ttu-id="df51f-116">O final deste tópico ilustra este tutorial.</span><span class="sxs-lookup"><span data-stu-id="df51f-116">The final topic in this tutorial illustrates this.</span></span>  
  
-   [<span data-ttu-id="df51f-117">Encadeando operadores de consulta padrão juntos (C#)</span><span class="sxs-lookup"><span data-stu-id="df51f-117">Chaining Standard Query Operators Together (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/chaining-standard-query-operators-together.md)  
  
## <a name="see-also"></a><span data-ttu-id="df51f-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="df51f-118">See Also</span></span>

- [<span data-ttu-id="df51f-119">Tutorial: encadear consultas juntas (C#)</span><span class="sxs-lookup"><span data-stu-id="df51f-119">Tutorial: Chaining Queries Together (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)
