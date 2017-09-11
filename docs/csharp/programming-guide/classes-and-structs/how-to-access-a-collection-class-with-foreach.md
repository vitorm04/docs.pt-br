---
title: "Como acessar uma classe de coleção com foreach (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- collection classes [C#], foreach statement
ms.assetid: a6b9cf5c-6c8d-4223-b12c-288949434493
caps.latest.revision: 21
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 2ad81ab699b079f4aabb04a886211e94a937335d
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-access-a-collection-class-with-foreach-c-programming-guide"></a><span data-ttu-id="244dd-102">Como acessar uma classe de coleção com foreach (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="244dd-102">How to: Access a Collection Class with foreach (C# Programming Guide)</span></span>
<span data-ttu-id="244dd-103">O exemplo de código a seguir ilustra como gravar uma classe de coleção não genérica que pode ser usada com [foreach](../../../csharp/language-reference/keywords/foreach-in.md).</span><span class="sxs-lookup"><span data-stu-id="244dd-103">The following code example illustrates how to write a non-generic collection class that can be used with [foreach](../../../csharp/language-reference/keywords/foreach-in.md).</span></span> <span data-ttu-id="244dd-104">O exemplo define uma classe do criador de token da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="244dd-104">The example defines a string tokenizer class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="244dd-105">Este exemplo representa a prática recomendada somente quando não é possível usar uma classe de coleção genérica.</span><span class="sxs-lookup"><span data-stu-id="244dd-105">This example represents recommended practice only when you cannot use a generic collection class.</span></span> <span data-ttu-id="244dd-106">Para obter um exemplo de como implementar uma classe de coleção genérica fortemente tipada com suporte para <xref:System.Collections.Generic.IEnumerable%601>, consulte [Iteradores](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span><span class="sxs-lookup"><span data-stu-id="244dd-106">For an example of how to implement a type-safe generic collection class that supports <xref:System.Collections.Generic.IEnumerable%601>, see [Iterators](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span></span>  
  
 <span data-ttu-id="244dd-107">No exemplo, o segmento de código a seguir utiliza a classe `Tokens` para interromper a frase: “Esta é uma frase de exemplo.”</span><span class="sxs-lookup"><span data-stu-id="244dd-107">In the example, the following code segment uses the `Tokens` class to break the sentence "This is a sample sentence."</span></span> <span data-ttu-id="244dd-108">em tokens, usando ' ' e '-' como separadores.</span><span class="sxs-lookup"><span data-stu-id="244dd-108">into tokens by using ' ' and '-' as separators.</span></span> <span data-ttu-id="244dd-109">O código, em seguida, exibe esses tokens usando uma instrução `foreach`.</span><span class="sxs-lookup"><span data-stu-id="244dd-109">The code then displays those tokens by using a `foreach` statement.</span></span>  
  
 <span data-ttu-id="244dd-110">[!code-cs[csProgGuideCollections#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-access-a-collection-class-with-foreach_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="244dd-110">[!code-cs[csProgGuideCollections#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-access-a-collection-class-with-foreach_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="244dd-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="244dd-111">Example</span></span>  
 <span data-ttu-id="244dd-112">Internamente, a classe `Tokens` usa uma matriz para armazenar os tokens.</span><span class="sxs-lookup"><span data-stu-id="244dd-112">Internally, the `Tokens` class uses an array to store the tokens.</span></span> <span data-ttu-id="244dd-113">Já que as matrizes implementam <xref:System.Collections.IEnumerator> e <xref:System.Collections.IEnumerable>, o exemplo de código poderia ter usado os métodos de enumeração da matriz (<xref:System.Collections.IEnumerable.GetEnumerator%2A>, <xref:System.Collections.IEnumerator.MoveNext%2A>, <xref:System.Collections.IEnumerator.Reset%2A> e <xref:System.Collections.IEnumerator.Current%2A>) em vez de defini-los na classe `Tokens`.</span><span class="sxs-lookup"><span data-stu-id="244dd-113">Because arrays implement <xref:System.Collections.IEnumerator> and <xref:System.Collections.IEnumerable>, the code example could have used the array's enumeration methods (<xref:System.Collections.IEnumerable.GetEnumerator%2A>, <xref:System.Collections.IEnumerator.MoveNext%2A>, <xref:System.Collections.IEnumerator.Reset%2A>, and <xref:System.Collections.IEnumerator.Current%2A>) instead of defining them in the `Tokens` class.</span></span> <span data-ttu-id="244dd-114">As definições de método estão incluídas no exemplo para esclarecer como elas são definidas e o que cada uma delas faz.</span><span class="sxs-lookup"><span data-stu-id="244dd-114">The method definitions are included in the example to clarify how they are defined and what each does.</span></span>  
  
 <span data-ttu-id="244dd-115">[!code-cs[csProgGuideCollections#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-access-a-collection-class-with-foreach_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="244dd-115">[!code-cs[csProgGuideCollections#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-access-a-collection-class-with-foreach_2.cs)]</span></span>  
  
 <span data-ttu-id="244dd-116">Em C#, não é necessário que uma classe de coleção implemente <xref:System.Collections.IEnumerable> e <xref:System.Collections.IEnumerator> para que seja compatível com `foreach`.</span><span class="sxs-lookup"><span data-stu-id="244dd-116">In C#, it is not necessary for a collection class to implement <xref:System.Collections.IEnumerable> and <xref:System.Collections.IEnumerator> to be compatible with `foreach`.</span></span> <span data-ttu-id="244dd-117">Se a classe tiver os membros <xref:System.Collections.IEnumerable.GetEnumerator%2A>, <xref:System.Collections.IEnumerator.MoveNext%2A>, <xref:System.Collections.IEnumerator.Reset%2A> e <xref:System.Collections.IEnumerator.Current%2A> necessários, ela funcionará com `foreach`.</span><span class="sxs-lookup"><span data-stu-id="244dd-117">If the class has the required <xref:System.Collections.IEnumerable.GetEnumerator%2A>, <xref:System.Collections.IEnumerator.MoveNext%2A>, <xref:System.Collections.IEnumerator.Reset%2A>, and <xref:System.Collections.IEnumerator.Current%2A> members, it will work with `foreach`.</span></span> <span data-ttu-id="244dd-118">A vantagem de omitir as interfaces é que isso permite definir um tipo de retorno para `Current` mais específico do que <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="244dd-118">Omitting the interfaces has the advantage of enabling you to define a return type for `Current` that is more specific than <xref:System.Object>.</span></span> <span data-ttu-id="244dd-119">Isso fornece segurança de tipos.</span><span class="sxs-lookup"><span data-stu-id="244dd-119">This provides type safety.</span></span>  
  
 <span data-ttu-id="244dd-120">Por exemplo, altere as seguintes linhas no exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="244dd-120">For example, change the following lines in the previous example.</span></span>  
  
```csharp  
// Change the Tokens class so that it no longer implements IEnumerable.  
public class Tokens  
{  
    // . . .  
  
    // Change the return type for the GetEnumerator method.  
    public TokenEnumerator GetEnumerator()  
    {   }  
  
    // Change TokenEnumerator so that it no longer implements IEnumerator.  
    public class TokenEnumerator  
    {  
        // . . .  
  
        // Change the return type of method Current to string.  
        public string Current  
        {   }  
    }  
 }  
```  
  
 <span data-ttu-id="244dd-121">Como `Current` retorna uma cadeia de caracteres, o compilador pode detectar quando um tipo incompatível for usado em uma instrução `foreach`, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="244dd-121">Because `Current` returns a string, the compiler can detect when an incompatible type is used in a `foreach` statement, as shown in the following code.</span></span>  
  
```csharp  
// Error: Cannot convert type string to int.  
foreach (int item in f)    
```  
  
 <span data-ttu-id="244dd-122">A desvantagem de omitir <xref:System.Collections.IEnumerable> e <xref:System.Collections.IEnumerator> é que a classe de coleção já não é interoperável com as instruções `foreach` ou instruções equivalentes de outras linguagens Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="244dd-122">The disadvantage of omitting <xref:System.Collections.IEnumerable> and <xref:System.Collections.IEnumerator> is that the collection class is no longer interoperable with the `foreach` statements, or equivalent statements, of other common language runtime languages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="244dd-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="244dd-123">See Also</span></span>  
 <span data-ttu-id="244dd-124"><xref:System.Collections.Generic></span><span class="sxs-lookup"><span data-stu-id="244dd-124"><xref:System.Collections.Generic></span></span>   
 <span data-ttu-id="244dd-125">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="244dd-125">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="244dd-126">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="244dd-126">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="244dd-127">[Matrizes](../../../csharp/programming-guide/arrays/index.md) </span><span class="sxs-lookup"><span data-stu-id="244dd-127">[Arrays](../../../csharp/programming-guide/arrays/index.md) </span></span>  
 [<span data-ttu-id="244dd-128">Coleções</span><span class="sxs-lookup"><span data-stu-id="244dd-128">Collections</span></span>](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b)

