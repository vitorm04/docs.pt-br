---
title: Particionando dados (C#)
ms.date: 07/20/2015
ms.assetid: 2a5c507b-fe22-443c-a768-dec7f9ec568d
ms.openlocfilehash: b857c8c6e6b56a7263e6725a747e98ccfe4ff4fc
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58832457"
---
# <a name="partitioning-data-c"></a><span data-ttu-id="e0242-102">Particionando dados (C#)</span><span class="sxs-lookup"><span data-stu-id="e0242-102">Partitioning Data (C#)</span></span>
<span data-ttu-id="e0242-103">Particionamento em LINQ refere-se à operação de dividir uma sequência de entrada em duas seções sem reorganizar os elementos e, depois, retornar uma das seções.</span><span class="sxs-lookup"><span data-stu-id="e0242-103">Partitioning in LINQ refers to the operation of dividing an input sequence into two sections, without rearranging the elements, and then returning one of the sections.</span></span>  
  
 <span data-ttu-id="e0242-104">A ilustração a seguir mostra os resultados de três operações de particionamento diferentes em uma sequência de caracteres.</span><span class="sxs-lookup"><span data-stu-id="e0242-104">The following illustration shows the results of three different partitioning operations on a sequence of characters.</span></span> <span data-ttu-id="e0242-105">A primeira operação retorna os três primeiros elementos na sequência.</span><span class="sxs-lookup"><span data-stu-id="e0242-105">The first operation returns the first three elements in the sequence.</span></span> <span data-ttu-id="e0242-106">A segunda operação ignora os três primeiros elementos e retorna os elementos restantes.</span><span class="sxs-lookup"><span data-stu-id="e0242-106">The second operation skips the first three elements and returns the remaining elements.</span></span> <span data-ttu-id="e0242-107">A terceira operação ignora os dois primeiros elementos na sequência e retorna os três elementos seguintes.</span><span class="sxs-lookup"><span data-stu-id="e0242-107">The third operation skips the first two elements in the sequence and returns the next three elements.</span></span>  
  
 ![Ilustração que mostra as três operações de particionamento do LINQ.](./media/partitioning-data/linq-partitioning-operations.png)  
  
 <span data-ttu-id="e0242-109">Os métodos de operador de consulta padrão que particionam sequências estão listados na seção a seguir.</span><span class="sxs-lookup"><span data-stu-id="e0242-109">The standard query operator methods that partition sequences are listed in the following section.</span></span>  
  
## <a name="operators"></a><span data-ttu-id="e0242-110">Operadores</span><span class="sxs-lookup"><span data-stu-id="e0242-110">Operators</span></span>  
  
|<span data-ttu-id="e0242-111">Nome do operador</span><span class="sxs-lookup"><span data-stu-id="e0242-111">Operator Name</span></span>|<span data-ttu-id="e0242-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="e0242-112">Description</span></span>|<span data-ttu-id="e0242-113">Sintaxe de expressão de consulta C#</span><span class="sxs-lookup"><span data-stu-id="e0242-113">C# Query Expression Syntax</span></span>|<span data-ttu-id="e0242-114">Mais informações</span><span class="sxs-lookup"><span data-stu-id="e0242-114">More Information</span></span>|  
|-------------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="e0242-115">Skip</span><span class="sxs-lookup"><span data-stu-id="e0242-115">Skip</span></span>|<span data-ttu-id="e0242-116">Ignora elementos até uma posição especificada na sequência.</span><span class="sxs-lookup"><span data-stu-id="e0242-116">Skips elements up to a specified position in a sequence.</span></span>|<span data-ttu-id="e0242-117">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="e0242-117">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="e0242-118">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="e0242-118">SkipWhile</span></span>|<span data-ttu-id="e0242-119">Ignora elementos com base em uma função de predicado até que um elemento não satisfaça a condição.</span><span class="sxs-lookup"><span data-stu-id="e0242-119">Skips elements based on a predicate function until an element does not satisfy the condition.</span></span>|<span data-ttu-id="e0242-120">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="e0242-120">Not applicable.</span></span>|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="e0242-121">Take</span><span class="sxs-lookup"><span data-stu-id="e0242-121">Take</span></span>|<span data-ttu-id="e0242-122">Aceita elementos até uma posição especificada na sequência.</span><span class="sxs-lookup"><span data-stu-id="e0242-122">Takes elements up to a specified position in a sequence.</span></span>|<span data-ttu-id="e0242-123">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="e0242-123">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="e0242-124">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="e0242-124">TakeWhile</span></span>|<span data-ttu-id="e0242-125">Aceita elementos com base em uma função de predicado até que um elemento não satisfaça a condição.</span><span class="sxs-lookup"><span data-stu-id="e0242-125">Takes elements based on a predicate function until an element does not satisfy the condition.</span></span>|<span data-ttu-id="e0242-126">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="e0242-126">Not applicable.</span></span>|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a><span data-ttu-id="e0242-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e0242-127">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="e0242-128">Visão geral de operadores de consulta padrão (C#)</span><span class="sxs-lookup"><span data-stu-id="e0242-128">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
