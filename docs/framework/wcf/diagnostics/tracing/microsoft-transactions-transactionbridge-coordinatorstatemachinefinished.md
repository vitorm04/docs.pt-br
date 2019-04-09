---
title: Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished
ms.date: 03/30/2017
ms.assetid: 16cb428d-d886-4789-a961-6fded4b0dbba
ms.openlocfilehash: bffaed4976d82202eaea9ce50f6d389548fdabfd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59144815"
---
# <a name="microsofttransactionstransactionbridgecoordinatorstatemachinefinished"></a><span data-ttu-id="c7e83-102">Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished</span><span class="sxs-lookup"><span data-stu-id="c7e83-102">Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished</span></span>
<span data-ttu-id="c7e83-103">A máquina de estado para uma inscrição de coordenador entrou em estado concluído.</span><span class="sxs-lookup"><span data-stu-id="c7e83-103">The state machine for a coordinator enlistment has entered the finished state.</span></span>  
  
## <a name="description"></a><span data-ttu-id="c7e83-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="c7e83-104">Description</span></span>  
 <span data-ttu-id="c7e83-105">Rastreada quando o Gerenciador de transações local acredita que uma inscrição de coordenador superior concluiu o processamento de 2pc.</span><span class="sxs-lookup"><span data-stu-id="c7e83-105">Traced when the local Transaction Manager believes a superior coordinator enlistment has completed 2pc processing.</span></span> <span data-ttu-id="c7e83-106">O resultado para a inscrição pode ser confirmado ou Aborted ou esquecidos.</span><span class="sxs-lookup"><span data-stu-id="c7e83-106">The outcome for the enlistment can be Committed or Aborted or Forgotten.</span></span> <span data-ttu-id="c7e83-107">Se o Gerenciador de transações local votos somente leitura durante a preparação também são rastreados.</span><span class="sxs-lookup"><span data-stu-id="c7e83-107">It is also traced if the local Transaction Manager votes ReadOnly during Prepare.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7e83-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c7e83-108">See also</span></span>

- [<span data-ttu-id="c7e83-109">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="c7e83-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="c7e83-110">Utilizando o rastreamento para solucionar problemas em seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="c7e83-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="c7e83-111">Administração e diagnósticos</span><span class="sxs-lookup"><span data-stu-id="c7e83-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
