---
description: Cláusula orderby – Referência de C#
title: Cláusula orderby – Referência de C#
ms.date: 07/20/2015
f1_keywords:
- orderby
- orderby_CSharpKeyword
helpviewer_keywords:
- orderby clause [C#]
- orderby keyword [C#]
ms.assetid: 21f87f48-d69d-4e95-9a52-6fec47b37e1f
ms.openlocfilehash: 2f64b45ff252c7cc02e56c465da21ccc5e861aec
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89142343"
---
# <a name="orderby-clause-c-reference"></a><span data-ttu-id="c5f49-103">Cláusula orderby (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="c5f49-103">orderby clause (C# Reference)</span></span>

<span data-ttu-id="c5f49-104">Em uma expressão de consulta, a cláusula `orderby` faz com que a sequência ou subsequência (grupo) retornada seja classificada em ordem crescente ou decrescente.</span><span class="sxs-lookup"><span data-stu-id="c5f49-104">In a query expression, the `orderby` clause causes the returned sequence or subsequence (group) to be sorted in either ascending or descending order.</span></span> <span data-ttu-id="c5f49-105">Várias chaves podem ser especificadas para executar uma ou mais operações de classificação secundárias.</span><span class="sxs-lookup"><span data-stu-id="c5f49-105">Multiple keys can be specified in order to perform one or more secondary sort operations.</span></span> <span data-ttu-id="c5f49-106">A classificação é executada pelo comparador padrão para o tipo do elemento.</span><span class="sxs-lookup"><span data-stu-id="c5f49-106">The sorting is performed by the default comparer for the type of the element.</span></span> <span data-ttu-id="c5f49-107">A ordem de classificação padrão é crescente.</span><span class="sxs-lookup"><span data-stu-id="c5f49-107">The default sort order is ascending.</span></span> <span data-ttu-id="c5f49-108">Também é possível especificar um comparador personalizado.</span><span class="sxs-lookup"><span data-stu-id="c5f49-108">You can also specify a custom comparer.</span></span> <span data-ttu-id="c5f49-109">No entanto, está disponível somente por meio da sintaxe baseada em método.</span><span class="sxs-lookup"><span data-stu-id="c5f49-109">However, it is only available by using method-based syntax.</span></span> <span data-ttu-id="c5f49-110">Para obter mais informações, consulte [Classificando dados](../../programming-guide/concepts/linq/sorting-data.md).</span><span class="sxs-lookup"><span data-stu-id="c5f49-110">For more information, see [Sorting Data](../../programming-guide/concepts/linq/sorting-data.md).</span></span>

## <a name="example"></a><span data-ttu-id="c5f49-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c5f49-111">Example</span></span>

<span data-ttu-id="c5f49-112">No exemplo a seguir, a primeira consulta classifica as palavras em ordem alfabética começando em A e a segunda consulta classifica as mesmas palavras em ordem decrescente.</span><span class="sxs-lookup"><span data-stu-id="c5f49-112">In the following example, the first query sorts the words in alphabetical order starting from A, and second query sorts the same words in descending order.</span></span> <span data-ttu-id="c5f49-113">(A palavra-chave `ascending` é o valor de classificação padrão e pode ser omitida.)</span><span class="sxs-lookup"><span data-stu-id="c5f49-113">(The `ascending` keyword is the default sort value and can be omitted.)</span></span>

[!code-csharp[cscsrefQueryKeywords#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Orderby.cs#20)]

## <a name="example"></a><span data-ttu-id="c5f49-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c5f49-114">Example</span></span>

<span data-ttu-id="c5f49-115">O exemplo a seguir executa uma classificação primária pelos sobrenomes dos alunos e, em seguida, uma classificação secundária pelos seus nomes.</span><span class="sxs-lookup"><span data-stu-id="c5f49-115">The following example performs a primary sort on the students' last names, and then a secondary sort on their first names.</span></span>

[!code-csharp[cscsrefQueryKeywords#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Orderby.cs#22)]

## <a name="remarks"></a><span data-ttu-id="c5f49-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="c5f49-116">Remarks</span></span>

<span data-ttu-id="c5f49-117">Em tempo de compilação, a cláusula `orderby` é convertida em uma chamada para o método <xref:System.Linq.Enumerable.OrderBy%2A>.</span><span class="sxs-lookup"><span data-stu-id="c5f49-117">At compile time, the `orderby` clause is translated to a call to the <xref:System.Linq.Enumerable.OrderBy%2A> method.</span></span> <span data-ttu-id="c5f49-118">Várias chaves na cláusula `orderby` são traduzidas para chamadas de método <xref:System.Linq.Enumerable.ThenBy%2A>.</span><span class="sxs-lookup"><span data-stu-id="c5f49-118">Multiple keys in the `orderby` clause translate to <xref:System.Linq.Enumerable.ThenBy%2A> method calls.</span></span>

## <a name="see-also"></a><span data-ttu-id="c5f49-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="c5f49-119">See also</span></span>

- [<span data-ttu-id="c5f49-120">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="c5f49-120">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c5f49-121">Palavras-chave de consulta (LINQ)</span><span class="sxs-lookup"><span data-stu-id="c5f49-121">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="c5f49-122">LINQ em C#</span><span class="sxs-lookup"><span data-stu-id="c5f49-122">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="c5f49-123">Cláusula group</span><span class="sxs-lookup"><span data-stu-id="c5f49-123">group clause</span></span>](group-clause.md)
- [<span data-ttu-id="c5f49-124">LINQ (Consulta Integrada à Linguagem)</span><span class="sxs-lookup"><span data-stu-id="c5f49-124">Language Integrated Query (LINQ)</span></span>](../../programming-guide/concepts/linq/index.md)
