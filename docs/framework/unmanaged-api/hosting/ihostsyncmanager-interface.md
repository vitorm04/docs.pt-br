---
title: Interface IHostSyncManager
ms.date: 03/30/2017
api_name:
- IHostSyncManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager
helpviewer_keywords:
- IHostSyncManager interface [.NET Framework hosting]
ms.assetid: 2e081a37-6a28-4c93-b7ab-1c96a464637c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 200da8b87b52a29c2b075d1e06929031d3f588b7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59174220"
---
# <a name="ihostsyncmanager-interface"></a><span data-ttu-id="7fe7b-102">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="7fe7b-102">IHostSyncManager Interface</span></span>
<span data-ttu-id="7fe7b-103">Fornece métodos que permitem que o common language runtime (CLR) para criar primitivos de sincronização chamando-se o host em vez de usar as funções de sincronização do Win32.</span><span class="sxs-lookup"><span data-stu-id="7fe7b-103">Provides methods that allow the common language runtime (CLR) to create synchronization primitives by calling the host instead of using the Win32 synchronization functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7fe7b-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="7fe7b-104">Methods</span></span>  
  
|<span data-ttu-id="7fe7b-105">Método</span><span class="sxs-lookup"><span data-stu-id="7fe7b-105">Method</span></span>|<span data-ttu-id="7fe7b-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="7fe7b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7fe7b-107">Método CreateAutoEvent</span><span class="sxs-lookup"><span data-stu-id="7fe7b-107">CreateAutoEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createautoevent-method.md)|<span data-ttu-id="7fe7b-108">Cria um objeto de evento de redefinição automática.</span><span class="sxs-lookup"><span data-stu-id="7fe7b-108">Creates an auto-reset event object.</span></span>|  
|[<span data-ttu-id="7fe7b-109">Método CreateCrst</span><span class="sxs-lookup"><span data-stu-id="7fe7b-109">CreateCrst Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createcrst-method.md)|<span data-ttu-id="7fe7b-110">Cria um objeto de seção crítica para a sincronização.</span><span class="sxs-lookup"><span data-stu-id="7fe7b-110">Creates a critical section object for synchronization.</span></span>|  
|[<span data-ttu-id="7fe7b-111">Método CreateCrstWithSpinCount</span><span class="sxs-lookup"><span data-stu-id="7fe7b-111">CreateCrstWithSpinCount Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createcrstwithspincount-method.md)|<span data-ttu-id="7fe7b-112">Cria um objeto de seção crítica com contagem de rotação para a sincronização.</span><span class="sxs-lookup"><span data-stu-id="7fe7b-112">Creates a critical section object with spin count for synchronization.</span></span>|  
|[<span data-ttu-id="7fe7b-113">Método CreateManualEvent</span><span class="sxs-lookup"><span data-stu-id="7fe7b-113">CreateManualEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmanualevent-method.md)|<span data-ttu-id="7fe7b-114">Cria um objeto de evento de redefinição manual.</span><span class="sxs-lookup"><span data-stu-id="7fe7b-114">Creates a manual-reset event object.</span></span>|  
|[<span data-ttu-id="7fe7b-115">Método CreateMonitorEvent</span><span class="sxs-lookup"><span data-stu-id="7fe7b-115">CreateMonitorEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md)|<span data-ttu-id="7fe7b-116">Cria um objeto de evento de redefinição automática monitorado.</span><span class="sxs-lookup"><span data-stu-id="7fe7b-116">Creates a monitored auto-reset event object.</span></span>|  
|[<span data-ttu-id="7fe7b-117">Método CreateRWLockReaderEvent</span><span class="sxs-lookup"><span data-stu-id="7fe7b-117">CreateRWLockReaderEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createrwlockreaderevent-method.md)|<span data-ttu-id="7fe7b-118">Cria um objeto de evento de redefinição manual para a implementação de um bloqueio de leitor.</span><span class="sxs-lookup"><span data-stu-id="7fe7b-118">Creates a manual-reset event object for the implementation of a reader lock.</span></span>|  
|[<span data-ttu-id="7fe7b-119">Método CreateRWLockWriterEvent</span><span class="sxs-lookup"><span data-stu-id="7fe7b-119">CreateRWLockWriterEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createrwlockwriterevent-method.md)|<span data-ttu-id="7fe7b-120">Cria um objeto de evento de redefinição automática para a implementação de um bloqueio de gravador.</span><span class="sxs-lookup"><span data-stu-id="7fe7b-120">Creates an auto-reset event object for the implementation of a writer lock.</span></span>|  
|[<span data-ttu-id="7fe7b-121">Método CreateSemaphore</span><span class="sxs-lookup"><span data-stu-id="7fe7b-121">CreateSemaphore Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createsemaphore-method.md)|<span data-ttu-id="7fe7b-122">Cria uma [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) objeto para o CLR a ser usado como um semáforo para eventos de espera.</span><span class="sxs-lookup"><span data-stu-id="7fe7b-122">Creates an [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) object for the CLR to use as a semaphore for wait events.</span></span>|  
|[<span data-ttu-id="7fe7b-123">Método SetCLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="7fe7b-123">SetCLRSyncManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-setclrsyncmanager-method.md)|<span data-ttu-id="7fe7b-124">Define o [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) instância a ser associado com o atual `IHostSyncManager` instância.</span><span class="sxs-lookup"><span data-stu-id="7fe7b-124">Sets the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) instance to associate with the current `IHostSyncManager` instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7fe7b-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="7fe7b-125">Remarks</span></span>  
 <span data-ttu-id="7fe7b-126">O CLR detecta a implementação do host do `IHostSyncManager` chamando o [ihostcontrol:: Gethostmanager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) método com um `IID` de IID_IHostSyncManager.</span><span class="sxs-lookup"><span data-stu-id="7fe7b-126">The CLR discovers the host's implementation of `IHostSyncManager` by calling the [IHostControl::GetHostManager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) method with an `IID` of IID_IHostSyncManager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7fe7b-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7fe7b-127">Requirements</span></span>  
 <span data-ttu-id="7fe7b-128">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7fe7b-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7fe7b-129">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7fe7b-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7fe7b-130">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="7fe7b-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="7fe7b-131">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="7fe7b-131">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7fe7b-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7fe7b-132">See also</span></span>

- [<span data-ttu-id="7fe7b-133">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="7fe7b-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="7fe7b-134">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="7fe7b-134">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
