---
title: Cláusula orderby (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- orderby
- orderby_CSharpKeyword
helpviewer_keywords:
- orderby clause [C#]
- orderby keyword [C#]
ms.assetid: 21f87f48-d69d-4e95-9a52-6fec47b37e1f
ms.openlocfilehash: 1fd0036e8bd3c838fe92ca27635cd7638d59ef1d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33268043"
---
# <a name="orderby-clause-c-reference"></a><span data-ttu-id="c82d5-102">Cláusula orderby (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="c82d5-102">orderby clause (C# Reference)</span></span>
<span data-ttu-id="c82d5-103">Em uma expressão de consulta, a cláusula `orderby` faz com que a sequência ou subsequência (grupo) retornada seja classificada em ordem crescente ou decrescente.</span><span class="sxs-lookup"><span data-stu-id="c82d5-103">In a query expression, the `orderby` clause causes the returned sequence or subsequence (group) to be sorted in either ascending or descending order.</span></span> <span data-ttu-id="c82d5-104">Várias chaves podem ser especificadas para executar uma ou mais operações de classificação secundárias.</span><span class="sxs-lookup"><span data-stu-id="c82d5-104">Multiple keys can be specified in order to perform one or more secondary sort operations.</span></span> <span data-ttu-id="c82d5-105">A classificação é executada pelo comparador padrão para o tipo do elemento.</span><span class="sxs-lookup"><span data-stu-id="c82d5-105">The sorting is performed by the default comparer for the type of the element.</span></span> <span data-ttu-id="c82d5-106">A ordem de classificação crescente é padrão.</span><span class="sxs-lookup"><span data-stu-id="c82d5-106">The default sort order is ascending.</span></span> <span data-ttu-id="c82d5-107">Também é possível especificar um comparador personalizado.</span><span class="sxs-lookup"><span data-stu-id="c82d5-107">You can also specify a custom comparer.</span></span> <span data-ttu-id="c82d5-108">No entanto, está disponível somente por meio da sintaxe baseada em método.</span><span class="sxs-lookup"><span data-stu-id="c82d5-108">However, it is only available by using method-based syntax.</span></span> <span data-ttu-id="c82d5-109">Para obter mais informações, consulte [Classificando dados](../../programming-guide/concepts/linq/sorting-data.md).</span><span class="sxs-lookup"><span data-stu-id="c82d5-109">For more information, see [Sorting Data](../../programming-guide/concepts/linq/sorting-data.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c82d5-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c82d5-110">Example</span></span>  
 <span data-ttu-id="c82d5-111">No exemplo a seguir, a primeira consulta classifica as palavras em ordem alfabética começando em A e a segunda consulta classifica as mesmas palavras em ordem decrescente.</span><span class="sxs-lookup"><span data-stu-id="c82d5-111">In the following example, the first query sorts the words in alphabetical order starting from A, and second query sorts the same words in descending order.</span></span> <span data-ttu-id="c82d5-112">(A palavra-chave `ascending` é o valor de classificação padrão e pode ser omitida.)</span><span class="sxs-lookup"><span data-stu-id="c82d5-112">(The `ascending` keyword is the default sort value and can be omitted.)</span></span>  
  
 [!code-csharp[cscsrefQueryKeywords#20](../../../csharp/language-reference/keywords/codesnippet/CSharp/orderby-clause_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="c82d5-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c82d5-113">Example</span></span>  
 <span data-ttu-id="c82d5-114">O exemplo a seguir executa uma classificação primária pelos sobrenomes dos alunos e, em seguida, uma classificação secundária pelos seus nomes.</span><span class="sxs-lookup"><span data-stu-id="c82d5-114">The following example performs a primary sort on the students' last names, and then a secondary sort on their first names.</span></span>  
  
 [!code-csharp[cscsrefQueryKeywords#22](../../../csharp/language-reference/keywords/codesnippet/CSharp/orderby-clause_2.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="c82d5-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="c82d5-115">Remarks</span></span>  
 <span data-ttu-id="c82d5-116">Em tempo de compilação, a cláusula `orderby` é convertida em uma chamada para o método <xref:System.Linq.Enumerable.OrderBy%2A>.</span><span class="sxs-lookup"><span data-stu-id="c82d5-116">At compile time, the `orderby` clause is translated to a call to the <xref:System.Linq.Enumerable.OrderBy%2A> method.</span></span> <span data-ttu-id="c82d5-117">Várias chaves na cláusula `orderby` são traduzidas para chamadas de método <xref:System.Linq.Enumerable.ThenBy%2A>.</span><span class="sxs-lookup"><span data-stu-id="c82d5-117">Multiple keys in the `orderby` clause translate to <xref:System.Linq.Enumerable.ThenBy%2A> method calls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c82d5-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c82d5-118">See Also</span></span>  
 [<span data-ttu-id="c82d5-119">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="c82d5-119">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="c82d5-120">Palavras-chave de Consulta (LINQ)</span><span class="sxs-lookup"><span data-stu-id="c82d5-120">Query Keywords (LINQ)</span></span>](../../../csharp/language-reference/keywords/query-keywords.md)  
 [<span data-ttu-id="c82d5-121">Expressões de consulta LINQ</span><span class="sxs-lookup"><span data-stu-id="c82d5-121">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [<span data-ttu-id="c82d5-122">Cláusula group</span><span class="sxs-lookup"><span data-stu-id="c82d5-122">group clause</span></span>](../../../csharp/language-reference/keywords/group-clause.md)  
 [<span data-ttu-id="c82d5-123">Introdução a LINQ em C#</span><span class="sxs-lookup"><span data-stu-id="c82d5-123">Getting Started with LINQ in C#</span></span>](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
