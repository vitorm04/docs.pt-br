---
title: "Como ouvir solicitações de cancelamento por meio de sondagem"
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
- cancellation, how to poll for requests
ms.assetid: c7f2f022-d08e-4e00-b4eb-ae84844cb1bc
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 56a927e10cb026814302728a72acb2f32223b29b
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-listen-for-cancellation-requests-by-polling"></a><span data-ttu-id="716b6-102">Como ouvir solicitações de cancelamento por meio de sondagem</span><span class="sxs-lookup"><span data-stu-id="716b6-102">How to: Listen for Cancellation Requests by Polling</span></span>
<span data-ttu-id="716b6-103">O exemplo a seguir mostra uma maneira de o código do usuário sondar um token de cancelamento em intervalos regulares para verificar se o thread de chamada solicitou o cancelamento.</span><span class="sxs-lookup"><span data-stu-id="716b6-103">The following example shows one way that user code can poll a cancellation token at regular intervals to see whether cancellation has been requested from the calling thread.</span></span> <span data-ttu-id="716b6-104">Este exemplo usa o tipo <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>, mas o mesmo padrão se aplica a operações assíncronas criadas diretamente pelo tipo <xref:System.Threading.ThreadPool?displayProperty=nameWithType> ou <xref:System.Threading.Thread?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="716b6-104">This example uses the <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> type, but the same pattern applies to asynchronous operations created directly by the <xref:System.Threading.ThreadPool?displayProperty=nameWithType> type or the <xref:System.Threading.Thread?displayProperty=nameWithType> type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="716b6-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="716b6-105">Example</span></span>  
 <span data-ttu-id="716b6-106">A sondagem requer um tipo de código recursivo ou de loop que possa fazer a leitura periódica do valor da propriedade booliana <xref:System.Threading.CancellationToken.IsCancellationRequested%2A>.</span><span class="sxs-lookup"><span data-stu-id="716b6-106">Polling requires some kind of loop or recursive code that can periodically read the value of the Boolean <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> property.</span></span> <span data-ttu-id="716b6-107">Se estiver usando o tipo <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> e estiver aguardando a conclusão da tarefa no thread de chamada, use o método <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> para verificar a propriedade e lançar a exceção.</span><span class="sxs-lookup"><span data-stu-id="716b6-107">If you are using the <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> type and you are waiting for the task to complete on the calling thread, you can use the <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> method to check the property and throw the exception.</span></span> <span data-ttu-id="716b6-108">Ao usar esse método, a exceção correta será gerada em resposta a uma solicitação.</span><span class="sxs-lookup"><span data-stu-id="716b6-108">By using this method, you ensure that the correct exception is thrown in response to a request.</span></span> <span data-ttu-id="716b6-109">Se estiver usando um <xref:System.Threading.Tasks.Task>, chamar este método é melhor do que gerar manualmente uma <xref:System.OperationCanceledException>.</span><span class="sxs-lookup"><span data-stu-id="716b6-109">If you are using a <xref:System.Threading.Tasks.Task>, then calling this method is better than manually throwing an <xref:System.OperationCanceledException>.</span></span> <span data-ttu-id="716b6-110">Se não precisar lançar a exceção, bastará verificar a propriedade e obter um retorno do método se a propriedade for `true`.</span><span class="sxs-lookup"><span data-stu-id="716b6-110">If you do not have to throw the exception, then you can just check the property and return from the method if the property is `true`.</span></span>  
  
 [!code-csharp[Cancellation#11](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex11.cs#11)]
 [!code-vb[Cancellation#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex11.vb#11)]  
  
 <span data-ttu-id="716b6-111">Chamar <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> é extremamente rápido e não apresenta uma sobrecarga significativa em loops.</span><span class="sxs-lookup"><span data-stu-id="716b6-111">Calling <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> is extremely fast and does not introduce significant overhead in loops.</span></span>  
  
 <span data-ttu-id="716b6-112">Se estiver chamando <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A>, basta verificar explicitamente a propriedade <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> se você tiver outro trabalho a fazer em resposta ao cancelamento, além de lançar a exceção.</span><span class="sxs-lookup"><span data-stu-id="716b6-112">If you are calling <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A>, you only have to explicitly check the <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> property if you have other work to do in response to the cancellation besides throwing the exception.</span></span> <span data-ttu-id="716b6-113">Neste exemplo, vemos que o código realmente acessa a propriedade duas vezes: uma no acesso explícito e novamente no método <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A>.</span><span class="sxs-lookup"><span data-stu-id="716b6-113">In this example, you can see that the code actually accesses the property twice: once in the explicit access and again in the <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> method.</span></span> <span data-ttu-id="716b6-114">Mas, como o ato de leitura da propriedade <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> envolve apenas uma instrução volátil de leitura por acesso, o acesso duplo não é significativo do ponto de vista do desempenho.</span><span class="sxs-lookup"><span data-stu-id="716b6-114">But because the act of reading the <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> property involves only one volatile read instruction per access, the double access is not significant from a performance perspective.</span></span> <span data-ttu-id="716b6-115">Ainda assim é melhor chamar o método do que lançar manualmente a <xref:System.OperationCanceledException>.</span><span class="sxs-lookup"><span data-stu-id="716b6-115">It is still preferable to call the method rather than manually throw the <xref:System.OperationCanceledException>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="716b6-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="716b6-116">See Also</span></span>  
 [<span data-ttu-id="716b6-117">Cancelamento em threads gerenciados</span><span class="sxs-lookup"><span data-stu-id="716b6-117">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)
