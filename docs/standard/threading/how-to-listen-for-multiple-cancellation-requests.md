---
title: 'Tutorial: Como ouvir várias solicitações de cancelamento'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation tokens, joining
- LinkedTokenSource, how to
ms.assetid: 6f4f3804-2ed7-41b4-a97a-6e32b93f6e05
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 17874b8b9733ea18d4877e2c79810fcd6247db0b
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57680224"
---
# <a name="how-to-listen-for-multiple-cancellation-requests"></a><span data-ttu-id="6d868-102">Tutorial: Como ouvir várias solicitações de cancelamento</span><span class="sxs-lookup"><span data-stu-id="6d868-102">How to: Listen for Multiple Cancellation Requests</span></span>
<span data-ttu-id="6d868-103">Este exemplo mostra como detectar dois tokens de cancelamento simultaneamente para que você possa cancelar uma operação se um dos tokens assim o solicitar.</span><span class="sxs-lookup"><span data-stu-id="6d868-103">This example shows how to listen to two cancellation tokens simultaneously so that you can cancel an operation if either token requests it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6d868-104">Se a opção "Apenas Meu Código" estiver habilitada, o Visual Studio em alguns casos interromperá na linha que lança a exceção e exibirá uma mensagem de erro que diz "exceção não tratada pelo código do usuário".</span><span class="sxs-lookup"><span data-stu-id="6d868-104">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="6d868-105">Esse erro é benigno.</span><span class="sxs-lookup"><span data-stu-id="6d868-105">This error is benign.</span></span> <span data-ttu-id="6d868-106">Você pode pressionar F5 para continuar a partir daí e ver o comportamento de tratamento de exceção, demonstrado nos exemplos a seguir.</span><span class="sxs-lookup"><span data-stu-id="6d868-106">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="6d868-107">Para impedir que o Visual Studio seja interrompido no primeiro erro, basta desmarcar a caixa de seleção "Apenas Meu Código" em **Ferramentas, Opções, Depuração, Geral**.</span><span class="sxs-lookup"><span data-stu-id="6d868-107">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d868-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6d868-108">Example</span></span>  
 <span data-ttu-id="6d868-109">No exemplo a seguir, o método <xref:System.Threading.CancellationTokenSource.CreateLinkedTokenSource%2A> é usado para juntar dois tokens em um token.</span><span class="sxs-lookup"><span data-stu-id="6d868-109">In the following example, the <xref:System.Threading.CancellationTokenSource.CreateLinkedTokenSource%2A> method is used to join two tokens into one token.</span></span> <span data-ttu-id="6d868-110">Isso permite que o token seja passado para métodos que levam apenas um token de cancelamento como argumento.</span><span class="sxs-lookup"><span data-stu-id="6d868-110">This enables the token to be passed to methods that take just one cancellation token as an argument.</span></span> <span data-ttu-id="6d868-111">O exemplo demonstra um cenário comum em que um método deve observar um token passado de fora da classe e um token gerado dentro da classe.</span><span class="sxs-lookup"><span data-stu-id="6d868-111">The example demonstrates a common scenario in which a method must observe both a token passed in from outside the class, and a token generated inside the class.</span></span>  
  
 [!code-csharp[Cancellation#13](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex13.cs#13)]
 [!code-vb[Cancellation#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex13.vb#13)]  
  
 <span data-ttu-id="6d868-112">Quando o token vinculado lança um <xref:System.OperationCanceledException>, o token que é passado para a exceção é o token vinculado, não qualquer um dos tokens anteriores.</span><span class="sxs-lookup"><span data-stu-id="6d868-112">When the linked token throws an <xref:System.OperationCanceledException>, the token that is passed to the exception is the linked token, not either of the predecessor tokens.</span></span> <span data-ttu-id="6d868-113">Para determinar qual dos tokens foi cancelado, verifique o status dos tokens anteriores diretamente.</span><span class="sxs-lookup"><span data-stu-id="6d868-113">To determine which of the tokens was canceled, check the status of the predecessor tokens directly.</span></span>  
  
 <span data-ttu-id="6d868-114">Neste exemplo, <xref:System.AggregateException> nunca deverá ser lançado, mas é capturado aqui porque em cenários do mundo real todas as outras exceções além de <xref:System.OperationCanceledException> que são lançadas pelo delegado da tarefa são encapsuladas em um <xref:System.AggregateException>.</span><span class="sxs-lookup"><span data-stu-id="6d868-114">In this example, <xref:System.AggregateException> should never be thrown, but it is caught here because in real-world scenarios any other exceptions besides <xref:System.OperationCanceledException> that are thrown from the task delegate are wrapped in a <xref:System.AggregateException>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d868-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6d868-115">See also</span></span>

- [<span data-ttu-id="6d868-116">Cancelamento em threads gerenciados</span><span class="sxs-lookup"><span data-stu-id="6d868-116">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)
