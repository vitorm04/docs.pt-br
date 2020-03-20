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
ms.openlocfilehash: 645b64c8b536029663c350bdcde9a716a715aab3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178092"
---
# <a name="iclrgcmanagersetgcstartuplimits-method"></a><span data-ttu-id="bf786-102">Método ICLRGCManager::SetGCStartupLimits</span><span class="sxs-lookup"><span data-stu-id="bf786-102">ICLRGCManager::SetGCStartupLimits Method</span></span>
<span data-ttu-id="bf786-103">Define o tamanho de um segmento de coleta de lixo e o tamanho máximo da geração 0 do sistema de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="bf786-103">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="bf786-104">Começando com o .NET Framework 4.5, você pode definir o `DWORD` tamanho do segmento e o tamanho máximo da geração 0 para valores maiores do que usando o método [ICLRGCManager2::SetGCStartupLimitsEx.](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md)</span><span class="sxs-lookup"><span data-stu-id="bf786-104">Starting with the .NET Framework 4.5, you can set segment size and maximum generation 0 size to values greater than `DWORD` by using the [ICLRGCManager2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf786-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bf786-105">Syntax</span></span>  
  
```cpp  
HRESULT SetGCStartupLimits (  
    [in] DWORD SegmentSize,
    [in] DWORD MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bf786-106">parâmetros</span><span class="sxs-lookup"><span data-stu-id="bf786-106">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="bf786-107">[em] O tamanho especificado de um segmento de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="bf786-107">[in] The specified size of a garbage collection segment.</span></span>  
  
 <span data-ttu-id="bf786-108">O tamanho mínimo do segmento é de 4 MB.</span><span class="sxs-lookup"><span data-stu-id="bf786-108">The minimum segment size is 4 MB.</span></span> <span data-ttu-id="bf786-109">Os segmentos podem ser aumentados em incrementos de 1 MB ou maiores.</span><span class="sxs-lookup"><span data-stu-id="bf786-109">Segments can be increased in increments of 1 MB or larger.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="bf786-110">[em] O tamanho máximo especificado para a geração 0.</span><span class="sxs-lookup"><span data-stu-id="bf786-110">[in] The specified maximum size for generation 0.</span></span>  
  
 <span data-ttu-id="bf786-111">O tamanho mínimo de geração 0 é de 64 KB.</span><span class="sxs-lookup"><span data-stu-id="bf786-111">The minimum generation 0 size is 64 KB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bf786-112">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="bf786-112">Return Value</span></span>  
  
|<span data-ttu-id="bf786-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bf786-113">HRESULT</span></span>|<span data-ttu-id="bf786-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="bf786-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bf786-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="bf786-115">S_OK</span></span>|<span data-ttu-id="bf786-116">`SetGCStartupLimits`retornou com sucesso.</span><span class="sxs-lookup"><span data-stu-id="bf786-116">`SetGCStartupLimits` returned successfully.</span></span>|  
|<span data-ttu-id="bf786-117">Host_e_clrnotavailable</span><span class="sxs-lookup"><span data-stu-id="bf786-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bf786-118">O tempo de execução do idioma comum (CLR) não foi carregado em um processo, ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com sucesso.</span><span class="sxs-lookup"><span data-stu-id="bf786-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="bf786-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bf786-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bf786-120">A chamada acabou.</span><span class="sxs-lookup"><span data-stu-id="bf786-120">The call timed out.</span></span>|  
|<span data-ttu-id="bf786-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bf786-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bf786-122">O interlocutor não é dono da fechadura.</span><span class="sxs-lookup"><span data-stu-id="bf786-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bf786-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bf786-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bf786-124">Um evento foi cancelado enquanto um fio ou fibra bloqueado estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="bf786-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bf786-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bf786-125">E_FAIL</span></span>|<span data-ttu-id="bf786-126">Uma falha catastrófica desconhecida ocorreu.</span><span class="sxs-lookup"><span data-stu-id="bf786-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bf786-127">Depois que um método retorna E_FAIL, a CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="bf786-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bf786-128">Chamadas subseqüentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="bf786-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bf786-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="bf786-129">Remarks</span></span>  
 <span data-ttu-id="bf786-130">Os valores que `SetGCStartupLimits` definem podem ser especificados apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="bf786-130">The values that `SetGCStartupLimits` sets can be specified only once.</span></span> <span data-ttu-id="bf786-131">Chamadas `SetGCStartupLimits` posteriores são ignoradas.</span><span class="sxs-lookup"><span data-stu-id="bf786-131">Later calls to `SetGCStartupLimits` are ignored.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf786-132">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bf786-132">Requirements</span></span>  
 <span data-ttu-id="bf786-133">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf786-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf786-134">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bf786-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bf786-135">**Biblioteca:** Incluído como um recurso em MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bf786-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bf786-136">**.NET Framework Versions:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf786-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf786-137">Confira também</span><span class="sxs-lookup"><span data-stu-id="bf786-137">See also</span></span>

- [<span data-ttu-id="bf786-138">Gerenciamento automático de memória</span><span class="sxs-lookup"><span data-stu-id="bf786-138">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="bf786-139">Coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="bf786-139">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="bf786-140">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="bf786-140">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="bf786-141">Interface ICLRGCManager</span><span class="sxs-lookup"><span data-stu-id="bf786-141">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)
