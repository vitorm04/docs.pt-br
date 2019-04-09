---
title: System.ServiceModel.TxCompletionStatusAbortedOnSessionClose
ms.date: 03/30/2017
ms.assetid: 7e142e9d-e81b-4309-974a-02e9cc064ea0
ms.openlocfilehash: 7b1f6a2f4a344b566c76d0095942b84a8a4e76f6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59166498"
---
# <a name="systemservicemodeltxcompletionstatusabortedonsessionclose"></a><span data-ttu-id="89b83-102">System.ServiceModel.TxCompletionStatusAbortedOnSessionClose</span><span class="sxs-lookup"><span data-stu-id="89b83-102">System.ServiceModel.TxCompletionStatusAbortedOnSessionClose</span></span>
<span data-ttu-id="89b83-103">A transação especificada foi anulada porque estava incompleta quando a sessão foi fechada e TransactionAutoCompleteOnSessionClose OperationBehaviorAttribute foi definida como false.</span><span class="sxs-lookup"><span data-stu-id="89b83-103">The specified transaction was aborted because it was uncompleted when the session was closed and the TransactionAutoCompleteOnSessionClose OperationBehaviorAttribute was set to false.</span></span>  
  
## <a name="description"></a><span data-ttu-id="89b83-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="89b83-104">Description</span></span>  
 <span data-ttu-id="89b83-105">Rastreados se a sessão ativa atual foi fechada e a transação não foi concluída e TransactionAutoCompleteOnSessionClose é definida como `false`.</span><span class="sxs-lookup"><span data-stu-id="89b83-105">Traced if the current active session was closed, and the transaction was not completed, and TransactionAutoCompleteOnSessionClose is set to `false`.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="89b83-106">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="89b83-106">Troubleshooting</span></span>  
 <span data-ttu-id="89b83-107">Este rastreamento indica um bug potencial do aplicativo que deve ser investigado.</span><span class="sxs-lookup"><span data-stu-id="89b83-107">This trace indicates a potential application bug that should be investigated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89b83-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="89b83-108">See also</span></span>

- [<span data-ttu-id="89b83-109">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="89b83-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="89b83-110">Utilizando o rastreamento para solucionar problemas em seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="89b83-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="89b83-111">Administração e diagnósticos</span><span class="sxs-lookup"><span data-stu-id="89b83-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
