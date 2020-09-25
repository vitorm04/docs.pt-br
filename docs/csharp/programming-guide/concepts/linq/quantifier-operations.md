---
title: Operações de quantificador (C#)
description: Saiba mais sobre as operações do quantificador. Essas operações retornam um valor booliano que indica se alguns ou todos os elementos em uma sequência atendem a uma condição.
ms.date: 07/20/2015
ms.assetid: 84ac2ac2-7a63-4581-bc4c-14e34be1493b
ms.openlocfilehash: ffefe1715fd8a074692967e825e0f55673bb2b27
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202533"
---
# <a name="quantifier-operations-c"></a><span data-ttu-id="5edf7-104">Operações de quantificador (C#)</span><span class="sxs-lookup"><span data-stu-id="5edf7-104">Quantifier Operations (C#)</span></span>

<span data-ttu-id="5edf7-105">As operações de quantificador retornam um valor <xref:System.Boolean> que indica se alguns ou todos os elementos em uma sequência satisfazem uma condição.</span><span class="sxs-lookup"><span data-stu-id="5edf7-105">Quantifier operations return a <xref:System.Boolean> value that indicates whether some or all of the elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="5edf7-106">A ilustração a seguir mostra duas operações de quantificador diferentes em duas sequências de origem diferentes.</span><span class="sxs-lookup"><span data-stu-id="5edf7-106">The following illustration depicts two different quantifier operations on two different source sequences.</span></span> <span data-ttu-id="5edf7-107">A primeira operação pergunta se um ou mais dos elementos são o caractere 'A' e o resultado é `true`.</span><span class="sxs-lookup"><span data-stu-id="5edf7-107">The first operation asks if one or more of the elements are the character 'A', and the result is `true`.</span></span> <span data-ttu-id="5edf7-108">A segunda operação pergunta se todos os elementos são o caractere 'A' e o resultado é `true`.</span><span class="sxs-lookup"><span data-stu-id="5edf7-108">The second operation asks if all the elements are the character 'A', and the result is `true`.</span></span>  
  
 ![Operações de quantificador LINQ](./media/quantifier-operations/linq-quantifier-operations.png)  
  
 <span data-ttu-id="5edf7-110">Os métodos de operador de consulta padrão que realizam operações de quantificador estão listados na seção a seguir.</span><span class="sxs-lookup"><span data-stu-id="5edf7-110">The standard query operator methods that perform quantifier operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5edf7-111">Métodos</span><span class="sxs-lookup"><span data-stu-id="5edf7-111">Methods</span></span>  
  
|<span data-ttu-id="5edf7-112">Nome do método</span><span class="sxs-lookup"><span data-stu-id="5edf7-112">Method Name</span></span>|<span data-ttu-id="5edf7-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="5edf7-113">Description</span></span>|<span data-ttu-id="5edf7-114">Sintaxe de expressão de consulta C#</span><span class="sxs-lookup"><span data-stu-id="5edf7-114">C# Query Expression Syntax</span></span>|<span data-ttu-id="5edf7-115">Mais informações</span><span class="sxs-lookup"><span data-stu-id="5edf7-115">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="5edf7-116">Tudo</span><span class="sxs-lookup"><span data-stu-id="5edf7-116">All</span></span>|<span data-ttu-id="5edf7-117">Determina se todos os elementos em uma sequência satisfazem uma condição.</span><span class="sxs-lookup"><span data-stu-id="5edf7-117">Determines whether all the elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="5edf7-118">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="5edf7-118">Not applicable.</span></span>|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="5edf7-119">Qualquer</span><span class="sxs-lookup"><span data-stu-id="5edf7-119">Any</span></span>|<span data-ttu-id="5edf7-120">Determina se todos os elementos em uma sequência satisfazem uma condição.</span><span class="sxs-lookup"><span data-stu-id="5edf7-120">Determines whether any elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="5edf7-121">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="5edf7-121">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="5edf7-122">Contém</span><span class="sxs-lookup"><span data-stu-id="5edf7-122">Contains</span></span>|<span data-ttu-id="5edf7-123">Determina se uma sequência contém um elemento especificado.</span><span class="sxs-lookup"><span data-stu-id="5edf7-123">Determines whether a sequence contains a specified element.</span></span>|<span data-ttu-id="5edf7-124">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="5edf7-124">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  

## <a name="query-expression-syntax-examples"></a><span data-ttu-id="5edf7-125">Exemplos de sintaxe de expressão de consulta</span><span class="sxs-lookup"><span data-stu-id="5edf7-125">Query Expression Syntax Examples</span></span>  
  
### <a name="all"></a><span data-ttu-id="5edf7-126">Tudo</span><span class="sxs-lookup"><span data-stu-id="5edf7-126">All</span></span>  

<span data-ttu-id="5edf7-127">O exemplo a seguir usa o `All` para verificar se todas as cadeias de caracteres são de um comprimento específico.</span><span class="sxs-lookup"><span data-stu-id="5edf7-127">The following example uses the `All` to check that all strings are of a specific length.</span></span>
  
[!code-csharp[All](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#All)]  
  
### <a name="any"></a><span data-ttu-id="5edf7-128">Qualquer</span><span class="sxs-lookup"><span data-stu-id="5edf7-128">Any</span></span>  

<span data-ttu-id="5edf7-129">O exemplo a seguir usa o `Any` para verificar se todas as cadeias de caracteres são iniciadas com ' o '.</span><span class="sxs-lookup"><span data-stu-id="5edf7-129">The following example uses the `Any` to check that any strings are start with 'o'.</span></span>  
  
[!code-csharp[Any](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#Any)]  
  
### <a name="contains"></a><span data-ttu-id="5edf7-130">Contém</span><span class="sxs-lookup"><span data-stu-id="5edf7-130">Contains</span></span>  

<span data-ttu-id="5edf7-131">O exemplo a seguir usa o `Contains` para verificar se uma matriz tem um elemento específico.</span><span class="sxs-lookup"><span data-stu-id="5edf7-131">The following example uses the `Contains` to check an array have a specific element.</span></span>  
  
[!code-csharp[Contains](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#Contains)]  
  
## <a name="see-also"></a><span data-ttu-id="5edf7-132">Veja também</span><span class="sxs-lookup"><span data-stu-id="5edf7-132">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="5edf7-133">Visão geral de operadores de consulta padrão (C#)</span><span class="sxs-lookup"><span data-stu-id="5edf7-133">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="5edf7-134">Especificar filtros predicados dinamicamente em runtime</span><span class="sxs-lookup"><span data-stu-id="5edf7-134">Dynamically specify predicate filters at runtime</span></span>](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
- [<span data-ttu-id="5edf7-135">Como consultar frases que contêm um conjunto especificado de palavras (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="5edf7-135">How to query for sentences that contain a specified set of words (LINQ) (C#)</span></span>](./how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)
