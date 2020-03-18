---
title: Cláusula orderby – Referência de C#
ms.date: 07/20/2015
f1_keywords:
- orderby
- orderby_CSharpKeyword
helpviewer_keywords:
- orderby clause [C#]
- orderby keyword [C#]
ms.assetid: 21f87f48-d69d-4e95-9a52-6fec47b37e1f
ms.openlocfilehash: cd76b2c33fe1a1a986bc05e3c3ed5f22809686ed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173569"
---
# <a name="orderby-clause-c-reference"></a><span data-ttu-id="12b31-102">Cláusula orderby (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="12b31-102">orderby clause (C# Reference)</span></span>

<span data-ttu-id="12b31-103">Em uma expressão de consulta, a cláusula `orderby` faz com que a sequência ou subsequência (grupo) retornada seja classificada em ordem crescente ou decrescente.</span><span class="sxs-lookup"><span data-stu-id="12b31-103">In a query expression, the `orderby` clause causes the returned sequence or subsequence (group) to be sorted in either ascending or descending order.</span></span> <span data-ttu-id="12b31-104">Várias chaves podem ser especificadas para executar uma ou mais operações de classificação secundárias.</span><span class="sxs-lookup"><span data-stu-id="12b31-104">Multiple keys can be specified in order to perform one or more secondary sort operations.</span></span> <span data-ttu-id="12b31-105">A classificação é executada pelo comparador padrão para o tipo do elemento.</span><span class="sxs-lookup"><span data-stu-id="12b31-105">The sorting is performed by the default comparer for the type of the element.</span></span> <span data-ttu-id="12b31-106">A ordem de classificação padrão é crescente.</span><span class="sxs-lookup"><span data-stu-id="12b31-106">The default sort order is ascending.</span></span> <span data-ttu-id="12b31-107">Também é possível especificar um comparador personalizado.</span><span class="sxs-lookup"><span data-stu-id="12b31-107">You can also specify a custom comparer.</span></span> <span data-ttu-id="12b31-108">No entanto, está disponível somente por meio da sintaxe baseada em método.</span><span class="sxs-lookup"><span data-stu-id="12b31-108">However, it is only available by using method-based syntax.</span></span> <span data-ttu-id="12b31-109">Para obter mais informações, consulte [Classificando dados](../../programming-guide/concepts/linq/sorting-data.md).</span><span class="sxs-lookup"><span data-stu-id="12b31-109">For more information, see [Sorting Data](../../programming-guide/concepts/linq/sorting-data.md).</span></span>

## <a name="example"></a><span data-ttu-id="12b31-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="12b31-110">Example</span></span>

<span data-ttu-id="12b31-111">No exemplo a seguir, a primeira consulta classifica as palavras em ordem alfabética começando em A e a segunda consulta classifica as mesmas palavras em ordem decrescente.</span><span class="sxs-lookup"><span data-stu-id="12b31-111">In the following example, the first query sorts the words in alphabetical order starting from A, and second query sorts the same words in descending order.</span></span> <span data-ttu-id="12b31-112">(A palavra-chave `ascending` é o valor de classificação padrão e pode ser omitida.)</span><span class="sxs-lookup"><span data-stu-id="12b31-112">(The `ascending` keyword is the default sort value and can be omitted.)</span></span>

[!code-csharp[cscsrefQueryKeywords#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Orderby.cs#20)]

## <a name="example"></a><span data-ttu-id="12b31-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="12b31-113">Example</span></span>

<span data-ttu-id="12b31-114">O exemplo a seguir executa uma classificação primária pelos sobrenomes dos alunos e, em seguida, uma classificação secundária pelos seus nomes.</span><span class="sxs-lookup"><span data-stu-id="12b31-114">The following example performs a primary sort on the students' last names, and then a secondary sort on their first names.</span></span>

[!code-csharp[cscsrefQueryKeywords#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Orderby.cs#22)]

## <a name="remarks"></a><span data-ttu-id="12b31-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="12b31-115">Remarks</span></span>

<span data-ttu-id="12b31-116">Em tempo de compilação, a cláusula `orderby` é convertida em uma chamada para o método <xref:System.Linq.Enumerable.OrderBy%2A>.</span><span class="sxs-lookup"><span data-stu-id="12b31-116">At compile time, the `orderby` clause is translated to a call to the <xref:System.Linq.Enumerable.OrderBy%2A> method.</span></span> <span data-ttu-id="12b31-117">Várias chaves na cláusula `orderby` são traduzidas para chamadas de método <xref:System.Linq.Enumerable.ThenBy%2A>.</span><span class="sxs-lookup"><span data-stu-id="12b31-117">Multiple keys in the `orderby` clause translate to <xref:System.Linq.Enumerable.ThenBy%2A> method calls.</span></span>

## <a name="see-also"></a><span data-ttu-id="12b31-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="12b31-118">See also</span></span>

- [<span data-ttu-id="12b31-119">C# Referência</span><span class="sxs-lookup"><span data-stu-id="12b31-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="12b31-120">Palavras-chave de consulta (LINQ)</span><span class="sxs-lookup"><span data-stu-id="12b31-120">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="12b31-121">LINQ em C#</span><span class="sxs-lookup"><span data-stu-id="12b31-121">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="12b31-122">Cláusula group</span><span class="sxs-lookup"><span data-stu-id="12b31-122">group clause</span></span>](group-clause.md)
- [<span data-ttu-id="12b31-123">Consulta Integrada ao Idioma (LINQ)</span><span class="sxs-lookup"><span data-stu-id="12b31-123">Language Integrated Query (LINQ)</span></span>](../../programming-guide/concepts/linq/index.md)
