---
title: "Método IHostAutoEvent::Wait"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IHostAutoEvent.Wait
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAutoEvent::Wait
helpviewer_keywords:
- Wait method, IHostAutoEvent interface [.NET Framework hosting]
- IHostAutoEvent::Wait method [.NET Framework hosting]
ms.assetid: 535d51c5-9112-401b-8c36-85f35d7ee609
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e4646e0bd04d69e7fe0125740c9c6e0c1b014071
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostautoeventwait-method"></a><span data-ttu-id="0ade8-102">Método IHostAutoEvent::Wait</span><span class="sxs-lookup"><span data-stu-id="0ade8-102">IHostAutoEvent::Wait Method</span></span>
<span data-ttu-id="0ade8-103">Faz com que o atual [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instância para aguardar até que ele é de propriedade ou um período de tempo especificado.</span><span class="sxs-lookup"><span data-stu-id="0ade8-103">Causes the current [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance to wait until it is owned or a specified amount of time elapses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ade8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0ade8-104">Syntax</span></span>  
  
```  
HRESULT Wait (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0ade8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ade8-105">Parameters</span></span>  
 `dwMilliseconds`  
 <span data-ttu-id="0ade8-106">[in] O número de milissegundos atual `IHostAutoEvent` instância deve esperar antes de retornar se nenhum thread ou fibra assume a propriedade.</span><span class="sxs-lookup"><span data-stu-id="0ade8-106">[in] The number of milliseconds the current `IHostAutoEvent` instance should wait before returning, if no thread or fiber takes ownership.</span></span>  
  
 `option`  
 <span data-ttu-id="0ade8-107">[in] Uma da [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) valores, especificar a ação que o host deve executar se este blocos de operação.</span><span class="sxs-lookup"><span data-stu-id="0ade8-107">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, specifying the action the host should take if this operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0ade8-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="0ade8-108">Return Value</span></span>  
  
|<span data-ttu-id="0ade8-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0ade8-109">HRESULT</span></span>|<span data-ttu-id="0ade8-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ade8-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0ade8-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="0ade8-111">S_OK</span></span>|<span data-ttu-id="0ade8-112">`Wait`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="0ade8-112">`Wait` returned successfully.</span></span>|  
|<span data-ttu-id="0ade8-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0ade8-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0ade8-114">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="0ade8-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0ade8-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0ade8-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0ade8-116">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="0ade8-116">The call timed out.</span></span>|  
|<span data-ttu-id="0ade8-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0ade8-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0ade8-118">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="0ade8-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0ade8-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0ade8-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0ade8-120">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="0ade8-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0ade8-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0ade8-121">E_FAIL</span></span>|<span data-ttu-id="0ade8-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="0ade8-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0ade8-123">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="0ade8-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0ade8-124">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0ade8-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0ade8-125">HOST_E_DEADLOCK</span><span class="sxs-lookup"><span data-stu-id="0ade8-125">HOST_E_DEADLOCK</span></span>|<span data-ttu-id="0ade8-126">O host detectou um deadlock durante o intervalo de espera e escolher o evento representado por atual `IHostAutoEvent` instância como vítima de deadlock.</span><span class="sxs-lookup"><span data-stu-id="0ade8-126">The host detected a deadlock during the wait interval, and chose the event represented by the current `IHostAutoEvent` instance as the deadlock victim.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0ade8-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0ade8-127">Requirements</span></span>  
 <span data-ttu-id="0ade8-128">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ade8-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ade8-129">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0ade8-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0ade8-130">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="0ade8-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0ade8-131">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ade8-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ade8-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ade8-132">See Also</span></span>  
 [<span data-ttu-id="0ade8-133">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="0ade8-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="0ade8-134">Interface IHostAutoEvent</span><span class="sxs-lookup"><span data-stu-id="0ade8-134">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="0ade8-135">Interface IHostManualEvent</span><span class="sxs-lookup"><span data-stu-id="0ade8-135">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="0ade8-136">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="0ade8-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
