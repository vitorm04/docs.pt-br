---
title: Particionando dados (C#)
description: Saiba como particionar dados no LINQ. Exiba uma ilustração que mostra os resultados das operações de particionamento.
ms.date: 07/20/2015
ms.assetid: 2a5c507b-fe22-443c-a768-dec7f9ec568d
ms.openlocfilehash: 3c85eaec2dc01b683234a27714750354982be440
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302601"
---
# <a name="partitioning-data-c"></a><span data-ttu-id="8bbfd-104">Particionando dados (C#)</span><span class="sxs-lookup"><span data-stu-id="8bbfd-104">Partitioning Data (C#)</span></span>
<span data-ttu-id="8bbfd-105">Particionamento em LINQ refere-se à operação de dividir uma sequência de entrada em duas seções sem reorganizar os elementos e, depois, retornar uma das seções.</span><span class="sxs-lookup"><span data-stu-id="8bbfd-105">Partitioning in LINQ refers to the operation of dividing an input sequence into two sections, without rearranging the elements, and then returning one of the sections.</span></span>  
  
 <span data-ttu-id="8bbfd-106">A ilustração a seguir mostra os resultados de três operações de particionamento diferentes em uma sequência de caracteres.</span><span class="sxs-lookup"><span data-stu-id="8bbfd-106">The following illustration shows the results of three different partitioning operations on a sequence of characters.</span></span> <span data-ttu-id="8bbfd-107">A primeira operação retorna os três primeiros elementos na sequência.</span><span class="sxs-lookup"><span data-stu-id="8bbfd-107">The first operation returns the first three elements in the sequence.</span></span> <span data-ttu-id="8bbfd-108">A segunda operação ignora os três primeiros elementos e retorna os elementos restantes.</span><span class="sxs-lookup"><span data-stu-id="8bbfd-108">The second operation skips the first three elements and returns the remaining elements.</span></span> <span data-ttu-id="8bbfd-109">A terceira operação ignora os dois primeiros elementos na sequência e retorna os três elementos seguintes.</span><span class="sxs-lookup"><span data-stu-id="8bbfd-109">The third operation skips the first two elements in the sequence and returns the next three elements.</span></span>  
  
 ![Ilustração que mostra as três operações de particionamento do LINQ.](./media/partitioning-data/linq-partitioning-operations.png)  
  
 <span data-ttu-id="8bbfd-111">Os métodos de operador de consulta padrão que particionam sequências estão listados na seção a seguir.</span><span class="sxs-lookup"><span data-stu-id="8bbfd-111">The standard query operator methods that partition sequences are listed in the following section.</span></span>  
  
## <a name="operators"></a><span data-ttu-id="8bbfd-112">Operadores</span><span class="sxs-lookup"><span data-stu-id="8bbfd-112">Operators</span></span>  
  
|<span data-ttu-id="8bbfd-113">Nome do operador</span><span class="sxs-lookup"><span data-stu-id="8bbfd-113">Operator Name</span></span>|<span data-ttu-id="8bbfd-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="8bbfd-114">Description</span></span>|<span data-ttu-id="8bbfd-115">Sintaxe de expressão de consulta C#</span><span class="sxs-lookup"><span data-stu-id="8bbfd-115">C# Query Expression Syntax</span></span>|<span data-ttu-id="8bbfd-116">Mais informações</span><span class="sxs-lookup"><span data-stu-id="8bbfd-116">More Information</span></span>|  
|-------------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="8bbfd-117">Ignorar</span><span class="sxs-lookup"><span data-stu-id="8bbfd-117">Skip</span></span>|<span data-ttu-id="8bbfd-118">Ignora elementos até uma posição especificada na sequência.</span><span class="sxs-lookup"><span data-stu-id="8bbfd-118">Skips elements up to a specified position in a sequence.</span></span>|<span data-ttu-id="8bbfd-119">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="8bbfd-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="8bbfd-120">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="8bbfd-120">SkipWhile</span></span>|<span data-ttu-id="8bbfd-121">Ignora elementos com base em uma função de predicado até que um elemento não satisfaça a condição.</span><span class="sxs-lookup"><span data-stu-id="8bbfd-121">Skips elements based on a predicate function until an element does not satisfy the condition.</span></span>|<span data-ttu-id="8bbfd-122">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="8bbfd-122">Not applicable.</span></span>|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="8bbfd-123">Take</span><span class="sxs-lookup"><span data-stu-id="8bbfd-123">Take</span></span>|<span data-ttu-id="8bbfd-124">Aceita elementos até uma posição especificada na sequência.</span><span class="sxs-lookup"><span data-stu-id="8bbfd-124">Takes elements up to a specified position in a sequence.</span></span>|<span data-ttu-id="8bbfd-125">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="8bbfd-125">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="8bbfd-126">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="8bbfd-126">TakeWhile</span></span>|<span data-ttu-id="8bbfd-127">Aceita elementos com base em uma função de predicado até que um elemento não satisfaça a condição.</span><span class="sxs-lookup"><span data-stu-id="8bbfd-127">Takes elements based on a predicate function until an element does not satisfy the condition.</span></span>|<span data-ttu-id="8bbfd-128">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="8bbfd-128">Not applicable.</span></span>|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a><span data-ttu-id="8bbfd-129">Veja também</span><span class="sxs-lookup"><span data-stu-id="8bbfd-129">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="8bbfd-130">Visão geral de operadores de consulta padrão (C#)</span><span class="sxs-lookup"><span data-stu-id="8bbfd-130">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
