---
title: into – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- into_CSharpKeyword
- into
helpviewer_keywords:
- into keyword [C#]
ms.assetid: 81ec62c1-f0b1-4755-8a31-959876e77f65
ms.openlocfilehash: dc1e2ee004c21bb3d05155eec3e42ea80bf641a1
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608645"
---
# <a name="into-c-reference"></a><span data-ttu-id="c6daf-102">into (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="c6daf-102">into (C# Reference)</span></span>

<span data-ttu-id="c6daf-103">A palavra-chave contextual `into` pode ser usada para criar um identificador temporário para armazenar os resultados de uma cláusula [group](group-clause.md), [join](join-clause.md) ou [select](select-clause.md) em um novo identificador.</span><span class="sxs-lookup"><span data-stu-id="c6daf-103">The `into` contextual keyword can be used to create a temporary identifier to store the results of a [group](group-clause.md), [join](join-clause.md) or [select](select-clause.md) clause into a new identifier.</span></span> <span data-ttu-id="c6daf-104">Esse identificador por si só pode ser um gerador de comandos de consulta adicionais.</span><span class="sxs-lookup"><span data-stu-id="c6daf-104">This identifier can itself be a generator for additional query commands.</span></span> <span data-ttu-id="c6daf-105">Quando usado em uma cláusula `group` ou `select`, o uso do novo identificador é, às vezes, conhecido como uma *continuação*.</span><span class="sxs-lookup"><span data-stu-id="c6daf-105">When used in a `group` or `select` clause, the use of the new identifier is sometimes referred to as a *continuation*.</span></span>

## <a name="example"></a><span data-ttu-id="c6daf-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c6daf-106">Example</span></span>

<span data-ttu-id="c6daf-107">O exemplo a seguir mostra o uso da palavra-chave `into` para habilitar um identificador temporário `fruitGroup` que tem um tipo inferido de `IGrouping`.</span><span class="sxs-lookup"><span data-stu-id="c6daf-107">The following example shows the use of the `into` keyword to enable a temporary identifier `fruitGroup` which has an inferred type of `IGrouping`.</span></span> <span data-ttu-id="c6daf-108">Usando o identificador, é possível invocar o método <xref:System.Linq.Enumerable.Count%2A> em cada grupo e selecionar apenas os grupos que contêm duas ou mais palavras.</span><span class="sxs-lookup"><span data-stu-id="c6daf-108">By using the identifier, you can invoke the <xref:System.Linq.Enumerable.Count%2A> method on each group and select only those groups that contain two or more words.</span></span>

[!code-csharp[cscsrefQueryKeywords#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Into.cs#18)]

<span data-ttu-id="c6daf-109">O uso de `into` em uma cláusula `group` só é necessário quando você deseja realizar operações de consulta adicionais em cada grupo.</span><span class="sxs-lookup"><span data-stu-id="c6daf-109">The use of `into` in a `group` clause is only necessary when you want to perform additional query operations on each group.</span></span> <span data-ttu-id="c6daf-110">Para obter mais informações, consulte [Cláusula group](group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="c6daf-110">For more information, see [group clause](group-clause.md).</span></span>

<span data-ttu-id="c6daf-111">Para obter um exemplo do uso de `into` em uma cláusula `join`, consulte [cláusula join](join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="c6daf-111">For an example of the use of `into` in a `join` clause, see [join clause](join-clause.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c6daf-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c6daf-112">See also</span></span>

- [<span data-ttu-id="c6daf-113">Palavras-chave de Consulta (LINQ)</span><span class="sxs-lookup"><span data-stu-id="c6daf-113">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="c6daf-114">Expressões de consulta LINQ</span><span class="sxs-lookup"><span data-stu-id="c6daf-114">LINQ Query Expressions</span></span>](../../programming-guide/linq-query-expressions/index.md)
- [<span data-ttu-id="c6daf-115">Cláusula group</span><span class="sxs-lookup"><span data-stu-id="c6daf-115">group clause</span></span>](group-clause.md)
