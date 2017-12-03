---
title: System.ServiceModel.Activation.WebHostServiceCloseFailed
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3cab9856-a5cf-4f0e-a0cb-89425e368f8e
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1761ef66bf2aedf2d4382558ba70bf1956af0f3e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="systemservicemodelactivationwebhostserviceclosefailed"></a><span data-ttu-id="71090-102">System.ServiceModel.Activation.WebHostServiceCloseFailed</span><span class="sxs-lookup"><span data-stu-id="71090-102">System.ServiceModel.Activation.WebHostServiceCloseFailed</span></span>
<span data-ttu-id="71090-103">Ocorre quando um serviço não pode ser fechado normalmente e será anulado.</span><span class="sxs-lookup"><span data-stu-id="71090-103">Occurs when a service cannot be closed gracefully and is aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="71090-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="71090-104">Description</span></span>  
 <span data-ttu-id="71090-105">Esse código de erro aparece somente no arquivo de log.</span><span class="sxs-lookup"><span data-stu-id="71090-105">This error code only appears in the log file.</span></span> <span data-ttu-id="71090-106">Ele normalmente indica um erro de programação, por exemplo, quando você tentar fechar um serviço após a anulação já foi chamada.</span><span class="sxs-lookup"><span data-stu-id="71090-106">It usually indicates a programming error, for example, when you try to close a service after Abort has already been called.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="71090-107">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="71090-107">Troubleshooting</span></span>  
 <span data-ttu-id="71090-108">Verifique o código de origem do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="71090-108">Check the application source code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71090-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="71090-109">See Also</span></span>  
 [<span data-ttu-id="71090-110">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="71090-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="71090-111">Usando o rastreamento para solucionar problemas de seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="71090-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 <span data-ttu-id="71090-112">[Administration and Diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md) (Administração e diagnósticos)</span><span class="sxs-lookup"><span data-stu-id="71090-112">[Administration and Diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md)</span></span>
