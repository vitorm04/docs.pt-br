---
title: Particionando dados (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 2a5c507b-fe22-443c-a768-dec7f9ec568d
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 32b95887e05767513dd818743dd1726149503b0f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="partitioning-data-c"></a><span data-ttu-id="6a2a6-102">Particionando dados (C#)</span><span class="sxs-lookup"><span data-stu-id="6a2a6-102">Partitioning Data (C#)</span></span>
<span data-ttu-id="6a2a6-103">Particionamento em LINQ refere-se à operação de dividir uma sequência de entrada em duas seções sem reorganizar os elementos e, depois, retornar uma das seções.</span><span class="sxs-lookup"><span data-stu-id="6a2a6-103">Partitioning in LINQ refers to the operation of dividing an input sequence into two sections, without rearranging the elements, and then returning one of the sections.</span></span>  
  
 <span data-ttu-id="6a2a6-104">A ilustração a seguir mostra os resultados de três operações de particionamento diferentes em uma sequência de caracteres.</span><span class="sxs-lookup"><span data-stu-id="6a2a6-104">The following illustration shows the results of three different partitioning operations on a sequence of characters.</span></span> <span data-ttu-id="6a2a6-105">A primeira operação retorna os três primeiros elementos na sequência.</span><span class="sxs-lookup"><span data-stu-id="6a2a6-105">The first operation returns the first three elements in the sequence.</span></span> <span data-ttu-id="6a2a6-106">A segunda operação ignora os três primeiros elementos e retorna os elementos restantes.</span><span class="sxs-lookup"><span data-stu-id="6a2a6-106">The second operation skips the first three elements and returns the remaining elements.</span></span> <span data-ttu-id="6a2a6-107">A terceira operação ignora os dois primeiros elementos na sequência e retorna os três elementos seguintes.</span><span class="sxs-lookup"><span data-stu-id="6a2a6-107">The third operation skips the first two elements in the sequence and returns the next three elements.</span></span>  
  
 <span data-ttu-id="6a2a6-108">![Operações de particionamento de LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_partition.png "LINQ_Partition")</span><span class="sxs-lookup"><span data-stu-id="6a2a6-108">![LINQ Partitioning Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_partition.png "LINQ_Partition")</span></span>  
  
 <span data-ttu-id="6a2a6-109">Os métodos de operador de consulta padrão que particionam sequências estão listados na seção a seguir.</span><span class="sxs-lookup"><span data-stu-id="6a2a6-109">The standard query operator methods that partition sequences are listed in the following section.</span></span>  
  
## <a name="operators"></a><span data-ttu-id="6a2a6-110">Operadores</span><span class="sxs-lookup"><span data-stu-id="6a2a6-110">Operators</span></span>  
  
|<span data-ttu-id="6a2a6-111">Nome do operador</span><span class="sxs-lookup"><span data-stu-id="6a2a6-111">Operator Name</span></span>|<span data-ttu-id="6a2a6-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="6a2a6-112">Description</span></span>|<span data-ttu-id="6a2a6-113">Sintaxe de expressão de consulta C#</span><span class="sxs-lookup"><span data-stu-id="6a2a6-113">C# Query Expression Syntax</span></span>|<span data-ttu-id="6a2a6-114">Mais informações</span><span class="sxs-lookup"><span data-stu-id="6a2a6-114">More Information</span></span>|  
|-------------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="6a2a6-115">Skip</span><span class="sxs-lookup"><span data-stu-id="6a2a6-115">Skip</span></span>|<span data-ttu-id="6a2a6-116">Ignora elementos até uma posição especificada na sequência.</span><span class="sxs-lookup"><span data-stu-id="6a2a6-116">Skips elements up to a specified position in a sequence.</span></span>|<span data-ttu-id="6a2a6-117">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="6a2a6-117">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="6a2a6-118">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="6a2a6-118">SkipWhile</span></span>|<span data-ttu-id="6a2a6-119">Ignora elementos com base em uma função de predicado até que um elemento não satisfaça a condição.</span><span class="sxs-lookup"><span data-stu-id="6a2a6-119">Skips elements based on a predicate function until an element does not satisfy the condition.</span></span>|<span data-ttu-id="6a2a6-120">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="6a2a6-120">Not applicable.</span></span>|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="6a2a6-121">Take</span><span class="sxs-lookup"><span data-stu-id="6a2a6-121">Take</span></span>|<span data-ttu-id="6a2a6-122">Aceita elementos até uma posição especificada na sequência.</span><span class="sxs-lookup"><span data-stu-id="6a2a6-122">Takes elements up to a specified position in a sequence.</span></span>|<span data-ttu-id="6a2a6-123">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="6a2a6-123">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="6a2a6-124">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="6a2a6-124">TakeWhile</span></span>|<span data-ttu-id="6a2a6-125">Aceita elementos com base em uma função de predicado até que um elemento não satisfaça a condição.</span><span class="sxs-lookup"><span data-stu-id="6a2a6-125">Takes elements based on a predicate function until an element does not satisfy the condition.</span></span>|<span data-ttu-id="6a2a6-126">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="6a2a6-126">Not applicable.</span></span>|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a><span data-ttu-id="6a2a6-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6a2a6-127">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="6a2a6-128">Visão geral de operadores de consulta padrão (C#)</span><span class="sxs-lookup"><span data-stu-id="6a2a6-128">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
