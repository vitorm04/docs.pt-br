---
title: "Método ICLRSyncManager::GetRWLockOwnerNext"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRSyncManager.GetRWLockOwnerNext
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRSyncManager::GetRWLockOwnerNext
helpviewer_keywords:
- ICLRSyncManager::GetRWLockOwnerNext method [.NET Framework hosting]
- GetRWLockOwnerNext method [.NET Framework hosting]
ms.assetid: 0e025b6a-280e-40a2-a2d0-b15f58777b81
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1181cbb71aa30281fbff634354162e1f245d05fe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrsyncmanagergetrwlockownernext-method"></a><span data-ttu-id="726e5-102">Método ICLRSyncManager::GetRWLockOwnerNext</span><span class="sxs-lookup"><span data-stu-id="726e5-102">ICLRSyncManager::GetRWLockOwnerNext Method</span></span>
<span data-ttu-id="726e5-103">Obtém o próximo [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instância que está bloqueada no bloqueio de leitor-gravador atual.</span><span class="sxs-lookup"><span data-stu-id="726e5-103">Gets the next [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that is blocked on the current reader-writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="726e5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="726e5-104">Syntax</span></span>  
  
```  
HRESULT GetRWLockOwnerNext (  
    [in] SIZE_T       Iterator,  
    [out] IHostTask  *ppOwnerHostTask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="726e5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="726e5-105">Parameters</span></span>  
 `Iterator`  
 <span data-ttu-id="726e5-106">[in] O iterador que foi criado usando uma chamada para [CreateRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).</span><span class="sxs-lookup"><span data-stu-id="726e5-106">[in] The iterator that was created by using a call to [CreateRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).</span></span>  
  
 `ppOwnerHostTask`  
 <span data-ttu-id="726e5-107">[out] Um ponteiro para o próximo `IHostTask` que está aguardando o bloqueio, ou nulo se nenhuma tarefa está esperando.</span><span class="sxs-lookup"><span data-stu-id="726e5-107">[out] A pointer to the next `IHostTask` that is waiting on the lock, or null if no task is waiting.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="726e5-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="726e5-108">Return Value</span></span>  
  
|<span data-ttu-id="726e5-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="726e5-109">HRESULT</span></span>|<span data-ttu-id="726e5-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="726e5-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="726e5-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="726e5-111">S_OK</span></span>|<span data-ttu-id="726e5-112">`GetRWLockOwnerNext`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="726e5-112">`GetRWLockOwnerNext` returned successfully.</span></span>|  
|<span data-ttu-id="726e5-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="726e5-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="726e5-114">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="726e5-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="726e5-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="726e5-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="726e5-116">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="726e5-116">The call timed out.</span></span>|  
|<span data-ttu-id="726e5-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="726e5-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="726e5-118">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="726e5-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="726e5-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="726e5-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="726e5-120">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="726e5-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="726e5-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="726e5-121">E_FAIL</span></span>|<span data-ttu-id="726e5-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="726e5-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="726e5-123">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="726e5-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="726e5-124">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="726e5-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="726e5-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="726e5-125">Remarks</span></span>  
 <span data-ttu-id="726e5-126">Se `ppOwnerHostTask` é definido como null, encerrou a iteração e o host deve chamar o [DeleteRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="726e5-126">If `ppOwnerHostTask` is set to null, the iteration has terminated, and the host should call the [DeleteRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="726e5-127">O CLR chama `AddRef` no `IHostTask` para o qual `ppOwnerHostTask` pontos para impedir que esta tarefa sair enquanto o host contém o ponteiro.</span><span class="sxs-lookup"><span data-stu-id="726e5-127">The CLR calls `AddRef` on the `IHostTask` to which `ppOwnerHostTask` points to prevent this task from exiting while the host holds the pointer.</span></span> <span data-ttu-id="726e5-128">O host deve chamar `Release` para diminuir a contagem de referência quando ele for concluído.</span><span class="sxs-lookup"><span data-stu-id="726e5-128">The host must call `Release` to decrement the reference count when it is finished.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="726e5-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="726e5-129">Requirements</span></span>  
 <span data-ttu-id="726e5-130">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="726e5-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="726e5-131">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="726e5-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="726e5-132">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="726e5-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="726e5-133">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="726e5-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="726e5-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="726e5-134">See Also</span></span>  
 [<span data-ttu-id="726e5-135">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="726e5-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="726e5-136">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="726e5-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
