---
title: "Cláusula select (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- select_CSharpKeyword
- select
dev_langs:
- CSharp
helpviewer_keywords:
- select keyword [C#]
- select clause [C#]
ms.assetid: df01e266-5781-4aaa-80c4-67cf28ea093f
caps.latest.revision: 19
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
ms.openlocfilehash: a505399eb79cbecbefcc53953329279a4abd92f6
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="select-clause-c-reference"></a><span data-ttu-id="9bd60-102">Cláusula select (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="9bd60-102">select clause (C# Reference)</span></span>
<span data-ttu-id="9bd60-103">Em uma expressão de consulta, a cláusula `select` especifica o tipo de valores que serão produzidos quando a consulta é executada.</span><span class="sxs-lookup"><span data-stu-id="9bd60-103">In a query expression, the `select` clause specifies the type of values that will be produced when the query is executed.</span></span> <span data-ttu-id="9bd60-104">O resultado é baseado na avaliação de todas as cláusulas anteriores e em quaisquer expressões na cláusula `select` em si.</span><span class="sxs-lookup"><span data-stu-id="9bd60-104">The result is based on the evaluation of all the previous clauses and on any expressions in the `select` clause itself.</span></span> <span data-ttu-id="9bd60-105">Uma expressão de consulta deve terminar com uma cláusula `select` ou uma cláusula [group](../../../csharp/language-reference/keywords/group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="9bd60-105">A query expression must terminate with either a `select` clause or a [group](../../../csharp/language-reference/keywords/group-clause.md) clause.</span></span>  
  
 <span data-ttu-id="9bd60-106">O exemplo a seguir mostra uma cláusula `select` simples em uma expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="9bd60-106">The following example shows a simple `select` clause in a query expression.</span></span>  
  
 <span data-ttu-id="9bd60-107">[!code-cs[cscsrefQueryKeywords#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/select-clause_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="9bd60-107">[!code-cs[cscsrefQueryKeywords#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/select-clause_1.cs)]</span></span>  
  
 <span data-ttu-id="9bd60-108">O tipo da sequência produzida pela cláusula `select` determina o tipo da variável de consulta `queryHighScores`.</span><span class="sxs-lookup"><span data-stu-id="9bd60-108">The type of the sequence produced by the `select` clause determines the type of the query variable `queryHighScores`.</span></span> <span data-ttu-id="9bd60-109">No caso mais simples, a cláusula `select` apenas especifica a variável de intervalo.</span><span class="sxs-lookup"><span data-stu-id="9bd60-109">In the simplest case, the `select` clause just specifies the range variable.</span></span> <span data-ttu-id="9bd60-110">Isso faz com que a sequência retornada contenha elementos do mesmo tipo que a fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="9bd60-110">This causes the returned sequence to contain elements of the same type as the data source.</span></span> <span data-ttu-id="9bd60-111">Para obter mais informações, consulte [Relacionamentos de tipo em operações de consulta LINQ](../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="9bd60-111">For more information, see [Type Relationships in LINQ Query Operations](../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span></span> <span data-ttu-id="9bd60-112">No entanto, a cláusula `select` também fornece um mecanismo poderoso para transformar (ou *projetar*) dados de origem em novos tipos.</span><span class="sxs-lookup"><span data-stu-id="9bd60-112">However, the `select` clause also provides a powerful mechanism for transforming (or *projecting*) source data into new types.</span></span> <span data-ttu-id="9bd60-113">Para obter mais informações, consulte [Transformações de dados com LINQ (C#)](../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md).</span><span class="sxs-lookup"><span data-stu-id="9bd60-113">For more information, see [Data Transformations with LINQ (C#)](../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9bd60-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9bd60-114">Example</span></span>  
 <span data-ttu-id="9bd60-115">O exemplo a seguir mostra todas as diferentes formas que uma cláusula `select` pode tomar.</span><span class="sxs-lookup"><span data-stu-id="9bd60-115">The following example shows all the different forms that a `select` clause may take.</span></span> <span data-ttu-id="9bd60-116">Em cada consulta, observe a relação entre a cláusula `select` e o tipo da *variável de consulta* (`studentQuery1`, `studentQuery2` e assim por diante).</span><span class="sxs-lookup"><span data-stu-id="9bd60-116">In each query, note the relationship between the `select` clause and the type of the *query variable* (`studentQuery1`, `studentQuery2`, and so on).</span></span>  
  
 <span data-ttu-id="9bd60-117">[!code-cs[cscsrefQueryKeywords#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/select-clause_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="9bd60-117">[!code-cs[cscsrefQueryKeywords#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/select-clause_2.cs)]</span></span>  
  
 <span data-ttu-id="9bd60-118">Conforme mostrado em `studentQuery8` no exemplo anterior, às vezes, convém que os elementos da sequência retornada contenham apenas um subconjunto das propriedades dos elementos de origem.</span><span class="sxs-lookup"><span data-stu-id="9bd60-118">As shown in `studentQuery8` in the previous example, sometimes you might want the elements of the returned sequence to contain only a subset of the properties of the source elements.</span></span> <span data-ttu-id="9bd60-119">Mantendo a sequência retornada a menor possível, é possível reduzir os requisitos de memória e aumentar a velocidade da execução da consulta.</span><span class="sxs-lookup"><span data-stu-id="9bd60-119">By keeping the returned sequence as small as possible you can reduce the memory requirements and increase the speed of the execution of the query.</span></span> <span data-ttu-id="9bd60-120">É possível fazer isso criando um tipo anônimo na cláusula `select` e usando um inicializador de objeto para inicializá-lo com as propriedades adequadas do elemento de origem.</span><span class="sxs-lookup"><span data-stu-id="9bd60-120">You can accomplish this by creating an anonymous type in the `select` clause and using an object initializer to initialize it with the appropriate properties from the source element.</span></span> <span data-ttu-id="9bd60-121">Para obter um exemplo de como fazer isso, consulte [Inicializadores de objeto e coleção](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).</span><span class="sxs-lookup"><span data-stu-id="9bd60-121">For an example of how to do this, see [Object and Collection Initializers](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9bd60-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="9bd60-122">Remarks</span></span>  
 <span data-ttu-id="9bd60-123">No tempo de compilação, a cláusula `select` é convertida em uma chamada de método para o operador de consulta padrão <xref:System.Linq.Enumerable.Select%2A>.</span><span class="sxs-lookup"><span data-stu-id="9bd60-123">At compile time, the `select` clause is translated to a method call to the <xref:System.Linq.Enumerable.Select%2A> standard query operator.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bd60-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9bd60-124">See Also</span></span>  
 <span data-ttu-id="9bd60-125">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="9bd60-125">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="9bd60-126">[Palavras-chave de Consulta (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md) </span><span class="sxs-lookup"><span data-stu-id="9bd60-126">[Query Keywords (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md) </span></span>  
 <span data-ttu-id="9bd60-127">[Cláusula from](../../../csharp/language-reference/keywords/from-clause.md) </span><span class="sxs-lookup"><span data-stu-id="9bd60-127">[from clause](../../../csharp/language-reference/keywords/from-clause.md) </span></span>  
 <span data-ttu-id="9bd60-128">[parcial (método) (Referência de C#)](../../../csharp/language-reference/keywords/partial-method.md) </span><span class="sxs-lookup"><span data-stu-id="9bd60-128">[partial (Method) (C# Reference)](../../../csharp/language-reference/keywords/partial-method.md) </span></span>  
 <span data-ttu-id="9bd60-129">[Tipos Anônimos](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md) </span><span class="sxs-lookup"><span data-stu-id="9bd60-129">[Anonymous Types](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md) </span></span>  
 <span data-ttu-id="9bd60-130">[Expressões de Consulta LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md) </span><span class="sxs-lookup"><span data-stu-id="9bd60-130">[LINQ Query Expressions](../../../csharp/programming-guide/linq-query-expressions/index.md) </span></span>  
 [<span data-ttu-id="9bd60-131">Introdução a LINQ em C#</span><span class="sxs-lookup"><span data-stu-id="9bd60-131">Getting Started with LINQ in C#</span></span>](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)

