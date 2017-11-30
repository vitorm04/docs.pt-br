---
title: "Como ouvir várias solicitações de cancelamento"
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
- cancellation tokens, joining
- LinkedTokenSource, how to
ms.assetid: 6f4f3804-2ed7-41b4-a97a-6e32b93f6e05
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 36cf338a15ad3f7d234f902c50a2dbb1b2e95847
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-listen-for-multiple-cancellation-requests"></a><span data-ttu-id="b274f-102">Como ouvir várias solicitações de cancelamento</span><span class="sxs-lookup"><span data-stu-id="b274f-102">How to: Listen for Multiple Cancellation Requests</span></span>
<span data-ttu-id="b274f-103">Este exemplo mostra como escutar dois tokens de cancelamento simultaneamente para que você pode cancelar uma operação, se o token solicitá-lo.</span><span class="sxs-lookup"><span data-stu-id="b274f-103">This example shows how to listen to two cancellation tokens simultaneously so that you can cancel an operation if either token requests it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b274f-104">Quando "Apenas meu código" estiver habilitado, o Visual Studio, em alguns casos quebrar a linha que lança a exceção e exibir uma mensagem de erro que diz "exceção não tratada pelo código do usuário".</span><span class="sxs-lookup"><span data-stu-id="b274f-104">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="b274f-105">Esse erro é benigno.</span><span class="sxs-lookup"><span data-stu-id="b274f-105">This error is benign.</span></span> <span data-ttu-id="b274f-106">Você pode pressionar F5 para continuar a partir dele e ver o comportamento de tratamento de exceção que é demonstrado nos exemplos a seguir.</span><span class="sxs-lookup"><span data-stu-id="b274f-106">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="b274f-107">Para impedir que o Visual Studio quebra no primeiro erro, simplesmente desmarque a caixa de seleção "Apenas meu código" em **ferramentas, opções, depuração, geral**.</span><span class="sxs-lookup"><span data-stu-id="b274f-107">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b274f-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b274f-108">Example</span></span>  
 <span data-ttu-id="b274f-109">No exemplo a seguir, o <xref:System.Threading.CancellationTokenSource.CreateLinkedTokenSource%2A> método é usado para unir dois tokens em um token.</span><span class="sxs-lookup"><span data-stu-id="b274f-109">In the following example, the <xref:System.Threading.CancellationTokenSource.CreateLinkedTokenSource%2A> method is used to join two tokens into one token.</span></span> <span data-ttu-id="b274f-110">Isso permite que o token a ser passado para métodos que usam o cancelamento apenas um token como um argumento.</span><span class="sxs-lookup"><span data-stu-id="b274f-110">This enables the token to be passed to methods that take just one cancellation token as an argument.</span></span> <span data-ttu-id="b274f-111">O exemplo demonstra um cenário comum em que um método deve observar os dois um token passado de fora da classe e um token gerado na classe.</span><span class="sxs-lookup"><span data-stu-id="b274f-111">The example demonstrates a common scenario in which a method must observe both a token passed in from outside the class, and a token generated inside the class.</span></span>  
  
 [!code-csharp[Cancellation#13](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex13.cs#13)]
 [!code-vb[Cancellation#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex13.vb#13)]  
  
 <span data-ttu-id="b274f-112">Quando o token vinculado gera um <xref:System.OperationCanceledException>, o token que é passado para a exceção é o token vinculado, não a qualquer um dos tokens predecessor.</span><span class="sxs-lookup"><span data-stu-id="b274f-112">When the linked token throws an <xref:System.OperationCanceledException>, the token that is passed to the exception is the linked token, not either of the predecessor tokens.</span></span> <span data-ttu-id="b274f-113">Para determinar qual dos tokens foi cancelada, verifique o status dos tokens predecessor diretamente.</span><span class="sxs-lookup"><span data-stu-id="b274f-113">To determine which of the tokens was canceled, check the status of the predecessor tokens directly.</span></span>  
  
 <span data-ttu-id="b274f-114">Neste exemplo, <xref:System.AggregateException> nunca deverá ser lançada, mas é capturado aqui porque em cenários do mundo real todas as outras exceções além <xref:System.OperationCanceledException> que são geradas pelo delegado tarefa são encapsuladas em um <xref:System.OperationCanceledException>.</span><span class="sxs-lookup"><span data-stu-id="b274f-114">In this example, <xref:System.AggregateException> should never be thrown, but it is caught here because in real-world scenarios any other exceptions besides <xref:System.OperationCanceledException> that are thrown from the task delegate are wrapped in a <xref:System.OperationCanceledException>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b274f-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b274f-115">See Also</span></span>  
 [<span data-ttu-id="b274f-116">Cancelamento em threads gerenciados</span><span class="sxs-lookup"><span data-stu-id="b274f-116">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)
