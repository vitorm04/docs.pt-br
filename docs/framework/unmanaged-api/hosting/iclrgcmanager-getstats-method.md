---
title: Método ICLRGCManager::GetStats
ms.date: 03/30/2017
api_name:
- ICLRGCManager.GetStats
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager::GetStats
helpviewer_keywords:
- GetStats method, ICLRGCManager interface [.NET Framework hosting]
- ICLRGCManager::GetStats method [.NET Framework hosting]
ms.assetid: ce259d1d-cd81-4490-a7a1-0d0ea0804872
topic_type:
- apiref
ms.openlocfilehash: 9e8b65c735028029f4fb44c2640df74ef171d9de
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141146"
---
# <a name="iclrgcmanagergetstats-method"></a><span data-ttu-id="15245-102">Método ICLRGCManager::GetStats</span><span class="sxs-lookup"><span data-stu-id="15245-102">ICLRGCManager::GetStats Method</span></span>
<span data-ttu-id="15245-103">Obtém um conjunto de estatísticas atuais sobre o sistema de coleta de lixo do Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="15245-103">Gets a set of current statistics about the common language runtime's garbage collection system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15245-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="15245-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="15245-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="15245-105">Parameters</span></span>  
 `pStats`  
 <span data-ttu-id="15245-106">[entrada, saída] Uma instância de [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) que contém as estatísticas solicitadas.</span><span class="sxs-lookup"><span data-stu-id="15245-106">[in, out] A [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) instance that contains the requested statistics.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="15245-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="15245-107">Return Value</span></span>  
  
|<span data-ttu-id="15245-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="15245-108">HRESULT</span></span>|<span data-ttu-id="15245-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="15245-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="15245-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="15245-110">S_OK</span></span>|<span data-ttu-id="15245-111">`GetStats` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="15245-111">`GetStats` returned successfully.</span></span>|  
|<span data-ttu-id="15245-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="15245-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="15245-113">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="15245-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="15245-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="15245-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="15245-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="15245-115">The call timed out.</span></span>|  
|<span data-ttu-id="15245-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="15245-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="15245-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="15245-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="15245-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="15245-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="15245-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="15245-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="15245-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="15245-120">E_FAIL</span></span>|<span data-ttu-id="15245-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="15245-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="15245-122">Depois que um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="15245-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="15245-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="15245-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="15245-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="15245-124">Remarks</span></span>  
 <span data-ttu-id="15245-125">O CLR calcula e retorna somente as estatísticas que são especificadas pelo campo `Flags` de `pStats`.</span><span class="sxs-lookup"><span data-stu-id="15245-125">The CLR calculates and returns only those statistics that are specified by the `Flags` field of `pStats`.</span></span>  
  
 <span data-ttu-id="15245-126">Defina o campo `Flags` como um ou mais valores da enumeração [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) para especificar quais estatísticas na estrutura [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) devem ser definidas.</span><span class="sxs-lookup"><span data-stu-id="15245-126">Set the `Flags` field to one or more values of the [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) enumeration to specify which statistics in the [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) structure are to be set.</span></span>  
  
 <span data-ttu-id="15245-127">Um exemplo de uso é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="15245-127">An example of the usage is as follows:</span></span>  
  
```cpp  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a><span data-ttu-id="15245-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="15245-128">Requirements</span></span>  
 <span data-ttu-id="15245-129">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15245-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15245-130">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="15245-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="15245-131">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="15245-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="15245-132">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15245-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15245-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="15245-133">See also</span></span>

- [<span data-ttu-id="15245-134">Gerenciamento Automático de Memória</span><span class="sxs-lookup"><span data-stu-id="15245-134">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="15245-135">Estrutura COR_GC_STATS</span><span class="sxs-lookup"><span data-stu-id="15245-135">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)
- [<span data-ttu-id="15245-136">Enumeração COR_GC_STAT_TYPES</span><span class="sxs-lookup"><span data-stu-id="15245-136">COR_GC_STAT_TYPES Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md)
- [<span data-ttu-id="15245-137">Coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="15245-137">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="15245-138">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="15245-138">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="15245-139">Interface ICLRGCManager</span><span class="sxs-lookup"><span data-stu-id="15245-139">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)
- [<span data-ttu-id="15245-140">Interfaces de hospedagem CLR</span><span class="sxs-lookup"><span data-stu-id="15245-140">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [<span data-ttu-id="15245-141">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="15245-141">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="15245-142">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="15245-142">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
