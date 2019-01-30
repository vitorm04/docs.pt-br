---
title: LINQ paralelo (PLINQ)
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- PLINQ, overview
ms.assetid: 3d4d0cd3-bde4-490b-99e7-f4e41be96455
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d597bc3590441494478c46b832aeed57ba761ca7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54500831"
---
# <a name="parallel-linq-plinq"></a><span data-ttu-id="78967-102">LINQ paralelo (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="78967-102">Parallel LINQ (PLINQ)</span></span>
<span data-ttu-id="78967-103">PLINQ (Parallel LINQ) é uma implementação paralela da LINQ to Objects.</span><span class="sxs-lookup"><span data-stu-id="78967-103">Parallel LINQ (PLINQ) is a parallel implementation of LINQ to Objects.</span></span> <span data-ttu-id="78967-104">O PLINQ implementa o conjunto completo de operadores de consulta padrão LINQ como métodos de extensão para o namespace <xref:System.Linq> e tem operadores adicionais para operações paralelas.</span><span class="sxs-lookup"><span data-stu-id="78967-104">PLINQ implements the full set of LINQ standard query operators as extension methods for the <xref:System.Linq> namespace and has additional operators for parallel operations.</span></span> <span data-ttu-id="78967-105">O PLINQ combina a simplicidade e a legibilidade da sintaxe LINQ com o poder da programação paralela.</span><span class="sxs-lookup"><span data-stu-id="78967-105">PLINQ combines the simplicity and readability of LINQ syntax with the power of parallel programming.</span></span> <span data-ttu-id="78967-106">Assim como código que tem como destino a Biblioteca de Paralelismo de Tarefas, as consultas PLINQ reduzem horizontalmente o grau de simultaneidade com base nos recursos do computador host.</span><span class="sxs-lookup"><span data-stu-id="78967-106">Just like code that targets the Task Parallel Library, PLINQ queries scale in the degree of concurrency based on the capabilities of the host computer.</span></span>  
  
 <span data-ttu-id="78967-107">Em muitos cenários, o PLINQ pode aumentar significativamente a velocidade das consultas LINQ to Objects usando todos os núcleos disponíveis no computador host com mais eficiência.</span><span class="sxs-lookup"><span data-stu-id="78967-107">In many scenarios, PLINQ can significantly increase the speed of LINQ to Objects queries by using all available cores on the host computer more efficiently.</span></span> <span data-ttu-id="78967-108">Esse aumento do desempenho traz a potência da computação de alto desempenho para a área de trabalho.</span><span class="sxs-lookup"><span data-stu-id="78967-108">This increased performance brings high-performance computing power onto the desktop.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="78967-109">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="78967-109">In This Section</span></span>  
 [<span data-ttu-id="78967-110">Introdução ao PLINQ</span><span class="sxs-lookup"><span data-stu-id="78967-110">Introduction to PLINQ</span></span>](../../../docs/standard/parallel-programming/introduction-to-plinq.md)  
  
 [<span data-ttu-id="78967-111">Noções básicas sobre agilização no PLINQ</span><span class="sxs-lookup"><span data-stu-id="78967-111">Understanding Speedup in PLINQ</span></span>](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)  
  
 [<span data-ttu-id="78967-112">Preservação da ordem em PLINQ</span><span class="sxs-lookup"><span data-stu-id="78967-112">Order Preservation in PLINQ</span></span>](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md)  
  
 [<span data-ttu-id="78967-113">Opções de mesclagem em PLINQ</span><span class="sxs-lookup"><span data-stu-id="78967-113">Merge Options in PLINQ</span></span>](../../../docs/standard/parallel-programming/merge-options-in-plinq.md)  
  
 [<span data-ttu-id="78967-114">Como: Criar e executar uma consulta PLINQ simples</span><span class="sxs-lookup"><span data-stu-id="78967-114">How to: Create and Execute a Simple PLINQ Query</span></span>](../../../docs/standard/parallel-programming/how-to-create-and-execute-a-simple-plinq-query.md)  
  
 [<span data-ttu-id="78967-115">Como: Controlar a ordem em uma consulta PLINQ</span><span class="sxs-lookup"><span data-stu-id="78967-115">How to: Control Ordering in a PLINQ Query</span></span>](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md)  
  
 [<span data-ttu-id="78967-116">Como: Combinar consultas LINQ paralelas e sequenciais</span><span class="sxs-lookup"><span data-stu-id="78967-116">How to: Combine Parallel and Sequential LINQ Queries</span></span>](../../../docs/standard/parallel-programming/how-to-combine-parallel-and-sequential-linq-queries.md)  
  
 [<span data-ttu-id="78967-117">Como: Tratar exceções em uma consulta PLINQ</span><span class="sxs-lookup"><span data-stu-id="78967-117">How to: Handle Exceptions in a PLINQ Query</span></span>](../../../docs/standard/parallel-programming/how-to-handle-exceptions-in-a-plinq-query.md)  
  
 [<span data-ttu-id="78967-118">Como: Cancelar uma consulta PLINQ</span><span class="sxs-lookup"><span data-stu-id="78967-118">How to: Cancel a PLINQ Query</span></span>](../../../docs/standard/parallel-programming/how-to-cancel-a-plinq-query.md)  
  
 [<span data-ttu-id="78967-119">Como: Escrever uma função de agregação PLINQ personalizada</span><span class="sxs-lookup"><span data-stu-id="78967-119">How to: Write a Custom PLINQ Aggregate Function</span></span>](../../../docs/standard/parallel-programming/how-to-write-a-custom-plinq-aggregate-function.md)  
  
 [<span data-ttu-id="78967-120">Como: Especificar o modo de execução em PLINQ</span><span class="sxs-lookup"><span data-stu-id="78967-120">How to: Specify the Execution Mode in PLINQ</span></span>](../../../docs/standard/parallel-programming/how-to-specify-the-execution-mode-in-plinq.md)  
  
 [<span data-ttu-id="78967-121">Como: Especificar opções de mesclagem em PLINQ</span><span class="sxs-lookup"><span data-stu-id="78967-121">How to: Specify Merge Options in PLINQ</span></span>](../../../docs/standard/parallel-programming/how-to-specify-merge-options-in-plinq.md)  
  
 [<span data-ttu-id="78967-122">Como: Iterar diretórios de arquivos com PLINQ</span><span class="sxs-lookup"><span data-stu-id="78967-122">How to: Iterate File Directories with PLINQ</span></span>](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-plinq.md)  
  
 [<span data-ttu-id="78967-123">Como: Avaliar o desempenho da consulta PLINQ</span><span class="sxs-lookup"><span data-stu-id="78967-123">How to: Measure PLINQ Query Performance</span></span>](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md)  
  
 [<span data-ttu-id="78967-124">Exemplo de dados PLINQ</span><span class="sxs-lookup"><span data-stu-id="78967-124">PLINQ Data Sample</span></span>](../../../docs/standard/parallel-programming/plinq-data-sample.md)  
  
## <a name="see-also"></a><span data-ttu-id="78967-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="78967-125">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>
- [<span data-ttu-id="78967-126">Programação paralela</span><span class="sxs-lookup"><span data-stu-id="78967-126">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)
- [<span data-ttu-id="78967-127">LINQ (Consulta Integrada à Linguagem)</span><span class="sxs-lookup"><span data-stu-id="78967-127">LINQ (Language-Integrated Query)</span></span>](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)
