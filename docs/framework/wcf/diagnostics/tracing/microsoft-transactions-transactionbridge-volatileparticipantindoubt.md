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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0dbfd04ed20a92a2ecf827ef3d6aa4f378eb6a15
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="microsofttransactionstransactionbridgevolatileparticipantindoubt"></a><span data-ttu-id="985c5-102">Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt</span><span class="sxs-lookup"><span data-stu-id="985c5-102">Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt</span></span>
<span data-ttu-id="985c5-103">O serviço de protocolo WS-AT recebeu uma mensagem preparada ou de repetição de um participante volátil não reconhecido.</span><span class="sxs-lookup"><span data-stu-id="985c5-103">The WS-AT protocol service received a Prepared or Replay message from an unrecognized volatile participant.</span></span> <span data-ttu-id="985c5-104">Foi retornada uma falha ao participante, declara que o resultado da transação em dúvida.</span><span class="sxs-lookup"><span data-stu-id="985c5-104">A fault was returned to the participant, declares that the transaction's outcome is in doubt.</span></span>  
  
## <a name="description"></a><span data-ttu-id="985c5-105">Descrição</span><span class="sxs-lookup"><span data-stu-id="985c5-105">Description</span></span>  
 <span data-ttu-id="985c5-106">Rastreada quando o Gerenciador de transações local recebe uma mensagem preparada ou de repetição de uma inscrição voláteis que ele já tiver esquecido.</span><span class="sxs-lookup"><span data-stu-id="985c5-106">Traced when the local Transaction Manager receives a Prepared or Replay message from a Volatile enlistment that it has already forgotten.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="985c5-107">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="985c5-107">Troubleshooting</span></span>  
 <span data-ttu-id="985c5-108">Investigue as causas possíveis recentes mensagens provenientes de um participante volátil.</span><span class="sxs-lookup"><span data-stu-id="985c5-108">Investigate potential causes of late messages coming from the Volatile participant.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="985c5-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="985c5-109">See Also</span></span>  
 [<span data-ttu-id="985c5-110">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="985c5-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="985c5-111">Usando o rastreamento para solucionar problemas do seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="985c5-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="985c5-112">Administração e diagnósticos</span><span class="sxs-lookup"><span data-stu-id="985c5-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
