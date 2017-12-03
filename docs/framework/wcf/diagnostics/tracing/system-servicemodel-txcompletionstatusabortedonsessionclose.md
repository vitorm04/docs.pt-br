---
title: System.ServiceModel.TxCompletionStatusAbortedOnSessionClose
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7e142e9d-e81b-4309-974a-02e9cc064ea0
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 695ebb2089147093601f2d51f11f11ca45861590
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="systemservicemodeltxcompletionstatusabortedonsessionclose"></a><span data-ttu-id="c69f3-102">System.ServiceModel.TxCompletionStatusAbortedOnSessionClose</span><span class="sxs-lookup"><span data-stu-id="c69f3-102">System.ServiceModel.TxCompletionStatusAbortedOnSessionClose</span></span>
<span data-ttu-id="c69f3-103">A transação especificada foi anulada porque não estava concluída quando a sessão foi fechada e o TransactionAutoCompleteOnSessionClose OperationBehaviorAttribute foi definido como false.</span><span class="sxs-lookup"><span data-stu-id="c69f3-103">The specified transaction was aborted because it was uncompleted when the session was closed and the TransactionAutoCompleteOnSessionClose OperationBehaviorAttribute was set to false.</span></span>  
  
## <a name="description"></a><span data-ttu-id="c69f3-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="c69f3-104">Description</span></span>  
 <span data-ttu-id="c69f3-105">Rastreado se a sessão ativa atual foi fechada e a transação não foi concluída e TransactionAutoCompleteOnSessionClose é definido como `false`.</span><span class="sxs-lookup"><span data-stu-id="c69f3-105">Traced if the current active session was closed, and the transaction was not completed, and TransactionAutoCompleteOnSessionClose is set to `false`.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="c69f3-106">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="c69f3-106">Troubleshooting</span></span>  
 <span data-ttu-id="c69f3-107">Este rastreamento indica um bug potencial de aplicativo que deve ser investigado.</span><span class="sxs-lookup"><span data-stu-id="c69f3-107">This trace indicates a potential application bug that should be investigated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c69f3-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c69f3-108">See Also</span></span>  
 [<span data-ttu-id="c69f3-109">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="c69f3-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="c69f3-110">Usando o rastreamento para solucionar problemas de seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="c69f3-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 <span data-ttu-id="c69f3-111">[Administration and Diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md) (Administração e diagnósticos)</span><span class="sxs-lookup"><span data-stu-id="c69f3-111">[Administration and Diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md)</span></span>
