---
title: Interface IHostSyncManager
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b51e1dd9219c30eb4918bf1e331c96585f7c03ac
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostsyncmanager-interface"></a><span data-ttu-id="6f906-102">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="6f906-102">IHostSyncManager Interface</span></span>
<span data-ttu-id="6f906-103">Fornece métodos que permitem que o common language runtime (CLR) para criar os primitivos de sincronização chamando o host em vez de usar as funções de sincronização do Win32.</span><span class="sxs-lookup"><span data-stu-id="6f906-103">Provides methods that allow the common language runtime (CLR) to create synchronization primitives by calling the host instead of using the Win32 synchronization functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6f906-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="6f906-104">Methods</span></span>  
  
|<span data-ttu-id="6f906-105">Método</span><span class="sxs-lookup"><span data-stu-id="6f906-105">Method</span></span>|<span data-ttu-id="6f906-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="6f906-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6f906-107">Método CreateAutoEvent</span><span class="sxs-lookup"><span data-stu-id="6f906-107">CreateAutoEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createautoevent-method.md)|<span data-ttu-id="6f906-108">Cria um objeto de evento de redefinição automática.</span><span class="sxs-lookup"><span data-stu-id="6f906-108">Creates an auto-reset event object.</span></span>|  
|[<span data-ttu-id="6f906-109">Método CreateCrst</span><span class="sxs-lookup"><span data-stu-id="6f906-109">CreateCrst Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createcrst-method.md)|<span data-ttu-id="6f906-110">Cria um objeto de seção crítica para sincronização.</span><span class="sxs-lookup"><span data-stu-id="6f906-110">Creates a critical section object for synchronization.</span></span>|  
|[<span data-ttu-id="6f906-111">Método CreateCrstWithSpinCount</span><span class="sxs-lookup"><span data-stu-id="6f906-111">CreateCrstWithSpinCount Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createcrstwithspincount-method.md)|<span data-ttu-id="6f906-112">Cria um objeto de seção crítica com contagem de rotação para sincronização.</span><span class="sxs-lookup"><span data-stu-id="6f906-112">Creates a critical section object with spin count for synchronization.</span></span>|  
|[<span data-ttu-id="6f906-113">Método CreateManualEvent</span><span class="sxs-lookup"><span data-stu-id="6f906-113">CreateManualEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmanualevent-method.md)|<span data-ttu-id="6f906-114">Cria um objeto de evento de redefinição manual.</span><span class="sxs-lookup"><span data-stu-id="6f906-114">Creates a manual-reset event object.</span></span>|  
|[<span data-ttu-id="6f906-115">Método CreateMonitorEvent</span><span class="sxs-lookup"><span data-stu-id="6f906-115">CreateMonitorEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md)|<span data-ttu-id="6f906-116">Cria um objeto de evento de redefinição automática monitorado.</span><span class="sxs-lookup"><span data-stu-id="6f906-116">Creates a monitored auto-reset event object.</span></span>|  
|[<span data-ttu-id="6f906-117">Método CreateRWLockReaderEvent</span><span class="sxs-lookup"><span data-stu-id="6f906-117">CreateRWLockReaderEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createrwlockreaderevent-method.md)|<span data-ttu-id="6f906-118">Cria um objeto de evento de redefinição manual para a implementação de um bloqueio de leitor.</span><span class="sxs-lookup"><span data-stu-id="6f906-118">Creates a manual-reset event object for the implementation of a reader lock.</span></span>|  
|[<span data-ttu-id="6f906-119">Método CreateRWLockWriterEvent</span><span class="sxs-lookup"><span data-stu-id="6f906-119">CreateRWLockWriterEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createrwlockwriterevent-method.md)|<span data-ttu-id="6f906-120">Cria um objeto de evento de redefinição automática para a implementação de um bloqueio de gravador.</span><span class="sxs-lookup"><span data-stu-id="6f906-120">Creates an auto-reset event object for the implementation of a writer lock.</span></span>|  
|[<span data-ttu-id="6f906-121">Método CreateSemaphore</span><span class="sxs-lookup"><span data-stu-id="6f906-121">CreateSemaphore Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createsemaphore-method.md)|<span data-ttu-id="6f906-122">Cria um [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) objeto para o CLR a ser usado como um sinal para eventos de espera.</span><span class="sxs-lookup"><span data-stu-id="6f906-122">Creates an [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) object for the CLR to use as a semaphore for wait events.</span></span>|  
|[<span data-ttu-id="6f906-123">Método SetCLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="6f906-123">SetCLRSyncManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-setclrsyncmanager-method.md)|<span data-ttu-id="6f906-124">Conjuntos de [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) instância para associar atual `IHostSyncManager` instância.</span><span class="sxs-lookup"><span data-stu-id="6f906-124">Sets the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) instance to associate with the current `IHostSyncManager` instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6f906-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="6f906-125">Remarks</span></span>  
 <span data-ttu-id="6f906-126">O CLR detecta a implementação do host de `IHostSyncManager` chamando o [Ihostcontrol](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) método com um `IID` de IID_IHostSyncManager.</span><span class="sxs-lookup"><span data-stu-id="6f906-126">The CLR discovers the host's implementation of `IHostSyncManager` by calling the [IHostControl::GetHostManager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) method with an `IID` of IID_IHostSyncManager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f906-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6f906-127">Requirements</span></span>  
 <span data-ttu-id="6f906-128">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f906-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f906-129">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6f906-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6f906-130">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="6f906-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6f906-131">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f906-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f906-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6f906-132">See Also</span></span>  
 [<span data-ttu-id="6f906-133">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="6f906-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="6f906-134">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="6f906-134">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
