---
title: "Como acessar uma classe de coleção com foreach (Guia de Programação em C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: collection classes [C#], foreach statement
ms.assetid: a6b9cf5c-6c8d-4223-b12c-288949434493
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0cf827e958d4dc3b951d17b53effd155356c0ca5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-a-collection-class-with-foreach-c-programming-guide"></a><span data-ttu-id="26cf6-102">Como acessar uma classe de coleção com foreach (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="26cf6-102">How to: Access a Collection Class with foreach (C# Programming Guide)</span></span>
<span data-ttu-id="26cf6-103">O exemplo de código a seguir ilustra como gravar uma classe de coleção não genérica que pode ser usada com [foreach](../../../csharp/language-reference/keywords/foreach-in.md).</span><span class="sxs-lookup"><span data-stu-id="26cf6-103">The following code example illustrates how to write a non-generic collection class that can be used with [foreach](../../../csharp/language-reference/keywords/foreach-in.md).</span></span> <span data-ttu-id="26cf6-104">O exemplo define uma classe do criador de token da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="26cf6-104">The example defines a string tokenizer class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="26cf6-105">Este exemplo representa a prática recomendada somente quando não é possível usar uma classe de coleção genérica.</span><span class="sxs-lookup"><span data-stu-id="26cf6-105">This example represents recommended practice only when you cannot use a generic collection class.</span></span> <span data-ttu-id="26cf6-106">Para obter um exemplo de como implementar uma classe de coleção genérica fortemente tipada com suporte para <xref:System.Collections.Generic.IEnumerable%601>, consulte [Iteradores](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span><span class="sxs-lookup"><span data-stu-id="26cf6-106">For an example of how to implement a type-safe generic collection class that supports <xref:System.Collections.Generic.IEnumerable%601>, see [Iterators](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span></span>  
  
 <span data-ttu-id="26cf6-107">No exemplo, o segmento de código a seguir utiliza a classe `Tokens` para interromper a frase: “Esta é uma frase de exemplo.”</span><span class="sxs-lookup"><span data-stu-id="26cf6-107">In the example, the following code segment uses the `Tokens` class to break the sentence "This is a sample sentence."</span></span> <span data-ttu-id="26cf6-108">em tokens, usando ' ' e '-' como separadores.</span><span class="sxs-lookup"><span data-stu-id="26cf6-108">into tokens by using ' ' and '-' as separators.</span></span> <span data-ttu-id="26cf6-109">O código, em seguida, exibe esses tokens usando uma instrução `foreach`.</span><span class="sxs-lookup"><span data-stu-id="26cf6-109">The code then displays those tokens by using a `foreach` statement.</span></span>  
  
 [!code-csharp[csProgGuideCollections#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-access-a-collection-class-with-foreach_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="26cf6-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="26cf6-110">Example</span></span>  
 <span data-ttu-id="26cf6-111">Internamente, a classe `Tokens` usa uma matriz para armazenar os tokens.</span><span class="sxs-lookup"><span data-stu-id="26cf6-111">Internally, the `Tokens` class uses an array to store the tokens.</span></span> <span data-ttu-id="26cf6-112">Já que as matrizes implementam <xref:System.Collections.IEnumerator> e <xref:System.Collections.IEnumerable>, o exemplo de código poderia ter usado os métodos de enumeração da matriz (<xref:System.Collections.IEnumerable.GetEnumerator%2A>, <xref:System.Collections.IEnumerator.MoveNext%2A>, <xref:System.Collections.IEnumerator.Reset%2A> e <xref:System.Collections.IEnumerator.Current%2A>) em vez de defini-los na classe `Tokens`.</span><span class="sxs-lookup"><span data-stu-id="26cf6-112">Because arrays implement <xref:System.Collections.IEnumerator> and <xref:System.Collections.IEnumerable>, the code example could have used the array's enumeration methods (<xref:System.Collections.IEnumerable.GetEnumerator%2A>, <xref:System.Collections.IEnumerator.MoveNext%2A>, <xref:System.Collections.IEnumerator.Reset%2A>, and <xref:System.Collections.IEnumerator.Current%2A>) instead of defining them in the `Tokens` class.</span></span> <span data-ttu-id="26cf6-113">As definições de método estão incluídas no exemplo para esclarecer como elas são definidas e o que cada uma delas faz.</span><span class="sxs-lookup"><span data-stu-id="26cf6-113">The method definitions are included in the example to clarify how they are defined and what each does.</span></span>  
  
 [!code-csharp[csProgGuideCollections#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-access-a-collection-class-with-foreach_2.cs)]  
  
 <span data-ttu-id="26cf6-114">Em C#, não é necessário que uma classe de coleção implemente <xref:System.Collections.IEnumerable> e <xref:System.Collections.IEnumerator> para que seja compatível com `foreach`.</span><span class="sxs-lookup"><span data-stu-id="26cf6-114">In C#, it is not necessary for a collection class to implement <xref:System.Collections.IEnumerable> and <xref:System.Collections.IEnumerator> to be compatible with `foreach`.</span></span> <span data-ttu-id="26cf6-115">Se a classe tiver os membros <xref:System.Collections.IEnumerable.GetEnumerator%2A>, <xref:System.Collections.IEnumerator.MoveNext%2A>, <xref:System.Collections.IEnumerator.Reset%2A> e <xref:System.Collections.IEnumerator.Current%2A> necessários, ela funcionará com `foreach`.</span><span class="sxs-lookup"><span data-stu-id="26cf6-115">If the class has the required <xref:System.Collections.IEnumerable.GetEnumerator%2A>, <xref:System.Collections.IEnumerator.MoveNext%2A>, <xref:System.Collections.IEnumerator.Reset%2A>, and <xref:System.Collections.IEnumerator.Current%2A> members, it will work with `foreach`.</span></span> <span data-ttu-id="26cf6-116">A vantagem de omitir as interfaces é que isso permite definir um tipo de retorno para `Current` mais específico do que <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="26cf6-116">Omitting the interfaces has the advantage of enabling you to define a return type for `Current` that is more specific than <xref:System.Object>.</span></span> <span data-ttu-id="26cf6-117">Isso fornece segurança de tipos.</span><span class="sxs-lookup"><span data-stu-id="26cf6-117">This provides type safety.</span></span>  
  
 <span data-ttu-id="26cf6-118">Por exemplo, altere as seguintes linhas no exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="26cf6-118">For example, change the following lines in the previous example.</span></span>  
  
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
  
 <span data-ttu-id="26cf6-119">Como `Current` retorna uma cadeia de caracteres, o compilador pode detectar quando um tipo incompatível for usado em uma instrução `foreach`, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="26cf6-119">Because `Current` returns a string, the compiler can detect when an incompatible type is used in a `foreach` statement, as shown in the following code.</span></span>  
  
```csharp  
// Error: Cannot convert type string to int.  
foreach (int item in f)    
```  
  
 <span data-ttu-id="26cf6-120">A desvantagem de omitir <xref:System.Collections.IEnumerable> e <xref:System.Collections.IEnumerator> é que a classe de coleção já não é interoperável com as instruções `foreach` ou instruções equivalentes de outras linguagens Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="26cf6-120">The disadvantage of omitting <xref:System.Collections.IEnumerable> and <xref:System.Collections.IEnumerator> is that the collection class is no longer interoperable with the `foreach` statements, or equivalent statements, of other common language runtime languages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26cf6-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="26cf6-121">See Also</span></span>  
 <xref:System.Collections.Generic>  
 [<span data-ttu-id="26cf6-122">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="26cf6-122">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="26cf6-123">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="26cf6-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="26cf6-124">Matrizes</span><span class="sxs-lookup"><span data-stu-id="26cf6-124">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
 [<span data-ttu-id="26cf6-125">Coleções</span><span class="sxs-lookup"><span data-stu-id="26cf6-125">Collections</span></span>](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b)
