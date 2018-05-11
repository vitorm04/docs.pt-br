---
title: Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished
ms.date: 03/30/2017
ms.assetid: 16cb428d-d886-4789-a961-6fded4b0dbba
ms.openlocfilehash: abb6a81d22da3a35c754c5d1485c5d612c9cd1e3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="microsofttransactionstransactionbridgecoordinatorstatemachinefinished"></a><span data-ttu-id="b2aac-102">Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished</span><span class="sxs-lookup"><span data-stu-id="b2aac-102">Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished</span></span>
<span data-ttu-id="b2aac-103">A máquina de estado para uma inscrição de coordenador entrou no estado terminado.</span><span class="sxs-lookup"><span data-stu-id="b2aac-103">The state machine for a coordinator enlistment has entered the finished state.</span></span>  
  
## <a name="description"></a><span data-ttu-id="b2aac-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="b2aac-104">Description</span></span>  
 <span data-ttu-id="b2aac-105">Rastreada quando o Gerenciador de transações local reconhece que uma inscrição de coordenador superior concluiu o processamento de 2pc.</span><span class="sxs-lookup"><span data-stu-id="b2aac-105">Traced when the local Transaction Manager believes a superior coordinator enlistment has completed 2pc processing.</span></span> <span data-ttu-id="b2aac-106">O resultado para a inscrição pode ser confirmado ou anulado ou Forgotten.</span><span class="sxs-lookup"><span data-stu-id="b2aac-106">The outcome for the enlistment can be Committed or Aborted or Forgotten.</span></span> <span data-ttu-id="b2aac-107">Se o Gerenciador de transações locais votos somente leitura durante a preparação também são rastreados.</span><span class="sxs-lookup"><span data-stu-id="b2aac-107">It is also traced if the local Transaction Manager votes ReadOnly during Prepare.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2aac-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b2aac-108">See Also</span></span>  
 [<span data-ttu-id="b2aac-109">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="b2aac-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="b2aac-110">Usando o rastreamento para solucionar problemas do seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="b2aac-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="b2aac-111">Administração e diagnósticos</span><span class="sxs-lookup"><span data-stu-id="b2aac-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
