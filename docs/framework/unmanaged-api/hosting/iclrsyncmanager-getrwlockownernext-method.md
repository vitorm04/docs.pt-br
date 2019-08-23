---
title: Método ICLRSyncManager::GetRWLockOwnerNext
ms.date: 03/30/2017
api_name:
- ICLRSyncManager.GetRWLockOwnerNext
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager::GetRWLockOwnerNext
helpviewer_keywords:
- ICLRSyncManager::GetRWLockOwnerNext method [.NET Framework hosting]
- GetRWLockOwnerNext method [.NET Framework hosting]
ms.assetid: 0e025b6a-280e-40a2-a2d0-b15f58777b81
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dbc38d9cf88f2449bbf689e4cf1b4101f47a0577
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943256"
---
# <a name="iclrsyncmanagergetrwlockownernext-method"></a><span data-ttu-id="a80d1-102">Método ICLRSyncManager::GetRWLockOwnerNext</span><span class="sxs-lookup"><span data-stu-id="a80d1-102">ICLRSyncManager::GetRWLockOwnerNext Method</span></span>
<span data-ttu-id="a80d1-103">Obtém a próxima instância de [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) que está bloqueada no bloqueio leitor-gravador atual.</span><span class="sxs-lookup"><span data-stu-id="a80d1-103">Gets the next [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that is blocked on the current reader-writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a80d1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a80d1-104">Syntax</span></span>  
  
```  
HRESULT GetRWLockOwnerNext (  
    [in] SIZE_T       Iterator,  
    [out] IHostTask  *ppOwnerHostTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a80d1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a80d1-105">Parameters</span></span>  
 `Iterator`  
 <span data-ttu-id="a80d1-106">no O iterador criado usando uma chamada para [CreateRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).</span><span class="sxs-lookup"><span data-stu-id="a80d1-106">[in] The iterator that was created by using a call to [CreateRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).</span></span>  
  
 `ppOwnerHostTask`  
 <span data-ttu-id="a80d1-107">fora Um ponteiro para o próximo `IHostTask` que está aguardando o bloqueio ou nulo se nenhuma tarefa estiver aguardando.</span><span class="sxs-lookup"><span data-stu-id="a80d1-107">[out] A pointer to the next `IHostTask` that is waiting on the lock, or null if no task is waiting.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a80d1-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="a80d1-108">Return Value</span></span>  
  
|<span data-ttu-id="a80d1-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a80d1-109">HRESULT</span></span>|<span data-ttu-id="a80d1-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="a80d1-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a80d1-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="a80d1-111">S_OK</span></span>|<span data-ttu-id="a80d1-112">`GetRWLockOwnerNext`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="a80d1-112">`GetRWLockOwnerNext` returned successfully.</span></span>|  
|<span data-ttu-id="a80d1-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a80d1-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a80d1-114">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="a80d1-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a80d1-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a80d1-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a80d1-116">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="a80d1-116">The call timed out.</span></span>|  
|<span data-ttu-id="a80d1-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a80d1-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a80d1-118">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="a80d1-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a80d1-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a80d1-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a80d1-120">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="a80d1-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a80d1-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a80d1-121">E_FAIL</span></span>|<span data-ttu-id="a80d1-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="a80d1-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a80d1-123">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="a80d1-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a80d1-124">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a80d1-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a80d1-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="a80d1-125">Remarks</span></span>  
 <span data-ttu-id="a80d1-126">Se `ppOwnerHostTask` é definido como NULL, a iteração foi encerrada e o host deve chamar o método [DeleteRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a80d1-126">If `ppOwnerHostTask` is set to null, the iteration has terminated, and the host should call the [DeleteRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a80d1-127">O CLR chama `AddRef` o para `IHostTask` o qual `ppOwnerHostTask` aponta para impedir que essa tarefa saia enquanto o host mantém o ponteiro.</span><span class="sxs-lookup"><span data-stu-id="a80d1-127">The CLR calls `AddRef` on the `IHostTask` to which `ppOwnerHostTask` points to prevent this task from exiting while the host holds the pointer.</span></span> <span data-ttu-id="a80d1-128">O host deve chamar `Release` para diminuir a contagem de referência quando for concluído.</span><span class="sxs-lookup"><span data-stu-id="a80d1-128">The host must call `Release` to decrement the reference count when it is finished.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a80d1-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a80d1-129">Requirements</span></span>  
 <span data-ttu-id="a80d1-130">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a80d1-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a80d1-131">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a80d1-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a80d1-132">**Biblioteca** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a80d1-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a80d1-133">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a80d1-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a80d1-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a80d1-134">See also</span></span>

- [<span data-ttu-id="a80d1-135">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="a80d1-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="a80d1-136">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="a80d1-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
