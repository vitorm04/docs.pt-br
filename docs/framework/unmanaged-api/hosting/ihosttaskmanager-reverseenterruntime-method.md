---
title: Método IHostTaskManager::ReverseEnterRuntime
ms.date: 03/30/2017
api_name:
- IHostTaskManager.ReverseEnterRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::ReverseEnterRuntime
helpviewer_keywords:
- IHostTaskManager::ReverseEnterRuntime method [.NET Framework hosting]
- ReverseEnterRuntime method [.NET Framework hosting]
ms.assetid: b1e26bff-d3ea-436e-9867-29720df999f4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d6e5beabb5ac1b5a4b2a34ae8e18b7fad7c86504
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959047"
---
# <a name="ihosttaskmanagerreverseenterruntime-method"></a><span data-ttu-id="1ec70-102">Método IHostTaskManager::ReverseEnterRuntime</span><span class="sxs-lookup"><span data-stu-id="1ec70-102">IHostTaskManager::ReverseEnterRuntime Method</span></span>
<span data-ttu-id="1ec70-103">Notifica o host de que uma chamada está sendo feita no Common Language Runtime (CLR) de código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="1ec70-103">Notifies the host that a call is being made into the common language runtime (CLR) from unmanaged code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ec70-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1ec70-104">Syntax</span></span>  
  
```cpp  
HRESULT ReverseEnterRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="1ec70-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="1ec70-105">Return Value</span></span>  
  
|<span data-ttu-id="1ec70-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1ec70-106">HRESULT</span></span>|<span data-ttu-id="1ec70-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="1ec70-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1ec70-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="1ec70-108">S_OK</span></span>|<span data-ttu-id="1ec70-109">`ReverseEnterRuntime`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="1ec70-109">`ReverseEnterRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="1ec70-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1ec70-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1ec70-111">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="1ec70-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1ec70-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1ec70-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1ec70-113">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="1ec70-113">The call timed out.</span></span>|  
|<span data-ttu-id="1ec70-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1ec70-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1ec70-115">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="1ec70-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1ec70-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1ec70-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1ec70-117">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="1ec70-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1ec70-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1ec70-118">E_FAIL</span></span>|<span data-ttu-id="1ec70-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="1ec70-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1ec70-120">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="1ec70-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1ec70-121">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1ec70-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="1ec70-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="1ec70-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="1ec70-123">Não há memória suficiente disponível para concluir a alocação de recursos solicitada.</span><span class="sxs-lookup"><span data-stu-id="1ec70-123">Not enough memory is available to complete the requested resource allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1ec70-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="1ec70-124">Remarks</span></span>  
 <span data-ttu-id="1ec70-125">Se a chamada para o CLR for feita de uma sequência originada em código gerenciado, cada chamada para `ReverseEnterRuntime` corresponderá a uma chamada para [ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span><span class="sxs-lookup"><span data-stu-id="1ec70-125">If the call into the CLR is made from a sequence that originated in managed code, each call to `ReverseEnterRuntime` corresponds to a call to [ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1ec70-126">As chamadas podem se originar de código não gerenciado sem serem aninhadas.</span><span class="sxs-lookup"><span data-stu-id="1ec70-126">Calls can originate from unmanaged code without being nested.</span></span> <span data-ttu-id="1ec70-127">Nesse caso, não há nenhuma chamada para [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)ou `ReverseLeaveRuntime`, e o número de chamadas para `ReverseEnterRuntime` não é igual ao número de chamadas para `ReverseLeaveRuntime`.</span><span class="sxs-lookup"><span data-stu-id="1ec70-127">In this case, there is no call to [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), or `ReverseLeaveRuntime`, and the number of calls to `ReverseEnterRuntime` does not equal the number of calls to `ReverseLeaveRuntime`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ec70-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1ec70-128">Requirements</span></span>  
 <span data-ttu-id="1ec70-129">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ec70-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ec70-130">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1ec70-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1ec70-131">**Biblioteca** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1ec70-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1ec70-132">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ec70-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ec70-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1ec70-133">See also</span></span>

- [<span data-ttu-id="1ec70-134">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="1ec70-134">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="1ec70-135">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="1ec70-135">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="1ec70-136">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="1ec70-136">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="1ec70-137">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="1ec70-137">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
