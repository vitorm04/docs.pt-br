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
ms.openlocfilehash: 2cf490bcd167b7a498ae21f479f616694ccb5521
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139482"
---
# <a name="ihostsemaphore-interface"></a><span data-ttu-id="3980a-102">Interface IHostSemaphore</span><span class="sxs-lookup"><span data-stu-id="3980a-102">IHostSemaphore Interface</span></span>
<span data-ttu-id="3980a-103">Representa a implementação do host de um semáforo para Threading.</span><span class="sxs-lookup"><span data-stu-id="3980a-103">Represents the host's implementation of a semaphore for threading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3980a-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="3980a-104">Methods</span></span>  
  
|<span data-ttu-id="3980a-105">Método</span><span class="sxs-lookup"><span data-stu-id="3980a-105">Method</span></span>|<span data-ttu-id="3980a-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="3980a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3980a-107">Método ReleaseSemaphore</span><span class="sxs-lookup"><span data-stu-id="3980a-107">ReleaseSemaphore Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-releasesemaphore-method.md)|<span data-ttu-id="3980a-108">Aumenta a contagem da instância de `IHostSemaphore` atual pelo valor especificado.</span><span class="sxs-lookup"><span data-stu-id="3980a-108">Increases the count of the current `IHostSemaphore` instance by the specified amount.</span></span>|  
|[<span data-ttu-id="3980a-109">Método Wait</span><span class="sxs-lookup"><span data-stu-id="3980a-109">Wait Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-wait-method.md)|<span data-ttu-id="3980a-110">Faz com que a instância atual de `IHostSemaphore` aguarde até que ela seja propriedade ou a quantidade especificada de tempo decorre.</span><span class="sxs-lookup"><span data-stu-id="3980a-110">Causes the current `IHostSemaphore` instance to wait until it is owned or the specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3980a-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3980a-111">Requirements</span></span>  
 <span data-ttu-id="3980a-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3980a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3980a-113">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3980a-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3980a-114">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3980a-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3980a-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3980a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3980a-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3980a-116">See also</span></span>

- [<span data-ttu-id="3980a-117">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="3980a-117">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="3980a-118">Interface IHostAutoEvent</span><span class="sxs-lookup"><span data-stu-id="3980a-118">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="3980a-119">Interface IHostManualEvent</span><span class="sxs-lookup"><span data-stu-id="3980a-119">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="3980a-120">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="3980a-120">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [<span data-ttu-id="3980a-121">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="3980a-121">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
