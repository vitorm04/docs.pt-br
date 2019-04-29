---
title: System.ServiceModel.Activation.WebHostServiceCloseFailed
ms.date: 03/30/2017
ms.assetid: 3cab9856-a5cf-4f0e-a0cb-89425e368f8e
ms.openlocfilehash: afe84db3d4df8914ff1ed001b064439d581ead89
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61752757"
---
# <a name="systemservicemodelactivationwebhostserviceclosefailed"></a><span data-ttu-id="c2d85-102">System.ServiceModel.Activation.WebHostServiceCloseFailed</span><span class="sxs-lookup"><span data-stu-id="c2d85-102">System.ServiceModel.Activation.WebHostServiceCloseFailed</span></span>
<span data-ttu-id="c2d85-103">Ocorre quando um serviço não pode ser fechado normalmente e será anulado.</span><span class="sxs-lookup"><span data-stu-id="c2d85-103">Occurs when a service cannot be closed gracefully and is aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="c2d85-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="c2d85-104">Description</span></span>  
 <span data-ttu-id="c2d85-105">Esse código de erro aparece somente no arquivo de log.</span><span class="sxs-lookup"><span data-stu-id="c2d85-105">This error code only appears in the log file.</span></span> <span data-ttu-id="c2d85-106">Ele normalmente indica um erro de programação, por exemplo, quando você tentar fechar um serviço após a anulação já foi chamada.</span><span class="sxs-lookup"><span data-stu-id="c2d85-106">It usually indicates a programming error, for example, when you try to close a service after Abort has already been called.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="c2d85-107">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="c2d85-107">Troubleshooting</span></span>  
 <span data-ttu-id="c2d85-108">Verifique o código de origem do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c2d85-108">Check the application source code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2d85-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c2d85-109">See also</span></span>

- [<span data-ttu-id="c2d85-110">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="c2d85-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="c2d85-111">Usando o rastreamento para solucionar problemas do seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="c2d85-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="c2d85-112">Administração e diagnósticos</span><span class="sxs-lookup"><span data-stu-id="c2d85-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
