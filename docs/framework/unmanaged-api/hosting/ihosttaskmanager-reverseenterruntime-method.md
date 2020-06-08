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
ms.openlocfilehash: 1981fdf25440a296801bdbd06c41ebcb4b87e870
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501378"
---
# <a name="ihosttaskmanagerreverseenterruntime-method"></a><span data-ttu-id="6670d-102">Método IHostTaskManager::ReverseEnterRuntime</span><span class="sxs-lookup"><span data-stu-id="6670d-102">IHostTaskManager::ReverseEnterRuntime Method</span></span>
<span data-ttu-id="6670d-103">Notifica o host de que uma chamada está sendo feita no Common Language Runtime (CLR) de código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="6670d-103">Notifies the host that a call is being made into the common language runtime (CLR) from unmanaged code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6670d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6670d-104">Syntax</span></span>  
  
```cpp  
HRESULT ReverseEnterRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="6670d-105">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="6670d-105">Return Value</span></span>  
  
|<span data-ttu-id="6670d-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6670d-106">HRESULT</span></span>|<span data-ttu-id="6670d-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="6670d-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6670d-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="6670d-108">S_OK</span></span>|<span data-ttu-id="6670d-109">`ReverseEnterRuntime`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="6670d-109">`ReverseEnterRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="6670d-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6670d-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6670d-111">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="6670d-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6670d-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6670d-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6670d-113">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="6670d-113">The call timed out.</span></span>|  
|<span data-ttu-id="6670d-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6670d-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6670d-115">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="6670d-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6670d-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6670d-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6670d-117">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="6670d-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6670d-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6670d-118">E_FAIL</span></span>|<span data-ttu-id="6670d-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="6670d-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6670d-120">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="6670d-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6670d-121">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="6670d-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="6670d-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="6670d-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="6670d-123">Não há memória suficiente disponível para concluir a alocação de recursos solicitada.</span><span class="sxs-lookup"><span data-stu-id="6670d-123">Not enough memory is available to complete the requested resource allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6670d-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="6670d-124">Remarks</span></span>  
 <span data-ttu-id="6670d-125">Se a chamada para o CLR for feita de uma sequência originada em código gerenciado, cada chamada para `ReverseEnterRuntime` corresponderá a uma chamada para [ReverseLeaveRuntime](ihosttaskmanager-reverseleaveruntime-method.md).</span><span class="sxs-lookup"><span data-stu-id="6670d-125">If the call into the CLR is made from a sequence that originated in managed code, each call to `ReverseEnterRuntime` corresponds to a call to [ReverseLeaveRuntime](ihosttaskmanager-reverseleaveruntime-method.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6670d-126">As chamadas podem se originar de código não gerenciado sem serem aninhadas.</span><span class="sxs-lookup"><span data-stu-id="6670d-126">Calls can originate from unmanaged code without being nested.</span></span> <span data-ttu-id="6670d-127">Nesse caso, não há nenhuma chamada para [EnterRuntime](ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](ihosttaskmanager-leaveruntime-method.md)ou `ReverseLeaveRuntime` , e o número de chamadas para não `ReverseEnterRuntime` é igual ao número de chamadas para `ReverseLeaveRuntime` .</span><span class="sxs-lookup"><span data-stu-id="6670d-127">In this case, there is no call to [EnterRuntime](ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](ihosttaskmanager-leaveruntime-method.md), or `ReverseLeaveRuntime`, and the number of calls to `ReverseEnterRuntime` does not equal the number of calls to `ReverseLeaveRuntime`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6670d-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6670d-128">Requirements</span></span>  
 <span data-ttu-id="6670d-129">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6670d-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6670d-130">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6670d-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6670d-131">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6670d-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6670d-132">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6670d-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6670d-133">Confira também</span><span class="sxs-lookup"><span data-stu-id="6670d-133">See also</span></span>

- [<span data-ttu-id="6670d-134">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="6670d-134">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="6670d-135">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="6670d-135">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="6670d-136">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="6670d-136">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="6670d-137">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="6670d-137">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
