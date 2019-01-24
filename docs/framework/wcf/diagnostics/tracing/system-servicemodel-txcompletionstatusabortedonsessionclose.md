---
title: System.ServiceModel.TxCompletionStatusAbortedOnSessionClose
ms.date: 03/30/2017
ms.assetid: 7e142e9d-e81b-4309-974a-02e9cc064ea0
ms.openlocfilehash: f41fd08138591a90b6173b5e4806e5ac73ff07da
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54662758"
---
# <a name="systemservicemodeltxcompletionstatusabortedonsessionclose"></a><span data-ttu-id="8d68d-102">System.ServiceModel.TxCompletionStatusAbortedOnSessionClose</span><span class="sxs-lookup"><span data-stu-id="8d68d-102">System.ServiceModel.TxCompletionStatusAbortedOnSessionClose</span></span>
<span data-ttu-id="8d68d-103">A transação especificada foi anulada porque estava incompleta quando a sessão foi fechada e TransactionAutoCompleteOnSessionClose OperationBehaviorAttribute foi definida como false.</span><span class="sxs-lookup"><span data-stu-id="8d68d-103">The specified transaction was aborted because it was uncompleted when the session was closed and the TransactionAutoCompleteOnSessionClose OperationBehaviorAttribute was set to false.</span></span>  
  
## <a name="description"></a><span data-ttu-id="8d68d-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="8d68d-104">Description</span></span>  
 <span data-ttu-id="8d68d-105">Rastreados se a sessão ativa atual foi fechada e a transação não foi concluída e TransactionAutoCompleteOnSessionClose é definida como `false`.</span><span class="sxs-lookup"><span data-stu-id="8d68d-105">Traced if the current active session was closed, and the transaction was not completed, and TransactionAutoCompleteOnSessionClose is set to `false`.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="8d68d-106">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="8d68d-106">Troubleshooting</span></span>  
 <span data-ttu-id="8d68d-107">Este rastreamento indica um bug potencial do aplicativo que deve ser investigado.</span><span class="sxs-lookup"><span data-stu-id="8d68d-107">This trace indicates a potential application bug that should be investigated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d68d-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8d68d-108">See also</span></span>
- [<span data-ttu-id="8d68d-109">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="8d68d-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="8d68d-110">Usando o rastreamento para solucionar problemas do seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="8d68d-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="8d68d-111">Administração e diagnósticos</span><span class="sxs-lookup"><span data-stu-id="8d68d-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
