---
title: Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished
ms.date: 03/30/2017
ms.assetid: 54b677f7-03ad-40f2-9c5d-297a8ad9bf90
ms.openlocfilehash: 7f37cb5d9ee3d2d9d56519f785388f278b3333b9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59170716"
---
# <a name="microsofttransactionstransactionbridgeparticipantstatemachinefinished"></a><span data-ttu-id="e5a28-102">Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished</span><span class="sxs-lookup"><span data-stu-id="e5a28-102">Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished</span></span>
<span data-ttu-id="e5a28-103">A máquina de estado para uma inscrição de participante entrou no estado concluído.</span><span class="sxs-lookup"><span data-stu-id="e5a28-103">The state machine for a participant enlistment entered the finished state.</span></span>  
  
## <a name="description"></a><span data-ttu-id="e5a28-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="e5a28-104">Description</span></span>  
 <span data-ttu-id="e5a28-105">Rastreada quando uma inscrição de participante subordinada concluiu o processamento de 2pc.</span><span class="sxs-lookup"><span data-stu-id="e5a28-105">Traced when a subordinate participant enlistment has completed 2pc processing.</span></span> <span data-ttu-id="e5a28-106">O resultado para a inscrição pode ser confirmadas ou anuladas.</span><span class="sxs-lookup"><span data-stu-id="e5a28-106">The outcome for the enlistment can be Committed or Aborted.</span></span> <span data-ttu-id="e5a28-107">Ele também é rastreado se qualquer participante votos somente leitura durante a preparação.</span><span class="sxs-lookup"><span data-stu-id="e5a28-107">It is also traced if any participant votes ReadOnly during Prepare.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5a28-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e5a28-108">See also</span></span>

- [<span data-ttu-id="e5a28-109">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="e5a28-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="e5a28-110">Usando o rastreamento para solucionar problemas do seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="e5a28-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="e5a28-111">Administração e diagnósticos</span><span class="sxs-lookup"><span data-stu-id="e5a28-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
