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
ms.openlocfilehash: 7b30919f6d89f151a93fc46407165279187ef6e4
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67749480"
---
# <a name="ihosttaskmanagerreverseenterruntime-method"></a><span data-ttu-id="3877a-102">Método IHostTaskManager::ReverseEnterRuntime</span><span class="sxs-lookup"><span data-stu-id="3877a-102">IHostTaskManager::ReverseEnterRuntime Method</span></span>
<span data-ttu-id="3877a-103">Notifica o host que está sendo feita uma chamada para o common language runtime (CLR) do código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="3877a-103">Notifies the host that a call is being made into the common language runtime (CLR) from unmanaged code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3877a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3877a-104">Syntax</span></span>  
  
```cpp  
HRESULT ReverseEnterRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="3877a-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="3877a-105">Return Value</span></span>  
  
|<span data-ttu-id="3877a-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3877a-106">HRESULT</span></span>|<span data-ttu-id="3877a-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="3877a-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3877a-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="3877a-108">S_OK</span></span>|<span data-ttu-id="3877a-109">`ReverseEnterRuntime` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="3877a-109">`ReverseEnterRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="3877a-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3877a-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3877a-111">O CLR não tenha sido carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="3877a-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3877a-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3877a-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3877a-113">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="3877a-113">The call timed out.</span></span>|  
|<span data-ttu-id="3877a-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3877a-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3877a-115">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="3877a-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3877a-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3877a-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3877a-117">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="3877a-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3877a-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3877a-118">E_FAIL</span></span>|<span data-ttu-id="3877a-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="3877a-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3877a-120">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="3877a-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3877a-121">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="3877a-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="3877a-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="3877a-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="3877a-123">Não há memória suficiente está disponível para concluir a alocação de recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="3877a-123">Not enough memory is available to complete the requested resource allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3877a-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="3877a-124">Remarks</span></span>  
 <span data-ttu-id="3877a-125">Se a chamada para o CLR é feita de uma sequência que tenham sido originados no código gerenciado, cada chamada para `ReverseEnterRuntime` corresponde a uma chamada para [ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span><span class="sxs-lookup"><span data-stu-id="3877a-125">If the call into the CLR is made from a sequence that originated in managed code, each call to `ReverseEnterRuntime` corresponds to a call to [ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3877a-126">Chamadas podem se originar de código não gerenciado sem estar aninhada.</span><span class="sxs-lookup"><span data-stu-id="3877a-126">Calls can originate from unmanaged code without being nested.</span></span> <span data-ttu-id="3877a-127">Nesse caso, não há nenhuma chamada para [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), ou `ReverseLeaveRuntime`e o número de chamadas para `ReverseEnterRuntime` não é igual ao número de chamadas para `ReverseLeaveRuntime`.</span><span class="sxs-lookup"><span data-stu-id="3877a-127">In this case, there is no call to [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), or `ReverseLeaveRuntime`, and the number of calls to `ReverseEnterRuntime` does not equal the number of calls to `ReverseLeaveRuntime`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3877a-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3877a-128">Requirements</span></span>  
 <span data-ttu-id="3877a-129">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3877a-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3877a-130">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3877a-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3877a-131">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="3877a-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3877a-132">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3877a-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3877a-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3877a-133">See also</span></span>

- [<span data-ttu-id="3877a-134">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="3877a-134">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="3877a-135">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="3877a-135">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="3877a-136">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="3877a-136">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="3877a-137">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="3877a-137">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
