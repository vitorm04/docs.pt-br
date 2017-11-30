---
title: LINQ paralelo (PLINQ)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: PLINQ, overview
ms.assetid: 3d4d0cd3-bde4-490b-99e7-f4e41be96455
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c0028d3d8c30bbc7f0592a4462ca1eeb80c8b1f9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="parallel-linq-plinq"></a><span data-ttu-id="cced7-102">LINQ paralelo (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="cced7-102">Parallel LINQ (PLINQ)</span></span>
<span data-ttu-id="cced7-103">LINQ paralelo (PLINQ) é uma implementação paralela de objetos LINQ to.</span><span class="sxs-lookup"><span data-stu-id="cced7-103">Parallel LINQ (PLINQ) is a parallel implementation of LINQ to Objects.</span></span> <span data-ttu-id="cced7-104">PLINQ implementa o conjunto completo de operadores de consulta padrão LINQ como métodos de extensão para o <xref:System.Linq> namespace e tem operadores adicionais para operações paralelas.</span><span class="sxs-lookup"><span data-stu-id="cced7-104">PLINQ implements the full set of LINQ standard query operators as extension methods for the <xref:System.Linq> namespace and has additional operators for parallel operations.</span></span> <span data-ttu-id="cced7-105">PLINQ combina a simplicidade e a legibilidade de sintaxe LINQ com o poder da programação paralela.</span><span class="sxs-lookup"><span data-stu-id="cced7-105">PLINQ combines the simplicity and readability of LINQ syntax with the power of parallel programming.</span></span> <span data-ttu-id="cced7-106">Assim como código que tem como destino a biblioteca paralela de tarefas, consultas PLINQ ampliar o grau de simultaneidade com base nos recursos do computador host.</span><span class="sxs-lookup"><span data-stu-id="cced7-106">Just like code that targets the Task Parallel Library, PLINQ queries scale in the degree of concurrency based on the capabilities of the host computer.</span></span>  
  
 <span data-ttu-id="cced7-107">Em muitos cenários, PLINQ pode aumentar significativamente a velocidade de LINQ para consultas de objetos usando todos os núcleos disponíveis no computador host com mais eficiência.</span><span class="sxs-lookup"><span data-stu-id="cced7-107">In many scenarios, PLINQ can significantly increase the speed of LINQ to Objects queries by using all available cores on the host computer more efficiently.</span></span> <span data-ttu-id="cced7-108">Esse aumento do desempenho traz a potência de computação de alto desempenho para a área de trabalho.</span><span class="sxs-lookup"><span data-stu-id="cced7-108">This increased performance brings high performance computing power onto the desktop.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cced7-109">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="cced7-109">In This Section</span></span>  
 [<span data-ttu-id="cced7-110">Introdução ao PLINQ</span><span class="sxs-lookup"><span data-stu-id="cced7-110">Introduction to PLINQ</span></span>](../../../docs/standard/parallel-programming/introduction-to-plinq.md)  
  
 [<span data-ttu-id="cced7-111">Noções básicas sobre agilização no PLINQ</span><span class="sxs-lookup"><span data-stu-id="cced7-111">Understanding Speedup in PLINQ</span></span>](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)  
  
 [<span data-ttu-id="cced7-112">Preservação da ordem em PLINQ</span><span class="sxs-lookup"><span data-stu-id="cced7-112">Order Preservation in PLINQ</span></span>](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md)  
  
 [<span data-ttu-id="cced7-113">Opções de mesclagem em PLINQ</span><span class="sxs-lookup"><span data-stu-id="cced7-113">Merge Options in PLINQ</span></span>](../../../docs/standard/parallel-programming/merge-options-in-plinq.md)  
  
 [<span data-ttu-id="cced7-114">Como criar e executar uma consulta PLINQ simples</span><span class="sxs-lookup"><span data-stu-id="cced7-114">How to: Create and Execute a Simple PLINQ Query</span></span>](../../../docs/standard/parallel-programming/how-to-create-and-execute-a-simple-plinq-query.md)  
  
 [<span data-ttu-id="cced7-115">Como controlar a ordem em uma consulta PLINQ</span><span class="sxs-lookup"><span data-stu-id="cced7-115">How to: Control Ordering in a PLINQ Query</span></span>](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md)  
  
 [<span data-ttu-id="cced7-116">Como combinar consultas LINQ paralelas e sequenciais</span><span class="sxs-lookup"><span data-stu-id="cced7-116">How to: Combine Parallel and Sequential LINQ Queries</span></span>](../../../docs/standard/parallel-programming/how-to-combine-parallel-and-sequential-linq-queries.md)  
  
 [<span data-ttu-id="cced7-117">Como tratar exceções em uma consulta PLINQ</span><span class="sxs-lookup"><span data-stu-id="cced7-117">How to: Handle Exceptions in a PLINQ Query</span></span>](../../../docs/standard/parallel-programming/how-to-handle-exceptions-in-a-plinq-query.md)  
  
 [<span data-ttu-id="cced7-118">Como cancelar uma consulta PLINQ</span><span class="sxs-lookup"><span data-stu-id="cced7-118">How to: Cancel a PLINQ Query</span></span>](../../../docs/standard/parallel-programming/how-to-cancel-a-plinq-query.md)  
  
 [<span data-ttu-id="cced7-119">Como escrever uma função de agregação PLINQ personalizada</span><span class="sxs-lookup"><span data-stu-id="cced7-119">How to: Write a Custom PLINQ Aggregate Function</span></span>](../../../docs/standard/parallel-programming/how-to-write-a-custom-plinq-aggregate-function.md)  
  
 [<span data-ttu-id="cced7-120">Como especificar o modo de execução em PLINQ</span><span class="sxs-lookup"><span data-stu-id="cced7-120">How to: Specify the Execution Mode in PLINQ</span></span>](../../../docs/standard/parallel-programming/how-to-specify-the-execution-mode-in-plinq.md)  
  
 [<span data-ttu-id="cced7-121">Como especificar opções de mesclagem em PLINQ</span><span class="sxs-lookup"><span data-stu-id="cced7-121">How to: Specify Merge Options in PLINQ</span></span>](../../../docs/standard/parallel-programming/how-to-specify-merge-options-in-plinq.md)  
  
 [<span data-ttu-id="cced7-122">Como iterar diretórios de arquivos com PLINQ</span><span class="sxs-lookup"><span data-stu-id="cced7-122">How to: Iterate File Directories with PLINQ</span></span>](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-plinq.md)  
  
 [<span data-ttu-id="cced7-123">Como avaliar o desempenho da consulta PLINQ</span><span class="sxs-lookup"><span data-stu-id="cced7-123">How to: Measure PLINQ Query Performance</span></span>](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md)  
  
 [<span data-ttu-id="cced7-124">Exemplo de dados PLINQ</span><span class="sxs-lookup"><span data-stu-id="cced7-124">PLINQ Data Sample</span></span>](../../../docs/standard/parallel-programming/plinq-data-sample.md)  
  
## <a name="see-also"></a><span data-ttu-id="cced7-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cced7-125">See Also</span></span>  
 <xref:System.Linq.ParallelEnumerable>  
 [<span data-ttu-id="cced7-126">Programação paralela</span><span class="sxs-lookup"><span data-stu-id="cced7-126">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)  
 [<span data-ttu-id="cced7-127">LINQ (Consulta Integrada à Linguagem)</span><span class="sxs-lookup"><span data-stu-id="cced7-127">LINQ (Language-Integrated Query)</span></span>](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)
