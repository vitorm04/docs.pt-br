---
title: Consultas de agregação
ms.date: 03/30/2017
ms.assetid: 13ec5580-05ce-4a1f-9d3d-8660be7891a2
ms.openlocfilehash: 1c8f6191cfb832a71bd32c60db492eafb8ca22ca
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43464147"
---
# <a name="aggregate-queries"></a><span data-ttu-id="1c56b-102">Consultas de agregação</span><span class="sxs-lookup"><span data-stu-id="1c56b-102">Aggregate Queries</span></span>
<span data-ttu-id="1c56b-103">O [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dá suporte aos operadores de agregação `Average`, `Count`, `Max`, `Min` e `Sum`.</span><span class="sxs-lookup"><span data-stu-id="1c56b-103">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] supports the `Average`, `Count`, `Max`, `Min`, and `Sum` aggregate operators.</span></span> <span data-ttu-id="1c56b-104">Observe as seguintes características dos operadores de agregação no [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="1c56b-104">Note the following characteristics of aggregate operators in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]:</span></span>  
  
-   <span data-ttu-id="1c56b-105">As consultas de agregação são executadas imediatamente.</span><span class="sxs-lookup"><span data-stu-id="1c56b-105">Aggregate queries are executed immediately.</span></span>  
  
     <span data-ttu-id="1c56b-106">Para obter mais informações, consulte [Introdução a Consultas de LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="1c56b-106">For more information, see [Introduction to LINQ Queries (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
-   <span data-ttu-id="1c56b-107">As consultas de agregação geralmente retornam um número em vez de uma coleção.</span><span class="sxs-lookup"><span data-stu-id="1c56b-107">Aggregate queries typically return a number instead of a collection.</span></span>  
  
     <span data-ttu-id="1c56b-108">Para obter mais informações, consulte [operações de agregação](https://msdn.microsoft.com/library/36d97c83-5de5-457d-971d-10a69365e7c4).</span><span class="sxs-lookup"><span data-stu-id="1c56b-108">For more information, see [Aggregation Operations](https://msdn.microsoft.com/library/36d97c83-5de5-457d-971d-10a69365e7c4).</span></span>  
  
-   <span data-ttu-id="1c56b-109">Você não pode chamar agregações em tipos anônimos.</span><span class="sxs-lookup"><span data-stu-id="1c56b-109">You cannot call aggregates against anonymous types.</span></span>  
  
 <span data-ttu-id="1c56b-110">Os exemplos nos seguintes tópicos derivam do banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="1c56b-110">The examples in the following topics derive from the Northwind sample database.</span></span> <span data-ttu-id="1c56b-111">Para obter mais informações, consulte [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="1c56b-111">For more information, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1c56b-112">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="1c56b-112">In This Section</span></span>  
 [<span data-ttu-id="1c56b-113">Retornar o valor médio de uma sequência numérica</span><span class="sxs-lookup"><span data-stu-id="1c56b-113">Return the Average Value From a Numeric Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-the-average-value-from-a-numeric-sequence.md)  
 <span data-ttu-id="1c56b-114">Demonstra como usar o operador <xref:System.Linq.Enumerable.Average%2A>.</span><span class="sxs-lookup"><span data-stu-id="1c56b-114">Demonstrates how to use the <xref:System.Linq.Enumerable.Average%2A> operator.</span></span>  
  
 [<span data-ttu-id="1c56b-115">Contar o número de elementos em uma sequência</span><span class="sxs-lookup"><span data-stu-id="1c56b-115">Count the Number of Elements in a Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/count-the-number-of-elements-in-a-sequence.md)  
 <span data-ttu-id="1c56b-116">Demonstra como usar o operador <xref:System.Linq.Enumerable.Count%2A>.</span><span class="sxs-lookup"><span data-stu-id="1c56b-116">Demonstrates how to use the <xref:System.Linq.Enumerable.Count%2A> operator.</span></span>  
  
 [<span data-ttu-id="1c56b-117">Localizar o valor máximo em uma sequência numérica</span><span class="sxs-lookup"><span data-stu-id="1c56b-117">Find the Maximum Value in a Numeric Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/find-the-maximum-value-in-a-numeric-sequence.md)  
 <span data-ttu-id="1c56b-118">Demonstra como usar o operador <xref:System.Linq.Enumerable.Max%2A>.</span><span class="sxs-lookup"><span data-stu-id="1c56b-118">Demonstrates how to use the <xref:System.Linq.Enumerable.Max%2A> operator.</span></span>  
  
 [<span data-ttu-id="1c56b-119">Localizar o valor mínimo em uma sequência numérica</span><span class="sxs-lookup"><span data-stu-id="1c56b-119">Find the Minimum Value in a Numeric Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/find-the-minimum-value-in-a-numeric-sequence.md)  
 <span data-ttu-id="1c56b-120">Demonstra como usar o operador <xref:System.Linq.Enumerable.Min%2A>.</span><span class="sxs-lookup"><span data-stu-id="1c56b-120">Demonstrates how to use the <xref:System.Linq.Enumerable.Min%2A> operator.</span></span>  
  
 [<span data-ttu-id="1c56b-121">Calcular a soma dos valores em uma sequência numérica</span><span class="sxs-lookup"><span data-stu-id="1c56b-121">Compute the Sum of Values in a Numeric Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/compute-the-sum-of-values-in-a-numeric-sequence.md)  
 <span data-ttu-id="1c56b-122">Demonstra como usar o operador <xref:System.Linq.Enumerable.Sum%2A>.</span><span class="sxs-lookup"><span data-stu-id="1c56b-122">Demonstrates how to use the <xref:System.Linq.Enumerable.Sum%2A> operator.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="1c56b-123">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="1c56b-123">Related Sections</span></span>  
 [<span data-ttu-id="1c56b-124">Exemplos de consulta</span><span class="sxs-lookup"><span data-stu-id="1c56b-124">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 <span data-ttu-id="1c56b-125">Fornece links para consultas do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] no Visual Basic e no C#.</span><span class="sxs-lookup"><span data-stu-id="1c56b-125">Provides links to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries in Visual Basic and C#.</span></span>  
  
 [<span data-ttu-id="1c56b-126">Conceitos de consulta</span><span class="sxs-lookup"><span data-stu-id="1c56b-126">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 <span data-ttu-id="1c56b-127">Fornece links para tópicos que explicam os conceitos para criar consultas do [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] no [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1c56b-127">Provides links to topics that explain concepts for designing [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="1c56b-128">Introdução a consultas LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="1c56b-128">Introduction to LINQ Queries (C#)</span></span>](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)  
 <span data-ttu-id="1c56b-129">Explica como as consultas funcionam no [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1c56b-129">Explains how queries work in [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span></span>
