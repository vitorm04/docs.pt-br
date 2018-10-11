---
title: Como usar Parallel.Invoke para executar operações em paralelo
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- task parallelism in .NET
- parallel programming, task parallelism
ms.assetid: 6b3ecd79-dec9-4ce1-abf4-62e5392a59c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c0192e12c86b21eb126293bbd220e093b334768b
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/29/2018
ms.locfileid: "47455993"
---
# <a name="how-to-use-parallelinvoke-to-execute-parallel-operations"></a><span data-ttu-id="0ff81-102">Como usar Parallel.Invoke para executar operações em paralelo</span><span class="sxs-lookup"><span data-stu-id="0ff81-102">How to: Use Parallel.Invoke to Execute Parallel Operations</span></span>

<span data-ttu-id="0ff81-103">Este exemplo mostra como paralelizar operações usando <xref:System.Threading.Tasks.Parallel.Invoke%2A> na Biblioteca de paralelismo de tarefas.</span><span class="sxs-lookup"><span data-stu-id="0ff81-103">This example shows how to parallelize operations by using <xref:System.Threading.Tasks.Parallel.Invoke%2A> in the Task Parallel Library.</span></span> <span data-ttu-id="0ff81-104">Três operações são executadas em uma fonte de dados compartilhada.</span><span class="sxs-lookup"><span data-stu-id="0ff81-104">Three operations are performed on a shared data source.</span></span> <span data-ttu-id="0ff81-105">Como nenhuma das operações modifica a fonte, elas podem ser executadas em paralelo de uma maneira simples.</span><span class="sxs-lookup"><span data-stu-id="0ff81-105">Because none of the operations modifies the source, they can be executed in parallel in a straightforward manner.</span></span>

> [!NOTE]
> <span data-ttu-id="0ff81-106">Esta documentação usa expressões lambda para definir delegados na TLP.</span><span class="sxs-lookup"><span data-stu-id="0ff81-106">This documentation uses lambda expressions to define delegates in TPL.</span></span> <span data-ttu-id="0ff81-107">Se você não estiver familiarizado com expressões lambda no C# ou no Visual Basic, veja [Expressões lambda em PLINQ e TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="0ff81-107">If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span></span>

## <a name="example"></a><span data-ttu-id="0ff81-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ff81-108">Example</span></span>

[!code-csharp[TPL_Parallel#06](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallelinvoke.cs#06)]
[!code-vb[TPL_Parallel#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/parallelinvoke.vb#06)]

<span data-ttu-id="0ff81-109">Observe que, com <xref:System.Threading.Tasks.Parallel.Invoke%2A>, você simplesmente expressa quais ações quer executar simultaneamente, e o tempo de execução trata todos os detalhes de agendamento do thread, incluindo o dimensionamento automaticamente para o número de núcleos no computador host.</span><span class="sxs-lookup"><span data-stu-id="0ff81-109">Note that with <xref:System.Threading.Tasks.Parallel.Invoke%2A>, you simply express which actions you want to run concurrently, and the runtime handles all thread scheduling details, including scaling automatically to the number of cores on the host computer.</span></span>

<span data-ttu-id="0ff81-110">Este exemplo paraleliza as operações, não os dados.</span><span class="sxs-lookup"><span data-stu-id="0ff81-110">This example parallelizes the operations, not the data.</span></span> <span data-ttu-id="0ff81-111">Como uma abordagem alternativa, você pode paralelizar as consultas do LINQ usando PLINQ e executar as consultas em sequência.</span><span class="sxs-lookup"><span data-stu-id="0ff81-111">As an alternate approach, you can parallelize the LINQ queries by using PLINQ and run the queries sequentially.</span></span> <span data-ttu-id="0ff81-112">Como alternativa, você poderia paralelizar os dados usando o PLINQ.</span><span class="sxs-lookup"><span data-stu-id="0ff81-112">Alternatively, you could parallelize the data by using PLINQ.</span></span> <span data-ttu-id="0ff81-113">Outra opção é paralelizar as consultas e as tarefas.</span><span class="sxs-lookup"><span data-stu-id="0ff81-113">Another option is to parallelize both the queries and the tasks.</span></span> <span data-ttu-id="0ff81-114">Embora a sobrecarga resultante possa degradar o desempenho em computadores de host com poucos processadores, ela será dimensionada muito melhor em computadores com vários processadores.</span><span class="sxs-lookup"><span data-stu-id="0ff81-114">Although the resulting overhead might degrade performance on host computers with relatively few processors, it would scale much better on computers with many processors.</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="0ff81-115">Compile o código</span><span class="sxs-lookup"><span data-stu-id="0ff81-115">Compile the Code</span></span>

<span data-ttu-id="0ff81-116">Copie e cole o exemplo inteiro em um projeto do Microsoft Visual Studio e pressione **F5**.</span><span class="sxs-lookup"><span data-stu-id="0ff81-116">Copy and paste the entire example into a Microsoft Visual Studio project and press **F5**.</span></span>

## <a name="see-also"></a><span data-ttu-id="0ff81-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ff81-117">See also</span></span>

- [<span data-ttu-id="0ff81-118">Programação paralela</span><span class="sxs-lookup"><span data-stu-id="0ff81-118">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)
- [<span data-ttu-id="0ff81-119">Como cancelar uma tarefa e seus filhos</span><span class="sxs-lookup"><span data-stu-id="0ff81-119">How to: Cancel a Task and Its Children</span></span>](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)
- [<span data-ttu-id="0ff81-120">PLINQ (LINQ paralelo)</span><span class="sxs-lookup"><span data-stu-id="0ff81-120">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
