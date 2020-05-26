---
title: Interface IHostManualEvent
ms.date: 03/30/2017
api_name:
- IHostManualEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostManualEvent
helpviewer_keywords:
- IHostManualEvent interface [.NET Framework hosting]
ms.assetid: 300c2661-b7d1-4c39-b080-9ebdef0fd523
topic_type:
- apiref
ms.openlocfilehash: 7c46f00063cdf9281a5f1080594e8d6dbc6c101e
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804590"
---
# <a name="ihostmanualevent-interface"></a><span data-ttu-id="85e4b-102">Interface IHostManualEvent</span><span class="sxs-lookup"><span data-stu-id="85e4b-102">IHostManualEvent Interface</span></span>
<span data-ttu-id="85e4b-103">Fornece a implementação do host de uma representação de um evento de redefinição manual.</span><span class="sxs-lookup"><span data-stu-id="85e4b-103">Provides the host's implementation of a representation of a manual reset event.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="85e4b-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="85e4b-104">Methods</span></span>  
  
|<span data-ttu-id="85e4b-105">Método</span><span class="sxs-lookup"><span data-stu-id="85e4b-105">Method</span></span>|<span data-ttu-id="85e4b-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="85e4b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="85e4b-107">Método Reset</span><span class="sxs-lookup"><span data-stu-id="85e4b-107">Reset Method</span></span>](ihostmanualevent-reset-method.md)|<span data-ttu-id="85e4b-108">Redefine a `IHostManualEvent` instância atual para um estado não sinalizado.</span><span class="sxs-lookup"><span data-stu-id="85e4b-108">Resets the current `IHostManualEvent` instance to a non-signaled state.</span></span>|  
|[<span data-ttu-id="85e4b-109">Método Set</span><span class="sxs-lookup"><span data-stu-id="85e4b-109">Set Method</span></span>](ihostmanualevent-set-method.md)|<span data-ttu-id="85e4b-110">Define a `IHostManualEvent` instância atual para um estado sinalizado.</span><span class="sxs-lookup"><span data-stu-id="85e4b-110">Sets the current `IHostManualEvent` instance to a signaled state.</span></span>|  
|[<span data-ttu-id="85e4b-111">Método Wait</span><span class="sxs-lookup"><span data-stu-id="85e4b-111">Wait Method</span></span>](ihostmanualevent-wait-method.md)|<span data-ttu-id="85e4b-112">Faz com que a `IHostManualEvent` instância atual aguarde até que ela seja propriedade ou uma quantidade especificada de tempo decorre.</span><span class="sxs-lookup"><span data-stu-id="85e4b-112">Causes the current `IHostManualEvent` instance to wait until it is owned, or a specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="85e4b-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="85e4b-113">Requirements</span></span>  
 <span data-ttu-id="85e4b-114">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85e4b-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85e4b-115">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="85e4b-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="85e4b-116">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="85e4b-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="85e4b-117">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85e4b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85e4b-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="85e4b-118">See also</span></span>

- [<span data-ttu-id="85e4b-119">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="85e4b-119">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="85e4b-120">Interface IHostAutoEvent</span><span class="sxs-lookup"><span data-stu-id="85e4b-120">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="85e4b-121">Interface IHostSemaphore</span><span class="sxs-lookup"><span data-stu-id="85e4b-121">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="85e4b-122">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="85e4b-122">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- [<span data-ttu-id="85e4b-123">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="85e4b-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
