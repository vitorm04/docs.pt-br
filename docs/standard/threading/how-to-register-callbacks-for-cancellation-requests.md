---
title: 'Como: registrar retornos de chamada para solicitações de cancelamento'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation, how to register callbacks
ms.assetid: 8838dd75-18ed-4b8b-b322-cd4531faac64
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 187d47f04761b85420f894c98d9495cd74c0c253
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913294"
---
# <a name="how-to-register-callbacks-for-cancellation-requests"></a><span data-ttu-id="96d34-102">Como: registrar retornos de chamada para solicitações de cancelamento</span><span class="sxs-lookup"><span data-stu-id="96d34-102">How to: Register Callbacks for Cancellation Requests</span></span>
<span data-ttu-id="96d34-103">O exemplo a seguir mostra como registrar um delegado que será invocado quando uma propriedade <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> tornar-se verdadeira, devido a uma chamada para <xref:System.Threading.CancellationTokenSource.Cancel%2A> no objeto que criou o token.</span><span class="sxs-lookup"><span data-stu-id="96d34-103">The following example shows how to register a delegate that will be invoked when a <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> property becomes true due to a call to <xref:System.Threading.CancellationTokenSource.Cancel%2A> on the object that created the token.</span></span> <span data-ttu-id="96d34-104">Use essa técnica para cancelar operações assíncronas que não dão suporte nativo à estrutura de cancelamento unificada e a métodos de desbloqueio que podem estar aguardando a conclusão de uma operação assíncrona.</span><span class="sxs-lookup"><span data-stu-id="96d34-104">Use this technique for cancelling asynchronous operations that do not natively support the unified cancellation framework, and for unblocking methods that might be waiting for an asynchronous operation to finish.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="96d34-105">Se a opção "Apenas Meu Código" estiver habilitada, o Visual Studio em alguns casos interromperá na linha que lança a exceção e exibirá uma mensagem de erro que diz "exceção não tratada pelo código do usuário".</span><span class="sxs-lookup"><span data-stu-id="96d34-105">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="96d34-106">Esse erro é benigno.</span><span class="sxs-lookup"><span data-stu-id="96d34-106">This error is benign.</span></span> <span data-ttu-id="96d34-107">Você pode pressionar F5 para continuar a partir daí e ver o comportamento de tratamento de exceção, demonstrado nos exemplos a seguir.</span><span class="sxs-lookup"><span data-stu-id="96d34-107">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="96d34-108">Para impedir que o Visual Studio seja interrompido no primeiro erro, basta desmarcar a caixa de seleção "Apenas Meu Código" em **Ferramentas, Opções, Depuração, Geral**.</span><span class="sxs-lookup"><span data-stu-id="96d34-108">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="96d34-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="96d34-109">Example</span></span>  
 <span data-ttu-id="96d34-110">No exemplo a seguir, o método <xref:System.Net.WebClient.CancelAsync%2A> é registrado como o método a ser invocado quando o cancelamento é solicitado por meio do token de cancelamento.</span><span class="sxs-lookup"><span data-stu-id="96d34-110">In the following example, the <xref:System.Net.WebClient.CancelAsync%2A> method is registered as the method to be invoked when cancellation is requested through the cancellation token.</span></span>  
  
 [!code-csharp[Conceptual.Cancellation.Callback#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.cancellation.callback/cs/howtoexample1.cs#1)]
 [!code-vb[Conceptual.Cancellation.Callback#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.cancellation.callback/vb/howtoexample1.vb#1)]  
  
 <span data-ttu-id="96d34-111">Se o cancelamento já tiver sido solicitado quando o retorno de chamada for registrado, ainda haverá garantia de chamada do retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="96d34-111">If cancellation has already been requested when the callback is registered, the callback is still guaranteed to be called.</span></span> <span data-ttu-id="96d34-112">Nesse caso específico, o método <xref:System.Net.WebClient.CancelAsync%2A> não fará nada se nenhuma operação assíncrona estiver em andamento, portanto, é seguro sempre chamar o método.</span><span class="sxs-lookup"><span data-stu-id="96d34-112">In this particular case, the <xref:System.Net.WebClient.CancelAsync%2A> method will do nothing if no asynchronous operation is in progress, so it is always safe to call the method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96d34-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="96d34-113">See also</span></span>

- [<span data-ttu-id="96d34-114">Cancelamento em threads gerenciados</span><span class="sxs-lookup"><span data-stu-id="96d34-114">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)
