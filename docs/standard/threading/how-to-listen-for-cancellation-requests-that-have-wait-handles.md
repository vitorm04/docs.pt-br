---
title: Como ouvir solicitações de cancelamento que têm identificadores de espera
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation, waiting with wait handles
ms.assetid: 6e2aa49b-fc84-4bcf-962b-17db98b7edcb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b1c8bfea5fc55bafbaa30d3b74edf60b674ef75c
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2018
ms.locfileid: "45624730"
---
# <a name="how-to-listen-for-cancellation-requests-that-have-wait-handles"></a><span data-ttu-id="ac7cb-102">Como ouvir solicitações de cancelamento que têm identificadores de espera</span><span class="sxs-lookup"><span data-stu-id="ac7cb-102">How to: Listen for Cancellation Requests That Have Wait Handles</span></span>
<span data-ttu-id="ac7cb-103">Se um método for bloqueado enquanto ele estiver aguardando que um evento seja sinalizado, ele não poderá verificar o valor do token de cancelamento e responder de maneira oportuna.</span><span class="sxs-lookup"><span data-stu-id="ac7cb-103">If a method is blocked while it is waiting for an event to be signaled, it cannot check the value of the cancellation token and respond in a timely manner.</span></span> <span data-ttu-id="ac7cb-104">O primeiro exemplo mostra como resolver esse problema quando você estiver trabalhando com eventos, como <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> que não dão suporte nativamente a estrutura de cancelamento unificado.</span><span class="sxs-lookup"><span data-stu-id="ac7cb-104">The first example shows how to solve this problem when you are working with events such as <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> that do not natively support the unified cancellation framework.</span></span> <span data-ttu-id="ac7cb-105">O segundo exemplo mostra uma abordagem mais simples que usa <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>, que dá suporte ao cancelamento unificado.</span><span class="sxs-lookup"><span data-stu-id="ac7cb-105">The second example shows a more streamlined approach that uses <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>, which does support unified cancellation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ac7cb-106">Se a opção "Apenas Meu Código" estiver habilitada, o Visual Studio em alguns casos interromperá na linha que lança a exceção e exibirá uma mensagem de erro que diz "exceção não tratada pelo código do usuário".</span><span class="sxs-lookup"><span data-stu-id="ac7cb-106">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="ac7cb-107">Esse erro é benigno.</span><span class="sxs-lookup"><span data-stu-id="ac7cb-107">This error is benign.</span></span> <span data-ttu-id="ac7cb-108">Você pode pressionar F5 para continuar a partir daí e ver o comportamento de tratamento de exceção, demonstrado nos exemplos a seguir.</span><span class="sxs-lookup"><span data-stu-id="ac7cb-108">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="ac7cb-109">Para impedir que o Visual Studio seja interrompido no primeiro erro, basta desmarcar a caixa de seleção "Apenas Meu Código" em **Ferramentas, Opções, Depuração, Geral**.</span><span class="sxs-lookup"><span data-stu-id="ac7cb-109">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac7cb-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ac7cb-110">Example</span></span>  
 <span data-ttu-id="ac7cb-111">O exemplo a seguir usa um <xref:System.Threading.ManualResetEvent> para demonstrar como desbloquear identificadores de espera que dão suporte ao cancelamento unificado.</span><span class="sxs-lookup"><span data-stu-id="ac7cb-111">The following example uses a <xref:System.Threading.ManualResetEvent> to demonstrate how to unblock wait handles that do not support unified cancellation.</span></span>  
  
 [!code-csharp[Cancellation#9](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex9.cs#9)]
 [!code-vb[Cancellation#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex9.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="ac7cb-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ac7cb-112">Example</span></span>  
 <span data-ttu-id="ac7cb-113">O exemplo a seguir usa um <xref:System.Threading.ManualResetEventSlim> para demonstrar como desbloquear primitivos de coordenação que dão suporte ao cancelamento unificado.</span><span class="sxs-lookup"><span data-stu-id="ac7cb-113">The following example uses a <xref:System.Threading.ManualResetEventSlim> to demonstrate how to unblock coordination primitives that do support unified cancellation.</span></span> <span data-ttu-id="ac7cb-114">A mesma abordagem pode ser usada com outros primitivos de coordenação leves, como <xref:System.Threading.Semaphore>`Slim` e <xref:System.Threading.CountdownEvent>.</span><span class="sxs-lookup"><span data-stu-id="ac7cb-114">The same approach can be used with other lightweight coordination primitives, such as <xref:System.Threading.Semaphore>`Slim` and <xref:System.Threading.CountdownEvent>.</span></span>  
  
 [!code-csharp[Cancellation#10](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex10.cs#10)]
 [!code-vb[Cancellation#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex10.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="ac7cb-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ac7cb-115">See also</span></span>

- [<span data-ttu-id="ac7cb-116">Cancelamento em threads gerenciados</span><span class="sxs-lookup"><span data-stu-id="ac7cb-116">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)
