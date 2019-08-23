---
title: Método ICLRGCManager2::SetGCStartupLimitsEx
ms.date: 03/30/2017
api_name:
- ICLRGCManager2.SetGCStartupLimitsEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager2::SetCLRGCStartupLimitsEx
helpviewer_keywords:
- ICLRGCManager2::SetGCStartupLimitsEx method [.NET Framework hosting]
- SetGCStartupLimitsEx method, ICLRGCManager2 interface [.NET Framework hosting]
ms.assetid: 6c3a08a9-5d65-48d4-8bbf-2a86ed7d356a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0d881c71d4725e1a73d743aa098aecc053182947
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918602"
---
# <a name="iclrgcmanager2setgcstartuplimitsex-method"></a><span data-ttu-id="b88ee-102">Método ICLRGCManager2::SetGCStartupLimitsEx</span><span class="sxs-lookup"><span data-stu-id="b88ee-102">ICLRGCManager2::SetGCStartupLimitsEx Method</span></span>
<span data-ttu-id="b88ee-103">Define o tamanho de um segmento de coleta de lixo e o tamanho máximo da geração 0 do sistema de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="b88ee-103">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b88ee-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b88ee-104">Syntax</span></span>  
  
```cpp  
HRESULT SetGCStartupLimitsEx (  
    [in] SIZE_T SegmentSize,   
    [in] SIZE_T MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b88ee-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b88ee-105">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="b88ee-106">no O tamanho especificado de um segmento de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="b88ee-106">[in] The specified size of a garbage collection segment.</span></span>  
  
 <span data-ttu-id="b88ee-107">O tamanho mínimo do segmento é 4 MB.</span><span class="sxs-lookup"><span data-stu-id="b88ee-107">The minimum segment size is 4 MB.</span></span> <span data-ttu-id="b88ee-108">Os segmentos podem ser aumentados em incrementos de 1 MB ou mais.</span><span class="sxs-lookup"><span data-stu-id="b88ee-108">Segments can be increased in increments of 1 MB or larger.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="b88ee-109">no O tamanho máximo especificado para a geração 0.</span><span class="sxs-lookup"><span data-stu-id="b88ee-109">[in] The specified maximum size for generation 0.</span></span>  
  
 <span data-ttu-id="b88ee-110">O tamanho mínimo de 0 de geração é 64 KB.</span><span class="sxs-lookup"><span data-stu-id="b88ee-110">The minimum generation 0 size is 64 KB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b88ee-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="b88ee-111">Return Value</span></span>  
  
|<span data-ttu-id="b88ee-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b88ee-112">HRESULT</span></span>|<span data-ttu-id="b88ee-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="b88ee-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b88ee-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="b88ee-114">S_OK</span></span>|<span data-ttu-id="b88ee-115">`SetGCStartupLimitsEx`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="b88ee-115">`SetGCStartupLimitsEx` returned successfully.</span></span>|  
|<span data-ttu-id="b88ee-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b88ee-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b88ee-117">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="b88ee-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b88ee-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b88ee-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b88ee-119">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="b88ee-119">The call timed out.</span></span>|  
|<span data-ttu-id="b88ee-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b88ee-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b88ee-121">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="b88ee-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b88ee-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b88ee-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b88ee-123">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="b88ee-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b88ee-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b88ee-124">E_FAIL</span></span>|<span data-ttu-id="b88ee-125">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="b88ee-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b88ee-126">Depois que um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="b88ee-126">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b88ee-127">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b88ee-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b88ee-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="b88ee-128">Remarks</span></span>  
 <span data-ttu-id="b88ee-129">Os valores que `SetGCStartupLimitsEx` conjuntos só podem ser especificados antes do host ser iniciado.</span><span class="sxs-lookup"><span data-stu-id="b88ee-129">The values that `SetGCStartupLimitsEx` sets can be specified only before the host is started.</span></span> <span data-ttu-id="b88ee-130">As chamadas posteriores para `SetGCStartupLimitsEx` são ignoradas.</span><span class="sxs-lookup"><span data-stu-id="b88ee-130">Later calls to `SetGCStartupLimitsEx` are ignored.</span></span>  
  
 <span data-ttu-id="b88ee-131">Para definir qualquer parâmetro sem afetar o outro, especifique 0 (zero) para o parâmetro que você não deseja alterar.</span><span class="sxs-lookup"><span data-stu-id="b88ee-131">To set either parameter without affecting the other, specify 0 (zero) for the parameter you don't want to change.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b88ee-132">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b88ee-132">Requirements</span></span>  
 <span data-ttu-id="b88ee-133">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b88ee-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b88ee-134">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b88ee-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b88ee-135">**Biblioteca** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b88ee-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b88ee-136">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b88ee-136">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b88ee-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b88ee-137">See also</span></span>

- [<span data-ttu-id="b88ee-138">Gerenciamento Automático de Memória</span><span class="sxs-lookup"><span data-stu-id="b88ee-138">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="b88ee-139">Coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="b88ee-139">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="b88ee-140">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="b88ee-140">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="b88ee-141">Interface ICLRGCManager2</span><span class="sxs-lookup"><span data-stu-id="b88ee-141">ICLRGCManager2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md)
