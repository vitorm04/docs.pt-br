---
title: Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished
ms.date: 03/30/2017
ms.assetid: 54b677f7-03ad-40f2-9c5d-297a8ad9bf90
ms.openlocfilehash: 85b8cc4e5044cc7c87ea784e09c160cc527dddaa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33473526"
---
# <a name="microsofttransactionstransactionbridgeparticipantstatemachinefinished"></a><span data-ttu-id="2cb28-102">Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished</span><span class="sxs-lookup"><span data-stu-id="2cb28-102">Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished</span></span>
<span data-ttu-id="2cb28-103">A máquina de estado para uma inscrição de participante entrou no estado terminado.</span><span class="sxs-lookup"><span data-stu-id="2cb28-103">The state machine for a participant enlistment entered the finished state.</span></span>  
  
## <a name="description"></a><span data-ttu-id="2cb28-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="2cb28-104">Description</span></span>  
 <span data-ttu-id="2cb28-105">Rastreada quando uma inscrição de participante subordinada concluiu o processamento 2pc.</span><span class="sxs-lookup"><span data-stu-id="2cb28-105">Traced when a subordinate participant enlistment has completed 2pc processing.</span></span> <span data-ttu-id="2cb28-106">O resultado para a inscrição pode ser confirmadas ou anuladas.</span><span class="sxs-lookup"><span data-stu-id="2cb28-106">The outcome for the enlistment can be Committed or Aborted.</span></span> <span data-ttu-id="2cb28-107">Se qualquer participante votos somente leitura durante a preparação também são rastreados.</span><span class="sxs-lookup"><span data-stu-id="2cb28-107">It is also traced if any participant votes ReadOnly during Prepare.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cb28-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2cb28-108">See Also</span></span>  
 [<span data-ttu-id="2cb28-109">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="2cb28-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="2cb28-110">Usando o rastreamento para solucionar problemas do seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="2cb28-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="2cb28-111">Administração e diagnósticos</span><span class="sxs-lookup"><span data-stu-id="2cb28-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
