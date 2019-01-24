---
title: Operações de quantificador (Visual Basic)
ms.date: 07/20/2015
ms.assetid: ae1a2b73-503c-4f4b-a3fd-31b5adbee67c
ms.openlocfilehash: 0f732cdb51ed4e26039fc8c1d02b95ad32f901e1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54551914"
---
# <a name="quantifier-operations-visual-basic"></a><span data-ttu-id="71bb0-102">Operações de quantificador (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="71bb0-102">Quantifier Operations (Visual Basic)</span></span>
<span data-ttu-id="71bb0-103">As operações de quantificador retornam um valor <xref:System.Boolean> que indica se alguns ou todos os elementos em uma sequência satisfazem uma condição.</span><span class="sxs-lookup"><span data-stu-id="71bb0-103">Quantifier operations return a <xref:System.Boolean> value that indicates whether some or all of the elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="71bb0-104">A ilustração a seguir mostra duas operações de quantificador diferentes em duas sequências de origem diferentes.</span><span class="sxs-lookup"><span data-stu-id="71bb0-104">The following illustration depicts two different quantifier operations on two different source sequences.</span></span> <span data-ttu-id="71bb0-105">A primeira operação pergunta se um ou mais dos elementos são o caractere 'A' e o resultado é `true`.</span><span class="sxs-lookup"><span data-stu-id="71bb0-105">The first operation asks if one or more of the elements are the character 'A', and the result is `true`.</span></span> <span data-ttu-id="71bb0-106">A segunda operação pergunta se todos os elementos são o caractere 'A' e o resultado é `true`.</span><span class="sxs-lookup"><span data-stu-id="71bb0-106">The second operation asks if all the elements are the character 'A', and the result is `true`.</span></span>  
  
 <span data-ttu-id="71bb0-107">![Operações de quantificador LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_quantifier.png "LINQ_Quantifier")</span><span class="sxs-lookup"><span data-stu-id="71bb0-107">![LINQ Quantifier Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_quantifier.png "LINQ_Quantifier")</span></span>  
  
 <span data-ttu-id="71bb0-108">Os métodos de operador de consulta padrão que realizam operações de quantificador estão listados na seção a seguir.</span><span class="sxs-lookup"><span data-stu-id="71bb0-108">The standard query operator methods that perform quantifier operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="71bb0-109">Métodos</span><span class="sxs-lookup"><span data-stu-id="71bb0-109">Methods</span></span>  
  
|<span data-ttu-id="71bb0-110">Nome do método</span><span class="sxs-lookup"><span data-stu-id="71bb0-110">Method Name</span></span>|<span data-ttu-id="71bb0-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="71bb0-111">Description</span></span>|<span data-ttu-id="71bb0-112">Sintaxe de expressão de consulta do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="71bb0-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="71bb0-113">Mais informações</span><span class="sxs-lookup"><span data-stu-id="71bb0-113">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="71bb0-114">Todos</span><span class="sxs-lookup"><span data-stu-id="71bb0-114">All</span></span>|<span data-ttu-id="71bb0-115">Determina se todos os elementos em uma sequência satisfazem uma condição.</span><span class="sxs-lookup"><span data-stu-id="71bb0-115">Determines whether all the elements in a sequence satisfy a condition.</span></span>|`Aggregate … In … Into All(…)`|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="71bb0-116">Qualquer</span><span class="sxs-lookup"><span data-stu-id="71bb0-116">Any</span></span>|<span data-ttu-id="71bb0-117">Determina se todos os elementos em uma sequência satisfazem uma condição.</span><span class="sxs-lookup"><span data-stu-id="71bb0-117">Determines whether any elements in a sequence satisfy a condition.</span></span>|`Aggregate … In … Into Any()`|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="71bb0-118">Contém</span><span class="sxs-lookup"><span data-stu-id="71bb0-118">Contains</span></span>|<span data-ttu-id="71bb0-119">Determina se uma sequência contém um elemento especificado.</span><span class="sxs-lookup"><span data-stu-id="71bb0-119">Determines whether a sequence contains a specified element.</span></span>|<span data-ttu-id="71bb0-120">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="71bb0-120">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="71bb0-121">Exemplos de sintaxe de expressão de consulta</span><span class="sxs-lookup"><span data-stu-id="71bb0-121">Query Expression Syntax Examples</span></span>  
 <span data-ttu-id="71bb0-122">Esses exemplos usam o `Aggregate` cláusula no Visual Basic como parte da condição de filtragem em uma consulta LINQ.</span><span class="sxs-lookup"><span data-stu-id="71bb0-122">These examples use the `Aggregate` clause in Visual Basic as part of the filtering condition in a LINQ query.</span></span>  
  
 <span data-ttu-id="71bb0-123">O exemplo a seguir usa o `Aggregate` cláusula e o <xref:System.Linq.Enumerable.All%2A> método de extensão para retornar de uma coleção às pessoas cujos animais de estimação são todos os mais antigos do que uma determinada idade.</span><span class="sxs-lookup"><span data-stu-id="71bb0-123">The following example uses the `Aggregate` clause and the <xref:System.Linq.Enumerable.All%2A> extension method to return from a collection those people whose pets are all older than a specified age.</span></span>  
  
 [!code-vb[CsLINQAnyAll#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/quantifier-operations_1.vb)]  
  
 <span data-ttu-id="71bb0-124">O próximo exemplo usa o `Aggregate` cláusula e o <xref:System.Linq.Enumerable.Any%2A> método de extensão para retornar de uma coleção, as pessoas que possuem pelo menos uma pet que é mais antigo que uma determinada idade.</span><span class="sxs-lookup"><span data-stu-id="71bb0-124">The next example uses the `Aggregate` clause and the <xref:System.Linq.Enumerable.Any%2A> extension method to return from a collection those people who have at least one pet that is older than a specified age.</span></span>  
  
 [!code-vb[CsLINQAnyAll#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/quantifier-operations_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="71bb0-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="71bb0-125">See also</span></span>
- <xref:System.Linq>
- [<span data-ttu-id="71bb0-126">Visão geral de operadores de consulta padrão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="71bb0-126">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="71bb0-127">Cláusula Aggregate</span><span class="sxs-lookup"><span data-stu-id="71bb0-127">Aggregate Clause</span></span>](../../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [<span data-ttu-id="71bb0-128">Como: Consultar sentenças que contenham um conjunto especificado de palavras (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="71bb0-128">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)
