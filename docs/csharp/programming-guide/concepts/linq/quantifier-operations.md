---
title: Operações de quantificador (C#)
description: Saiba mais sobre as operações do quantificador. Essas operações retornam um valor booliano que indica se alguns ou todos os elementos em uma sequência atendem a uma condição.
ms.date: 07/20/2015
ms.assetid: 84ac2ac2-7a63-4581-bc4c-14e34be1493b
ms.openlocfilehash: ce06f887d3ad7b10cbdedf9e33072df2c0819ef1
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87299143"
---
# <a name="quantifier-operations-c"></a><span data-ttu-id="efa92-104">Operações de quantificador (C#)</span><span class="sxs-lookup"><span data-stu-id="efa92-104">Quantifier Operations (C#)</span></span>
<span data-ttu-id="efa92-105">As operações de quantificador retornam um valor <xref:System.Boolean> que indica se alguns ou todos os elementos em uma sequência satisfazem uma condição.</span><span class="sxs-lookup"><span data-stu-id="efa92-105">Quantifier operations return a <xref:System.Boolean> value that indicates whether some or all of the elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="efa92-106">A ilustração a seguir mostra duas operações de quantificador diferentes em duas sequências de origem diferentes.</span><span class="sxs-lookup"><span data-stu-id="efa92-106">The following illustration depicts two different quantifier operations on two different source sequences.</span></span> <span data-ttu-id="efa92-107">A primeira operação pergunta se um ou mais dos elementos são o caractere 'A' e o resultado é `true`.</span><span class="sxs-lookup"><span data-stu-id="efa92-107">The first operation asks if one or more of the elements are the character 'A', and the result is `true`.</span></span> <span data-ttu-id="efa92-108">A segunda operação pergunta se todos os elementos são o caractere 'A' e o resultado é `true`.</span><span class="sxs-lookup"><span data-stu-id="efa92-108">The second operation asks if all the elements are the character 'A', and the result is `true`.</span></span>  
  
 ![Operações de quantificador LINQ](./media/quantifier-operations/linq-quantifier-operations.png)  
  
 <span data-ttu-id="efa92-110">Os métodos de operador de consulta padrão que realizam operações de quantificador estão listados na seção a seguir.</span><span class="sxs-lookup"><span data-stu-id="efa92-110">The standard query operator methods that perform quantifier operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="efa92-111">Métodos</span><span class="sxs-lookup"><span data-stu-id="efa92-111">Methods</span></span>  
  
|<span data-ttu-id="efa92-112">Nome do método</span><span class="sxs-lookup"><span data-stu-id="efa92-112">Method Name</span></span>|<span data-ttu-id="efa92-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="efa92-113">Description</span></span>|<span data-ttu-id="efa92-114">Sintaxe de expressão de consulta C#</span><span class="sxs-lookup"><span data-stu-id="efa92-114">C# Query Expression Syntax</span></span>|<span data-ttu-id="efa92-115">Mais informações</span><span class="sxs-lookup"><span data-stu-id="efa92-115">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="efa92-116">Todos</span><span class="sxs-lookup"><span data-stu-id="efa92-116">All</span></span>|<span data-ttu-id="efa92-117">Determina se todos os elementos em uma sequência satisfazem uma condição.</span><span class="sxs-lookup"><span data-stu-id="efa92-117">Determines whether all the elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="efa92-118">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="efa92-118">Not applicable.</span></span>|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="efa92-119">Qualquer</span><span class="sxs-lookup"><span data-stu-id="efa92-119">Any</span></span>|<span data-ttu-id="efa92-120">Determina se todos os elementos em uma sequência satisfazem uma condição.</span><span class="sxs-lookup"><span data-stu-id="efa92-120">Determines whether any elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="efa92-121">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="efa92-121">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="efa92-122">Contém</span><span class="sxs-lookup"><span data-stu-id="efa92-122">Contains</span></span>|<span data-ttu-id="efa92-123">Determina se uma sequência contém um elemento especificado.</span><span class="sxs-lookup"><span data-stu-id="efa92-123">Determines whether a sequence contains a specified element.</span></span>|<span data-ttu-id="efa92-124">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="efa92-124">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  

## <a name="query-expression-syntax-examples"></a><span data-ttu-id="efa92-125">Exemplos de sintaxe de expressão de consulta</span><span class="sxs-lookup"><span data-stu-id="efa92-125">Query Expression Syntax Examples</span></span>  
  
### <a name="all"></a><span data-ttu-id="efa92-126">Todos</span><span class="sxs-lookup"><span data-stu-id="efa92-126">All</span></span>  
<span data-ttu-id="efa92-127">O exemplo a seguir usa o `All` para verificar se todas as cadeias de caracteres são de um comprimento específico.</span><span class="sxs-lookup"><span data-stu-id="efa92-127">The following example uses the `All` to check that all strings are of a specific length.</span></span>
  
[!code-csharp[All](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#All)]  
  
### <a name="any"></a><span data-ttu-id="efa92-128">Qualquer</span><span class="sxs-lookup"><span data-stu-id="efa92-128">Any</span></span>  
<span data-ttu-id="efa92-129">O exemplo a seguir usa o `Any` para verificar se todas as cadeias de caracteres são iniciadas com ' o '.</span><span class="sxs-lookup"><span data-stu-id="efa92-129">The following example uses the `Any` to check that any strings are start with 'o'.</span></span>  
  
[!code-csharp[Any](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#Any)]  
  
### <a name="contains"></a><span data-ttu-id="efa92-130">Contém</span><span class="sxs-lookup"><span data-stu-id="efa92-130">Contains</span></span>  
<span data-ttu-id="efa92-131">O exemplo a seguir usa o `Contains` para verificar se uma matriz tem um elemento específico.</span><span class="sxs-lookup"><span data-stu-id="efa92-131">The following example uses the `Contains` to check an array have a specific element.</span></span>  
  
[!code-csharp[Contains](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#Contains)]  
  
## <a name="see-also"></a><span data-ttu-id="efa92-132">Veja também</span><span class="sxs-lookup"><span data-stu-id="efa92-132">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="efa92-133">Visão geral de operadores de consulta padrão (C#)</span><span class="sxs-lookup"><span data-stu-id="efa92-133">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="efa92-134">Especificar filtros predicados dinamicamente em runtime</span><span class="sxs-lookup"><span data-stu-id="efa92-134">Dynamically specify predicate filters at runtime</span></span>](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
- [<span data-ttu-id="efa92-135">Como consultar frases que contêm um conjunto especificado de palavras (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="efa92-135">How to query for sentences that contain a specified set of words (LINQ) (C#)</span></span>](./how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)
