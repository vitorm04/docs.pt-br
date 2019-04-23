---
title: System.ServiceModel.TxFailedToNegotiateOleTx
ms.date: 03/30/2017
ms.assetid: 3f0f0b4b-a1ad-4704-8329-455daf54892d
ms.openlocfilehash: 2de1aa51d58d9d86f953e027fd3f7f172e3887d3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59097558"
---
# <a name="systemservicemodeltxfailedtonegotiateoletx"></a><span data-ttu-id="0f994-102">System.ServiceModel.TxFailedToNegotiateOleTx</span><span class="sxs-lookup"><span data-stu-id="0f994-102">System.ServiceModel.TxFailedToNegotiateOleTx</span></span>
<span data-ttu-id="0f994-103">A negociação de protocolo OleTransactions falhou na conclusão para o contexto de coordenação especificado.</span><span class="sxs-lookup"><span data-stu-id="0f994-103">The OleTransactions protocol negotiation failed to complete for the specified coordination context.</span></span>  
  
## <a name="description"></a><span data-ttu-id="0f994-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="0f994-104">Description</span></span>  
 <span data-ttu-id="0f994-105">Rastreada quando uma transação de entrada com as informações de OleTx não pode usar as informações de OleTx anexadas e será retorno usando WS-AT em vez disso.</span><span class="sxs-lookup"><span data-stu-id="0f994-105">Traced when an incoming transaction with OleTx information is unable to use the attached OleTx information, and will fall-back to using WS-AT instead.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="0f994-106">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="0f994-106">Troubleshooting</span></span>  
 <span data-ttu-id="0f994-107">Indica um possível problema com a comunicação de RPC MSDTC entre as máquinas.</span><span class="sxs-lookup"><span data-stu-id="0f994-107">Indicates a potential problem with MSDTC RPC communication between the machines.</span></span> <span data-ttu-id="0f994-108">Se muitos desses rastreamentos aparecem no log, uma queda drástica no desempenho pode resultar.</span><span class="sxs-lookup"><span data-stu-id="0f994-108">If many of these traces appear in the log, a drastic decrease in performance can result.</span></span>  <span data-ttu-id="0f994-109">Se OleTx não for desejado, defina `OleTxUpgradeEnabled` como 0 na configuração do registro WS-AT.</span><span class="sxs-lookup"><span data-stu-id="0f994-109">If OleTx is not desired, set `OleTxUpgradeEnabled` to 0 in the WS-AT registry configuration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f994-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0f994-110">See also</span></span>

- [<span data-ttu-id="0f994-111">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="0f994-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="0f994-112">Usando o rastreamento para solucionar problemas do seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="0f994-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="0f994-113">Administração e diagnósticos</span><span class="sxs-lookup"><span data-stu-id="0f994-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
