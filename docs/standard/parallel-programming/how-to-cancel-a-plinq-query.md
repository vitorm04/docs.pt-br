---
title: Como cancelar uma consulta PLINQ
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to cancel
- cancellation, PLINQ
ms.assetid: 80b14640-edfa-4153-be1b-3e003d3e9c1a
ms.openlocfilehash: 312c71b787ac7b4aa092f1517d2ed5af314a22e4
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635875"
---
# <a name="how-to-cancel-a-plinq-query"></a><span data-ttu-id="dca6c-102">Como cancelar uma consulta PLINQ</span><span class="sxs-lookup"><span data-stu-id="dca6c-102">How to: Cancel a PLINQ Query</span></span>
<span data-ttu-id="dca6c-103">Os exemplos a seguir mostram duas maneiras de cancelar uma consulta PLINQ.</span><span class="sxs-lookup"><span data-stu-id="dca6c-103">The following examples show two ways to cancel a PLINQ query.</span></span> <span data-ttu-id="dca6c-104">O primeiro exemplo mostra como cancelar uma consulta composta principalmente de travessia de dados.</span><span class="sxs-lookup"><span data-stu-id="dca6c-104">The first example shows how to cancel a query that consists mostly of data traversal.</span></span> <span data-ttu-id="dca6c-105">O segundo exemplo mostra como cancelar uma consulta que contém uma função de usuário que gasta muitos recursos de computação.</span><span class="sxs-lookup"><span data-stu-id="dca6c-105">The second example shows how to cancel a query that contains a user function that is computationally expensive.</span></span>

> [!NOTE]
> <span data-ttu-id="dca6c-106">Se a opção "Apenas Meu Código" estiver habilitada, o Visual Studio interromperá na linha que gerou a exceção e exibirá a mensagem de erro "exceção não tratada pelo código do usuário".</span><span class="sxs-lookup"><span data-stu-id="dca6c-106">When "Just My Code" is enabled, Visual Studio will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="dca6c-107">Esse erro é benigno.</span><span class="sxs-lookup"><span data-stu-id="dca6c-107">This error is benign.</span></span> <span data-ttu-id="dca6c-108">Você pode pressionar F5 para continuar a partir daí e ver o comportamento de tratamento de exceção, demonstrado nos exemplos a seguir.</span><span class="sxs-lookup"><span data-stu-id="dca6c-108">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="dca6c-109">Para impedir que o Visual Studio seja interrompido no primeiro erro, basta desmarcar a caixa de seleção "Apenas Meu Código" em **Ferramentas, Opções, Depuração, Geral**.</span><span class="sxs-lookup"><span data-stu-id="dca6c-109">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>
>
> <span data-ttu-id="dca6c-110">Este exemplo tem como objetivo demonstrar o uso e pode não executar tão rápido quanto a consulta LINQ to Objects sequencial equivalente.</span><span class="sxs-lookup"><span data-stu-id="dca6c-110">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="dca6c-111">Para saber mais sobre agilização, confira [Noções básicas sobre agilização no PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="dca6c-111">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>

## <a name="example"></a><span data-ttu-id="dca6c-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="dca6c-112">Example</span></span>

[!code-csharp[PLINQ#16](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#16)]
[!code-vb[PLINQ#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#16)]

<span data-ttu-id="dca6c-113">A estrutura do PLINQ não implementa um único <xref:System.OperationCanceledException> em uma <xref:System.AggregateException?displayProperty=nameWithType>; o <xref:System.OperationCanceledException> deve ser tratado em um bloco catch separado.</span><span class="sxs-lookup"><span data-stu-id="dca6c-113">The PLINQ framework does not roll a single <xref:System.OperationCanceledException> into an <xref:System.AggregateException?displayProperty=nameWithType>; the <xref:System.OperationCanceledException> must be handled in a separate catch block.</span></span> <span data-ttu-id="dca6c-114">Se um ou mais delegados de usuário gerar uma OperationCanceledException(externalCT) (usando um <xref:System.Threading.CancellationToken?displayProperty=nameWithType> externo), mas nenhuma outra exceção, e a consulta tiver sido definida como `AsParallel().WithCancellation(externalCT)`, PLINQ emitirá uma única <xref:System.OperationCanceledException> (externalCT) em vez de uma <xref:System.AggregateException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="dca6c-114">If one or more user delegates throws an OperationCanceledException(externalCT) (by using an external <xref:System.Threading.CancellationToken?displayProperty=nameWithType>) but no other exception, and the query was defined as `AsParallel().WithCancellation(externalCT)`, then PLINQ will issue a single <xref:System.OperationCanceledException> (externalCT) rather than an <xref:System.AggregateException?displayProperty=nameWithType>.</span></span> <span data-ttu-id="dca6c-115">No entanto, se um delegado de usuário lançar uma <xref:System.OperationCanceledException>, e outro delegado lançar outro tipo de exceção, as duas exceções serão transferidas para um <xref:System.AggregateException>.</span><span class="sxs-lookup"><span data-stu-id="dca6c-115">However, if one user delegate throws an <xref:System.OperationCanceledException>, and another delegate throws another exception type, then both exceptions will be rolled into an <xref:System.AggregateException>.</span></span>

<span data-ttu-id="dca6c-116">A orientação geral sobre o cancelamento é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="dca6c-116">The general guidance on cancellation is as follows:</span></span>

1. <span data-ttu-id="dca6c-117">Se você realizar o cancelamento do usuário-delegado, <xref:System.Threading.CancellationToken> você deve <xref:System.OperationCanceledException>informar plinq sobre o externo e jogar um (externalCT).</span><span class="sxs-lookup"><span data-stu-id="dca6c-117">If you perform user-delegate cancellation, you should inform PLINQ about the external <xref:System.Threading.CancellationToken> and throw an <xref:System.OperationCanceledException>(externalCT).</span></span>

2. <span data-ttu-id="dca6c-118">Se ocorrer cancelamento e nenhuma outra exceção <xref:System.OperationCanceledException> for <xref:System.AggregateException>lançada, então manuseie um em vez de um .</span><span class="sxs-lookup"><span data-stu-id="dca6c-118">If cancellation occurs and no other exceptions are thrown, then handle an <xref:System.OperationCanceledException> rather than an <xref:System.AggregateException>.</span></span>

## <a name="example"></a><span data-ttu-id="dca6c-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="dca6c-119">Example</span></span>

<span data-ttu-id="dca6c-120">O exemplo a seguir mostra como tratar o cancelamento quando você tem uma função que consome muitos recursos de computação no código do usuário.</span><span class="sxs-lookup"><span data-stu-id="dca6c-120">The following example shows how to handle cancellation when you have a computationally expensive function in user code.</span></span>

[!code-csharp[PLINQ#17](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#17)]
[!code-vb[PLINQ#17](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#17)]

<span data-ttu-id="dca6c-121">Quando você processa o cancelamento no código do usuário, não precisa usar <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> na definição da consulta.</span><span class="sxs-lookup"><span data-stu-id="dca6c-121">When you handle the cancellation in user code, you do not have to use <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> in the query definition.</span></span> <span data-ttu-id="dca6c-122">No entanto, recomendamos <xref:System.Linq.ParallelEnumerable.WithCancellation%2A>que <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> você use, porque não tem efeito no desempenho da consulta e permite que o cancelamento seja tratado pelas operadoras de consulta e pelo seu código de usuário.</span><span class="sxs-lookup"><span data-stu-id="dca6c-122">However, we recommended that you do use <xref:System.Linq.ParallelEnumerable.WithCancellation%2A>, because <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> has no effect on query performance and it enables the cancellation to be handled by query operators and your user code.</span></span>

<span data-ttu-id="dca6c-123">Para garantir a capacidade de resposta do sistema, recomendamos que você verifique o cancelamento uma vez a cada milissegundo; no entanto, qualquer período de até 10 milissegundos é considerado aceitável.</span><span class="sxs-lookup"><span data-stu-id="dca6c-123">In order to ensure system responsiveness, we recommend that you check for cancellation around once per millisecond; however, any period up to 10 milliseconds is considered acceptable.</span></span> <span data-ttu-id="dca6c-124">Essa frequência não deve ter um impacto negativo no desempenho do seu código.</span><span class="sxs-lookup"><span data-stu-id="dca6c-124">This frequency should not have a negative impact on your code's performance.</span></span>

<span data-ttu-id="dca6c-125">Quando um enumerador é eliminado, por exemplo, quando o código sai de um loop foreach (For Each in Visual Basic) que está iterando sobre os resultados da consulta, então a consulta é cancelada, mas nenhuma exceção é lançada.</span><span class="sxs-lookup"><span data-stu-id="dca6c-125">When an enumerator is disposed, for example when code breaks out of a foreach (For Each in Visual Basic) loop that is iterating over query results, then the query is canceled, but no exception is thrown.</span></span>

## <a name="see-also"></a><span data-ttu-id="dca6c-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="dca6c-126">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>
- [<span data-ttu-id="dca6c-127">PLINQ (LINQ paralelo)</span><span class="sxs-lookup"><span data-stu-id="dca6c-127">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
- [<span data-ttu-id="dca6c-128">Cancelamento em threads gerenciados</span><span class="sxs-lookup"><span data-stu-id="dca6c-128">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)
