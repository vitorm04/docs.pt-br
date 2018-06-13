---
title: Operações de quantificador (C#)
ms.date: 07/20/2015
ms.assetid: 84ac2ac2-7a63-4581-bc4c-14e34be1493b
ms.openlocfilehash: dac5ca7349a45f5fc37cff0cb83bd6b2e1292568
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33339859"
---
# <a name="quantifier-operations-c"></a><span data-ttu-id="440da-102">Operações de quantificador (C#)</span><span class="sxs-lookup"><span data-stu-id="440da-102">Quantifier Operations (C#)</span></span>
<span data-ttu-id="440da-103">As operações de quantificador retornam um valor <xref:System.Boolean> que indica se alguns ou todos os elementos em uma sequência satisfazem uma condição.</span><span class="sxs-lookup"><span data-stu-id="440da-103">Quantifier operations return a <xref:System.Boolean> value that indicates whether some or all of the elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="440da-104">A ilustração a seguir mostra duas operações de quantificador diferentes em duas sequências de origem diferentes.</span><span class="sxs-lookup"><span data-stu-id="440da-104">The following illustration depicts two different quantifier operations on two different source sequences.</span></span> <span data-ttu-id="440da-105">A primeira operação pergunta se um ou mais dos elementos são o caractere 'A' e o resultado é `true`.</span><span class="sxs-lookup"><span data-stu-id="440da-105">The first operation asks if one or more of the elements are the character 'A', and the result is `true`.</span></span> <span data-ttu-id="440da-106">A segunda operação pergunta se todos os elementos são o caractere 'A' e o resultado é `true`.</span><span class="sxs-lookup"><span data-stu-id="440da-106">The second operation asks if all the elements are the character 'A', and the result is `true`.</span></span>  
  
 <span data-ttu-id="440da-107">![Operações de quantificador LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_quantifier.png "LINQ_Quantifier")</span><span class="sxs-lookup"><span data-stu-id="440da-107">![LINQ Quantifier Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_quantifier.png "LINQ_Quantifier")</span></span>  
  
 <span data-ttu-id="440da-108">Os métodos de operador de consulta padrão que realizam operações de quantificador estão listados na seção a seguir.</span><span class="sxs-lookup"><span data-stu-id="440da-108">The standard query operator methods that perform quantifier operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="440da-109">Métodos</span><span class="sxs-lookup"><span data-stu-id="440da-109">Methods</span></span>  
  
|<span data-ttu-id="440da-110">Nome do método</span><span class="sxs-lookup"><span data-stu-id="440da-110">Method Name</span></span>|<span data-ttu-id="440da-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="440da-111">Description</span></span>|<span data-ttu-id="440da-112">Sintaxe de expressão de consulta C#</span><span class="sxs-lookup"><span data-stu-id="440da-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="440da-113">Mais informações</span><span class="sxs-lookup"><span data-stu-id="440da-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="440da-114">Todos</span><span class="sxs-lookup"><span data-stu-id="440da-114">All</span></span>|<span data-ttu-id="440da-115">Determina se todos os elementos em uma sequência satisfazem uma condição.</span><span class="sxs-lookup"><span data-stu-id="440da-115">Determines whether all the elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="440da-116">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="440da-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="440da-117">Qualquer</span><span class="sxs-lookup"><span data-stu-id="440da-117">Any</span></span>|<span data-ttu-id="440da-118">Determina se todos os elementos em uma sequência satisfazem uma condição.</span><span class="sxs-lookup"><span data-stu-id="440da-118">Determines whether any elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="440da-119">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="440da-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="440da-120">Contém</span><span class="sxs-lookup"><span data-stu-id="440da-120">Contains</span></span>|<span data-ttu-id="440da-121">Determina se uma sequência contém um elemento especificado.</span><span class="sxs-lookup"><span data-stu-id="440da-121">Determines whether a sequence contains a specified element.</span></span>|<span data-ttu-id="440da-122">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="440da-122">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a><span data-ttu-id="440da-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="440da-123">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="440da-124">Visão geral de operadores de consulta padrão (C#)</span><span class="sxs-lookup"><span data-stu-id="440da-124">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="440da-125">Como especificar filtros predicados dinamicamente em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="440da-125">How to: Dynamically Specify Predicate Filters at Runtime</span></span>](../../../../csharp/programming-guide/linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md)  
 [<span data-ttu-id="440da-126">Como consultar sentenças que contenham um conjunto especificado de palavras (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="440da-126">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)
