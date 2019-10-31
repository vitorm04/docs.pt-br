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
ms.openlocfilehash: 8eba189d6dfca3781c28631a72a9af3c037efeda
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136790"
---
# <a name="ihostmanualevent-interface"></a><span data-ttu-id="4c637-102">Interface IHostManualEvent</span><span class="sxs-lookup"><span data-stu-id="4c637-102">IHostManualEvent Interface</span></span>
<span data-ttu-id="4c637-103">Fornece a implementação do host de uma representação de um evento de redefinição manual.</span><span class="sxs-lookup"><span data-stu-id="4c637-103">Provides the host's implementation of a representation of a manual reset event.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4c637-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="4c637-104">Methods</span></span>  
  
|<span data-ttu-id="4c637-105">Método</span><span class="sxs-lookup"><span data-stu-id="4c637-105">Method</span></span>|<span data-ttu-id="4c637-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="4c637-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4c637-107">Método Reset</span><span class="sxs-lookup"><span data-stu-id="4c637-107">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-reset-method.md)|<span data-ttu-id="4c637-108">Redefine a instância de `IHostManualEvent` atual para um estado não sinalizado.</span><span class="sxs-lookup"><span data-stu-id="4c637-108">Resets the current `IHostManualEvent` instance to a non-signaled state.</span></span>|  
|[<span data-ttu-id="4c637-109">Método Set</span><span class="sxs-lookup"><span data-stu-id="4c637-109">Set Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-set-method.md)|<span data-ttu-id="4c637-110">Define a instância de `IHostManualEvent` atual como um estado sinalizado.</span><span class="sxs-lookup"><span data-stu-id="4c637-110">Sets the current `IHostManualEvent` instance to a signaled state.</span></span>|  
|[<span data-ttu-id="4c637-111">Método Wait</span><span class="sxs-lookup"><span data-stu-id="4c637-111">Wait Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-wait-method.md)|<span data-ttu-id="4c637-112">Faz com que a instância atual de `IHostManualEvent` aguarde até que ela seja propriedade ou um período de tempo especificado decorre.</span><span class="sxs-lookup"><span data-stu-id="4c637-112">Causes the current `IHostManualEvent` instance to wait until it is owned, or a specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4c637-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4c637-113">Requirements</span></span>  
 <span data-ttu-id="4c637-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c637-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c637-115">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4c637-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4c637-116">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4c637-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4c637-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c637-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c637-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4c637-118">See also</span></span>

- [<span data-ttu-id="4c637-119">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="4c637-119">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="4c637-120">Interface IHostAutoEvent</span><span class="sxs-lookup"><span data-stu-id="4c637-120">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="4c637-121">Interface IHostSemaphore</span><span class="sxs-lookup"><span data-stu-id="4c637-121">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="4c637-122">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="4c637-122">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [<span data-ttu-id="4c637-123">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="4c637-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
