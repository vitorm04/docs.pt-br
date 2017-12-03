---
title: System.ServiceModel.TxFailedToNegotiateOleTx
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f0f0b4b-a1ad-4704-8329-455daf54892d
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6c0e688e1f24171494b4adaae964ac1fc2be2309
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="systemservicemodeltxfailedtonegotiateoletx"></a><span data-ttu-id="48886-102">System.ServiceModel.TxFailedToNegotiateOleTx</span><span class="sxs-lookup"><span data-stu-id="48886-102">System.ServiceModel.TxFailedToNegotiateOleTx</span></span>
<span data-ttu-id="48886-103">A negociação de protocolo OleTransactions não foi concluída para o contexto de coordenação especificado.</span><span class="sxs-lookup"><span data-stu-id="48886-103">The OleTransactions protocol negotiation failed to complete for the specified coordination context.</span></span>  
  
## <a name="description"></a><span data-ttu-id="48886-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="48886-104">Description</span></span>  
 <span data-ttu-id="48886-105">Rastreada quando uma transação de entrada com informações de OleTx não pode usar as informações de OleTx anexadas e será retorno usando o WS-AT em vez disso.</span><span class="sxs-lookup"><span data-stu-id="48886-105">Traced when an incoming transaction with OleTx information is unable to use the attached OleTx information, and will fall-back to using WS-AT instead.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="48886-106">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="48886-106">Troubleshooting</span></span>  
 <span data-ttu-id="48886-107">Indica um possível problema com a comunicação do MSDTC RPC entre os computadores.</span><span class="sxs-lookup"><span data-stu-id="48886-107">Indicates a potential problem with MSDTC RPC communication between the machines.</span></span> <span data-ttu-id="48886-108">Se muitos esses rastreamentos aparecem no log, pode resultar uma redução significativa no desempenho.</span><span class="sxs-lookup"><span data-stu-id="48886-108">If many of these traces appear in the log, a drastic decrease in performance can result.</span></span>  <span data-ttu-id="48886-109">Se OleTx não for desejada, defina `OleTxUpgradeEnabled` como 0 na configuração de registro do WS-AT.</span><span class="sxs-lookup"><span data-stu-id="48886-109">If OleTx is not desired, set `OleTxUpgradeEnabled` to 0 in the WS-AT registry configuration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48886-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="48886-110">See Also</span></span>  
 [<span data-ttu-id="48886-111">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="48886-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="48886-112">Usando o rastreamento para solucionar problemas de seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="48886-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 <span data-ttu-id="48886-113">[Administration and Diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md) (Administração e diagnósticos)</span><span class="sxs-lookup"><span data-stu-id="48886-113">[Administration and Diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md)</span></span>
