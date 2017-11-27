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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8550c30f74968d4f58d9a2fd1deac69bf9d3abe7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodelactivationwebhostserviceclosefailed"></a><span data-ttu-id="11126-102">System.ServiceModel.Activation.WebHostServiceCloseFailed</span><span class="sxs-lookup"><span data-stu-id="11126-102">System.ServiceModel.Activation.WebHostServiceCloseFailed</span></span>
<span data-ttu-id="11126-103">Ocorre quando um serviço não pode ser fechado normalmente e será anulado.</span><span class="sxs-lookup"><span data-stu-id="11126-103">Occurs when a service cannot be closed gracefully and is aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="11126-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="11126-104">Description</span></span>  
 <span data-ttu-id="11126-105">Esse código de erro aparece somente no arquivo de log.</span><span class="sxs-lookup"><span data-stu-id="11126-105">This error code only appears in the log file.</span></span> <span data-ttu-id="11126-106">Ele normalmente indica um erro de programação, por exemplo, quando você tentar fechar um serviço após a anulação já foi chamada.</span><span class="sxs-lookup"><span data-stu-id="11126-106">It usually indicates a programming error, for example, when you try to close a service after Abort has already been called.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="11126-107">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="11126-107">Troubleshooting</span></span>  
 <span data-ttu-id="11126-108">Verifique o código de origem do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="11126-108">Check the application source code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11126-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="11126-109">See Also</span></span>  
 [<span data-ttu-id="11126-110">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="11126-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="11126-111">Usando o rastreamento para solucionar problemas de seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="11126-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 <span data-ttu-id="11126-112">[Administration and Diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md) (Administração e diagnósticos)</span><span class="sxs-lookup"><span data-stu-id="11126-112">[Administration and Diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md)</span></span>
