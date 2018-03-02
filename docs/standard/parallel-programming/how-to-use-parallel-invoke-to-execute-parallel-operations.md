---
title: "Como usar Parallel.Invoke para executar operações em paralelo"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- task parallelism in .NET
- parallel programming, task parallelism
ms.assetid: 6b3ecd79-dec9-4ce1-abf4-62e5392a59c6
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 942ba120fa5273f84ac3d0a51e276223de5f5484
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-use-parallelinvoke-to-execute-parallel-operations"></a><span data-ttu-id="6497b-102">Como usar Parallel.Invoke para executar operações em paralelo</span><span class="sxs-lookup"><span data-stu-id="6497b-102">How to: Use Parallel.Invoke to Execute Parallel Operations</span></span>
<span data-ttu-id="6497b-103">Este exemplo mostra como paralelizar operações usando <xref:System.Threading.Tasks.Parallel.Invoke%2A> na Biblioteca de paralelismo de tarefas.</span><span class="sxs-lookup"><span data-stu-id="6497b-103">This example shows how to parallelize operations by using <xref:System.Threading.Tasks.Parallel.Invoke%2A> in the Task Parallel Library.</span></span> <span data-ttu-id="6497b-104">Três operações são executadas em uma fonte de dados compartilhada.</span><span class="sxs-lookup"><span data-stu-id="6497b-104">Three operations are performed on a shared data source.</span></span> <span data-ttu-id="6497b-105">Como nenhuma das operações modifica a fonte, elas podem ser executadas em paralelo de uma maneira simples.</span><span class="sxs-lookup"><span data-stu-id="6497b-105">Because none of the operations modifies the source, they can be executed in parallel in a straightforward manner.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6497b-106">Esta documentação usa expressões lambda para definir delegados na TLP.</span><span class="sxs-lookup"><span data-stu-id="6497b-106">This documentation uses lambda expressions to define delegates in TPL.</span></span> <span data-ttu-id="6497b-107">Se você não estiver familiarizado com expressões lambda no C# ou no Visual Basic, veja [Expressões lambda em PLINQ e TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="6497b-107">If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6497b-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6497b-108">Example</span></span>  
 [!code-csharp[TPL_Parallel#06](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallelinvoke.cs#06)]
 [!code-vb[TPL_Parallel#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/parallelinvoke.vb#06)]  
  
 <span data-ttu-id="6497b-109">Observe que, com <xref:System.Threading.Tasks.Parallel.Invoke%2A>, você simplesmente expressa quais ações quer executar simultaneamente, e o tempo de execução trata todos os detalhes de agendamento do thread, incluindo o dimensionamento automaticamente para o número de núcleos no computador host.</span><span class="sxs-lookup"><span data-stu-id="6497b-109">Note that with <xref:System.Threading.Tasks.Parallel.Invoke%2A>, you simply express which actions you want to run concurrently, and the runtime handles all thread scheduling details, including scaling automatically to the number of cores on the host computer.</span></span>  
  
 <span data-ttu-id="6497b-110">Este exemplo paraleliza as operações, não os dados.</span><span class="sxs-lookup"><span data-stu-id="6497b-110">This example parallelizes the operations, not the data.</span></span> <span data-ttu-id="6497b-111">Como uma abordagem alternativa, você pode paralelizar as consultas do LINQ usando PLINQ e executar as consultas em sequência.</span><span class="sxs-lookup"><span data-stu-id="6497b-111">As an alternate approach, you can parallelize the LINQ queries by using PLINQ and run the queries sequentially.</span></span> <span data-ttu-id="6497b-112">Como alternativa, você poderia paralelizar os dados usando o PLINQ.</span><span class="sxs-lookup"><span data-stu-id="6497b-112">Alternatively, you could parallelize the data by using PLINQ.</span></span> <span data-ttu-id="6497b-113">Outra opção é paralelizar as consultas e as tarefas.</span><span class="sxs-lookup"><span data-stu-id="6497b-113">Another option is to parallelize both the queries and the tasks.</span></span> <span data-ttu-id="6497b-114">Embora a sobrecarga resultante possa degradar o desempenho em computadores de host com poucos processadores, ela será dimensionada muito melhor em computadores com vários processadores.</span><span class="sxs-lookup"><span data-stu-id="6497b-114">Although the resulting overhead might degrade performance on host computers with relatively few processors, it would scale much better on computers with many processors.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6497b-115">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="6497b-115">Compiling the Code</span></span>  
  
-   <span data-ttu-id="6497b-116">Copie e cole o exemplo inteiro em um projeto do Microsoft Visual Studio 2010 e pressione F5.</span><span class="sxs-lookup"><span data-stu-id="6497b-116">Copy and paste the entire example into a Microsoft Visual Studio 2010 project and press F5.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6497b-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6497b-117">See Also</span></span>  
 [<span data-ttu-id="6497b-118">Programação paralela</span><span class="sxs-lookup"><span data-stu-id="6497b-118">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)  
 [<span data-ttu-id="6497b-119">Como cancelar uma tarefa e seus filhos</span><span class="sxs-lookup"><span data-stu-id="6497b-119">How to: Cancel a Task and Its Children</span></span>](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)  
 [<span data-ttu-id="6497b-120">PLINQ (LINQ paralelo)</span><span class="sxs-lookup"><span data-stu-id="6497b-120">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
