---
title: Particionando dados (C#)
ms.date: 07/20/2015
ms.assetid: 2a5c507b-fe22-443c-a768-dec7f9ec568d
ms.openlocfilehash: d9330e9973b2f25903e1f81a7296362e2a7c756b
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591582"
---
# <a name="partitioning-data-c"></a><span data-ttu-id="7d1fb-102">Particionando dados (C#)</span><span class="sxs-lookup"><span data-stu-id="7d1fb-102">Partitioning Data (C#)</span></span>
<span data-ttu-id="7d1fb-103">Particionamento em LINQ refere-se à operação de dividir uma sequência de entrada em duas seções sem reorganizar os elementos e, depois, retornar uma das seções.</span><span class="sxs-lookup"><span data-stu-id="7d1fb-103">Partitioning in LINQ refers to the operation of dividing an input sequence into two sections, without rearranging the elements, and then returning one of the sections.</span></span>  
  
 <span data-ttu-id="7d1fb-104">A ilustração a seguir mostra os resultados de três operações de particionamento diferentes em uma sequência de caracteres.</span><span class="sxs-lookup"><span data-stu-id="7d1fb-104">The following illustration shows the results of three different partitioning operations on a sequence of characters.</span></span> <span data-ttu-id="7d1fb-105">A primeira operação retorna os três primeiros elementos na sequência.</span><span class="sxs-lookup"><span data-stu-id="7d1fb-105">The first operation returns the first three elements in the sequence.</span></span> <span data-ttu-id="7d1fb-106">A segunda operação ignora os três primeiros elementos e retorna os elementos restantes.</span><span class="sxs-lookup"><span data-stu-id="7d1fb-106">The second operation skips the first three elements and returns the remaining elements.</span></span> <span data-ttu-id="7d1fb-107">A terceira operação ignora os dois primeiros elementos na sequência e retorna os três elementos seguintes.</span><span class="sxs-lookup"><span data-stu-id="7d1fb-107">The third operation skips the first two elements in the sequence and returns the next three elements.</span></span>  
  
 ![Ilustração que mostra as três operações de particionamento do LINQ.](./media/partitioning-data/linq-partitioning-operations.png)  
  
 <span data-ttu-id="7d1fb-109">Os métodos de operador de consulta padrão que particionam sequências estão listados na seção a seguir.</span><span class="sxs-lookup"><span data-stu-id="7d1fb-109">The standard query operator methods that partition sequences are listed in the following section.</span></span>  
  
## <a name="operators"></a><span data-ttu-id="7d1fb-110">Operadores</span><span class="sxs-lookup"><span data-stu-id="7d1fb-110">Operators</span></span>  
  
|<span data-ttu-id="7d1fb-111">Nome do operador</span><span class="sxs-lookup"><span data-stu-id="7d1fb-111">Operator Name</span></span>|<span data-ttu-id="7d1fb-112">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="7d1fb-112">Description</span></span>|<span data-ttu-id="7d1fb-113">Sintaxe de expressão de consulta C#</span><span class="sxs-lookup"><span data-stu-id="7d1fb-113">C# Query Expression Syntax</span></span>|<span data-ttu-id="7d1fb-114">Mais informações</span><span class="sxs-lookup"><span data-stu-id="7d1fb-114">More Information</span></span>|  
|-------------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="7d1fb-115">Skip</span><span class="sxs-lookup"><span data-stu-id="7d1fb-115">Skip</span></span>|<span data-ttu-id="7d1fb-116">Ignora elementos até uma posição especificada na sequência.</span><span class="sxs-lookup"><span data-stu-id="7d1fb-116">Skips elements up to a specified position in a sequence.</span></span>|<span data-ttu-id="7d1fb-117">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="7d1fb-117">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="7d1fb-118">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="7d1fb-118">SkipWhile</span></span>|<span data-ttu-id="7d1fb-119">Ignora elementos com base em uma função de predicado até que um elemento não satisfaça a condição.</span><span class="sxs-lookup"><span data-stu-id="7d1fb-119">Skips elements based on a predicate function until an element does not satisfy the condition.</span></span>|<span data-ttu-id="7d1fb-120">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="7d1fb-120">Not applicable.</span></span>|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="7d1fb-121">Take</span><span class="sxs-lookup"><span data-stu-id="7d1fb-121">Take</span></span>|<span data-ttu-id="7d1fb-122">Aceita elementos até uma posição especificada na sequência.</span><span class="sxs-lookup"><span data-stu-id="7d1fb-122">Takes elements up to a specified position in a sequence.</span></span>|<span data-ttu-id="7d1fb-123">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="7d1fb-123">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="7d1fb-124">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="7d1fb-124">TakeWhile</span></span>|<span data-ttu-id="7d1fb-125">Aceita elementos com base em uma função de predicado até que um elemento não satisfaça a condição.</span><span class="sxs-lookup"><span data-stu-id="7d1fb-125">Takes elements based on a predicate function until an element does not satisfy the condition.</span></span>|<span data-ttu-id="7d1fb-126">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="7d1fb-126">Not applicable.</span></span>|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a><span data-ttu-id="7d1fb-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7d1fb-127">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="7d1fb-128">Visão geral de operadores de consulta padrão (C#)</span><span class="sxs-lookup"><span data-stu-id="7d1fb-128">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
