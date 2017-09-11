---
title: Particionando dados (C#)
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
ms.assetid: 2a5c507b-fe22-443c-a768-dec7f9ec568d
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
ms.openlocfilehash: 2f1690dac93d5e74f1305bd457f8bc749bec5449
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="partitioning-data-c"></a><span data-ttu-id="a347a-102">Particionando dados (C#)</span><span class="sxs-lookup"><span data-stu-id="a347a-102">Partitioning Data (C#)</span></span>
<span data-ttu-id="a347a-103">Particionamento em LINQ refere-se à operação de dividir uma sequência de entrada em duas seções sem reorganizar os elementos e, depois, retornar uma das seções.</span><span class="sxs-lookup"><span data-stu-id="a347a-103">Partitioning in LINQ refers to the operation of dividing an input sequence into two sections, without rearranging the elements, and then returning one of the sections.</span></span>  
  
 <span data-ttu-id="a347a-104">A ilustração a seguir mostra os resultados de três operações de particionamento diferentes em uma sequência de caracteres.</span><span class="sxs-lookup"><span data-stu-id="a347a-104">The following illustration shows the results of three different partitioning operations on a sequence of characters.</span></span> <span data-ttu-id="a347a-105">A primeira operação retorna os três primeiros elementos na sequência.</span><span class="sxs-lookup"><span data-stu-id="a347a-105">The first operation returns the first three elements in the sequence.</span></span> <span data-ttu-id="a347a-106">A segunda operação ignora os três primeiros elementos e retorna os elementos restantes.</span><span class="sxs-lookup"><span data-stu-id="a347a-106">The second operation skips the first three elements and returns the remaining elements.</span></span> <span data-ttu-id="a347a-107">A terceira operação ignora os dois primeiros elementos na sequência e retorna os três elementos seguintes.</span><span class="sxs-lookup"><span data-stu-id="a347a-107">The third operation skips the first two elements in the sequence and returns the next three elements.</span></span>  
  
 <span data-ttu-id="a347a-108">![Operações de particionamento de LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_partition.png "LINQ_Partition")</span><span class="sxs-lookup"><span data-stu-id="a347a-108">![LINQ Partitioning Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_partition.png "LINQ_Partition")</span></span>  
  
 <span data-ttu-id="a347a-109">Os métodos de operador de consulta padrão que particionam sequências estão listados na seção a seguir.</span><span class="sxs-lookup"><span data-stu-id="a347a-109">The standard query operator methods that partition sequences are listed in the following section.</span></span>  
  
## <a name="operators"></a><span data-ttu-id="a347a-110">Operadores</span><span class="sxs-lookup"><span data-stu-id="a347a-110">Operators</span></span>  
  
|<span data-ttu-id="a347a-111">Nome do operador</span><span class="sxs-lookup"><span data-stu-id="a347a-111">Operator Name</span></span>|<span data-ttu-id="a347a-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="a347a-112">Description</span></span>|<span data-ttu-id="a347a-113">Sintaxe de expressão de consulta C#</span><span class="sxs-lookup"><span data-stu-id="a347a-113">C# Query Expression Syntax</span></span>|<span data-ttu-id="a347a-114">Mais informações</span><span class="sxs-lookup"><span data-stu-id="a347a-114">More Information</span></span>|  
|-------------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="a347a-115">Skip</span><span class="sxs-lookup"><span data-stu-id="a347a-115">Skip</span></span>|<span data-ttu-id="a347a-116">Ignora elementos até uma posição especificada na sequência.</span><span class="sxs-lookup"><span data-stu-id="a347a-116">Skips elements up to a specified position in a sequence.</span></span>|<span data-ttu-id="a347a-117">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="a347a-117">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=fullName>|  
|<span data-ttu-id="a347a-118">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="a347a-118">SkipWhile</span></span>|<span data-ttu-id="a347a-119">Ignora elementos com base em uma função de predicado até que um elemento não satisfaça a condição.</span><span class="sxs-lookup"><span data-stu-id="a347a-119">Skips elements based on a predicate function until an element does not satisfy the condition.</span></span>|<span data-ttu-id="a347a-120">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="a347a-120">Not applicable.</span></span>|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=fullName>|  
|<span data-ttu-id="a347a-121">Take</span><span class="sxs-lookup"><span data-stu-id="a347a-121">Take</span></span>|<span data-ttu-id="a347a-122">Aceita elementos até uma posição especificada na sequência.</span><span class="sxs-lookup"><span data-stu-id="a347a-122">Takes elements up to a specified position in a sequence.</span></span>|<span data-ttu-id="a347a-123">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="a347a-123">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Take%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=fullName>|  
|<span data-ttu-id="a347a-124">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="a347a-124">TakeWhile</span></span>|<span data-ttu-id="a347a-125">Aceita elementos com base em uma função de predicado até que um elemento não satisfaça a condição.</span><span class="sxs-lookup"><span data-stu-id="a347a-125">Takes elements based on a predicate function until an element does not satisfy the condition.</span></span>|<span data-ttu-id="a347a-126">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="a347a-126">Not applicable.</span></span>|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=fullName>|  
  
## <a name="see-also"></a><span data-ttu-id="a347a-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a347a-127">See Also</span></span>  
 <span data-ttu-id="a347a-128"><xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="a347a-128"><xref:System.Linq></span></span>   
 [<span data-ttu-id="a347a-129">Visão geral de operadores de consulta padrão (C#)</span><span class="sxs-lookup"><span data-stu-id="a347a-129">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)

