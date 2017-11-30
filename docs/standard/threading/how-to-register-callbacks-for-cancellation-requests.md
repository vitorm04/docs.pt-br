---
title: "Como registrar retornos de chamada para solicitações de cancelamento"
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
helpviewer_keywords: cancellation, how to register callbacks
ms.assetid: 8838dd75-18ed-4b8b-b322-cd4531faac64
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 85b15ed610d80958ac9d7e3762ac8ea7b781b8d0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-register-callbacks-for-cancellation-requests"></a><span data-ttu-id="2b053-102">Como registrar retornos de chamada para solicitações de cancelamento</span><span class="sxs-lookup"><span data-stu-id="2b053-102">How to: Register Callbacks for Cancellation Requests</span></span>
<span data-ttu-id="2b053-103">O exemplo a seguir mostra como registrar um delegado que será invocado quando uma <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> propriedade torna-se verdadeiro devido a uma chamada para <xref:System.Threading.CancellationTokenSource.Cancel%2A> no objeto que criou o token.</span><span class="sxs-lookup"><span data-stu-id="2b053-103">The following example shows how to register a delegate that will be invoked when a <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> property becomes true due to a call to <xref:System.Threading.CancellationTokenSource.Cancel%2A> on the object that created the token.</span></span> <span data-ttu-id="2b053-104">Use essa técnica para cancelar operações assíncronas que não suportam nativamente o framework de cancelamento unificada e para métodos de desbloqueio que podem estar aguardando para uma operação assíncrona concluir.</span><span class="sxs-lookup"><span data-stu-id="2b053-104">Use this technique for cancelling asynchronous operations that do not natively support the unified cancellation framework, and for unblocking methods that might be waiting for an asynchronous operation to finish.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2b053-105">Quando "Apenas meu código" estiver habilitado, o Visual Studio, em alguns casos quebrar a linha que lança a exceção e exibir uma mensagem de erro que diz "exceção não tratada pelo código do usuário".</span><span class="sxs-lookup"><span data-stu-id="2b053-105">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="2b053-106">Esse erro é benigno.</span><span class="sxs-lookup"><span data-stu-id="2b053-106">This error is benign.</span></span> <span data-ttu-id="2b053-107">Você pode pressionar F5 para continuar a partir dele e ver o comportamento de tratamento de exceção que é demonstrado nos exemplos a seguir.</span><span class="sxs-lookup"><span data-stu-id="2b053-107">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="2b053-108">Para impedir que o Visual Studio quebra no primeiro erro, simplesmente desmarque a caixa de seleção "Apenas meu código" em **ferramentas, opções, depuração, geral**.</span><span class="sxs-lookup"><span data-stu-id="2b053-108">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b053-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2b053-109">Example</span></span>  
 <span data-ttu-id="2b053-110">No exemplo a seguir, o <xref:System.Net.WebClient.CancelAsync%2A> método é registrado como o método a ser invocado quando o cancelamento for solicitado por meio do token de cancelamento.</span><span class="sxs-lookup"><span data-stu-id="2b053-110">In the following example, the <xref:System.Net.WebClient.CancelAsync%2A> method is registered as the method to be invoked when cancellation is requested through the cancellation token.</span></span>  
  
 [!code-csharp[Conceptual.Cancellation.Callback#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.cancellation.callback/cs/howtoexample1.cs#1)]
 [!code-vb[Conceptual.Cancellation.Callback#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.cancellation.callback/vb/howtoexample1.vb#1)]  
  
 <span data-ttu-id="2b053-111">Se o cancelamento já foi solicitado quando o retorno de chamada for registrado, o retorno de chamada ainda é garantido para ser chamado.</span><span class="sxs-lookup"><span data-stu-id="2b053-111">If cancellation has already been requested when the callback is registered, the callback is still guaranteed to be called.</span></span> <span data-ttu-id="2b053-112">Nesse caso específico, o <xref:System.Net.WebClient.CancelAsync%2A> método não fará nada se nenhuma operação assíncrona está em andamento, portanto, é sempre seguro chamar o método.</span><span class="sxs-lookup"><span data-stu-id="2b053-112">In this particular case, the <xref:System.Net.WebClient.CancelAsync%2A> method will do nothing if no asynchronous operation is in progress, so it is always safe to call the method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b053-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2b053-113">See Also</span></span>  
 [<span data-ttu-id="2b053-114">Cancelamento em threads gerenciados</span><span class="sxs-lookup"><span data-stu-id="2b053-114">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)
