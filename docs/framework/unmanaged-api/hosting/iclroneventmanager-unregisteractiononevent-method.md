---
title: "Método ICLROnEventManager::UnregisterActionOnEvent"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLROnEventManager.UnregisterActionOnEvent
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLROnEventManager::UnregisterActionOnEvent
helpviewer_keywords:
- UnRegisterActionOnEvent method [.NET Framework hosting]
- ICLROnEventManager::UnRegisterActionOnEvent method [.NET Framework hosting]
ms.assetid: 4c02ec37-cdf0-46b2-890e-235092741236
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8d295817a7c6f8a177de3ff251904beeaf8ca828
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclroneventmanagerunregisteractiononevent-method"></a><span data-ttu-id="b2369-102">Método ICLROnEventManager::UnregisterActionOnEvent</span><span class="sxs-lookup"><span data-stu-id="b2369-102">ICLROnEventManager::UnregisterActionOnEvent Method</span></span>
<span data-ttu-id="b2369-103">Cancela o registro de um ponteiro de retorno de chamada registrado anteriormente para o evento especificado.</span><span class="sxs-lookup"><span data-stu-id="b2369-103">Unregisters a previously registered callback pointer for the specified event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2369-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b2369-104">Syntax</span></span>  
  
```  
HRESULT UnregisterActionOnEvent (  
    [in] EClrEvent event,  
    [in] IActionOnCLREvent *pAction  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b2369-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b2369-105">Parameters</span></span>  
 `event`  
 <span data-ttu-id="b2369-106">[in] Uma da [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) valores, indicando que o evento para o qual cancelar o registro de ponteiro de retorno de chamada descrito pelo `pAction`.</span><span class="sxs-lookup"><span data-stu-id="b2369-106">[in] One of the [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) values, indicating the event for which to unregister the callback pointer described by `pAction`.</span></span>  
  
 `pAction`  
 <span data-ttu-id="b2369-107">[in] Um ponteiro para um [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) objeto passado como um parâmetro para o [RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="b2369-107">[in] A pointer to an [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) object that was passed as a parameter to the [RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b2369-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="b2369-108">Return Value</span></span>  
  
|<span data-ttu-id="b2369-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b2369-109">HRESULT</span></span>|<span data-ttu-id="b2369-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="b2369-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b2369-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="b2369-111">S_OK</span></span>|<span data-ttu-id="b2369-112">`UnregisterActionOnEvent`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="b2369-112">`UnregisterActionOnEvent` returned successfully.</span></span>|  
|<span data-ttu-id="b2369-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b2369-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b2369-114">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="b2369-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b2369-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b2369-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b2369-116">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="b2369-116">The call timed out.</span></span>|  
|<span data-ttu-id="b2369-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b2369-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b2369-118">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="b2369-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b2369-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b2369-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b2369-120">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="b2369-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b2369-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b2369-121">E_FAIL</span></span>|<span data-ttu-id="b2369-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="b2369-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b2369-123">Depois que um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="b2369-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b2369-124">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b2369-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b2369-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b2369-125">Requirements</span></span>  
 <span data-ttu-id="b2369-126">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2369-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2369-127">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b2369-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b2369-128">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="b2369-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b2369-129">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2369-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2369-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b2369-130">See Also</span></span>  
 [<span data-ttu-id="b2369-131">Enumeração EClrEvent</span><span class="sxs-lookup"><span data-stu-id="b2369-131">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)  
 [<span data-ttu-id="b2369-132">Interface IActionOnCLREvent</span><span class="sxs-lookup"><span data-stu-id="b2369-132">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)  
 [<span data-ttu-id="b2369-133">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="b2369-133">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="b2369-134">Interface ICLROnEventManager</span><span class="sxs-lookup"><span data-stu-id="b2369-134">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)
