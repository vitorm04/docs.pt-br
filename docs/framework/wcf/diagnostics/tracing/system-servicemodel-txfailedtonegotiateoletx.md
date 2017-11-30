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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 61360eff4f2c403eea98bbc0a2eae36e516b3d7a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodeltxfailedtonegotiateoletx"></a><span data-ttu-id="e19ab-102">System.ServiceModel.TxFailedToNegotiateOleTx</span><span class="sxs-lookup"><span data-stu-id="e19ab-102">System.ServiceModel.TxFailedToNegotiateOleTx</span></span>
<span data-ttu-id="e19ab-103">A negociação de protocolo OleTransactions não foi concluída para o contexto de coordenação especificado.</span><span class="sxs-lookup"><span data-stu-id="e19ab-103">The OleTransactions protocol negotiation failed to complete for the specified coordination context.</span></span>  
  
## <a name="description"></a><span data-ttu-id="e19ab-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="e19ab-104">Description</span></span>  
 <span data-ttu-id="e19ab-105">Rastreada quando uma transação de entrada com informações de OleTx não pode usar as informações de OleTx anexadas e será retorno usando o WS-AT em vez disso.</span><span class="sxs-lookup"><span data-stu-id="e19ab-105">Traced when an incoming transaction with OleTx information is unable to use the attached OleTx information, and will fall-back to using WS-AT instead.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="e19ab-106">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="e19ab-106">Troubleshooting</span></span>  
 <span data-ttu-id="e19ab-107">Indica um possível problema com a comunicação do MSDTC RPC entre os computadores.</span><span class="sxs-lookup"><span data-stu-id="e19ab-107">Indicates a potential problem with MSDTC RPC communication between the machines.</span></span> <span data-ttu-id="e19ab-108">Se muitos esses rastreamentos aparecem no log, pode resultar uma redução significativa no desempenho.</span><span class="sxs-lookup"><span data-stu-id="e19ab-108">If many of these traces appear in the log, a drastic decrease in performance can result.</span></span>  <span data-ttu-id="e19ab-109">Se OleTx não for desejada, defina `OleTxUpgradeEnabled` como 0 na configuração de registro do WS-AT.</span><span class="sxs-lookup"><span data-stu-id="e19ab-109">If OleTx is not desired, set `OleTxUpgradeEnabled` to 0 in the WS-AT registry configuration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e19ab-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e19ab-110">See Also</span></span>  
 [<span data-ttu-id="e19ab-111">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="e19ab-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="e19ab-112">Usando o rastreamento para solucionar problemas de seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="e19ab-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 <span data-ttu-id="e19ab-113">[Administration and Diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md) (Administração e diagnósticos)</span><span class="sxs-lookup"><span data-stu-id="e19ab-113">[Administration and Diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md)</span></span>
