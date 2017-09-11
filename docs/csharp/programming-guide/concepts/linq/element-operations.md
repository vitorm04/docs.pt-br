---
title: "Operações de elemento (C#)"
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
ms.assetid: 283206c9-3246-4c48-b01a-d9de409a7231
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
ms.openlocfilehash: da747e884960c89fabc45d3761da92f913d66362
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="element-operations-c"></a><span data-ttu-id="9612e-102">Operações de elemento (C#)</span><span class="sxs-lookup"><span data-stu-id="9612e-102">Element Operations (C#)</span></span>
<span data-ttu-id="9612e-103">Operações de elemento retornam um único elemento específico de uma sequência.</span><span class="sxs-lookup"><span data-stu-id="9612e-103">Element operations return a single, specific element from a sequence.</span></span>  
  
 <span data-ttu-id="9612e-104">Os métodos de operador de consulta padrão que executam operações de elemento estão listados na seção a seguir.</span><span class="sxs-lookup"><span data-stu-id="9612e-104">The standard query operator methods that perform element operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9612e-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="9612e-105">Methods</span></span>  
  
|<span data-ttu-id="9612e-106">Nome do método</span><span class="sxs-lookup"><span data-stu-id="9612e-106">Method Name</span></span>|<span data-ttu-id="9612e-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="9612e-107">Description</span></span>|<span data-ttu-id="9612e-108">Sintaxe de expressão de consulta C#</span><span class="sxs-lookup"><span data-stu-id="9612e-108">C# Query Expression Syntax</span></span>|<span data-ttu-id="9612e-109">Mais informações</span><span class="sxs-lookup"><span data-stu-id="9612e-109">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="9612e-110">ElementAt</span><span class="sxs-lookup"><span data-stu-id="9612e-110">ElementAt</span></span>|<span data-ttu-id="9612e-111">Retorna o elemento em um índice especificado em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="9612e-111">Returns the element at a specified index in a collection.</span></span>|<span data-ttu-id="9612e-112">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="9612e-112">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ElementAt%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.ElementAt%2A?displayProperty=fullName>|  
|<span data-ttu-id="9612e-113">ElementAtOrDefault</span><span class="sxs-lookup"><span data-stu-id="9612e-113">ElementAtOrDefault</span></span>|<span data-ttu-id="9612e-114">Retorna o elemento em um índice especificado em uma coleção ou um valor padrão se o índice estiver fora do intervalo.</span><span class="sxs-lookup"><span data-stu-id="9612e-114">Returns the element at a specified index in a collection or a default value if the index is out of range.</span></span>|<span data-ttu-id="9612e-115">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="9612e-115">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ElementAtOrDefault%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.ElementAtOrDefault%2A?displayProperty=fullName>|  
|<span data-ttu-id="9612e-116">Primeiro</span><span class="sxs-lookup"><span data-stu-id="9612e-116">First</span></span>|<span data-ttu-id="9612e-117">Retorna o primeiro elemento de uma coleção ou o primeiro elemento que satisfaz uma condição.</span><span class="sxs-lookup"><span data-stu-id="9612e-117">Returns the first element of a collection, or the first element that satisfies a condition.</span></span>|<span data-ttu-id="9612e-118">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="9612e-118">Not applicable.</span></span>|<xref:System.Linq.Enumerable.First%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.First%2A?displayProperty=fullName>|  
|<span data-ttu-id="9612e-119">FirstOrDefault</span><span class="sxs-lookup"><span data-stu-id="9612e-119">FirstOrDefault</span></span>|<span data-ttu-id="9612e-120">Retorna o primeiro elemento de uma coleção ou o primeiro elemento que satisfaz uma condição.</span><span class="sxs-lookup"><span data-stu-id="9612e-120">Returns the first element of a collection, or the first element that satisfies a condition.</span></span> <span data-ttu-id="9612e-121">Retorna um valor padrão se esse elemento não existir.</span><span class="sxs-lookup"><span data-stu-id="9612e-121">Returns a default value if no such element exists.</span></span>|<span data-ttu-id="9612e-122">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="9612e-122">Not applicable.</span></span>|<xref:System.Linq.Enumerable.FirstOrDefault%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.FirstOrDefault%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.FirstOrDefault%60%601%28System.Linq.IQueryable%7B%60%600%7D%29?displayProperty=fullName>|  
|<span data-ttu-id="9612e-123">Último</span><span class="sxs-lookup"><span data-stu-id="9612e-123">Last</span></span>|<span data-ttu-id="9612e-124">Retorna o último elemento de uma coleção ou o último elemento que satisfaz uma condição.</span><span class="sxs-lookup"><span data-stu-id="9612e-124">Returns the last element of a collection, or the last element that satisfies a condition.</span></span>|<span data-ttu-id="9612e-125">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="9612e-125">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Last%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Last%2A?displayProperty=fullName>|  
|<span data-ttu-id="9612e-126">LastOrDefault</span><span class="sxs-lookup"><span data-stu-id="9612e-126">LastOrDefault</span></span>|<span data-ttu-id="9612e-127">Retorna o último elemento de uma coleção ou o último elemento que satisfaz uma condição.</span><span class="sxs-lookup"><span data-stu-id="9612e-127">Returns the last element of a collection, or the last element that satisfies a condition.</span></span> <span data-ttu-id="9612e-128">Retorna um valor padrão se esse elemento não existir.</span><span class="sxs-lookup"><span data-stu-id="9612e-128">Returns a default value if no such element exists.</span></span>|<span data-ttu-id="9612e-129">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="9612e-129">Not applicable.</span></span>|<xref:System.Linq.Enumerable.LastOrDefault%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.LastOrDefault%2A?displayProperty=fullName>|  
|<span data-ttu-id="9612e-130">Simples</span><span class="sxs-lookup"><span data-stu-id="9612e-130">Single</span></span>|<span data-ttu-id="9612e-131">Retorna o único elemento de uma coleção ou o único elemento que satisfaz uma condição.</span><span class="sxs-lookup"><span data-stu-id="9612e-131">Returns the only element of a collection, or the only element that satisfies a condition.</span></span>|<span data-ttu-id="9612e-132">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="9612e-132">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Single%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Single%2A?displayProperty=fullName>|  
|<span data-ttu-id="9612e-133">SingleOrDefault</span><span class="sxs-lookup"><span data-stu-id="9612e-133">SingleOrDefault</span></span>|<span data-ttu-id="9612e-134">Retorna o único elemento de uma coleção ou o único elemento que satisfaz uma condição.</span><span class="sxs-lookup"><span data-stu-id="9612e-134">Returns the only element of a collection, or the only element that satisfies a condition.</span></span> <span data-ttu-id="9612e-135">Retorna um valor padrão se esse elemento não existir ou se a coleção não contiver exatamente um elemento.</span><span class="sxs-lookup"><span data-stu-id="9612e-135">Returns a default value if no such element exists or the collection does not contain exactly one element.</span></span>|<span data-ttu-id="9612e-136">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="9612e-136">Not applicable.</span></span>|<xref:System.Linq.Enumerable.SingleOrDefault%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.SingleOrDefault%2A?displayProperty=fullName>|  
  
## <a name="see-also"></a><span data-ttu-id="9612e-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9612e-137">See Also</span></span>  
 <span data-ttu-id="9612e-138"><xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="9612e-138"><xref:System.Linq></span></span>   
 <span data-ttu-id="9612e-139">[Visão geral de operadores de consulta padrão (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) </span><span class="sxs-lookup"><span data-stu-id="9612e-139">[Standard Query Operators Overview (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) </span></span>  
 [<span data-ttu-id="9612e-140">Como consultar o maior arquivo ou arquivos em uma árvore de diretório (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="9612e-140">How to: Query for the Largest File or Files in a Directory Tree (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq.md)

