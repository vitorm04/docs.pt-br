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
ms.openlocfilehash: d3efe80c0442e765274b309e39a79cc867676043
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59169644"
---
# <a name="iclrsyncmanagergetrwlockownernext-method"></a><span data-ttu-id="f9b6c-102">Método ICLRSyncManager::GetRWLockOwnerNext</span><span class="sxs-lookup"><span data-stu-id="f9b6c-102">ICLRSyncManager::GetRWLockOwnerNext Method</span></span>
<span data-ttu-id="f9b6c-103">Obtém o próximo [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instância que está bloqueada no bloqueio de leitor-gravador atual.</span><span class="sxs-lookup"><span data-stu-id="f9b6c-103">Gets the next [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that is blocked on the current reader-writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9b6c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f9b6c-104">Syntax</span></span>  
  
```  
HRESULT GetRWLockOwnerNext (  
    [in] SIZE_T       Iterator,  
    [out] IHostTask  *ppOwnerHostTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f9b6c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f9b6c-105">Parameters</span></span>  
 `Iterator`  
 <span data-ttu-id="f9b6c-106">[in] O que foi criado por meio de uma chamada ao iterador [CreateRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).</span><span class="sxs-lookup"><span data-stu-id="f9b6c-106">[in] The iterator that was created by using a call to [CreateRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).</span></span>  
  
 `ppOwnerHostTask`  
 <span data-ttu-id="f9b6c-107">[out] Um ponteiro para o próximo `IHostTask` que está aguardando o bloqueio ou nulo se nenhuma tarefa está esperando.</span><span class="sxs-lookup"><span data-stu-id="f9b6c-107">[out] A pointer to the next `IHostTask` that is waiting on the lock, or null if no task is waiting.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f9b6c-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="f9b6c-108">Return Value</span></span>  
  
|<span data-ttu-id="f9b6c-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f9b6c-109">HRESULT</span></span>|<span data-ttu-id="f9b6c-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="f9b6c-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f9b6c-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="f9b6c-111">S_OK</span></span>|<span data-ttu-id="f9b6c-112">`GetRWLockOwnerNext` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="f9b6c-112">`GetRWLockOwnerNext` returned successfully.</span></span>|  
|<span data-ttu-id="f9b6c-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f9b6c-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f9b6c-114">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="f9b6c-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f9b6c-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f9b6c-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f9b6c-116">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="f9b6c-116">The call timed out.</span></span>|  
|<span data-ttu-id="f9b6c-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f9b6c-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f9b6c-118">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="f9b6c-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f9b6c-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f9b6c-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f9b6c-120">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="f9b6c-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f9b6c-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f9b6c-121">E_FAIL</span></span>|<span data-ttu-id="f9b6c-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="f9b6c-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f9b6c-123">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="f9b6c-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f9b6c-124">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f9b6c-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f9b6c-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="f9b6c-125">Remarks</span></span>  
 <span data-ttu-id="f9b6c-126">Se `ppOwnerHostTask` é definido como nulo, a iteração foi encerrado e o host deve chamar o [DeleteRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="f9b6c-126">If `ppOwnerHostTask` is set to null, the iteration has terminated, and the host should call the [DeleteRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f9b6c-127">O CLR chama `AddRef` sobre o `IHostTask` ao qual `ppOwnerHostTask` pontos para impedir que esta tarefa sair enquanto o host mantém o ponteiro.</span><span class="sxs-lookup"><span data-stu-id="f9b6c-127">The CLR calls `AddRef` on the `IHostTask` to which `ppOwnerHostTask` points to prevent this task from exiting while the host holds the pointer.</span></span> <span data-ttu-id="f9b6c-128">O host deve chamar `Release` para diminuir a contagem de referência quando ele for concluído.</span><span class="sxs-lookup"><span data-stu-id="f9b6c-128">The host must call `Release` to decrement the reference count when it is finished.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9b6c-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f9b6c-129">Requirements</span></span>  
 <span data-ttu-id="f9b6c-130">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9b6c-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9b6c-131">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f9b6c-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f9b6c-132">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="f9b6c-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f9b6c-133">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9b6c-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9b6c-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f9b6c-134">See also</span></span>

- [<span data-ttu-id="f9b6c-135">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="f9b6c-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="f9b6c-136">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="f9b6c-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
