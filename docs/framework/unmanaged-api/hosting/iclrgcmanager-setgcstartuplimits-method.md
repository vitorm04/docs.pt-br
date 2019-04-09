---
title: Método ICLRGCManager::SetGCStartupLimits
ms.date: 03/30/2017
api_name:
- ICLRGCManager.SetGCStartupLimits
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager::SetGCStartupLimits
helpviewer_keywords:
- SetGCStartupLimits method, ICLRGCManager interface [.NET Framework hosting]
- ICLRGCManager::SetGCStartupLimits method [.NET Framework hosting]
ms.assetid: 1c8d9959-95b5-4131-be4a-556d97774014
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1ffbe29db96cbb6162adc3b4cc77b45dcef27a46
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59117281"
---
# <a name="iclrgcmanagersetgcstartuplimits-method"></a><span data-ttu-id="6a3b5-102">Método ICLRGCManager::SetGCStartupLimits</span><span class="sxs-lookup"><span data-stu-id="6a3b5-102">ICLRGCManager::SetGCStartupLimits Method</span></span>
<span data-ttu-id="6a3b5-103">Define o tamanho de um segmento de coleta de lixo e o tamanho máximo da geração do sistema de coleta de lixo 0.</span><span class="sxs-lookup"><span data-stu-id="6a3b5-103">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6a3b5-104">Começando com o [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], você pode definir o tamanho do segmento de tamanho máximo de geração 0 para valores e maior `DWORD` usando o [ICLRGCManager2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="6a3b5-104">Starting with the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], you can set segment size and maximum generation 0 size to values greater than `DWORD` by using the [ICLRGCManager2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a3b5-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6a3b5-105">Syntax</span></span>  
  
```  
HRESULT SetGCStartupLimits (  
    [in] DWORD SegmentSize,   
    [in] DWORD MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6a3b5-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6a3b5-106">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="6a3b5-107">[in] O tamanho especificado de um segmento de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="6a3b5-107">[in] The specified size of a garbage collection segment.</span></span>  
  
 <span data-ttu-id="6a3b5-108">O tamanho do segmento mínimo é de 4 MB.</span><span class="sxs-lookup"><span data-stu-id="6a3b5-108">The minimum segment size is 4 MB.</span></span> <span data-ttu-id="6a3b5-109">Segmentos podem ser aumentado em incrementos de 1 MB ou maiores.</span><span class="sxs-lookup"><span data-stu-id="6a3b5-109">Segments can be increased in increments of 1 MB or larger.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="6a3b5-110">[in] O tamanho máximo especificado para a geração 0.</span><span class="sxs-lookup"><span data-stu-id="6a3b5-110">[in] The specified maximum size for generation 0.</span></span>  
  
 <span data-ttu-id="6a3b5-111">O tamanho mínimo de geração 0 é 64 KB.</span><span class="sxs-lookup"><span data-stu-id="6a3b5-111">The minimum generation 0 size is 64 KB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6a3b5-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="6a3b5-112">Return Value</span></span>  
  
|<span data-ttu-id="6a3b5-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6a3b5-113">HRESULT</span></span>|<span data-ttu-id="6a3b5-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="6a3b5-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6a3b5-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="6a3b5-115">S_OK</span></span>|`SetGCStartupLimits` <span data-ttu-id="6a3b5-116">retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="6a3b5-116">returned successfully.</span></span>|  
|<span data-ttu-id="6a3b5-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6a3b5-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6a3b5-118">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="6a3b5-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6a3b5-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6a3b5-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6a3b5-120">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="6a3b5-120">The call timed out.</span></span>|  
|<span data-ttu-id="6a3b5-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6a3b5-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6a3b5-122">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="6a3b5-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6a3b5-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6a3b5-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6a3b5-124">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="6a3b5-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6a3b5-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6a3b5-125">E_FAIL</span></span>|<span data-ttu-id="6a3b5-126">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="6a3b5-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6a3b5-127">Depois que um método retorna E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="6a3b5-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6a3b5-128">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="6a3b5-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6a3b5-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="6a3b5-129">Remarks</span></span>  
 <span data-ttu-id="6a3b5-130">Os valores que `SetGCStartupLimits` conjuntos podem ser especificados apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="6a3b5-130">The values that `SetGCStartupLimits` sets can be specified only once.</span></span> <span data-ttu-id="6a3b5-131">Chamadas posteriores para `SetGCStartupLimits` são ignorados.</span><span class="sxs-lookup"><span data-stu-id="6a3b5-131">Later calls to `SetGCStartupLimits` are ignored.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a3b5-132">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6a3b5-132">Requirements</span></span>  
 <span data-ttu-id="6a3b5-133">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a3b5-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a3b5-134">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6a3b5-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6a3b5-135">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="6a3b5-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="6a3b5-136">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="6a3b5-136">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6a3b5-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6a3b5-137">See also</span></span>

- [<span data-ttu-id="6a3b5-138">Gerenciamento automático de memória</span><span class="sxs-lookup"><span data-stu-id="6a3b5-138">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)
- [<span data-ttu-id="6a3b5-139">Coleta de Lixo</span><span class="sxs-lookup"><span data-stu-id="6a3b5-139">Garbage Collection</span></span>](../../../../docs/standard/garbage-collection/index.md)
- [<span data-ttu-id="6a3b5-140">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="6a3b5-140">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="6a3b5-141">Interface ICLRGCManager</span><span class="sxs-lookup"><span data-stu-id="6a3b5-141">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)
