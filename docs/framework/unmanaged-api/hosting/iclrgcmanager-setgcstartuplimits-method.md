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
ms.openlocfilehash: 0dce86a12ed3e93983ee62620fa0ddf7dfbc48f5
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616938"
---
# <a name="iclrgcmanagersetgcstartuplimits-method"></a><span data-ttu-id="27a8a-102">Método ICLRGCManager::SetGCStartupLimits</span><span class="sxs-lookup"><span data-stu-id="27a8a-102">ICLRGCManager::SetGCStartupLimits Method</span></span>
<span data-ttu-id="27a8a-103">Define o tamanho de um segmento de coleta de lixo e o tamanho máximo da geração 0 do sistema de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="27a8a-103">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="27a8a-104">A partir do .NET Framework 4,5, você pode definir o tamanho do segmento e o tamanho máximo de geração 0 para valores maiores do que `DWORD` usar o método [ICLRGCManager2:: SetGCStartupLimitsEx](iclrgcmanager2-setgcstartuplimitsex-method.md) .</span><span class="sxs-lookup"><span data-stu-id="27a8a-104">Starting with the .NET Framework 4.5, you can set segment size and maximum generation 0 size to values greater than `DWORD` by using the [ICLRGCManager2::SetGCStartupLimitsEx](iclrgcmanager2-setgcstartuplimitsex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27a8a-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="27a8a-105">Syntax</span></span>  
  
```cpp  
HRESULT SetGCStartupLimits (  
    [in] DWORD SegmentSize,
    [in] DWORD MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="27a8a-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="27a8a-106">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="27a8a-107">no O tamanho especificado de um segmento de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="27a8a-107">[in] The specified size of a garbage collection segment.</span></span>  
  
 <span data-ttu-id="27a8a-108">O tamanho mínimo do segmento é 4 MB.</span><span class="sxs-lookup"><span data-stu-id="27a8a-108">The minimum segment size is 4 MB.</span></span> <span data-ttu-id="27a8a-109">Os segmentos podem ser aumentados em incrementos de 1 MB ou mais.</span><span class="sxs-lookup"><span data-stu-id="27a8a-109">Segments can be increased in increments of 1 MB or larger.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="27a8a-110">no O tamanho máximo especificado para a geração 0.</span><span class="sxs-lookup"><span data-stu-id="27a8a-110">[in] The specified maximum size for generation 0.</span></span>  
  
 <span data-ttu-id="27a8a-111">O tamanho mínimo de 0 de geração é 64 KB.</span><span class="sxs-lookup"><span data-stu-id="27a8a-111">The minimum generation 0 size is 64 KB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="27a8a-112">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="27a8a-112">Return Value</span></span>  
  
|<span data-ttu-id="27a8a-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="27a8a-113">HRESULT</span></span>|<span data-ttu-id="27a8a-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="27a8a-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="27a8a-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="27a8a-115">S_OK</span></span>|<span data-ttu-id="27a8a-116">`SetGCStartupLimits`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="27a8a-116">`SetGCStartupLimits` returned successfully.</span></span>|  
|<span data-ttu-id="27a8a-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="27a8a-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="27a8a-118">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="27a8a-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="27a8a-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="27a8a-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="27a8a-120">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="27a8a-120">The call timed out.</span></span>|  
|<span data-ttu-id="27a8a-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="27a8a-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="27a8a-122">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="27a8a-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="27a8a-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="27a8a-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="27a8a-124">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="27a8a-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="27a8a-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="27a8a-125">E_FAIL</span></span>|<span data-ttu-id="27a8a-126">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="27a8a-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="27a8a-127">Depois que um método retorna E_FAIL, o CLR não pode mais ser usado no processo.</span><span class="sxs-lookup"><span data-stu-id="27a8a-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="27a8a-128">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="27a8a-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="27a8a-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="27a8a-129">Remarks</span></span>  
 <span data-ttu-id="27a8a-130">Os valores que `SetGCStartupLimits` definem podem ser especificados apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="27a8a-130">The values that `SetGCStartupLimits` sets can be specified only once.</span></span> <span data-ttu-id="27a8a-131">As chamadas posteriores para `SetGCStartupLimits` são ignoradas.</span><span class="sxs-lookup"><span data-stu-id="27a8a-131">Later calls to `SetGCStartupLimits` are ignored.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27a8a-132">Requisitos</span><span class="sxs-lookup"><span data-stu-id="27a8a-132">Requirements</span></span>  
 <span data-ttu-id="27a8a-133">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27a8a-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27a8a-134">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="27a8a-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="27a8a-135">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="27a8a-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="27a8a-136">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27a8a-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27a8a-137">Confira também</span><span class="sxs-lookup"><span data-stu-id="27a8a-137">See also</span></span>

- [<span data-ttu-id="27a8a-138">Gerenciamento automático de memória</span><span class="sxs-lookup"><span data-stu-id="27a8a-138">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="27a8a-139">Coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="27a8a-139">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="27a8a-140">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="27a8a-140">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="27a8a-141">Interface ICLRGCManager</span><span class="sxs-lookup"><span data-stu-id="27a8a-141">ICLRGCManager Interface</span></span>](iclrgcmanager-interface.md)
