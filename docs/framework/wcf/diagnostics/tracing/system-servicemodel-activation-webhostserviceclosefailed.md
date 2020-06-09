---
title: System.ServiceModel.Activation.WebHostServiceCloseFailed
ms.date: 03/30/2017
ms.assetid: 3cab9856-a5cf-4f0e-a0cb-89425e368f8e
ms.openlocfilehash: af24847d5174475103340725c86ff44024556671
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84588854"
---
# <a name="systemservicemodelactivationwebhostserviceclosefailed"></a><span data-ttu-id="c8044-102">System.ServiceModel.Activation.WebHostServiceCloseFailed</span><span class="sxs-lookup"><span data-stu-id="c8044-102">System.ServiceModel.Activation.WebHostServiceCloseFailed</span></span>
<span data-ttu-id="c8044-103">Ocorre quando um serviço não pode ser fechado normalmente e é anulado.</span><span class="sxs-lookup"><span data-stu-id="c8044-103">Occurs when a service cannot be closed gracefully and is aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="c8044-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="c8044-104">Description</span></span>  
 <span data-ttu-id="c8044-105">Esse código de erro aparece apenas no arquivo de log.</span><span class="sxs-lookup"><span data-stu-id="c8044-105">This error code only appears in the log file.</span></span> <span data-ttu-id="c8044-106">Isso geralmente indica um erro de programação, por exemplo, quando você tenta fechar um serviço após a anulação já ter sido chamada.</span><span class="sxs-lookup"><span data-stu-id="c8044-106">It usually indicates a programming error, for example, when you try to close a service after Abort has already been called.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="c8044-107">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="c8044-107">Troubleshooting</span></span>  
 <span data-ttu-id="c8044-108">Verifique o código-fonte do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c8044-108">Check the application source code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8044-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c8044-109">See also</span></span>

- [<span data-ttu-id="c8044-110">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="c8044-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="c8044-111">Utilizando o rastreamento para solucionar problemas em seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="c8044-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="c8044-112">Administração e diagnóstico</span><span class="sxs-lookup"><span data-stu-id="c8044-112">Administration and Diagnostics</span></span>](../index.md)
