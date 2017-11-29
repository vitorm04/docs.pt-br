---
title: "Método ICLRGCManager::SetGCStartupLimits"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRGCManager.SetGCStartupLimits
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRGCManager::SetGCStartupLimits
helpviewer_keywords:
- SetGCStartupLimits method, ICLRGCManager interface [.NET Framework hosting]
- ICLRGCManager::SetGCStartupLimits method [.NET Framework hosting]
ms.assetid: 1c8d9959-95b5-4131-be4a-556d97774014
topic_type: apiref
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1fd0c31fd6f988d4ee36bfe140b95ec258d4214e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrgcmanagersetgcstartuplimits-method"></a><span data-ttu-id="5392e-102">Método ICLRGCManager::SetGCStartupLimits</span><span class="sxs-lookup"><span data-stu-id="5392e-102">ICLRGCManager::SetGCStartupLimits Method</span></span>
<span data-ttu-id="5392e-103">Define o tamanho de um segmento de coleta de lixo e o tamanho máximo da geração do sistema de coleta de lixo 0.</span><span class="sxs-lookup"><span data-stu-id="5392e-103">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5392e-104">Começando com o [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], você pode definir o tamanho do segmento e o tamanho máximo de geração 0 para valores maior `DWORD` usando o [Iclrgcmanager2](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="5392e-104">Starting with the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], you can set segment size and maximum generation 0 size to values greater than `DWORD` by using the [ICLRGCManager2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5392e-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5392e-105">Syntax</span></span>  
  
```  
HRESULT SetGCStartupLimits (  
    [in] DWORD SegmentSize,   
    [in] DWORD MaxGen0Size  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5392e-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5392e-106">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="5392e-107">[in] O tamanho especificado de um segmento de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="5392e-107">[in] The specified size of a garbage collection segment.</span></span>  
  
 <span data-ttu-id="5392e-108">O tamanho do segmento mínimo é de 4 MB.</span><span class="sxs-lookup"><span data-stu-id="5392e-108">The minimum segment size is 4 MB.</span></span> <span data-ttu-id="5392e-109">Segmentos podem ser aumentada em incrementos de 1 MB ou maior.</span><span class="sxs-lookup"><span data-stu-id="5392e-109">Segments can be increased in increments of 1 MB or larger.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="5392e-110">[in] O tamanho máximo especificado para a geração 0.</span><span class="sxs-lookup"><span data-stu-id="5392e-110">[in] The specified maximum size for generation 0.</span></span>  
  
 <span data-ttu-id="5392e-111">O tamanho mínimo de geração 0 é 64 KB.</span><span class="sxs-lookup"><span data-stu-id="5392e-111">The minimum generation 0 size is 64 KB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5392e-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="5392e-112">Return Value</span></span>  
  
|<span data-ttu-id="5392e-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5392e-113">HRESULT</span></span>|<span data-ttu-id="5392e-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="5392e-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5392e-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="5392e-115">S_OK</span></span>|<span data-ttu-id="5392e-116">`SetGCStartupLimits`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="5392e-116">`SetGCStartupLimits` returned successfully.</span></span>|  
|<span data-ttu-id="5392e-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5392e-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5392e-118">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="5392e-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5392e-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5392e-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5392e-120">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="5392e-120">The call timed out.</span></span>|  
|<span data-ttu-id="5392e-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5392e-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5392e-122">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="5392e-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5392e-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5392e-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5392e-124">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="5392e-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5392e-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5392e-125">E_FAIL</span></span>|<span data-ttu-id="5392e-126">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="5392e-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5392e-127">Depois que um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="5392e-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5392e-128">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="5392e-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5392e-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="5392e-129">Remarks</span></span>  
 <span data-ttu-id="5392e-130">Os valores que `SetGCStartupLimits` conjuntos podem ser especificados somente uma vez.</span><span class="sxs-lookup"><span data-stu-id="5392e-130">The values that `SetGCStartupLimits` sets can be specified only once.</span></span> <span data-ttu-id="5392e-131">Chamadas posteriores para `SetGCStartupLimits` são ignorados.</span><span class="sxs-lookup"><span data-stu-id="5392e-131">Later calls to `SetGCStartupLimits` are ignored.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5392e-132">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5392e-132">Requirements</span></span>  
 <span data-ttu-id="5392e-133">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5392e-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5392e-134">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5392e-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5392e-135">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="5392e-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5392e-136">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5392e-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5392e-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5392e-137">See Also</span></span>  
 [<span data-ttu-id="5392e-138">Gerenciamento Automático de Memória</span><span class="sxs-lookup"><span data-stu-id="5392e-138">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)  
 [<span data-ttu-id="5392e-139">Coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="5392e-139">Garbage Collection</span></span>](../../../../docs/standard/garbage-collection/index.md)  
 [<span data-ttu-id="5392e-140">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="5392e-140">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="5392e-141">Interface ICLRGCManager</span><span class="sxs-lookup"><span data-stu-id="5392e-141">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)
