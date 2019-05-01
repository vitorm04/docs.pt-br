---
title: Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished
ms.date: 03/30/2017
ms.assetid: 54b677f7-03ad-40f2-9c5d-297a8ad9bf90
ms.openlocfilehash: 7f37cb5d9ee3d2d9d56519f785388f278b3333b9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61997874"
---
# <a name="microsofttransactionstransactionbridgeparticipantstatemachinefinished"></a><span data-ttu-id="bcd4f-102">Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished</span><span class="sxs-lookup"><span data-stu-id="bcd4f-102">Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished</span></span>
<span data-ttu-id="bcd4f-103">A máquina de estado para uma inscrição de participante entrou no estado concluído.</span><span class="sxs-lookup"><span data-stu-id="bcd4f-103">The state machine for a participant enlistment entered the finished state.</span></span>  
  
## <a name="description"></a><span data-ttu-id="bcd4f-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="bcd4f-104">Description</span></span>  
 <span data-ttu-id="bcd4f-105">Rastreada quando uma inscrição de participante subordinada concluiu o processamento de 2pc.</span><span class="sxs-lookup"><span data-stu-id="bcd4f-105">Traced when a subordinate participant enlistment has completed 2pc processing.</span></span> <span data-ttu-id="bcd4f-106">O resultado para a inscrição pode ser confirmadas ou anuladas.</span><span class="sxs-lookup"><span data-stu-id="bcd4f-106">The outcome for the enlistment can be Committed or Aborted.</span></span> <span data-ttu-id="bcd4f-107">Ele também é rastreado se qualquer participante votos somente leitura durante a preparação.</span><span class="sxs-lookup"><span data-stu-id="bcd4f-107">It is also traced if any participant votes ReadOnly during Prepare.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcd4f-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bcd4f-108">See also</span></span>

- [<span data-ttu-id="bcd4f-109">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="bcd4f-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="bcd4f-110">Usando o rastreamento para solucionar problemas do seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="bcd4f-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="bcd4f-111">Administração e diagnósticos</span><span class="sxs-lookup"><span data-stu-id="bcd4f-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
