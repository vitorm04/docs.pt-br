---
title: Operações de quantificador
ms.date: 07/20/2015
ms.assetid: ae1a2b73-503c-4f4b-a3fd-31b5adbee67c
ms.openlocfilehash: 0c1c69cb36ac16126454dc0c24cd84fc85b0b218
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91075298"
---
# <a name="quantifier-operations-visual-basic"></a><span data-ttu-id="6b6b8-102">Operações do quantificador (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6b6b8-102">Quantifier Operations (Visual Basic)</span></span>

<span data-ttu-id="6b6b8-103">As operações de quantificador retornam um valor <xref:System.Boolean> que indica se alguns ou todos os elementos em uma sequência satisfazem uma condição.</span><span class="sxs-lookup"><span data-stu-id="6b6b8-103">Quantifier operations return a <xref:System.Boolean> value that indicates whether some or all of the elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="6b6b8-104">A ilustração a seguir mostra duas operações de quantificador diferentes em duas sequências de origem diferentes.</span><span class="sxs-lookup"><span data-stu-id="6b6b8-104">The following illustration depicts two different quantifier operations on two different source sequences.</span></span> <span data-ttu-id="6b6b8-105">A primeira operação pergunta se um ou mais dos elementos são o caractere 'A' e o resultado é `true`.</span><span class="sxs-lookup"><span data-stu-id="6b6b8-105">The first operation asks if one or more of the elements are the character 'A', and the result is `true`.</span></span> <span data-ttu-id="6b6b8-106">A segunda operação pergunta se todos os elementos são o caractere 'A' e o resultado é `true`.</span><span class="sxs-lookup"><span data-stu-id="6b6b8-106">The second operation asks if all the elements are the character 'A', and the result is `true`.</span></span>  
  
 ![Operações de quantificador LINQ](./media/quantifier-operations/linq-quantifier-operations.png)  
  
 <span data-ttu-id="6b6b8-108">Os métodos de operador de consulta padrão que realizam operações de quantificador estão listados na seção a seguir.</span><span class="sxs-lookup"><span data-stu-id="6b6b8-108">The standard query operator methods that perform quantifier operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6b6b8-109">Métodos</span><span class="sxs-lookup"><span data-stu-id="6b6b8-109">Methods</span></span>  
  
|<span data-ttu-id="6b6b8-110">Nome do método</span><span class="sxs-lookup"><span data-stu-id="6b6b8-110">Method Name</span></span>|<span data-ttu-id="6b6b8-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="6b6b8-111">Description</span></span>|<span data-ttu-id="6b6b8-112">Visual Basic sintaxe de expressão de consulta</span><span class="sxs-lookup"><span data-stu-id="6b6b8-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="6b6b8-113">Mais informações</span><span class="sxs-lookup"><span data-stu-id="6b6b8-113">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="6b6b8-114">Tudo</span><span class="sxs-lookup"><span data-stu-id="6b6b8-114">All</span></span>|<span data-ttu-id="6b6b8-115">Determina se todos os elementos em uma sequência satisfazem uma condição.</span><span class="sxs-lookup"><span data-stu-id="6b6b8-115">Determines whether all the elements in a sequence satisfy a condition.</span></span>|`Aggregate … In … Into All(…)`|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="6b6b8-116">Qualquer</span><span class="sxs-lookup"><span data-stu-id="6b6b8-116">Any</span></span>|<span data-ttu-id="6b6b8-117">Determina se todos os elementos em uma sequência satisfazem uma condição.</span><span class="sxs-lookup"><span data-stu-id="6b6b8-117">Determines whether any elements in a sequence satisfy a condition.</span></span>|`Aggregate … In … Into Any()`|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="6b6b8-118">Contém</span><span class="sxs-lookup"><span data-stu-id="6b6b8-118">Contains</span></span>|<span data-ttu-id="6b6b8-119">Determina se uma sequência contém um elemento especificado.</span><span class="sxs-lookup"><span data-stu-id="6b6b8-119">Determines whether a sequence contains a specified element.</span></span>|<span data-ttu-id="6b6b8-120">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="6b6b8-120">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="6b6b8-121">Exemplos de sintaxe de expressão de consulta</span><span class="sxs-lookup"><span data-stu-id="6b6b8-121">Query Expression Syntax Examples</span></span>  

 <span data-ttu-id="6b6b8-122">Esses exemplos usam a `Aggregate` cláusula em Visual Basic como parte da condição de filtragem em uma consulta LINQ.</span><span class="sxs-lookup"><span data-stu-id="6b6b8-122">These examples use the `Aggregate` clause in Visual Basic as part of the filtering condition in a LINQ query.</span></span>  
  
 <span data-ttu-id="6b6b8-123">O exemplo a seguir usa a `Aggregate` cláusula e o <xref:System.Linq.Enumerable.All%2A> método de extensão para retornar de uma coleção as pessoas cujos animais de estimação são todos mais antigos do que uma idade especificada.</span><span class="sxs-lookup"><span data-stu-id="6b6b8-123">The following example uses the `Aggregate` clause and the <xref:System.Linq.Enumerable.All%2A> extension method to return from a collection those people whose pets are all older than a specified age.</span></span>  
  
 [!code-vb[CsLINQAnyAll#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAnyAll/VB/AnyAll.vb#1)]  
  
 <span data-ttu-id="6b6b8-124">O exemplo a seguir usa a `Aggregate` cláusula e o <xref:System.Linq.Enumerable.Any%2A> método de extensão para retornar de uma coleção as pessoas que têm pelo menos um animal de estimação que seja mais antigo que uma idade especificada.</span><span class="sxs-lookup"><span data-stu-id="6b6b8-124">The next example uses the `Aggregate` clause and the <xref:System.Linq.Enumerable.Any%2A> extension method to return from a collection those people who have at least one pet that is older than a specified age.</span></span>  
  
 [!code-vb[CsLINQAnyAll#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAnyAll/VB/AnyAll.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="6b6b8-125">Confira também</span><span class="sxs-lookup"><span data-stu-id="6b6b8-125">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="6b6b8-126">Visão geral de operadores de consulta padrão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6b6b8-126">Standard Query Operators Overview (Visual Basic)</span></span>](standard-query-operators-overview.md)
- [<span data-ttu-id="6b6b8-127">Cláusula Aggregate</span><span class="sxs-lookup"><span data-stu-id="6b6b8-127">Aggregate Clause</span></span>](../../../language-reference/queries/aggregate-clause.md)
- [<span data-ttu-id="6b6b8-128">Como consultar frases que contêm um conjunto especificado de palavras (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6b6b8-128">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (Visual Basic)</span></span>](how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)
