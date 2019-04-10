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
ms.openlocfilehash: 6eefdaf5dee423b0a9ae054446224a3ea97e3c9b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59213773"
---
# <a name="ihosttaskmanagerreverseenterruntime-method"></a><span data-ttu-id="4ce64-102">Método IHostTaskManager::ReverseEnterRuntime</span><span class="sxs-lookup"><span data-stu-id="4ce64-102">IHostTaskManager::ReverseEnterRuntime Method</span></span>
<span data-ttu-id="4ce64-103">Notifica o host que está sendo feita uma chamada para o common language runtime (CLR) do código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="4ce64-103">Notifies the host that a call is being made into the common language runtime (CLR) from unmanaged code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ce64-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4ce64-104">Syntax</span></span>  
  
```  
HRESULT ReverseEnterRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="4ce64-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="4ce64-105">Return Value</span></span>  
  
|<span data-ttu-id="4ce64-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4ce64-106">HRESULT</span></span>|<span data-ttu-id="4ce64-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="4ce64-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4ce64-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="4ce64-108">S_OK</span></span>|`ReverseEnterRuntime` <span data-ttu-id="4ce64-109">retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="4ce64-109">returned successfully.</span></span>|  
|<span data-ttu-id="4ce64-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4ce64-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4ce64-111">O CLR não tenha sido carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="4ce64-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4ce64-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4ce64-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4ce64-113">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="4ce64-113">The call timed out.</span></span>|  
|<span data-ttu-id="4ce64-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4ce64-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4ce64-115">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="4ce64-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4ce64-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4ce64-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4ce64-117">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="4ce64-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4ce64-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4ce64-118">E_FAIL</span></span>|<span data-ttu-id="4ce64-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="4ce64-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4ce64-120">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="4ce64-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4ce64-121">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="4ce64-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="4ce64-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="4ce64-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="4ce64-123">Não há memória suficiente está disponível para concluir a alocação de recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="4ce64-123">Not enough memory is available to complete the requested resource allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4ce64-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="4ce64-124">Remarks</span></span>  
 <span data-ttu-id="4ce64-125">Se a chamada para o CLR é feita de uma sequência que tenham sido originados no código gerenciado, cada chamada para `ReverseEnterRuntime` corresponde a uma chamada para [ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span><span class="sxs-lookup"><span data-stu-id="4ce64-125">If the call into the CLR is made from a sequence that originated in managed code, each call to `ReverseEnterRuntime` corresponds to a call to [ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4ce64-126">Chamadas podem se originar de código não gerenciado sem estar aninhada.</span><span class="sxs-lookup"><span data-stu-id="4ce64-126">Calls can originate from unmanaged code without being nested.</span></span> <span data-ttu-id="4ce64-127">Nesse caso, não há nenhuma chamada para [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), ou `ReverseLeaveRuntime`e o número de chamadas para `ReverseEnterRuntime` não é igual ao número de chamadas para `ReverseLeaveRuntime`.</span><span class="sxs-lookup"><span data-stu-id="4ce64-127">In this case, there is no call to [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), or `ReverseLeaveRuntime`, and the number of calls to `ReverseEnterRuntime` does not equal the number of calls to `ReverseLeaveRuntime`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ce64-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4ce64-128">Requirements</span></span>  
 <span data-ttu-id="4ce64-129">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4ce64-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ce64-130">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4ce64-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4ce64-131">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="4ce64-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="4ce64-132">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="4ce64-132">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4ce64-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4ce64-133">See also</span></span>

- [<span data-ttu-id="4ce64-134">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="4ce64-134">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="4ce64-135">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="4ce64-135">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="4ce64-136">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="4ce64-136">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="4ce64-137">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="4ce64-137">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
