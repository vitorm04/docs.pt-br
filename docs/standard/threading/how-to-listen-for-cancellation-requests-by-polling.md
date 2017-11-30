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
helpviewer_keywords: cancellation, how to poll for requests
ms.assetid: c7f2f022-d08e-4e00-b4eb-ae84844cb1bc
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3f0e05e3f66d591a28d7e84d358934959764dab6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-listen-for-cancellation-requests-by-polling"></a><span data-ttu-id="8bc97-102">Como ouvir solicitações de cancelamento por meio de sondagem</span><span class="sxs-lookup"><span data-stu-id="8bc97-102">How to: Listen for Cancellation Requests by Polling</span></span>
<span data-ttu-id="8bc97-103">O exemplo a seguir mostra uma maneira que o código do usuário pode sondar um token de cancelamento em intervalos regulares para ver se cancelamento foi solicitado o thread de chamada.</span><span class="sxs-lookup"><span data-stu-id="8bc97-103">The following example shows one way that user code can poll a cancellation token at regular intervals to see whether cancellation has been requested from the calling thread.</span></span> <span data-ttu-id="8bc97-104">Este exemplo usa o <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> tipo, mas o mesmo padrão aplica-se a operações assíncronas criadas diretamente pelo <xref:System.Threading.ThreadPool?displayProperty=nameWithType> tipo ou o <xref:System.Threading.Thread?displayProperty=nameWithType> tipo.</span><span class="sxs-lookup"><span data-stu-id="8bc97-104">This example uses the <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> type, but the same pattern applies to asynchronous operations created directly by the <xref:System.Threading.ThreadPool?displayProperty=nameWithType> type or the <xref:System.Threading.Thread?displayProperty=nameWithType> type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8bc97-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8bc97-105">Example</span></span>  
 <span data-ttu-id="8bc97-106">Sondagem requer algum tipo de código de loop ou recursiva que periodicamente pode ler o valor de booliano <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="8bc97-106">Polling requires some kind of loop or recursive code that can periodically read the value of the Boolean <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> property.</span></span> <span data-ttu-id="8bc97-107">Se você estiver usando o <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> tipo e estão aguardando a conclusão no thread de chamada da tarefa, você pode usar o <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> método para verificar a propriedade e lançar a exceção.</span><span class="sxs-lookup"><span data-stu-id="8bc97-107">If you are using the <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> type and you are waiting for the task to complete on the calling thread, you can use the <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> method to check the property and throw the exception.</span></span> <span data-ttu-id="8bc97-108">Usando esse método, você garantir que a exceção correta é gerada em resposta a uma solicitação.</span><span class="sxs-lookup"><span data-stu-id="8bc97-108">By using this method, you ensure that the correct exception is thrown in response to a request.</span></span> <span data-ttu-id="8bc97-109">Se você estiver usando um <xref:System.Threading.Tasks.Task>, e em seguida, chamar este método é melhor do que gerar manualmente um <xref:System.OperationCanceledException>.</span><span class="sxs-lookup"><span data-stu-id="8bc97-109">If you are using a <xref:System.Threading.Tasks.Task>, then calling this method is better than manually throwing an <xref:System.OperationCanceledException>.</span></span> <span data-ttu-id="8bc97-110">Se você não tiver lançar a exceção, basta verificar a propriedade e se a propriedade de retorno do método `true`.</span><span class="sxs-lookup"><span data-stu-id="8bc97-110">If you do not have to throw the exception, then you can just check the property and return from the method if the property is `true`.</span></span>  
  
 [!code-csharp[Cancellation#11](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex11.cs#11)]
 [!code-vb[Cancellation#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex11.vb#11)]  
  
 <span data-ttu-id="8bc97-111">Chamando <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> é extremamente rápido e não apresenta uma sobrecarga significativa em loops.</span><span class="sxs-lookup"><span data-stu-id="8bc97-111">Calling <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> is extremely fast and does not introduce significant overhead in loops.</span></span>  
  
 <span data-ttu-id="8bc97-112">Se você estiver chamando <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A>, você só precisa verificar explicitamente o <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> propriedade se você tiver outro trabalho em resposta ao cancelamento além lançando a exceção.</span><span class="sxs-lookup"><span data-stu-id="8bc97-112">If you are calling <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A>, you only have to explicitly check the <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> property if you have other work to do in response to the cancellation besides throwing the exception.</span></span> <span data-ttu-id="8bc97-113">Neste exemplo, você pode ver que o código realmente acessa a propriedade duas vezes: uma vez no acesso explícito e novamente no <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> método.</span><span class="sxs-lookup"><span data-stu-id="8bc97-113">In this example, you can see that the code actually accesses the property twice: once in the explicit access and again in the <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> method.</span></span> <span data-ttu-id="8bc97-114">Mas, como o ato de leitura de <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> propriedade envolve volátil apenas uma instrução por acesso de leitura, o acesso duplo não é significativo de uma perspectiva de desempenho.</span><span class="sxs-lookup"><span data-stu-id="8bc97-114">But because the act of reading the <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> property involves only one volatile read instruction per access, the double access is not significant from a performance perspective.</span></span> <span data-ttu-id="8bc97-115">Ainda é melhor para chamar o método em vez de lançar manualmente a <xref:System.OperationCanceledException>.</span><span class="sxs-lookup"><span data-stu-id="8bc97-115">It is still preferable to call the method rather than manually throw the <xref:System.OperationCanceledException>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bc97-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8bc97-116">See Also</span></span>  
 [<span data-ttu-id="8bc97-117">Cancelamento em threads gerenciados</span><span class="sxs-lookup"><span data-stu-id="8bc97-117">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)
