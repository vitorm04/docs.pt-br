---
title: Cláusula where – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- whereclause_CSharpKeyword
helpviewer_keywords:
- where keyword [C#]
- where clause [C#]
ms.assetid: 7f9bf952-7744-4f91-b676-cddb55d107c3
ms.openlocfilehash: 15df6339cec9eabadf5aa4c184d7504c4e065032
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73421926"
---
# <a name="where-clause-c-reference"></a><span data-ttu-id="df113-102">Cláusula where (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="df113-102">where clause (C# Reference)</span></span>

<span data-ttu-id="df113-103">A cláusula `where` é usada em uma expressão de consulta para especificar quais elementos da fonte de dados serão retornados na expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="df113-103">The `where` clause is used in a query expression to specify which elements from the data source will be returned in the query expression.</span></span> <span data-ttu-id="df113-104">Aplica-se uma condição booliana (*predicate*) para cada elemento de origem (referenciado pela variável de intervalo) e retorna aqueles para os quais a condição especificada for verdadeira.</span><span class="sxs-lookup"><span data-stu-id="df113-104">It applies a Boolean condition (*predicate*) to each source element (referenced by the range variable) and returns those for which the specified condition is true.</span></span> <span data-ttu-id="df113-105">Uma única expressão de consulta pode conter várias cláusulas `where` e uma única cláusula pode conter várias subexpressões de predicado.</span><span class="sxs-lookup"><span data-stu-id="df113-105">A single query expression may contain multiple `where` clauses and a single clause may contain multiple predicate subexpressions.</span></span>

## <a name="example"></a><span data-ttu-id="df113-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="df113-106">Example</span></span>

<span data-ttu-id="df113-107">No exemplo a seguir, a cláusula `where` filtra todos os números, exceto aqueles que são menores que cinco.</span><span class="sxs-lookup"><span data-stu-id="df113-107">In the following example, the `where` clause filters out all numbers except those that are less than five.</span></span> <span data-ttu-id="df113-108">Se você remover a cláusula `where`, todos os números da fonte de dados serão retornados.</span><span class="sxs-lookup"><span data-stu-id="df113-108">If you remove the `where` clause, all numbers from the data source would be returned.</span></span> <span data-ttu-id="df113-109">A expressão `num < 5` é o predicado aplicado a cada elemento.</span><span class="sxs-lookup"><span data-stu-id="df113-109">The expression `num < 5` is the predicate that is applied to each element.</span></span>

[!code-csharp[cscsrefQueryKeywords#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#5)]

## <a name="example"></a><span data-ttu-id="df113-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="df113-110">Example</span></span>

<span data-ttu-id="df113-111">Dentro de uma única cláusula `where`, você pode especificar tantos predicados quanto necessário usando os operadores [&&](../operators/boolean-logical-operators.md#conditional-logical-and-operator-) e [&#124;&#124;](../operators/boolean-logical-operators.md#conditional-logical-or-operator-).</span><span class="sxs-lookup"><span data-stu-id="df113-111">Within a single `where` clause, you can specify as many predicates as necessary by using the [&&](../operators/boolean-logical-operators.md#conditional-logical-and-operator-) and [&#124;&#124;](../operators/boolean-logical-operators.md#conditional-logical-or-operator-) operators.</span></span> <span data-ttu-id="df113-112">No exemplo a seguir, a consulta especifica dois predicados para selecionar apenas os números pares que são menores que cinco.</span><span class="sxs-lookup"><span data-stu-id="df113-112">In the following example, the query specifies two predicates in order to select only the even numbers that are less than five.</span></span>

[!code-csharp[cscsrefQueryKeywords#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#6)]  

## <a name="example"></a><span data-ttu-id="df113-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="df113-113">Example</span></span>

<span data-ttu-id="df113-114">Uma cláusula `where` pode conter um ou mais métodos que retornam valores boolianos.</span><span class="sxs-lookup"><span data-stu-id="df113-114">A `where` clause may contain one or more methods that return Boolean values.</span></span> <span data-ttu-id="df113-115">No exemplo a seguir, a cláusula `where` usa um método para determinar se o valor atual da variável de intervalo é par ou ímpar.</span><span class="sxs-lookup"><span data-stu-id="df113-115">In the following example, the `where` clause uses a method to determine whether the current value of the range variable is even or odd.</span></span>

[!code-csharp[cscsrefQueryKeywords#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#7)]

## <a name="remarks"></a><span data-ttu-id="df113-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="df113-116">Remarks</span></span>

<span data-ttu-id="df113-117">A cláusula `where` é um mecanismo de filtragem.</span><span class="sxs-lookup"><span data-stu-id="df113-117">The `where` clause is a filtering mechanism.</span></span> <span data-ttu-id="df113-118">Ela pode ser posicionada em quase qualquer lugar em uma expressão de consulta, exceto que ela não pode ser a primeira ou a última cláusula.</span><span class="sxs-lookup"><span data-stu-id="df113-118">It can be positioned almost anywhere in a query expression, except it cannot be the first or last clause.</span></span> <span data-ttu-id="df113-119">A cláusula `where` pode aparecer antes ou depois de uma cláusula [group](group-clause.md) dependendo se você tiver que filtrar os elementos de origem antes ou depois de eles serem agrupados.</span><span class="sxs-lookup"><span data-stu-id="df113-119">A `where` clause may appear either before or after a [group](group-clause.md) clause depending on whether you have to filter the source elements before or after they are grouped.</span></span>

<span data-ttu-id="df113-120">Se um predicado especificado não for válido para os elementos na fonte de dados, o resultado será um erro em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="df113-120">If a specified predicate is not valid for the elements in the data source, a compile-time error will result.</span></span> <span data-ttu-id="df113-121">Essa é uma vantagem da verificação de tipo forte fornecida pelo [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="df113-121">This is one benefit of the strong type-checking provided by [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].</span></span>

<span data-ttu-id="df113-122">Em tempo de compilação, a palavra-chave `where` é convertida em uma chamada para o método de operador de consulta padrão <xref:System.Linq.Enumerable.Where%2A>.</span><span class="sxs-lookup"><span data-stu-id="df113-122">At compile time the `where` keyword is converted into a call to the <xref:System.Linq.Enumerable.Where%2A> Standard Query Operator method.</span></span>

## <a name="see-also"></a><span data-ttu-id="df113-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="df113-123">See also</span></span>

- [<span data-ttu-id="df113-124">Palavras-chave de Consulta (LINQ)</span><span class="sxs-lookup"><span data-stu-id="df113-124">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="df113-125">Cláusula From</span><span class="sxs-lookup"><span data-stu-id="df113-125">from clause</span></span>](from-clause.md)
- [<span data-ttu-id="df113-126">Cláusula select</span><span class="sxs-lookup"><span data-stu-id="df113-126">select clause</span></span>](select-clause.md)
- [<span data-ttu-id="df113-127">Filtrando Dados</span><span class="sxs-lookup"><span data-stu-id="df113-127">Filtering Data</span></span>](../../programming-guide/concepts/linq/filtering-data.md)
- [<span data-ttu-id="df113-128">LINQ em C#</span><span class="sxs-lookup"><span data-stu-id="df113-128">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="df113-129">Introdução a LINQ em C#</span><span class="sxs-lookup"><span data-stu-id="df113-129">Getting Started with LINQ in C#</span></span>](/dotnet/csharp/programming-guide/concepts/linq/)
