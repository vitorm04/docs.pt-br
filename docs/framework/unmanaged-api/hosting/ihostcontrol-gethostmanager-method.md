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
ms.openlocfilehash: 25e931ec17cad3508d548fb4ca7e53b0ade3f119
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804962"
---
# <a name="ihostcontrolgethostmanager-method"></a><span data-ttu-id="df0b2-102">Método IHostControl::GetHostManager</span><span class="sxs-lookup"><span data-stu-id="df0b2-102">IHostControl::GetHostManager Method</span></span>
<span data-ttu-id="df0b2-103">Obtém um ponteiro de interface para a implementação do host da interface com o especificado `IID` .</span><span class="sxs-lookup"><span data-stu-id="df0b2-103">Gets an interface pointer to the host's implementation of the interface with the specified `IID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df0b2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="df0b2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHostManager (  
    [in] REFIID riid,  
    [out, iid_is(riid)] void** ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="df0b2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="df0b2-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="df0b2-106">no O `IID` da interface que o Common Language Runtime (CLR) está consultando.</span><span class="sxs-lookup"><span data-stu-id="df0b2-106">[in] The `IID` of the interface that the common language runtime (CLR) is querying for.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="df0b2-107">fora Um ponteiro para a interface implementada pelo host, ou NULL se o host não oferecer suporte a essa interface.</span><span class="sxs-lookup"><span data-stu-id="df0b2-107">[out] A pointer to the host-implemented interface, or null if the host does not support this interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="df0b2-108">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="df0b2-108">Return Value</span></span>  
  
|<span data-ttu-id="df0b2-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="df0b2-109">HRESULT</span></span>|<span data-ttu-id="df0b2-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="df0b2-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="df0b2-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="df0b2-111">S_OK</span></span>|<span data-ttu-id="df0b2-112">`GetHostManager`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="df0b2-112">`GetHostManager` returned successfully.</span></span>|  
|<span data-ttu-id="df0b2-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="df0b2-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="df0b2-114">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="df0b2-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="df0b2-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="df0b2-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="df0b2-116">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="df0b2-116">The call timed out.</span></span>|  
|<span data-ttu-id="df0b2-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="df0b2-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="df0b2-118">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="df0b2-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="df0b2-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="df0b2-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="df0b2-120">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="df0b2-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="df0b2-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="df0b2-121">E_FAIL</span></span>|<span data-ttu-id="df0b2-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="df0b2-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="df0b2-123">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="df0b2-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="df0b2-124">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="df0b2-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="df0b2-125">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="df0b2-125">E_INVALIDARG</span></span>|<span data-ttu-id="df0b2-126">O solicitado `IID` não é válido.</span><span class="sxs-lookup"><span data-stu-id="df0b2-126">The requested `IID` is not valid.</span></span>|  
|<span data-ttu-id="df0b2-127">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="df0b2-127">E_NOINTERFACE</span></span>|<span data-ttu-id="df0b2-128">Não há suporte para a interface solicitada.</span><span class="sxs-lookup"><span data-stu-id="df0b2-128">The requested interface is not supported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="df0b2-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="df0b2-129">Remarks</span></span>  
 <span data-ttu-id="df0b2-130">O CLR consulta o host para determinar se ele dá suporte a uma ou mais das seguintes interfaces:</span><span class="sxs-lookup"><span data-stu-id="df0b2-130">The CLR queries the host to determine whether it supports one or more of the following interfaces:</span></span>  
  
- [<span data-ttu-id="df0b2-131">IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="df0b2-131">IHostMemoryManager</span></span>](ihostmemorymanager-interface.md)  
  
- [<span data-ttu-id="df0b2-132">IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="df0b2-132">IHostTaskManager</span></span>](ihosttaskmanager-interface.md)  
  
- [<span data-ttu-id="df0b2-133">IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="df0b2-133">IHostThreadPoolManager</span></span>](ihostthreadpoolmanager-interface.md)  
  
- [<span data-ttu-id="df0b2-134">IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="df0b2-134">IHostIoCompletionManager</span></span>](ihostiocompletionmanager-interface.md)  
  
- [<span data-ttu-id="df0b2-135">IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="df0b2-135">IHostSyncManager</span></span>](ihostsyncmanager-interface.md)  
  
- [<span data-ttu-id="df0b2-136">IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="df0b2-136">IHostAssemblyManager</span></span>](ihostassemblymanager-interface.md)  
  
- [<span data-ttu-id="df0b2-137">IHostGCManager</span><span class="sxs-lookup"><span data-stu-id="df0b2-137">IHostGCManager</span></span>](ihostgcmanager-interface.md)  
  
- [<span data-ttu-id="df0b2-138">O IHostPolicyManager</span><span class="sxs-lookup"><span data-stu-id="df0b2-138">IHostPolicyManager</span></span>](ihostpolicymanager-interface.md)  
  
- [<span data-ttu-id="df0b2-139">IHostSecurityManager</span><span class="sxs-lookup"><span data-stu-id="df0b2-139">IHostSecurityManager</span></span>](ihostsecuritymanager-interface.md)  
  
 <span data-ttu-id="df0b2-140">Se o host oferecer suporte à interface especificada, ele definirá `ppObject` como sua implementação dessa interface.</span><span class="sxs-lookup"><span data-stu-id="df0b2-140">If the host supports the specified interface, it sets `ppObject` to its implementation of that interface.</span></span> <span data-ttu-id="df0b2-141">Caso contrário, ele será definido `ppObject` como NULL.</span><span class="sxs-lookup"><span data-stu-id="df0b2-141">Otherwise, it sets `ppObject` to null.</span></span>  
  
 <span data-ttu-id="df0b2-142">O CLR não chama `Release` os gerenciadores de host, mesmo quando você o desliga.</span><span class="sxs-lookup"><span data-stu-id="df0b2-142">The CLR does not call `Release` on host managers, even when you shut it down.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df0b2-143">Requisitos</span><span class="sxs-lookup"><span data-stu-id="df0b2-143">Requirements</span></span>  
 <span data-ttu-id="df0b2-144">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df0b2-144">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df0b2-145">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="df0b2-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="df0b2-146">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="df0b2-146">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="df0b2-147">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df0b2-147">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df0b2-148">Confira também</span><span class="sxs-lookup"><span data-stu-id="df0b2-148">See also</span></span>

- [<span data-ttu-id="df0b2-149">Interface IHostControl</span><span class="sxs-lookup"><span data-stu-id="df0b2-149">IHostControl Interface</span></span>](ihostcontrol-interface.md)
