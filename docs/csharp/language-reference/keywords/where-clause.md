---
title: "Cláusula where (Referência de C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: whereclause_CSharpKeyword
helpviewer_keywords:
- where keyword [C#]
- where clause [C#]
ms.assetid: 7f9bf952-7744-4f91-b676-cddb55d107c3
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0324346ee5e214bf467fcb522ef781c91fa1b76f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="where-clause-c-reference"></a><span data-ttu-id="1e192-102">Cláusula where (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="1e192-102">where clause (C# Reference)</span></span>
<span data-ttu-id="1e192-103">A cláusula `where` é usada em uma expressão de consulta para especificar quais elementos da fonte de dados serão retornados na expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="1e192-103">The `where` clause is used in a query expression to specify which elements from the data source will be returned in the query expression.</span></span> <span data-ttu-id="1e192-104">Aplica-se uma condição booliana (*predicate*) para cada elemento de origem (referenciado pela variável de intervalo) e retorna aqueles para os quais a condição especificada for verdadeira.</span><span class="sxs-lookup"><span data-stu-id="1e192-104">It applies a Boolean condition (*predicate*) to each source element (referenced by the range variable) and returns those for which the specified condition is true.</span></span> <span data-ttu-id="1e192-105">Uma única expressão de consulta pode conter várias cláusulas `where` e uma única cláusula pode conter várias subexpressões de predicado.</span><span class="sxs-lookup"><span data-stu-id="1e192-105">A single query expression may contain multiple `where` clauses and a single clause may contain multiple predicate subexpressions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e192-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1e192-106">Example</span></span>  
 <span data-ttu-id="1e192-107">No exemplo a seguir, a cláusula `where` filtra todos os números, exceto aqueles que são menores que cinco.</span><span class="sxs-lookup"><span data-stu-id="1e192-107">In the following example, the `where` clause filters out all numbers except those that are less than five.</span></span> <span data-ttu-id="1e192-108">Se você remover a cláusula `where`, todos os números da fonte de dados serão retornados.</span><span class="sxs-lookup"><span data-stu-id="1e192-108">If you remove the `where` clause, all numbers from the data source would be returned.</span></span> <span data-ttu-id="1e192-109">A expressão `num < 5` é o predicado aplicado a cada elemento.</span><span class="sxs-lookup"><span data-stu-id="1e192-109">The expression `num < 5` is the predicate that is applied to each element.</span></span>  
  
 [!code-csharp[cscsrefQueryKeywords#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-clause_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="1e192-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1e192-110">Example</span></span>  
 <span data-ttu-id="1e192-111">Dentro de uma única cláusula `where`, você pode especificar tantos predicados quanto necessário usando os operadores [&&](../../../csharp/language-reference/operators/conditional-and-operator.md) e [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md).</span><span class="sxs-lookup"><span data-stu-id="1e192-111">Within a single `where` clause, you can specify as many predicates as necessary by using the [&&](../../../csharp/language-reference/operators/conditional-and-operator.md) and [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) operators.</span></span> <span data-ttu-id="1e192-112">No exemplo a seguir, a consulta especifica dois predicados para selecionar apenas os números pares que são menores que cinco.</span><span class="sxs-lookup"><span data-stu-id="1e192-112">In the following example, the query specifies two predicates in order to select only the even numbers that are less than five.</span></span>  
  
 [!code-csharp[cscsrefQueryKeywords#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-clause_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="1e192-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1e192-113">Example</span></span>  
 <span data-ttu-id="1e192-114">Uma cláusula `where` pode conter um ou mais métodos que retornam valores boolianos.</span><span class="sxs-lookup"><span data-stu-id="1e192-114">A `where` clause may contain one or more methods that return Boolean values.</span></span> <span data-ttu-id="1e192-115">No exemplo a seguir, a cláusula `where` usa um método para determinar se o valor atual da variável de intervalo é par ou ímpar.</span><span class="sxs-lookup"><span data-stu-id="1e192-115">In the following example, the `where` clause uses a method to determine whether the current value of the range variable is even or odd.</span></span>  
  
 [!code-csharp[cscsrefQueryKeywords#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-clause_3.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="1e192-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="1e192-116">Remarks</span></span>  
 <span data-ttu-id="1e192-117">A cláusula `where` é um mecanismo de filtragem.</span><span class="sxs-lookup"><span data-stu-id="1e192-117">The `where` clause is a filtering mechanism.</span></span> <span data-ttu-id="1e192-118">Ela pode ser posicionada em quase qualquer lugar em uma expressão de consulta, exceto que ela não pode ser a primeira ou a última cláusula.</span><span class="sxs-lookup"><span data-stu-id="1e192-118">It can be positioned almost anywhere in a query expression, except it cannot be the first or last clause.</span></span> <span data-ttu-id="1e192-119">A cláusula `where` pode aparecer antes ou depois de uma cláusula [group](../../../csharp/language-reference/keywords/group-clause.md) dependendo se você tiver que filtrar os elementos de origem antes ou depois de eles serem agrupados.</span><span class="sxs-lookup"><span data-stu-id="1e192-119">A `where` clause may appear either before or after a [group](../../../csharp/language-reference/keywords/group-clause.md) clause depending on whether you have to filter the source elements before or after they are grouped.</span></span>  
  
 <span data-ttu-id="1e192-120">Se um predicado especificado não for válido para os elementos na fonte de dados, o resultado será um erro em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="1e192-120">If a specified predicate is not valid for the elements in the data source, a compile-time error will result.</span></span> <span data-ttu-id="1e192-121">Essa é uma vantagem da verificação de tipo forte fornecida pelo [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1e192-121">This is one benefit of the strong type-checking provided by [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].</span></span>  
  
 <span data-ttu-id="1e192-122">Em tempo de compilação, a palavra-chave `where` é convertida em uma chamada para o método de operador de consulta padrão <xref:System.Linq.Enumerable.Where%2A>.</span><span class="sxs-lookup"><span data-stu-id="1e192-122">At compile time the `where` keyword is converted into a call to the <xref:System.Linq.Enumerable.Where%2A> Standard Query Operator method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e192-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1e192-123">See Also</span></span>  
 [<span data-ttu-id="1e192-124">Palavras-chave de Consulta (LINQ)</span><span class="sxs-lookup"><span data-stu-id="1e192-124">Query Keywords (LINQ)</span></span>](../../../csharp/language-reference/keywords/query-keywords.md)  
 [<span data-ttu-id="1e192-125">Cláusula From</span><span class="sxs-lookup"><span data-stu-id="1e192-125">from clause</span></span>](../../../csharp/language-reference/keywords/from-clause.md)  
 [<span data-ttu-id="1e192-126">Cláusula select</span><span class="sxs-lookup"><span data-stu-id="1e192-126">select clause</span></span>](../../../csharp/language-reference/keywords/select-clause.md)  
 [<span data-ttu-id="1e192-127">Filtrando Dados</span><span class="sxs-lookup"><span data-stu-id="1e192-127">Filtering Data</span></span>](../../programming-guide/concepts/linq/filtering-data.md)  
 [<span data-ttu-id="1e192-128">Expressões de consulta LINQ</span><span class="sxs-lookup"><span data-stu-id="1e192-128">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [<span data-ttu-id="1e192-129">Introdução a LINQ em C#</span><span class="sxs-lookup"><span data-stu-id="1e192-129">Getting Started with LINQ in C#</span></span>](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
