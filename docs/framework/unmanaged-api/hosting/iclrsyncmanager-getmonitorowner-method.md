---
title: Método ICLRSyncManager::GetMonitorOwner
ms.date: 03/30/2017
api_name:
- ICLRSyncManager.GetMonitorOwner
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager::GetMonitorOwner
helpviewer_keywords:
- ICLRSyncManager::GetMonitorOwner method [.NET Framework hosting]
- GetMonitorOwner method [.NET Framework hosting]
ms.assetid: 840983a4-396d-47b4-86a0-d35f9b437cdb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4b14421bbe71b68ca677cf712512a7f10aa30583
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763614"
---
# <a name="iclrsyncmanagergetmonitorowner-method"></a><span data-ttu-id="abda4-102">Método ICLRSyncManager::GetMonitorOwner</span><span class="sxs-lookup"><span data-stu-id="abda4-102">ICLRSyncManager::GetMonitorOwner Method</span></span>
<span data-ttu-id="abda4-103">Obtém o [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instância que detém o monitor identificado pelo cookie especificado.</span><span class="sxs-lookup"><span data-stu-id="abda4-103">Gets the [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that owns the monitor identified by the specified cookie.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abda4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="abda4-104">Syntax</span></span>  
  
```  
HRESULT GetMonitorOwner (  
    [in]  SIZE_T     cookie,  
    [out] IHostTask *ppOwnerHostTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="abda4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="abda4-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="abda4-106">[in] O cookie associado ao monitor.</span><span class="sxs-lookup"><span data-stu-id="abda4-106">[in] The cookie associated with the monitor.</span></span>  
  
 `ppOwnerHostTask`  
 <span data-ttu-id="abda4-107">[out] Um ponteiro para o `IHostTask` que atualmente possui o monitor ou nulo se nenhuma tarefa tem a propriedade.</span><span class="sxs-lookup"><span data-stu-id="abda4-107">[out] A pointer to the `IHostTask` that currently owns the monitor, or null if no task has ownership.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="abda4-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="abda4-108">Return Value</span></span>  
  
|<span data-ttu-id="abda4-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="abda4-109">HRESULT</span></span>|<span data-ttu-id="abda4-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="abda4-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="abda4-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="abda4-111">S_OK</span></span>|<span data-ttu-id="abda4-112">`GetMonitorOwner` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="abda4-112">`GetMonitorOwner` returned successfully.</span></span>|  
|<span data-ttu-id="abda4-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="abda4-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="abda4-114">O CLR não tenha sido carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="abda4-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="abda4-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="abda4-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="abda4-116">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="abda4-116">The call timed out.</span></span>|  
|<span data-ttu-id="abda4-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="abda4-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="abda4-118">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="abda4-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="abda4-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="abda4-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="abda4-120">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="abda4-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="abda4-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="abda4-121">E_FAIL</span></span>|<span data-ttu-id="abda4-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="abda4-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="abda4-123">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="abda4-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="abda4-124">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="abda4-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="abda4-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="abda4-125">Remarks</span></span>  
 <span data-ttu-id="abda4-126">O host normalmente chama `GetMonitorOwner` como parte de um mecanismo de detecção de deadlock.</span><span class="sxs-lookup"><span data-stu-id="abda4-126">The host typically calls `GetMonitorOwner` as part of a deadlock-detection mechanism.</span></span> <span data-ttu-id="abda4-127">O cookie é associado um monitor quando ele é criado usando uma chamada para [ihostsyncmanager:: Createmonitorevent](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md).</span><span class="sxs-lookup"><span data-stu-id="abda4-127">The cookie is associated with a monitor when it is created by using a call to [IHostSyncManager::CreateMonitorEvent](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="abda4-128">Uma chamada para liberar o evento subjacente o monitor pode bloquear — mas não será bloqueada — se uma chamada para esse método está atualmente em vigor no cookie associado a esse monitor.</span><span class="sxs-lookup"><span data-stu-id="abda4-128">A call to release the event underlying the monitor might block—but will not deadlock—if a call to this method is currently in effect on the cookie associated with that monitor.</span></span> <span data-ttu-id="abda4-129">Outras tarefas também podem bloquear se eles tentam adquirir o monitor.</span><span class="sxs-lookup"><span data-stu-id="abda4-129">Other tasks might also block if they attempt to acquire this monitor.</span></span>  
  
 <span data-ttu-id="abda4-130">`GetMonitorOwner` sempre retorna imediatamente e pode ser chamado a qualquer momento após uma chamada para `CreateMonitorEvent`.</span><span class="sxs-lookup"><span data-stu-id="abda4-130">`GetMonitorOwner` always returns immediately and can be called any time after a call to `CreateMonitorEvent`.</span></span> <span data-ttu-id="abda4-131">O host não precisa esperar até que uma tarefa está esperando o evento.</span><span class="sxs-lookup"><span data-stu-id="abda4-131">The host does not need to wait until a task is waiting on the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="abda4-132">Requisitos</span><span class="sxs-lookup"><span data-stu-id="abda4-132">Requirements</span></span>  
 <span data-ttu-id="abda4-133">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="abda4-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="abda4-134">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="abda4-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="abda4-135">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="abda4-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="abda4-136">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="abda4-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abda4-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="abda4-137">See also</span></span>

- [<span data-ttu-id="abda4-138">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="abda4-138">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="abda4-139">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="abda4-139">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
