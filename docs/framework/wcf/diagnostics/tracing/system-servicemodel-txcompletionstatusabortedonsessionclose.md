---
title: System.ServiceModel.TxCompletionStatusAbortedOnSessionClose
ms.date: 03/30/2017
ms.assetid: 7e142e9d-e81b-4309-974a-02e9cc064ea0
ms.openlocfilehash: c398fc52d5924c033500b95924f9287b43cc9e9d
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84576597"
---
# <a name="systemservicemodeltxcompletionstatusabortedonsessionclose"></a><span data-ttu-id="d1826-102">System.ServiceModel.TxCompletionStatusAbortedOnSessionClose</span><span class="sxs-lookup"><span data-stu-id="d1826-102">System.ServiceModel.TxCompletionStatusAbortedOnSessionClose</span></span>
<span data-ttu-id="d1826-103">A transação especificada foi anulada porque estava incompleta quando a sessão foi fechada e o TransactionAutoCompleteOnSessionClose OperationBehaviorAttribute foi definido como falso.</span><span class="sxs-lookup"><span data-stu-id="d1826-103">The specified transaction was aborted because it was uncompleted when the session was closed and the TransactionAutoCompleteOnSessionClose OperationBehaviorAttribute was set to false.</span></span>  
  
## <a name="description"></a><span data-ttu-id="d1826-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="d1826-104">Description</span></span>  
 <span data-ttu-id="d1826-105">Rastreado se a sessão ativa atual foi fechada e a transação não foi concluída e a TransactionAutoCompleteOnSessionClose está definida como `false` .</span><span class="sxs-lookup"><span data-stu-id="d1826-105">Traced if the current active session was closed, and the transaction was not completed, and TransactionAutoCompleteOnSessionClose is set to `false`.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="d1826-106">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="d1826-106">Troubleshooting</span></span>  
 <span data-ttu-id="d1826-107">Esse rastreamento indica um possível bug de aplicativo que deve ser investigado.</span><span class="sxs-lookup"><span data-stu-id="d1826-107">This trace indicates a potential application bug that should be investigated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1826-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d1826-108">See also</span></span>

- [<span data-ttu-id="d1826-109">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="d1826-109">Tracing</span></span>](index.md)
- [<span data-ttu-id="d1826-110">Utilizando o rastreamento para solucionar problemas em seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="d1826-110">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="d1826-111">Administração e diagnóstico</span><span class="sxs-lookup"><span data-stu-id="d1826-111">Administration and Diagnostics</span></span>](../index.md)
