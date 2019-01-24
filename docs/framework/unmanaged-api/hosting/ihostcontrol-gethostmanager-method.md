---
title: Método IHostControl::GetHostManager
ms.date: 03/30/2017
api_name:
- IHostControl.GetHostManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostControl::GetHostManager
helpviewer_keywords:
- GetHostManager method [.NET Framework hosting]
- IHostControl::GetHostManager method [.NET Framework hosting]
ms.assetid: 0fa34bca-ed18-4626-9e78-d33684d18edb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 821968fbde6d3f5434b83adf8c9661fe39d96293
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54742023"
---
# <a name="ihostcontrolgethostmanager-method"></a><span data-ttu-id="76b92-102">Método IHostControl::GetHostManager</span><span class="sxs-lookup"><span data-stu-id="76b92-102">IHostControl::GetHostManager Method</span></span>
<span data-ttu-id="76b92-103">Obtém um ponteiro de interface para a implementação do host da interface com especificado `IID`.</span><span class="sxs-lookup"><span data-stu-id="76b92-103">Gets an interface pointer to the host's implementation of the interface with the specified `IID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76b92-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="76b92-104">Syntax</span></span>  
  
```  
HRESULT GetHostManager (  
    [in] REFIID riid,  
    [out, iid_is(riid)] void** ppObject  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="76b92-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="76b92-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="76b92-106">[in] O `IID` da interface que está consultando o common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="76b92-106">[in] The `IID` of the interface that the common language runtime (CLR) is querying for.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="76b92-107">[out] Um ponteiro para a interface implementada pelo host ou nulo se o host não dá suporte a essa interface.</span><span class="sxs-lookup"><span data-stu-id="76b92-107">[out] A pointer to the host-implemented interface, or null if the host does not support this interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="76b92-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="76b92-108">Return Value</span></span>  
  
|<span data-ttu-id="76b92-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="76b92-109">HRESULT</span></span>|<span data-ttu-id="76b92-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="76b92-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="76b92-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="76b92-111">S_OK</span></span>|<span data-ttu-id="76b92-112">`GetHostManager` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="76b92-112">`GetHostManager` returned successfully.</span></span>|  
|<span data-ttu-id="76b92-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="76b92-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="76b92-114">O CLR não tenha sido carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="76b92-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="76b92-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="76b92-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="76b92-116">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="76b92-116">The call timed out.</span></span>|  
|<span data-ttu-id="76b92-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="76b92-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="76b92-118">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="76b92-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="76b92-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="76b92-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="76b92-120">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="76b92-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="76b92-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="76b92-121">E_FAIL</span></span>|<span data-ttu-id="76b92-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="76b92-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="76b92-123">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="76b92-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="76b92-124">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="76b92-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="76b92-125">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="76b92-125">E_INVALIDARG</span></span>|<span data-ttu-id="76b92-126">A solicitação `IID` não é válido.</span><span class="sxs-lookup"><span data-stu-id="76b92-126">The requested `IID` is not valid.</span></span>|  
|<span data-ttu-id="76b92-127">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="76b92-127">E_NOINTERFACE</span></span>|<span data-ttu-id="76b92-128">Não há suporte para a interface solicitada.</span><span class="sxs-lookup"><span data-stu-id="76b92-128">The requested interface is not supported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="76b92-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="76b92-129">Remarks</span></span>  
 <span data-ttu-id="76b92-130">O CLR consulta o host para determinar se ele dá suporte a uma ou mais das seguintes interfaces:</span><span class="sxs-lookup"><span data-stu-id="76b92-130">The CLR queries the host to determine whether it supports one or more of the following interfaces:</span></span>  
  
-   [<span data-ttu-id="76b92-131">IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="76b92-131">IHostMemoryManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
  
-   [<span data-ttu-id="76b92-132">IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="76b92-132">IHostTaskManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
  
-   [<span data-ttu-id="76b92-133">IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="76b92-133">IHostThreadPoolManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)  
  
-   [<span data-ttu-id="76b92-134">IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="76b92-134">IHostIoCompletionManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
  
-   [<span data-ttu-id="76b92-135">IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="76b92-135">IHostSyncManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
  
-   [<span data-ttu-id="76b92-136">IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="76b92-136">IHostAssemblyManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
  
-   [<span data-ttu-id="76b92-137">IHostGCManager</span><span class="sxs-lookup"><span data-stu-id="76b92-137">IHostGCManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)  
  
-   [<span data-ttu-id="76b92-138">IHostPolicyManager</span><span class="sxs-lookup"><span data-stu-id="76b92-138">IHostPolicyManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
  
-   [<span data-ttu-id="76b92-139">IHostSecurityManager</span><span class="sxs-lookup"><span data-stu-id="76b92-139">IHostSecurityManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
  
 <span data-ttu-id="76b92-140">Se o host oferece suporte a interface especificada, ele define `ppObject` à sua implementação dessa interface.</span><span class="sxs-lookup"><span data-stu-id="76b92-140">If the host supports the specified interface, it sets `ppObject` to its implementation of that interface.</span></span> <span data-ttu-id="76b92-141">Caso contrário, ele define `ppObject` como null.</span><span class="sxs-lookup"><span data-stu-id="76b92-141">Otherwise, it sets `ppObject` to null.</span></span>  
  
 <span data-ttu-id="76b92-142">O CLR não chama `Release` sobre gerenciadores de host, mesmo quando você desligar.</span><span class="sxs-lookup"><span data-stu-id="76b92-142">The CLR does not call `Release` on host managers, even when you shut it down.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76b92-143">Requisitos</span><span class="sxs-lookup"><span data-stu-id="76b92-143">Requirements</span></span>  
 <span data-ttu-id="76b92-144">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="76b92-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76b92-145">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="76b92-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="76b92-146">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="76b92-146">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="76b92-147">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76b92-147">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76b92-148">Consulte também</span><span class="sxs-lookup"><span data-stu-id="76b92-148">See also</span></span>
- [<span data-ttu-id="76b92-149">Interface IHostControl</span><span class="sxs-lookup"><span data-stu-id="76b92-149">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
