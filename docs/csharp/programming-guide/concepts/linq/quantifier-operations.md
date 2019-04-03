---
title: Operações de quantificador (C#)
ms.date: 07/20/2015
ms.assetid: 84ac2ac2-7a63-4581-bc4c-14e34be1493b
ms.openlocfilehash: 090bc53c3dcedc82972ab7d16fa2968011a7db65
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2019
ms.locfileid: "58412247"
---
# <a name="quantifier-operations-c"></a><span data-ttu-id="2b0ed-102">Operações de quantificador (C#)</span><span class="sxs-lookup"><span data-stu-id="2b0ed-102">Quantifier Operations (C#)</span></span>
<span data-ttu-id="2b0ed-103">As operações de quantificador retornam um valor <xref:System.Boolean> que indica se alguns ou todos os elementos em uma sequência satisfazem uma condição.</span><span class="sxs-lookup"><span data-stu-id="2b0ed-103">Quantifier operations return a <xref:System.Boolean> value that indicates whether some or all of the elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="2b0ed-104">A ilustração a seguir mostra duas operações de quantificador diferentes em duas sequências de origem diferentes.</span><span class="sxs-lookup"><span data-stu-id="2b0ed-104">The following illustration depicts two different quantifier operations on two different source sequences.</span></span> <span data-ttu-id="2b0ed-105">A primeira operação pergunta se um ou mais dos elementos são o caractere 'A' e o resultado é `true`.</span><span class="sxs-lookup"><span data-stu-id="2b0ed-105">The first operation asks if one or more of the elements are the character 'A', and the result is `true`.</span></span> <span data-ttu-id="2b0ed-106">A segunda operação pergunta se todos os elementos são o caractere 'A' e o resultado é `true`.</span><span class="sxs-lookup"><span data-stu-id="2b0ed-106">The second operation asks if all the elements are the character 'A', and the result is `true`.</span></span>  
  
 ![Operações de quantificador LINQ](./media/quantifier-operations/linq-quantifier-operations.png)  
  
 <span data-ttu-id="2b0ed-108">Os métodos de operador de consulta padrão que realizam operações de quantificador estão listados na seção a seguir.</span><span class="sxs-lookup"><span data-stu-id="2b0ed-108">The standard query operator methods that perform quantifier operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2b0ed-109">Métodos</span><span class="sxs-lookup"><span data-stu-id="2b0ed-109">Methods</span></span>  
  
|<span data-ttu-id="2b0ed-110">Nome do método</span><span class="sxs-lookup"><span data-stu-id="2b0ed-110">Method Name</span></span>|<span data-ttu-id="2b0ed-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b0ed-111">Description</span></span>|<span data-ttu-id="2b0ed-112">Sintaxe de expressão de consulta C#</span><span class="sxs-lookup"><span data-stu-id="2b0ed-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="2b0ed-113">Mais informações</span><span class="sxs-lookup"><span data-stu-id="2b0ed-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="2b0ed-114">Todos</span><span class="sxs-lookup"><span data-stu-id="2b0ed-114">All</span></span>|<span data-ttu-id="2b0ed-115">Determina se todos os elementos em uma sequência satisfazem uma condição.</span><span class="sxs-lookup"><span data-stu-id="2b0ed-115">Determines whether all the elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="2b0ed-116">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="2b0ed-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="2b0ed-117">Qualquer</span><span class="sxs-lookup"><span data-stu-id="2b0ed-117">Any</span></span>|<span data-ttu-id="2b0ed-118">Determina se todos os elementos em uma sequência satisfazem uma condição.</span><span class="sxs-lookup"><span data-stu-id="2b0ed-118">Determines whether any elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="2b0ed-119">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="2b0ed-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="2b0ed-120">Contém</span><span class="sxs-lookup"><span data-stu-id="2b0ed-120">Contains</span></span>|<span data-ttu-id="2b0ed-121">Determina se uma sequência contém um elemento especificado.</span><span class="sxs-lookup"><span data-stu-id="2b0ed-121">Determines whether a sequence contains a specified element.</span></span>|<span data-ttu-id="2b0ed-122">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="2b0ed-122">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a><span data-ttu-id="2b0ed-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2b0ed-123">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="2b0ed-124">Visão geral de operadores de consulta padrão (C#)</span><span class="sxs-lookup"><span data-stu-id="2b0ed-124">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="2b0ed-125">Como: Especificar filtros de predicado dinamicamente em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="2b0ed-125">How to: Dynamically Specify Predicate Filters at Runtime</span></span>](../../../../csharp/programming-guide/linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md)
- [<span data-ttu-id="2b0ed-126">Como: Consultar sentenças que contêm um conjunto especificado de palavras (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="2b0ed-126">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)
