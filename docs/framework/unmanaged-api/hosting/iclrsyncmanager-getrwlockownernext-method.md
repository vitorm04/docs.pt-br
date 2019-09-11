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
ms.openlocfilehash: 2461d20dc65706fcfdb8b9a2088d634c771fa1fb
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855594"
---
# <a name="iclrsyncmanagergetrwlockownernext-method"></a><span data-ttu-id="7fc1a-102">Método ICLRSyncManager::GetRWLockOwnerNext</span><span class="sxs-lookup"><span data-stu-id="7fc1a-102">ICLRSyncManager::GetRWLockOwnerNext Method</span></span>
<span data-ttu-id="7fc1a-103">Obtém a próxima instância de [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) que está bloqueada no bloqueio leitor-gravador atual.</span><span class="sxs-lookup"><span data-stu-id="7fc1a-103">Gets the next [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that is blocked on the current reader-writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7fc1a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7fc1a-104">Syntax</span></span>  
  
```cpp
HRESULT GetRWLockOwnerNext (  
    [in] SIZE_T       Iterator,  
    [out] IHostTask  *ppOwnerHostTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7fc1a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7fc1a-105">Parameters</span></span>  
 `Iterator`  
 <span data-ttu-id="7fc1a-106">no O iterador criado usando uma chamada para [CreateRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).</span><span class="sxs-lookup"><span data-stu-id="7fc1a-106">[in] The iterator that was created by using a call to [CreateRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).</span></span>  
  
 `ppOwnerHostTask`  
 <span data-ttu-id="7fc1a-107">fora Um ponteiro para o próximo `IHostTask` que está aguardando o bloqueio ou nulo se nenhuma tarefa estiver aguardando.</span><span class="sxs-lookup"><span data-stu-id="7fc1a-107">[out] A pointer to the next `IHostTask` that is waiting on the lock, or null if no task is waiting.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7fc1a-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="7fc1a-108">Return Value</span></span>  
  
|<span data-ttu-id="7fc1a-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7fc1a-109">HRESULT</span></span>|<span data-ttu-id="7fc1a-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="7fc1a-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7fc1a-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="7fc1a-111">S_OK</span></span>|<span data-ttu-id="7fc1a-112">`GetRWLockOwnerNext`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="7fc1a-112">`GetRWLockOwnerNext` returned successfully.</span></span>|  
|<span data-ttu-id="7fc1a-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7fc1a-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7fc1a-114">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="7fc1a-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7fc1a-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7fc1a-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7fc1a-116">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="7fc1a-116">The call timed out.</span></span>|  
|<span data-ttu-id="7fc1a-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7fc1a-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7fc1a-118">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="7fc1a-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7fc1a-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7fc1a-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7fc1a-120">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="7fc1a-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7fc1a-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7fc1a-121">E_FAIL</span></span>|<span data-ttu-id="7fc1a-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="7fc1a-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7fc1a-123">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="7fc1a-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7fc1a-124">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7fc1a-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7fc1a-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="7fc1a-125">Remarks</span></span>  
 <span data-ttu-id="7fc1a-126">Se `ppOwnerHostTask` é definido como NULL, a iteração foi encerrada e o host deve chamar o método [DeleteRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) .</span><span class="sxs-lookup"><span data-stu-id="7fc1a-126">If `ppOwnerHostTask` is set to null, the iteration has terminated, and the host should call the [DeleteRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7fc1a-127">O CLR chama `AddRef` o para `IHostTask` o qual `ppOwnerHostTask` aponta para impedir que essa tarefa saia enquanto o host mantém o ponteiro.</span><span class="sxs-lookup"><span data-stu-id="7fc1a-127">The CLR calls `AddRef` on the `IHostTask` to which `ppOwnerHostTask` points to prevent this task from exiting while the host holds the pointer.</span></span> <span data-ttu-id="7fc1a-128">O host deve chamar `Release` para diminuir a contagem de referência quando for concluído.</span><span class="sxs-lookup"><span data-stu-id="7fc1a-128">The host must call `Release` to decrement the reference count when it is finished.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7fc1a-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7fc1a-129">Requirements</span></span>  
 <span data-ttu-id="7fc1a-130">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7fc1a-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7fc1a-131">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7fc1a-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7fc1a-132">**Biblioteca** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7fc1a-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7fc1a-133">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7fc1a-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fc1a-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7fc1a-134">See also</span></span>

- [<span data-ttu-id="7fc1a-135">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="7fc1a-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="7fc1a-136">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="7fc1a-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
