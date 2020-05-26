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
ms.openlocfilehash: e96492270c403f93687245cee8b680dc16b3c787
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803120"
---
# <a name="ihostsyncmanager-interface"></a><span data-ttu-id="93765-102">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="93765-102">IHostSyncManager Interface</span></span>
<span data-ttu-id="93765-103">Fornece métodos que permitem que o Common Language Runtime (CLR) crie primitivos de sincronização chamando o host em vez de usar as funções de sincronização do Win32.</span><span class="sxs-lookup"><span data-stu-id="93765-103">Provides methods that allow the common language runtime (CLR) to create synchronization primitives by calling the host instead of using the Win32 synchronization functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="93765-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="93765-104">Methods</span></span>  
  
|<span data-ttu-id="93765-105">Método</span><span class="sxs-lookup"><span data-stu-id="93765-105">Method</span></span>|<span data-ttu-id="93765-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="93765-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="93765-107">Método CreateAutoEvent</span><span class="sxs-lookup"><span data-stu-id="93765-107">CreateAutoEvent Method</span></span>](ihostsyncmanager-createautoevent-method.md)|<span data-ttu-id="93765-108">Cria um objeto de evento de redefinição automática.</span><span class="sxs-lookup"><span data-stu-id="93765-108">Creates an auto-reset event object.</span></span>|  
|[<span data-ttu-id="93765-109">Método CreateCrst</span><span class="sxs-lookup"><span data-stu-id="93765-109">CreateCrst Method</span></span>](ihostsyncmanager-createcrst-method.md)|<span data-ttu-id="93765-110">Cria um objeto de seção crítica para sincronização.</span><span class="sxs-lookup"><span data-stu-id="93765-110">Creates a critical section object for synchronization.</span></span>|  
|[<span data-ttu-id="93765-111">Método CreateCrstWithSpinCount</span><span class="sxs-lookup"><span data-stu-id="93765-111">CreateCrstWithSpinCount Method</span></span>](ihostsyncmanager-createcrstwithspincount-method.md)|<span data-ttu-id="93765-112">Cria um objeto de seção crítica com contagem de rotação para sincronização.</span><span class="sxs-lookup"><span data-stu-id="93765-112">Creates a critical section object with spin count for synchronization.</span></span>|  
|[<span data-ttu-id="93765-113">Método CreateManualEvent</span><span class="sxs-lookup"><span data-stu-id="93765-113">CreateManualEvent Method</span></span>](ihostsyncmanager-createmanualevent-method.md)|<span data-ttu-id="93765-114">Cria um objeto de evento de redefinição manual.</span><span class="sxs-lookup"><span data-stu-id="93765-114">Creates a manual-reset event object.</span></span>|  
|[<span data-ttu-id="93765-115">Método CreateMonitorEvent</span><span class="sxs-lookup"><span data-stu-id="93765-115">CreateMonitorEvent Method</span></span>](ihostsyncmanager-createmonitorevent-method.md)|<span data-ttu-id="93765-116">Cria um objeto de evento monitorado de redefinição automática.</span><span class="sxs-lookup"><span data-stu-id="93765-116">Creates a monitored auto-reset event object.</span></span>|  
|[<span data-ttu-id="93765-117">Método CreateRWLockReaderEvent</span><span class="sxs-lookup"><span data-stu-id="93765-117">CreateRWLockReaderEvent Method</span></span>](ihostsyncmanager-createrwlockreaderevent-method.md)|<span data-ttu-id="93765-118">Cria um objeto de evento de redefinição manual para a implementação de um bloqueio de leitor.</span><span class="sxs-lookup"><span data-stu-id="93765-118">Creates a manual-reset event object for the implementation of a reader lock.</span></span>|  
|[<span data-ttu-id="93765-119">Método CreateRWLockWriterEvent</span><span class="sxs-lookup"><span data-stu-id="93765-119">CreateRWLockWriterEvent Method</span></span>](ihostsyncmanager-createrwlockwriterevent-method.md)|<span data-ttu-id="93765-120">Cria um objeto de evento de redefinição automática para a implementação de um bloqueio de gravador.</span><span class="sxs-lookup"><span data-stu-id="93765-120">Creates an auto-reset event object for the implementation of a writer lock.</span></span>|  
|[<span data-ttu-id="93765-121">Método CreateSemaphore</span><span class="sxs-lookup"><span data-stu-id="93765-121">CreateSemaphore Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createsemaphore-method.md)|<span data-ttu-id="93765-122">Cria um objeto [IHostSemaphore](ihostsemaphore-interface.md) para o CLR usar como um semáforo para eventos de espera.</span><span class="sxs-lookup"><span data-stu-id="93765-122">Creates an [IHostSemaphore](ihostsemaphore-interface.md) object for the CLR to use as a semaphore for wait events.</span></span>|  
|[<span data-ttu-id="93765-123">Método SetCLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="93765-123">SetCLRSyncManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-setclrsyncmanager-method.md)|<span data-ttu-id="93765-124">Define a instância de [ICLRSyncManager](iclrsyncmanager-interface.md) a ser associada à `IHostSyncManager` instância atual.</span><span class="sxs-lookup"><span data-stu-id="93765-124">Sets the [ICLRSyncManager](iclrsyncmanager-interface.md) instance to associate with the current `IHostSyncManager` instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="93765-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="93765-125">Remarks</span></span>  
 <span data-ttu-id="93765-126">O CLR descobre a implementação do host do `IHostSyncManager` chamando o método [IHostControl:: GetHostManager](ihostcontrol-gethostmanager-method.md) com um `IID` de IID_IHostSyncManager.</span><span class="sxs-lookup"><span data-stu-id="93765-126">The CLR discovers the host's implementation of `IHostSyncManager` by calling the [IHostControl::GetHostManager](ihostcontrol-gethostmanager-method.md) method with an `IID` of IID_IHostSyncManager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93765-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="93765-127">Requirements</span></span>  
 <span data-ttu-id="93765-128">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93765-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93765-129">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="93765-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="93765-130">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="93765-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="93765-131">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93765-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93765-132">Confira também</span><span class="sxs-lookup"><span data-stu-id="93765-132">See also</span></span>

- [<span data-ttu-id="93765-133">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="93765-133">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="93765-134">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="93765-134">Hosting Interfaces</span></span>](hosting-interfaces.md)
