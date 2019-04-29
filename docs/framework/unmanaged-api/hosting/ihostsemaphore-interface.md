---
title: Interface IHostSemaphore
ms.date: 03/30/2017
api_name:
- IHostSemaphore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSemaphore
helpviewer_keywords:
- IHostSemaphore interface [.NET Framework hosting]
ms.assetid: c0765321-656c-441e-bab5-58176292be1e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d7d4a295832a958fb6a8fe2e6c43a09135500d3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61696672"
---
# <a name="ihostsemaphore-interface"></a><span data-ttu-id="3912d-102">Interface IHostSemaphore</span><span class="sxs-lookup"><span data-stu-id="3912d-102">IHostSemaphore Interface</span></span>
<span data-ttu-id="3912d-103">Representa a implementação do host de um sinal para threading.</span><span class="sxs-lookup"><span data-stu-id="3912d-103">Represents the host's implementation of a semaphore for threading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3912d-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="3912d-104">Methods</span></span>  
  
|<span data-ttu-id="3912d-105">Método</span><span class="sxs-lookup"><span data-stu-id="3912d-105">Method</span></span>|<span data-ttu-id="3912d-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="3912d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3912d-107">Método ReleaseSemaphore</span><span class="sxs-lookup"><span data-stu-id="3912d-107">ReleaseSemaphore Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-releasesemaphore-method.md)|<span data-ttu-id="3912d-108">Aumenta a contagem atual `IHostSemaphore` instância pelo valor especificado.</span><span class="sxs-lookup"><span data-stu-id="3912d-108">Increases the count of the current `IHostSemaphore` instance by the specified amount.</span></span>|  
|[<span data-ttu-id="3912d-109">Método Wait</span><span class="sxs-lookup"><span data-stu-id="3912d-109">Wait Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-wait-method.md)|<span data-ttu-id="3912d-110">Faz com que o atual `IHostSemaphore` instância aguardar até que ele pertence ou a quantidade especificada de tempo passa.</span><span class="sxs-lookup"><span data-stu-id="3912d-110">Causes the current `IHostSemaphore` instance to wait until it is owned or the specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3912d-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3912d-111">Requirements</span></span>  
 <span data-ttu-id="3912d-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3912d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3912d-113">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3912d-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3912d-114">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="3912d-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3912d-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3912d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3912d-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3912d-116">See also</span></span>

- [<span data-ttu-id="3912d-117">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="3912d-117">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="3912d-118">Interface IHostAutoEvent</span><span class="sxs-lookup"><span data-stu-id="3912d-118">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="3912d-119">Interface IHostManualEvent</span><span class="sxs-lookup"><span data-stu-id="3912d-119">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="3912d-120">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="3912d-120">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [<span data-ttu-id="3912d-121">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="3912d-121">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
