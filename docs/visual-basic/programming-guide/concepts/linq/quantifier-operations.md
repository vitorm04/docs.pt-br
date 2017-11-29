---
title: "Operações de quantificador (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ae1a2b73-503c-4f4b-a3fd-31b5adbee67c
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9bc48c69179b1f8876efaa465295e94a9a0e0fb6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="quantifier-operations-visual-basic"></a><span data-ttu-id="52b38-102">Operações de quantificador (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="52b38-102">Quantifier Operations (Visual Basic)</span></span>
<span data-ttu-id="52b38-103">As operações de quantificador retornam um valor <xref:System.Boolean> que indica se alguns ou todos os elementos em uma sequência satisfazem uma condição.</span><span class="sxs-lookup"><span data-stu-id="52b38-103">Quantifier operations return a <xref:System.Boolean> value that indicates whether some or all of the elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="52b38-104">A ilustração a seguir mostra duas operações de quantificador diferentes em duas sequências de origem diferentes.</span><span class="sxs-lookup"><span data-stu-id="52b38-104">The following illustration depicts two different quantifier operations on two different source sequences.</span></span> <span data-ttu-id="52b38-105">A primeira operação pergunta se um ou mais dos elementos são o caractere 'A' e o resultado é `true`.</span><span class="sxs-lookup"><span data-stu-id="52b38-105">The first operation asks if one or more of the elements are the character 'A', and the result is `true`.</span></span> <span data-ttu-id="52b38-106">A segunda operação pergunta se todos os elementos são o caractere 'A' e o resultado é `true`.</span><span class="sxs-lookup"><span data-stu-id="52b38-106">The second operation asks if all the elements are the character 'A', and the result is `true`.</span></span>  
  
 <span data-ttu-id="52b38-107">![Operações de quantificador LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_quantifier.png "LINQ_Quantifier")</span><span class="sxs-lookup"><span data-stu-id="52b38-107">![LINQ Quantifier Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_quantifier.png "LINQ_Quantifier")</span></span>  
  
 <span data-ttu-id="52b38-108">Os métodos de operador de consulta padrão que realizam operações de quantificador estão listados na seção a seguir.</span><span class="sxs-lookup"><span data-stu-id="52b38-108">The standard query operator methods that perform quantifier operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="52b38-109">Métodos</span><span class="sxs-lookup"><span data-stu-id="52b38-109">Methods</span></span>  
  
|<span data-ttu-id="52b38-110">Nome do método</span><span class="sxs-lookup"><span data-stu-id="52b38-110">Method Name</span></span>|<span data-ttu-id="52b38-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="52b38-111">Description</span></span>|<span data-ttu-id="52b38-112">Sintaxe de expressão de consulta do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="52b38-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="52b38-113">Mais informações</span><span class="sxs-lookup"><span data-stu-id="52b38-113">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="52b38-114">Todos</span><span class="sxs-lookup"><span data-stu-id="52b38-114">All</span></span>|<span data-ttu-id="52b38-115">Determina se todos os elementos em uma sequência satisfazem uma condição.</span><span class="sxs-lookup"><span data-stu-id="52b38-115">Determines whether all the elements in a sequence satisfy a condition.</span></span>|`Aggregate … In … Into All(…)`|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="52b38-116">Qualquer</span><span class="sxs-lookup"><span data-stu-id="52b38-116">Any</span></span>|<span data-ttu-id="52b38-117">Determina se todos os elementos em uma sequência satisfazem uma condição.</span><span class="sxs-lookup"><span data-stu-id="52b38-117">Determines whether any elements in a sequence satisfy a condition.</span></span>|`Aggregate … In … Into Any()`|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="52b38-118">Contém</span><span class="sxs-lookup"><span data-stu-id="52b38-118">Contains</span></span>|<span data-ttu-id="52b38-119">Determina se uma sequência contém um elemento especificado.</span><span class="sxs-lookup"><span data-stu-id="52b38-119">Determines whether a sequence contains a specified element.</span></span>|<span data-ttu-id="52b38-120">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="52b38-120">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="52b38-121">Exemplos de sintaxe de expressão de consulta</span><span class="sxs-lookup"><span data-stu-id="52b38-121">Query Expression Syntax Examples</span></span>  
 <span data-ttu-id="52b38-122">Esses exemplos usam o `Aggregate` cláusula no Visual Basic, como parte da condição de filtragem em uma consulta LINQ.</span><span class="sxs-lookup"><span data-stu-id="52b38-122">These examples use the `Aggregate` clause in Visual Basic as part of the filtering condition in a LINQ query.</span></span>  
  
 <span data-ttu-id="52b38-123">O exemplo a seguir usa o `Aggregate` cláusula e o <xref:System.Linq.Enumerable.All%2A> método de extensão para as pessoas cujos animais de estimação são todos os mais antigos do que uma determinada idade de retorno de uma coleção.</span><span class="sxs-lookup"><span data-stu-id="52b38-123">The following example uses the `Aggregate` clause and the <xref:System.Linq.Enumerable.All%2A> extension method to return from a collection those people whose pets are all older than a specified age.</span></span>  
  
 [!code-vb[CsLINQAnyAll#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/quantifier-operations_1.vb)]  
  
 <span data-ttu-id="52b38-124">O exemplo a seguir usa o `Aggregate` cláusula e o <xref:System.Linq.Enumerable.Any%2A> método de extensão para retornar de uma coleção, as pessoas que possuem pelo menos um pet que é mais de uma determinada idade.</span><span class="sxs-lookup"><span data-stu-id="52b38-124">The next example uses the `Aggregate` clause and the <xref:System.Linq.Enumerable.Any%2A> extension method to return from a collection those people who have at least one pet that is older than a specified age.</span></span>  
  
 [!code-vb[CsLINQAnyAll#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/quantifier-operations_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="52b38-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="52b38-125">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="52b38-126">Visão geral de operadores de consulta padrão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="52b38-126">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="52b38-127">Cláusula Aggregate</span><span class="sxs-lookup"><span data-stu-id="52b38-127">Aggregate Clause</span></span>](../../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [<span data-ttu-id="52b38-128">Como: consultar sentenças que contêm um conjunto especificado de palavras (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="52b38-128">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)
