---
title: Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3e8fc825-9f22-47e7-9c16-d64ef291c932
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3b497231326c640b93b96500df39732104e0f0c8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="microsofttransactionstransactionbridgevolatileparticipantindoubt"></a><span data-ttu-id="7f46c-102">Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt</span><span class="sxs-lookup"><span data-stu-id="7f46c-102">Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt</span></span>
<span data-ttu-id="7f46c-103">O serviço de protocolo WS-AT recebeu uma mensagem preparada ou de repetição de um participante volátil não reconhecido.</span><span class="sxs-lookup"><span data-stu-id="7f46c-103">The WS-AT protocol service received a Prepared or Replay message from an unrecognized volatile participant.</span></span> <span data-ttu-id="7f46c-104">Foi retornada uma falha ao participante, declara que o resultado da transação em dúvida.</span><span class="sxs-lookup"><span data-stu-id="7f46c-104">A fault was returned to the participant, declares that the transaction's outcome is in doubt.</span></span>  
  
## <a name="description"></a><span data-ttu-id="7f46c-105">Descrição</span><span class="sxs-lookup"><span data-stu-id="7f46c-105">Description</span></span>  
 <span data-ttu-id="7f46c-106">Rastreada quando o Gerenciador de transações local recebe uma mensagem preparada ou de repetição de uma inscrição voláteis que ele já tiver esquecido.</span><span class="sxs-lookup"><span data-stu-id="7f46c-106">Traced when the local Transaction Manager receives a Prepared or Replay message from a Volatile enlistment that it has already forgotten.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="7f46c-107">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="7f46c-107">Troubleshooting</span></span>  
 <span data-ttu-id="7f46c-108">Investigue as causas possíveis recentes mensagens provenientes de um participante volátil.</span><span class="sxs-lookup"><span data-stu-id="7f46c-108">Investigate potential causes of late messages coming from the Volatile participant.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f46c-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7f46c-109">See Also</span></span>  
 [<span data-ttu-id="7f46c-110">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="7f46c-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="7f46c-111">Usando o rastreamento para solucionar problemas de seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="7f46c-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 <span data-ttu-id="7f46c-112">[Administration and Diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md) (Administração e diagnósticos)</span><span class="sxs-lookup"><span data-stu-id="7f46c-112">[Administration and Diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md)</span></span>
