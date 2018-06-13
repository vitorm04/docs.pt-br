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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 53aaf4c23861666962e5567a6cf9eb9fffc6292f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33438750"
---
# <a name="ihostmanualevent-interface"></a><span data-ttu-id="d30e5-102">Interface IHostManualEvent</span><span class="sxs-lookup"><span data-stu-id="d30e5-102">IHostManualEvent Interface</span></span>
<span data-ttu-id="d30e5-103">Fornece a implementação do host de uma representação de um evento de redefinição manual.</span><span class="sxs-lookup"><span data-stu-id="d30e5-103">Provides the host's implementation of a representation of a manual reset event.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d30e5-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="d30e5-104">Methods</span></span>  
  
|<span data-ttu-id="d30e5-105">Método</span><span class="sxs-lookup"><span data-stu-id="d30e5-105">Method</span></span>|<span data-ttu-id="d30e5-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="d30e5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d30e5-107">Método Reset</span><span class="sxs-lookup"><span data-stu-id="d30e5-107">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-reset-method.md)|<span data-ttu-id="d30e5-108">Redefine o atual `IHostManualEvent` instância para um estado não sinalizado.</span><span class="sxs-lookup"><span data-stu-id="d30e5-108">Resets the current `IHostManualEvent` instance to a non-signaled state.</span></span>|  
|[<span data-ttu-id="d30e5-109">Método Set</span><span class="sxs-lookup"><span data-stu-id="d30e5-109">Set Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-set-method.md)|<span data-ttu-id="d30e5-110">Define o atual `IHostManualEvent` instância para um estado sinalizado.</span><span class="sxs-lookup"><span data-stu-id="d30e5-110">Sets the current `IHostManualEvent` instance to a signaled state.</span></span>|  
|[<span data-ttu-id="d30e5-111">Método Wait</span><span class="sxs-lookup"><span data-stu-id="d30e5-111">Wait Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-wait-method.md)|<span data-ttu-id="d30e5-112">Faz com que o atual `IHostManualEvent` instância para aguardar até que ele pertence, ou um período de tempo especificado.</span><span class="sxs-lookup"><span data-stu-id="d30e5-112">Causes the current `IHostManualEvent` instance to wait until it is owned, or a specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d30e5-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d30e5-113">Requirements</span></span>  
 <span data-ttu-id="d30e5-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d30e5-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d30e5-115">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d30e5-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d30e5-116">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="d30e5-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d30e5-117">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d30e5-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d30e5-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d30e5-118">See Also</span></span>  
 [<span data-ttu-id="d30e5-119">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="d30e5-119">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="d30e5-120">Interface IHostAutoEvent</span><span class="sxs-lookup"><span data-stu-id="d30e5-120">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="d30e5-121">Interface IHostSemaphore</span><span class="sxs-lookup"><span data-stu-id="d30e5-121">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 [<span data-ttu-id="d30e5-122">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="d30e5-122">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [<span data-ttu-id="d30e5-123">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="d30e5-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
