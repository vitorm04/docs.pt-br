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
ms.workload: dotnet
ms.openlocfilehash: cc2b0dc75e8e8748e25c1faf28150e0c156a20ae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodelactivationwebhostserviceclosefailed"></a><span data-ttu-id="5116d-102">System.ServiceModel.Activation.WebHostServiceCloseFailed</span><span class="sxs-lookup"><span data-stu-id="5116d-102">System.ServiceModel.Activation.WebHostServiceCloseFailed</span></span>
<span data-ttu-id="5116d-103">Ocorre quando um serviço não pode ser fechado normalmente e será anulado.</span><span class="sxs-lookup"><span data-stu-id="5116d-103">Occurs when a service cannot be closed gracefully and is aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="5116d-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="5116d-104">Description</span></span>  
 <span data-ttu-id="5116d-105">Esse código de erro aparece somente no arquivo de log.</span><span class="sxs-lookup"><span data-stu-id="5116d-105">This error code only appears in the log file.</span></span> <span data-ttu-id="5116d-106">Ele normalmente indica um erro de programação, por exemplo, quando você tentar fechar um serviço após a anulação já foi chamada.</span><span class="sxs-lookup"><span data-stu-id="5116d-106">It usually indicates a programming error, for example, when you try to close a service after Abort has already been called.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="5116d-107">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="5116d-107">Troubleshooting</span></span>  
 <span data-ttu-id="5116d-108">Verifique o código de origem do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5116d-108">Check the application source code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5116d-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5116d-109">See Also</span></span>  
 [<span data-ttu-id="5116d-110">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="5116d-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="5116d-111">Usando o rastreamento para solucionar problemas do seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="5116d-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="5116d-112">Administração e diagnósticos</span><span class="sxs-lookup"><span data-stu-id="5116d-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
