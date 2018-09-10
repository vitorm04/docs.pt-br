---
title: Operações de quantificador (C#)
ms.date: 07/20/2015
ms.assetid: 84ac2ac2-7a63-4581-bc4c-14e34be1493b
ms.openlocfilehash: 24c8f9a6b589592c26c8a514bc44ff9623a82d2f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43523099"
---
# <a name="quantifier-operations-c"></a><span data-ttu-id="3b0a1-102">Operações de quantificador (C#)</span><span class="sxs-lookup"><span data-stu-id="3b0a1-102">Quantifier Operations (C#)</span></span>
<span data-ttu-id="3b0a1-103">As operações de quantificador retornam um valor <xref:System.Boolean> que indica se alguns ou todos os elementos em uma sequência satisfazem uma condição.</span><span class="sxs-lookup"><span data-stu-id="3b0a1-103">Quantifier operations return a <xref:System.Boolean> value that indicates whether some or all of the elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="3b0a1-104">A ilustração a seguir mostra duas operações de quantificador diferentes em duas sequências de origem diferentes.</span><span class="sxs-lookup"><span data-stu-id="3b0a1-104">The following illustration depicts two different quantifier operations on two different source sequences.</span></span> <span data-ttu-id="3b0a1-105">A primeira operação pergunta se um ou mais dos elementos são o caractere 'A' e o resultado é `true`.</span><span class="sxs-lookup"><span data-stu-id="3b0a1-105">The first operation asks if one or more of the elements are the character 'A', and the result is `true`.</span></span> <span data-ttu-id="3b0a1-106">A segunda operação pergunta se todos os elementos são o caractere 'A' e o resultado é `true`.</span><span class="sxs-lookup"><span data-stu-id="3b0a1-106">The second operation asks if all the elements are the character 'A', and the result is `true`.</span></span>  
  
 <span data-ttu-id="3b0a1-107">![Operações de quantificador LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_quantifier.png "LINQ_Quantifier")</span><span class="sxs-lookup"><span data-stu-id="3b0a1-107">![LINQ Quantifier Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_quantifier.png "LINQ_Quantifier")</span></span>  
  
 <span data-ttu-id="3b0a1-108">Os métodos de operador de consulta padrão que realizam operações de quantificador estão listados na seção a seguir.</span><span class="sxs-lookup"><span data-stu-id="3b0a1-108">The standard query operator methods that perform quantifier operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3b0a1-109">Métodos</span><span class="sxs-lookup"><span data-stu-id="3b0a1-109">Methods</span></span>  
  
|<span data-ttu-id="3b0a1-110">Nome do método</span><span class="sxs-lookup"><span data-stu-id="3b0a1-110">Method Name</span></span>|<span data-ttu-id="3b0a1-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="3b0a1-111">Description</span></span>|<span data-ttu-id="3b0a1-112">Sintaxe de expressão de consulta C#</span><span class="sxs-lookup"><span data-stu-id="3b0a1-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="3b0a1-113">Mais informações</span><span class="sxs-lookup"><span data-stu-id="3b0a1-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="3b0a1-114">Todos</span><span class="sxs-lookup"><span data-stu-id="3b0a1-114">All</span></span>|<span data-ttu-id="3b0a1-115">Determina se todos os elementos em uma sequência satisfazem uma condição.</span><span class="sxs-lookup"><span data-stu-id="3b0a1-115">Determines whether all the elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="3b0a1-116">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="3b0a1-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="3b0a1-117">Qualquer</span><span class="sxs-lookup"><span data-stu-id="3b0a1-117">Any</span></span>|<span data-ttu-id="3b0a1-118">Determina se todos os elementos em uma sequência satisfazem uma condição.</span><span class="sxs-lookup"><span data-stu-id="3b0a1-118">Determines whether any elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="3b0a1-119">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="3b0a1-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="3b0a1-120">Contém</span><span class="sxs-lookup"><span data-stu-id="3b0a1-120">Contains</span></span>|<span data-ttu-id="3b0a1-121">Determina se uma sequência contém um elemento especificado.</span><span class="sxs-lookup"><span data-stu-id="3b0a1-121">Determines whether a sequence contains a specified element.</span></span>|<span data-ttu-id="3b0a1-122">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="3b0a1-122">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a><span data-ttu-id="3b0a1-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3b0a1-123">See Also</span></span>

- <xref:System.Linq>  
- [<span data-ttu-id="3b0a1-124">Visão geral de operadores de consulta padrão (C#)</span><span class="sxs-lookup"><span data-stu-id="3b0a1-124">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
- [<span data-ttu-id="3b0a1-125">Como especificar filtros predicados dinamicamente em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="3b0a1-125">How to: Dynamically Specify Predicate Filters at Runtime</span></span>](../../../../csharp/programming-guide/linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md)  
- [<span data-ttu-id="3b0a1-126">Como consultar sentenças que contenham um conjunto especificado de palavras (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="3b0a1-126">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)
