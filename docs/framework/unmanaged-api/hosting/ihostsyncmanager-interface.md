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
ms.openlocfilehash: 02a59b8ef63f7e866e419db4e3232da7eec19558
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132625"
---
# <a name="ihostsyncmanager-interface"></a><span data-ttu-id="b6cd9-102">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="b6cd9-102">IHostSyncManager Interface</span></span>
<span data-ttu-id="b6cd9-103">Fornece métodos que permitem que o Common Language Runtime (CLR) crie primitivos de sincronização chamando o host em vez de usar as funções de sincronização do Win32.</span><span class="sxs-lookup"><span data-stu-id="b6cd9-103">Provides methods that allow the common language runtime (CLR) to create synchronization primitives by calling the host instead of using the Win32 synchronization functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b6cd9-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="b6cd9-104">Methods</span></span>  
  
|<span data-ttu-id="b6cd9-105">Método</span><span class="sxs-lookup"><span data-stu-id="b6cd9-105">Method</span></span>|<span data-ttu-id="b6cd9-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="b6cd9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b6cd9-107">Método CreateAutoEvent</span><span class="sxs-lookup"><span data-stu-id="b6cd9-107">CreateAutoEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createautoevent-method.md)|<span data-ttu-id="b6cd9-108">Cria um objeto de evento de redefinição automática.</span><span class="sxs-lookup"><span data-stu-id="b6cd9-108">Creates an auto-reset event object.</span></span>|  
|[<span data-ttu-id="b6cd9-109">Método CreateCrst</span><span class="sxs-lookup"><span data-stu-id="b6cd9-109">CreateCrst Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createcrst-method.md)|<span data-ttu-id="b6cd9-110">Cria um objeto de seção crítica para sincronização.</span><span class="sxs-lookup"><span data-stu-id="b6cd9-110">Creates a critical section object for synchronization.</span></span>|  
|[<span data-ttu-id="b6cd9-111">Método CreateCrstWithSpinCount</span><span class="sxs-lookup"><span data-stu-id="b6cd9-111">CreateCrstWithSpinCount Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createcrstwithspincount-method.md)|<span data-ttu-id="b6cd9-112">Cria um objeto de seção crítica com contagem de rotação para sincronização.</span><span class="sxs-lookup"><span data-stu-id="b6cd9-112">Creates a critical section object with spin count for synchronization.</span></span>|  
|[<span data-ttu-id="b6cd9-113">Método CreateManualEvent</span><span class="sxs-lookup"><span data-stu-id="b6cd9-113">CreateManualEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmanualevent-method.md)|<span data-ttu-id="b6cd9-114">Cria um objeto de evento de redefinição manual.</span><span class="sxs-lookup"><span data-stu-id="b6cd9-114">Creates a manual-reset event object.</span></span>|  
|[<span data-ttu-id="b6cd9-115">Método CreateMonitorEvent</span><span class="sxs-lookup"><span data-stu-id="b6cd9-115">CreateMonitorEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md)|<span data-ttu-id="b6cd9-116">Cria um objeto de evento monitorado de redefinição automática.</span><span class="sxs-lookup"><span data-stu-id="b6cd9-116">Creates a monitored auto-reset event object.</span></span>|  
|[<span data-ttu-id="b6cd9-117">Método CreateRWLockReaderEvent</span><span class="sxs-lookup"><span data-stu-id="b6cd9-117">CreateRWLockReaderEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createrwlockreaderevent-method.md)|<span data-ttu-id="b6cd9-118">Cria um objeto de evento de redefinição manual para a implementação de um bloqueio de leitor.</span><span class="sxs-lookup"><span data-stu-id="b6cd9-118">Creates a manual-reset event object for the implementation of a reader lock.</span></span>|  
|[<span data-ttu-id="b6cd9-119">Método CreateRWLockWriterEvent</span><span class="sxs-lookup"><span data-stu-id="b6cd9-119">CreateRWLockWriterEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createrwlockwriterevent-method.md)|<span data-ttu-id="b6cd9-120">Cria um objeto de evento de redefinição automática para a implementação de um bloqueio de gravador.</span><span class="sxs-lookup"><span data-stu-id="b6cd9-120">Creates an auto-reset event object for the implementation of a writer lock.</span></span>|  
|[<span data-ttu-id="b6cd9-121">Método CreateSemaphore</span><span class="sxs-lookup"><span data-stu-id="b6cd9-121">CreateSemaphore Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createsemaphore-method.md)|<span data-ttu-id="b6cd9-122">Cria um objeto [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) para o CLR usar como um semáforo para eventos de espera.</span><span class="sxs-lookup"><span data-stu-id="b6cd9-122">Creates an [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) object for the CLR to use as a semaphore for wait events.</span></span>|  
|[<span data-ttu-id="b6cd9-123">Método SetCLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="b6cd9-123">SetCLRSyncManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-setclrsyncmanager-method.md)|<span data-ttu-id="b6cd9-124">Define a instância de [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) a ser associada à instância de `IHostSyncManager` atual.</span><span class="sxs-lookup"><span data-stu-id="b6cd9-124">Sets the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) instance to associate with the current `IHostSyncManager` instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b6cd9-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="b6cd9-125">Remarks</span></span>  
 <span data-ttu-id="b6cd9-126">O CLR descobre a implementação do host de `IHostSyncManager` chamando o método [IHostControl:: GetHostManager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) com um `IID` de IID_IHostSyncManager.</span><span class="sxs-lookup"><span data-stu-id="b6cd9-126">The CLR discovers the host's implementation of `IHostSyncManager` by calling the [IHostControl::GetHostManager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) method with an `IID` of IID_IHostSyncManager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6cd9-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b6cd9-127">Requirements</span></span>  
 <span data-ttu-id="b6cd9-128">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6cd9-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6cd9-129">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b6cd9-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b6cd9-130">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b6cd9-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b6cd9-131">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6cd9-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6cd9-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b6cd9-132">See also</span></span>

- [<span data-ttu-id="b6cd9-133">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="b6cd9-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="b6cd9-134">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="b6cd9-134">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
