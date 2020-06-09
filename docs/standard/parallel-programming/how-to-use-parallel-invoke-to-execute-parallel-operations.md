---
title: 'Como: usar Parallel.Invoke para executar operações paralelas'
description: Consulte como usar o método Parallel. Invoke na TPL (biblioteca paralela de tarefas), que faz operações paralelas em uma fonte de dados compartilhada no .NET.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- task parallelism in .NET
- parallel programming, task parallelism
ms.assetid: 6b3ecd79-dec9-4ce1-abf4-62e5392a59c6
ms.openlocfilehash: 084ade48b1406d23a11eb311739525f35ac973df
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596339"
---
# <a name="how-to-use-parallelinvoke-to-execute-parallel-operations"></a><span data-ttu-id="d875c-103">Como: usar Parallel.Invoke para executar operações paralelas</span><span class="sxs-lookup"><span data-stu-id="d875c-103">How to: Use Parallel.Invoke to Execute Parallel Operations</span></span>

<span data-ttu-id="d875c-104">Este exemplo mostra como paralelizar operações usando <xref:System.Threading.Tasks.Parallel.Invoke%2A> na Biblioteca de paralelismo de tarefas.</span><span class="sxs-lookup"><span data-stu-id="d875c-104">This example shows how to parallelize operations by using <xref:System.Threading.Tasks.Parallel.Invoke%2A> in the Task Parallel Library.</span></span> <span data-ttu-id="d875c-105">Três operações são executadas em uma fonte de dados compartilhada.</span><span class="sxs-lookup"><span data-stu-id="d875c-105">Three operations are performed on a shared data source.</span></span> <span data-ttu-id="d875c-106">As operações podem ser executadas em paralelo de maneira simples, porque nenhuma delas modifica a origem.</span><span class="sxs-lookup"><span data-stu-id="d875c-106">The operations can be executed in parallel in a straightforward manner, because none of them modifies the source.</span></span>

> [!NOTE]
> <span data-ttu-id="d875c-107">Esta documentação usa expressões lambda para definir delegados na TLP.</span><span class="sxs-lookup"><span data-stu-id="d875c-107">This documentation uses lambda expressions to define delegates in TPL.</span></span> <span data-ttu-id="d875c-108">Se você não estiver familiarizado com expressões lambda em C# ou Visual Basic, consulte [expressões lambda em PLINQ e TPL](lambda-expressions-in-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="d875c-108">If you aren't familiar with lambda expressions in C# or Visual Basic, see [Lambda Expressions in PLINQ and TPL](lambda-expressions-in-plinq-and-tpl.md).</span></span>

## <a name="example"></a><span data-ttu-id="d875c-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d875c-109">Example</span></span>

[!code-csharp[TPL_Parallel#06](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallelinvoke.cs#06)]
[!code-vb[TPL_Parallel#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/parallelinvoke.vb#06)]

<span data-ttu-id="d875c-110">Com o <xref:System.Threading.Tasks.Parallel.Invoke%2A> , basta expressar quais ações você deseja executar simultaneamente, e o tempo de execução manipula todos os detalhes de agendamento de thread, incluindo o dimensionamento automático para o número de núcleos no computador host.</span><span class="sxs-lookup"><span data-stu-id="d875c-110">With <xref:System.Threading.Tasks.Parallel.Invoke%2A>, you simply express which actions you want to run concurrently, and the runtime handles all thread scheduling details, including scaling automatically to the number of cores on the host computer.</span></span>

<span data-ttu-id="d875c-111">Este exemplo paraleliza as operações, não os dados.</span><span class="sxs-lookup"><span data-stu-id="d875c-111">This example parallelizes the operations, not the data.</span></span> <span data-ttu-id="d875c-112">Como uma abordagem alternativa, você pode paralelizar as consultas do LINQ usando PLINQ e executar as consultas em sequência.</span><span class="sxs-lookup"><span data-stu-id="d875c-112">As an alternate approach, you can parallelize the LINQ queries by using PLINQ and run the queries sequentially.</span></span> <span data-ttu-id="d875c-113">Como alternativa, você poderia paralelizar os dados usando o PLINQ.</span><span class="sxs-lookup"><span data-stu-id="d875c-113">Alternatively, you could parallelize the data by using PLINQ.</span></span> <span data-ttu-id="d875c-114">Outra opção é paralelizar as consultas e as tarefas.</span><span class="sxs-lookup"><span data-stu-id="d875c-114">Another option is to parallelize both the queries and the tasks.</span></span> <span data-ttu-id="d875c-115">Embora a sobrecarga resultante possa prejudicar o desempenho em computadores host com relativamente poucos processadores, ela é dimensionada melhor em computadores com muitos processadores.</span><span class="sxs-lookup"><span data-stu-id="d875c-115">Although the resulting overhead might degrade performance on host computers with relatively few processors, it scales better on computers with many processors.</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="d875c-116">Compile o código</span><span class="sxs-lookup"><span data-stu-id="d875c-116">Compile the Code</span></span>

<span data-ttu-id="d875c-117">Copie e cole o exemplo inteiro em um projeto do Microsoft Visual Studio e pressione **F5**.</span><span class="sxs-lookup"><span data-stu-id="d875c-117">Copy and paste the entire example into a Microsoft Visual Studio project and press **F5**.</span></span>

## <a name="see-also"></a><span data-ttu-id="d875c-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d875c-118">See also</span></span>

- [<span data-ttu-id="d875c-119">Programação paralela</span><span class="sxs-lookup"><span data-stu-id="d875c-119">Parallel Programming</span></span>](index.md)
- [<span data-ttu-id="d875c-120">Como: Cancelar uma tarefa e seus filhos</span><span class="sxs-lookup"><span data-stu-id="d875c-120">How to: Cancel a Task and Its Children</span></span>](how-to-cancel-a-task-and-its-children.md)
- [<span data-ttu-id="d875c-121">LINQ paralelo (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="d875c-121">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
