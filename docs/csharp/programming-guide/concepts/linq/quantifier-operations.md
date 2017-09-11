---
title: "Operações de quantificador (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 84ac2ac2-7a63-4581-bc4c-14e34be1493b
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: f82df05693dffec64bcbc66cc2c0b9db2a7deb20
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="quantifier-operations-c"></a><span data-ttu-id="194f3-102">Operações de quantificador (C#)</span><span class="sxs-lookup"><span data-stu-id="194f3-102">Quantifier Operations (C#)</span></span>
<span data-ttu-id="194f3-103">As operações de quantificador retornam um valor <xref:System.Boolean> que indica se alguns ou todos os elementos em uma sequência satisfazem uma condição.</span><span class="sxs-lookup"><span data-stu-id="194f3-103">Quantifier operations return a <xref:System.Boolean> value that indicates whether some or all of the elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="194f3-104">A ilustração a seguir mostra duas operações de quantificador diferentes em duas sequências de origem diferentes.</span><span class="sxs-lookup"><span data-stu-id="194f3-104">The following illustration depicts two different quantifier operations on two different source sequences.</span></span> <span data-ttu-id="194f3-105">A primeira operação pergunta se um ou mais dos elementos são o caractere 'A' e o resultado é `true`.</span><span class="sxs-lookup"><span data-stu-id="194f3-105">The first operation asks if one or more of the elements are the character 'A', and the result is `true`.</span></span> <span data-ttu-id="194f3-106">A segunda operação pergunta se todos os elementos são o caractere 'A' e o resultado é `true`.</span><span class="sxs-lookup"><span data-stu-id="194f3-106">The second operation asks if all the elements are the character 'A', and the result is `true`.</span></span>  
  
 <span data-ttu-id="194f3-107">![Operações de quantificador LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_quantifier.png "LINQ_Quantifier")</span><span class="sxs-lookup"><span data-stu-id="194f3-107">![LINQ Quantifier Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_quantifier.png "LINQ_Quantifier")</span></span>  
  
 <span data-ttu-id="194f3-108">Os métodos de operador de consulta padrão que realizam operações de quantificador estão listados na seção a seguir.</span><span class="sxs-lookup"><span data-stu-id="194f3-108">The standard query operator methods that perform quantifier operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="194f3-109">Métodos</span><span class="sxs-lookup"><span data-stu-id="194f3-109">Methods</span></span>  
  
|<span data-ttu-id="194f3-110">Nome do método</span><span class="sxs-lookup"><span data-stu-id="194f3-110">Method Name</span></span>|<span data-ttu-id="194f3-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="194f3-111">Description</span></span>|<span data-ttu-id="194f3-112">Sintaxe de expressão de consulta C#</span><span class="sxs-lookup"><span data-stu-id="194f3-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="194f3-113">Mais informações</span><span class="sxs-lookup"><span data-stu-id="194f3-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="194f3-114">Todos</span><span class="sxs-lookup"><span data-stu-id="194f3-114">All</span></span>|<span data-ttu-id="194f3-115">Determina se todos os elementos em uma sequência satisfazem uma condição.</span><span class="sxs-lookup"><span data-stu-id="194f3-115">Determines whether all the elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="194f3-116">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="194f3-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.All%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=fullName>|  
|<span data-ttu-id="194f3-117">Qualquer</span><span class="sxs-lookup"><span data-stu-id="194f3-117">Any</span></span>|<span data-ttu-id="194f3-118">Determina se todos os elementos em uma sequência satisfazem uma condição.</span><span class="sxs-lookup"><span data-stu-id="194f3-118">Determines whether any elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="194f3-119">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="194f3-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Any%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=fullName>|  
|<span data-ttu-id="194f3-120">Contém</span><span class="sxs-lookup"><span data-stu-id="194f3-120">Contains</span></span>|<span data-ttu-id="194f3-121">Determina se uma sequência contém um elemento especificado.</span><span class="sxs-lookup"><span data-stu-id="194f3-121">Determines whether a sequence contains a specified element.</span></span>|<span data-ttu-id="194f3-122">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="194f3-122">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=fullName>|  
  
## <a name="see-also"></a><span data-ttu-id="194f3-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="194f3-123">See Also</span></span>  
 <span data-ttu-id="194f3-124"><xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="194f3-124"><xref:System.Linq></span></span>   
 <span data-ttu-id="194f3-125">[Visão geral de operadores de consulta padrão (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) </span><span class="sxs-lookup"><span data-stu-id="194f3-125">[Standard Query Operators Overview (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) </span></span>  
 <span data-ttu-id="194f3-126">[Como especificar filtros predicados dinamicamente em tempo de execução](../../../../csharp/programming-guide/linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md) </span><span class="sxs-lookup"><span data-stu-id="194f3-126">[How to: Dynamically Specify Predicate Filters at Runtime](../../../../csharp/programming-guide/linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md) </span></span>  
 [<span data-ttu-id="194f3-127">Como consultar sentenças que contenham um conjunto especificado de palavras (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="194f3-127">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)

