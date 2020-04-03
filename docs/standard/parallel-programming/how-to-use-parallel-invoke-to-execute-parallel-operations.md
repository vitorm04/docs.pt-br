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
ms.openlocfilehash: f61bbf10bbeef736f66710f50e621c3619355a1d
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635798"
---
# <a name="how-to-use-parallelinvoke-to-execute-parallel-operations"></a><span data-ttu-id="f998e-102">Como usar Parallel.Invoke para executar operações em paralelo</span><span class="sxs-lookup"><span data-stu-id="f998e-102">How to: Use Parallel.Invoke to Execute Parallel Operations</span></span>

<span data-ttu-id="f998e-103">Este exemplo mostra como paralelizar operações usando <xref:System.Threading.Tasks.Parallel.Invoke%2A> na Biblioteca de paralelismo de tarefas.</span><span class="sxs-lookup"><span data-stu-id="f998e-103">This example shows how to parallelize operations by using <xref:System.Threading.Tasks.Parallel.Invoke%2A> in the Task Parallel Library.</span></span> <span data-ttu-id="f998e-104">Três operações são executadas em uma fonte de dados compartilhada.</span><span class="sxs-lookup"><span data-stu-id="f998e-104">Three operations are performed on a shared data source.</span></span> <span data-ttu-id="f998e-105">As operações podem ser executadas em paralelo de forma direta, porque nenhuma delas modifica a fonte.</span><span class="sxs-lookup"><span data-stu-id="f998e-105">The operations can be executed in parallel in a straightforward manner, because none of them modifies the source.</span></span>

> [!NOTE]
> <span data-ttu-id="f998e-106">Esta documentação usa expressões lambda para definir delegados na TLP.</span><span class="sxs-lookup"><span data-stu-id="f998e-106">This documentation uses lambda expressions to define delegates in TPL.</span></span> <span data-ttu-id="f998e-107">Se você não estiver familiarizado com expressões lambda em C# ou Visual Basic, consulte [Expressões Lambda em PLINQ e TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="f998e-107">If you aren't familiar with lambda expressions in C# or Visual Basic, see [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span></span>

## <a name="example"></a><span data-ttu-id="f998e-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f998e-108">Example</span></span>

[!code-csharp[TPL_Parallel#06](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallelinvoke.cs#06)]
[!code-vb[TPL_Parallel#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/parallelinvoke.vb#06)]

<span data-ttu-id="f998e-109">Com <xref:System.Threading.Tasks.Parallel.Invoke%2A>, você simplesmente expressa quais ações deseja executar simultaneamente, e o tempo de execução lida com todos os detalhes de agendamento de thread, incluindo o dimensionamento automático para o número de núcleos no computador host.</span><span class="sxs-lookup"><span data-stu-id="f998e-109">With <xref:System.Threading.Tasks.Parallel.Invoke%2A>, you simply express which actions you want to run concurrently, and the runtime handles all thread scheduling details, including scaling automatically to the number of cores on the host computer.</span></span>

<span data-ttu-id="f998e-110">Este exemplo paraleliza as operações, não os dados.</span><span class="sxs-lookup"><span data-stu-id="f998e-110">This example parallelizes the operations, not the data.</span></span> <span data-ttu-id="f998e-111">Como uma abordagem alternativa, você pode paralelizar as consultas do LINQ usando PLINQ e executar as consultas em sequência.</span><span class="sxs-lookup"><span data-stu-id="f998e-111">As an alternate approach, you can parallelize the LINQ queries by using PLINQ and run the queries sequentially.</span></span> <span data-ttu-id="f998e-112">Como alternativa, você poderia paralelizar os dados usando o PLINQ.</span><span class="sxs-lookup"><span data-stu-id="f998e-112">Alternatively, you could parallelize the data by using PLINQ.</span></span> <span data-ttu-id="f998e-113">Outra opção é paralelizar as consultas e as tarefas.</span><span class="sxs-lookup"><span data-stu-id="f998e-113">Another option is to parallelize both the queries and the tasks.</span></span> <span data-ttu-id="f998e-114">Embora a sobrecarga resultante possa degradar o desempenho em computadores host com relativamente poucos processadores, ele escala melhor em computadores com muitos processadores.</span><span class="sxs-lookup"><span data-stu-id="f998e-114">Although the resulting overhead might degrade performance on host computers with relatively few processors, it scales better on computers with many processors.</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="f998e-115">Compile o código</span><span class="sxs-lookup"><span data-stu-id="f998e-115">Compile the Code</span></span>

<span data-ttu-id="f998e-116">Copie e cole o exemplo inteiro em um projeto do Microsoft Visual Studio e pressione **F5**.</span><span class="sxs-lookup"><span data-stu-id="f998e-116">Copy and paste the entire example into a Microsoft Visual Studio project and press **F5**.</span></span>

## <a name="see-also"></a><span data-ttu-id="f998e-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="f998e-117">See also</span></span>

- [<span data-ttu-id="f998e-118">Programação Paralela</span><span class="sxs-lookup"><span data-stu-id="f998e-118">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)
- [<span data-ttu-id="f998e-119">Como cancelar uma tarefa e seus filhos</span><span class="sxs-lookup"><span data-stu-id="f998e-119">How to: Cancel a Task and Its Children</span></span>](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)
- [<span data-ttu-id="f998e-120">PLINQ (LINQ paralelo)</span><span class="sxs-lookup"><span data-stu-id="f998e-120">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
