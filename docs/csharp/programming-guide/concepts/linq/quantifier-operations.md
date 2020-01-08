---
title: Operações de quantificador (C#)
ms.date: 07/20/2015
ms.assetid: 84ac2ac2-7a63-4581-bc4c-14e34be1493b
ms.openlocfilehash: 5c931e0971a2ae7970415905be8772a64a82ee39
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635477"
---
# <a name="quantifier-operations-c"></a><span data-ttu-id="95c37-102">Operações de quantificador (C#)</span><span class="sxs-lookup"><span data-stu-id="95c37-102">Quantifier Operations (C#)</span></span>
<span data-ttu-id="95c37-103">As operações de quantificador retornam um valor <xref:System.Boolean> que indica se alguns ou todos os elementos em uma sequência satisfazem uma condição.</span><span class="sxs-lookup"><span data-stu-id="95c37-103">Quantifier operations return a <xref:System.Boolean> value that indicates whether some or all of the elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="95c37-104">A ilustração a seguir mostra duas operações de quantificador diferentes em duas sequências de origem diferentes.</span><span class="sxs-lookup"><span data-stu-id="95c37-104">The following illustration depicts two different quantifier operations on two different source sequences.</span></span> <span data-ttu-id="95c37-105">A primeira operação pergunta se um ou mais dos elementos são o caractere 'A' e o resultado é `true`.</span><span class="sxs-lookup"><span data-stu-id="95c37-105">The first operation asks if one or more of the elements are the character 'A', and the result is `true`.</span></span> <span data-ttu-id="95c37-106">A segunda operação pergunta se todos os elementos são o caractere 'A' e o resultado é `true`.</span><span class="sxs-lookup"><span data-stu-id="95c37-106">The second operation asks if all the elements are the character 'A', and the result is `true`.</span></span>  
  
 ![Operações de quantificador LINQ](./media/quantifier-operations/linq-quantifier-operations.png)  
  
 <span data-ttu-id="95c37-108">Os métodos de operador de consulta padrão que realizam operações de quantificador estão listados na seção a seguir.</span><span class="sxs-lookup"><span data-stu-id="95c37-108">The standard query operator methods that perform quantifier operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="95c37-109">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="95c37-109">Methods</span></span>  
  
|<span data-ttu-id="95c37-110">Nome do método</span><span class="sxs-lookup"><span data-stu-id="95c37-110">Method Name</span></span>|<span data-ttu-id="95c37-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="95c37-111">Description</span></span>|<span data-ttu-id="95c37-112">Sintaxe de expressão de consulta C#</span><span class="sxs-lookup"><span data-stu-id="95c37-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="95c37-113">Mais Informações</span><span class="sxs-lookup"><span data-stu-id="95c37-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="95c37-114">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="95c37-114">All</span></span>|<span data-ttu-id="95c37-115">Determina se todos os elementos em uma sequência satisfazem uma condição.</span><span class="sxs-lookup"><span data-stu-id="95c37-115">Determines whether all the elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="95c37-116">{1&gt;Não aplicável.&lt;1}</span><span class="sxs-lookup"><span data-stu-id="95c37-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="95c37-117">Qualquer</span><span class="sxs-lookup"><span data-stu-id="95c37-117">Any</span></span>|<span data-ttu-id="95c37-118">Determina se todos os elementos em uma sequência satisfazem uma condição.</span><span class="sxs-lookup"><span data-stu-id="95c37-118">Determines whether any elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="95c37-119">{1&gt;Não aplicável.&lt;1}</span><span class="sxs-lookup"><span data-stu-id="95c37-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="95c37-120">Contém</span><span class="sxs-lookup"><span data-stu-id="95c37-120">Contains</span></span>|<span data-ttu-id="95c37-121">Determina se uma sequência contém um elemento especificado.</span><span class="sxs-lookup"><span data-stu-id="95c37-121">Determines whether a sequence contains a specified element.</span></span>|<span data-ttu-id="95c37-122">{1&gt;Não aplicável.&lt;1}</span><span class="sxs-lookup"><span data-stu-id="95c37-122">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  

## <a name="query-expression-syntax-examples"></a><span data-ttu-id="95c37-123">Exemplos de sintaxe de expressão de consulta</span><span class="sxs-lookup"><span data-stu-id="95c37-123">Query Expression Syntax Examples</span></span>  
  
### <a name="all"></a><span data-ttu-id="95c37-124">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="95c37-124">All</span></span>  
<span data-ttu-id="95c37-125">O exemplo a seguir usa o `All` para verificar se todas as cadeias de caracteres são de um comprimento específico.</span><span class="sxs-lookup"><span data-stu-id="95c37-125">The following example uses the `All` to check that all strings are of a specific length.</span></span>
  
[!code-csharp[All](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#All)]  
  
### <a name="any"></a><span data-ttu-id="95c37-126">Qualquer</span><span class="sxs-lookup"><span data-stu-id="95c37-126">Any</span></span>  
<span data-ttu-id="95c37-127">O exemplo a seguir usa o `Any` para verificar se todas as cadeias de caracteres são iniciadas com ' o '.</span><span class="sxs-lookup"><span data-stu-id="95c37-127">The following example uses the `Any` to check that any strings are start with 'o'.</span></span>  
  
[!code-csharp[Any](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#Any)]  
  
### <a name="contains"></a><span data-ttu-id="95c37-128">Contém</span><span class="sxs-lookup"><span data-stu-id="95c37-128">Contains</span></span>  
<span data-ttu-id="95c37-129">O exemplo a seguir usa o `Contains` para verificar se uma matriz tem um elemento específico.</span><span class="sxs-lookup"><span data-stu-id="95c37-129">The following example uses the `Contains` to check an array have a specific element.</span></span>  
  
[!code-csharp[Contains](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#Contains)]  
  
## <a name="see-also"></a><span data-ttu-id="95c37-130">Veja também</span><span class="sxs-lookup"><span data-stu-id="95c37-130">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="95c37-131">Visão geral de operadores de consulta padrão (C#)</span><span class="sxs-lookup"><span data-stu-id="95c37-131">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="95c37-132">Especificar filtros predicados dinamicamente em runtime</span><span class="sxs-lookup"><span data-stu-id="95c37-132">Dynamically specify predicate filters at runtime</span></span>](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
- [<span data-ttu-id="95c37-133">Como consultar frases que contenham um conjunto especificado de palavras (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="95c37-133">How to query for sentences that contain a specified set of words (LINQ) (C#)</span></span>](./how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)
