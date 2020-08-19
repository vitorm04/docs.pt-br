---
title: Registrar retornos de chamada para solicitações de cancelamento
ms.date: 08/14/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation, how to register callbacks
ms.assetid: 8838dd75-18ed-4b8b-b322-cd4531faac64
ms.openlocfilehash: faa8dada5779f6eaee7a60e6210ec604f5fb4680
ms.sourcegitcommit: cbb19e56d48cf88375d35d0c27554d4722761e0d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2020
ms.locfileid: "88608449"
---
# <a name="register-callbacks-for-cancellation-requests"></a><span data-ttu-id="48271-102">Registrar retornos de chamada para solicitações de cancelamento</span><span class="sxs-lookup"><span data-stu-id="48271-102">Register callbacks for cancellation requests</span></span>

<span data-ttu-id="48271-103">Saiba como registrar um delegado que será invocado quando uma <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> propriedade se tornar verdadeira.</span><span class="sxs-lookup"><span data-stu-id="48271-103">Learn how to register a delegate that will be invoked when a <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> property becomes true.</span></span> <span data-ttu-id="48271-104">O valor muda de false para true quando uma chamada para <xref:System.Threading.CancellationTokenSource.Cancel%2A> no objeto que criou o token é feita.</span><span class="sxs-lookup"><span data-stu-id="48271-104">The value changes from false to true when a call to <xref:System.Threading.CancellationTokenSource.Cancel%2A> on the object that created the token is made.</span></span> <span data-ttu-id="48271-105">Use essa técnica para cancelar operações assíncronas que não dão suporte nativo à estrutura de cancelamento unificada e para métodos de desbloqueio que podem estar aguardando a conclusão de uma operação assíncrona.</span><span class="sxs-lookup"><span data-stu-id="48271-105">Use this technique for canceling asynchronous operations that do not natively support the unified cancellation framework, and for unblocking methods that might be waiting for an asynchronous operation to finish.</span></span>

> [!NOTE]
> <span data-ttu-id="48271-106">Se a opção "Apenas Meu Código" estiver habilitada, o Visual Studio em alguns casos interromperá na linha que lança a exceção e exibirá uma mensagem de erro que diz "exceção não tratada pelo código do usuário".</span><span class="sxs-lookup"><span data-stu-id="48271-106">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="48271-107">Esse erro é benigno.</span><span class="sxs-lookup"><span data-stu-id="48271-107">This error is benign.</span></span> <span data-ttu-id="48271-108">Você pode pressionar <kbd>F5</kbd> para continuar a partir dele e ver o comportamento de tratamento de exceção que é demonstrado nos exemplos abaixo.</span><span class="sxs-lookup"><span data-stu-id="48271-108">You can press <kbd>F5</kbd> to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="48271-109">Para impedir que o Visual Studio seja interrompido no primeiro erro, basta desmarcar a caixa de seleção "Apenas Meu Código" em **Ferramentas, Opções, Depuração, Geral**.</span><span class="sxs-lookup"><span data-stu-id="48271-109">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>

## <a name="example"></a><span data-ttu-id="48271-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="48271-110">Example</span></span>

<span data-ttu-id="48271-111">No exemplo a seguir, o método <xref:System.Net.WebClient.CancelAsync%2A> é registrado como o método a ser invocado quando o cancelamento é solicitado por meio do token de cancelamento.</span><span class="sxs-lookup"><span data-stu-id="48271-111">In the following example, the <xref:System.Net.WebClient.CancelAsync%2A> method is registered as the method to be invoked when cancellation is requested through the cancellation token.</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.cancellation.callback/cs/howtoexample1.cs":::
:::code language="vb" source="../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.cancellation.callback/vb/howtoexample1.vb":::

<span data-ttu-id="48271-112">Se o cancelamento já tiver sido solicitado quando o retorno de chamada for registrado, ainda haverá garantia de chamada do retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="48271-112">If cancellation has already been requested when the callback is registered, the callback is still guaranteed to be called.</span></span> <span data-ttu-id="48271-113">Nesse caso específico, o método <xref:System.Net.WebClient.CancelAsync%2A> não fará nada se nenhuma operação assíncrona estiver em andamento, portanto, é seguro sempre chamar o método.</span><span class="sxs-lookup"><span data-stu-id="48271-113">In this particular case, the <xref:System.Net.WebClient.CancelAsync%2A> method will do nothing if no asynchronous operation is in progress, so it is always safe to call the method.</span></span>

## <a name="see-also"></a><span data-ttu-id="48271-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="48271-114">See also</span></span>

- [<span data-ttu-id="48271-115">Cancelamento em threads gerenciados</span><span class="sxs-lookup"><span data-stu-id="48271-115">Cancellation in managed threads</span></span>](cancellation-in-managed-threads.md)
- <xref:System.Net.WebClient.DownloadStringTaskAsync(System.String)?displayProperty=nameWithType>
