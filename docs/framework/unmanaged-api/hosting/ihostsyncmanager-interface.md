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
ms.openlocfilehash: fd3c941d89fbd93f30fc1af235f6310b23758973
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501450"
---
# <a name="ihostsyncmanager-interface"></a><span data-ttu-id="4b068-102">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="4b068-102">IHostSyncManager Interface</span></span>
<span data-ttu-id="4b068-103">Fornece métodos que permitem que o Common Language Runtime (CLR) crie primitivos de sincronização chamando o host em vez de usar as funções de sincronização do Win32.</span><span class="sxs-lookup"><span data-stu-id="4b068-103">Provides methods that allow the common language runtime (CLR) to create synchronization primitives by calling the host instead of using the Win32 synchronization functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4b068-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="4b068-104">Methods</span></span>  
  
|<span data-ttu-id="4b068-105">Método</span><span class="sxs-lookup"><span data-stu-id="4b068-105">Method</span></span>|<span data-ttu-id="4b068-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="4b068-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4b068-107">Método CreateAutoEvent</span><span class="sxs-lookup"><span data-stu-id="4b068-107">CreateAutoEvent Method</span></span>](ihostsyncmanager-createautoevent-method.md)|<span data-ttu-id="4b068-108">Cria um objeto de evento de redefinição automática.</span><span class="sxs-lookup"><span data-stu-id="4b068-108">Creates an auto-reset event object.</span></span>|  
|[<span data-ttu-id="4b068-109">Método CreateCrst</span><span class="sxs-lookup"><span data-stu-id="4b068-109">CreateCrst Method</span></span>](ihostsyncmanager-createcrst-method.md)|<span data-ttu-id="4b068-110">Cria um objeto de seção crítica para sincronização.</span><span class="sxs-lookup"><span data-stu-id="4b068-110">Creates a critical section object for synchronization.</span></span>|  
|[<span data-ttu-id="4b068-111">Método CreateCrstWithSpinCount</span><span class="sxs-lookup"><span data-stu-id="4b068-111">CreateCrstWithSpinCount Method</span></span>](ihostsyncmanager-createcrstwithspincount-method.md)|<span data-ttu-id="4b068-112">Cria um objeto de seção crítica com contagem de rotação para sincronização.</span><span class="sxs-lookup"><span data-stu-id="4b068-112">Creates a critical section object with spin count for synchronization.</span></span>|  
|[<span data-ttu-id="4b068-113">Método CreateManualEvent</span><span class="sxs-lookup"><span data-stu-id="4b068-113">CreateManualEvent Method</span></span>](ihostsyncmanager-createmanualevent-method.md)|<span data-ttu-id="4b068-114">Cria um objeto de evento de redefinição manual.</span><span class="sxs-lookup"><span data-stu-id="4b068-114">Creates a manual-reset event object.</span></span>|  
|[<span data-ttu-id="4b068-115">Método CreateMonitorEvent</span><span class="sxs-lookup"><span data-stu-id="4b068-115">CreateMonitorEvent Method</span></span>](ihostsyncmanager-createmonitorevent-method.md)|<span data-ttu-id="4b068-116">Cria um objeto de evento monitorado de redefinição automática.</span><span class="sxs-lookup"><span data-stu-id="4b068-116">Creates a monitored auto-reset event object.</span></span>|  
|[<span data-ttu-id="4b068-117">Método CreateRWLockReaderEvent</span><span class="sxs-lookup"><span data-stu-id="4b068-117">CreateRWLockReaderEvent Method</span></span>](ihostsyncmanager-createrwlockreaderevent-method.md)|<span data-ttu-id="4b068-118">Cria um objeto de evento de redefinição manual para a implementação de um bloqueio de leitor.</span><span class="sxs-lookup"><span data-stu-id="4b068-118">Creates a manual-reset event object for the implementation of a reader lock.</span></span>|  
|[<span data-ttu-id="4b068-119">Método CreateRWLockWriterEvent</span><span class="sxs-lookup"><span data-stu-id="4b068-119">CreateRWLockWriterEvent Method</span></span>](ihostsyncmanager-createrwlockwriterevent-method.md)|<span data-ttu-id="4b068-120">Cria um objeto de evento de redefinição automática para a implementação de um bloqueio de gravador.</span><span class="sxs-lookup"><span data-stu-id="4b068-120">Creates an auto-reset event object for the implementation of a writer lock.</span></span>|  
|[<span data-ttu-id="4b068-121">Método CreateSemaphore</span><span class="sxs-lookup"><span data-stu-id="4b068-121">CreateSemaphore Method</span></span>](ihostsyncmanager-createsemaphore-method.md)|<span data-ttu-id="4b068-122">Cria um objeto [IHostSemaphore](ihostsemaphore-interface.md) para o CLR usar como um semáforo para eventos de espera.</span><span class="sxs-lookup"><span data-stu-id="4b068-122">Creates an [IHostSemaphore](ihostsemaphore-interface.md) object for the CLR to use as a semaphore for wait events.</span></span>|  
|[<span data-ttu-id="4b068-123">Método SetCLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="4b068-123">SetCLRSyncManager Method</span></span>](ihostsyncmanager-setclrsyncmanager-method.md)|<span data-ttu-id="4b068-124">Define a instância de [ICLRSyncManager](iclrsyncmanager-interface.md) a ser associada à `IHostSyncManager` instância atual.</span><span class="sxs-lookup"><span data-stu-id="4b068-124">Sets the [ICLRSyncManager](iclrsyncmanager-interface.md) instance to associate with the current `IHostSyncManager` instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4b068-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="4b068-125">Remarks</span></span>  
 <span data-ttu-id="4b068-126">O CLR descobre a implementação do host do `IHostSyncManager` chamando o método [IHostControl:: GetHostManager](ihostcontrol-gethostmanager-method.md) com um `IID` de IID_IHostSyncManager.</span><span class="sxs-lookup"><span data-stu-id="4b068-126">The CLR discovers the host's implementation of `IHostSyncManager` by calling the [IHostControl::GetHostManager](ihostcontrol-gethostmanager-method.md) method with an `IID` of IID_IHostSyncManager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b068-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4b068-127">Requirements</span></span>  
 <span data-ttu-id="4b068-128">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b068-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b068-129">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4b068-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4b068-130">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4b068-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4b068-131">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b068-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b068-132">Confira também</span><span class="sxs-lookup"><span data-stu-id="4b068-132">See also</span></span>

- [<span data-ttu-id="4b068-133">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="4b068-133">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="4b068-134">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="4b068-134">Hosting Interfaces</span></span>](hosting-interfaces.md)
