---
title: System.ServiceModel.TxCompletionStatusAbortedOnSessionClose
ms.date: 03/30/2017
ms.assetid: 7e142e9d-e81b-4309-974a-02e9cc064ea0
ms.openlocfilehash: 7ecc70f1c4d7184401dd29908968f628f2e6792a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33484208"
---
# <a name="systemservicemodeltxcompletionstatusabortedonsessionclose"></a><span data-ttu-id="4cf48-102">System.ServiceModel.TxCompletionStatusAbortedOnSessionClose</span><span class="sxs-lookup"><span data-stu-id="4cf48-102">System.ServiceModel.TxCompletionStatusAbortedOnSessionClose</span></span>
<span data-ttu-id="4cf48-103">A transação especificada foi anulada porque não estava concluída quando a sessão foi fechada e o TransactionAutoCompleteOnSessionClose OperationBehaviorAttribute foi definido como false.</span><span class="sxs-lookup"><span data-stu-id="4cf48-103">The specified transaction was aborted because it was uncompleted when the session was closed and the TransactionAutoCompleteOnSessionClose OperationBehaviorAttribute was set to false.</span></span>  
  
## <a name="description"></a><span data-ttu-id="4cf48-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="4cf48-104">Description</span></span>  
 <span data-ttu-id="4cf48-105">Rastreado se a sessão ativa atual foi fechada e a transação não foi concluída e TransactionAutoCompleteOnSessionClose é definido como `false`.</span><span class="sxs-lookup"><span data-stu-id="4cf48-105">Traced if the current active session was closed, and the transaction was not completed, and TransactionAutoCompleteOnSessionClose is set to `false`.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="4cf48-106">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="4cf48-106">Troubleshooting</span></span>  
 <span data-ttu-id="4cf48-107">Este rastreamento indica um bug potencial de aplicativo que deve ser investigado.</span><span class="sxs-lookup"><span data-stu-id="4cf48-107">This trace indicates a potential application bug that should be investigated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cf48-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4cf48-108">See Also</span></span>  
 [<span data-ttu-id="4cf48-109">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="4cf48-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="4cf48-110">Usando o rastreamento para solucionar problemas do seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="4cf48-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="4cf48-111">Administração e diagnósticos</span><span class="sxs-lookup"><span data-stu-id="4cf48-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
