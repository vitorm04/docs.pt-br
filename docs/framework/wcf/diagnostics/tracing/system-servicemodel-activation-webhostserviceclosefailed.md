---
title: System.ServiceModel.Activation.WebHostServiceCloseFailed
ms.date: 03/30/2017
ms.assetid: 3cab9856-a5cf-4f0e-a0cb-89425e368f8e
ms.openlocfilehash: 0ed3a9a1c16247f94c739a43d84d51e4750b3c2f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54597652"
---
# <a name="systemservicemodelactivationwebhostserviceclosefailed"></a><span data-ttu-id="4f09d-102">System.ServiceModel.Activation.WebHostServiceCloseFailed</span><span class="sxs-lookup"><span data-stu-id="4f09d-102">System.ServiceModel.Activation.WebHostServiceCloseFailed</span></span>
<span data-ttu-id="4f09d-103">Ocorre quando um serviço não pode ser fechado normalmente e será anulado.</span><span class="sxs-lookup"><span data-stu-id="4f09d-103">Occurs when a service cannot be closed gracefully and is aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="4f09d-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="4f09d-104">Description</span></span>  
 <span data-ttu-id="4f09d-105">Esse código de erro aparece somente no arquivo de log.</span><span class="sxs-lookup"><span data-stu-id="4f09d-105">This error code only appears in the log file.</span></span> <span data-ttu-id="4f09d-106">Ele normalmente indica um erro de programação, por exemplo, quando você tentar fechar um serviço após a anulação já foi chamada.</span><span class="sxs-lookup"><span data-stu-id="4f09d-106">It usually indicates a programming error, for example, when you try to close a service after Abort has already been called.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="4f09d-107">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="4f09d-107">Troubleshooting</span></span>  
 <span data-ttu-id="4f09d-108">Verifique o código de origem do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4f09d-108">Check the application source code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f09d-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4f09d-109">See also</span></span>
- [<span data-ttu-id="4f09d-110">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="4f09d-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="4f09d-111">Usando o rastreamento para solucionar problemas do seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="4f09d-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="4f09d-112">Administração e diagnósticos</span><span class="sxs-lookup"><span data-stu-id="4f09d-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
