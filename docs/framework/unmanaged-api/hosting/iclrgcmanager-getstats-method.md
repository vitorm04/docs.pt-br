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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9df9263a0356b0c3c1a6d1da950c670f5a020d1e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966225"
---
# <a name="iclrgcmanagergetstats-method"></a><span data-ttu-id="7425c-102">Método ICLRGCManager::GetStats</span><span class="sxs-lookup"><span data-stu-id="7425c-102">ICLRGCManager::GetStats Method</span></span>
<span data-ttu-id="7425c-103">Obtém um conjunto de estatísticas atuais sobre o sistema de coleta de lixo do Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="7425c-103">Gets a set of current statistics about the common language runtime's garbage collection system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7425c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7425c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7425c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7425c-105">Parameters</span></span>  
 `pStats`  
 <span data-ttu-id="7425c-106">[entrada, saída] Uma instância de [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) que contém as estatísticas solicitadas.</span><span class="sxs-lookup"><span data-stu-id="7425c-106">[in, out] A [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) instance that contains the requested statistics.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7425c-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="7425c-107">Return Value</span></span>  
  
|<span data-ttu-id="7425c-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7425c-108">HRESULT</span></span>|<span data-ttu-id="7425c-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="7425c-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7425c-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="7425c-110">S_OK</span></span>|<span data-ttu-id="7425c-111">`GetStats`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="7425c-111">`GetStats` returned successfully.</span></span>|  
|<span data-ttu-id="7425c-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7425c-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7425c-113">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="7425c-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7425c-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7425c-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7425c-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="7425c-115">The call timed out.</span></span>|  
|<span data-ttu-id="7425c-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7425c-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7425c-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="7425c-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7425c-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7425c-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7425c-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="7425c-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7425c-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7425c-120">E_FAIL</span></span>|<span data-ttu-id="7425c-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="7425c-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7425c-122">Depois que um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="7425c-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7425c-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7425c-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7425c-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="7425c-124">Remarks</span></span>  
 <span data-ttu-id="7425c-125">O CLR calcula e retorna somente as estatísticas que são especificadas pelo `Flags` campo de. `pStats`</span><span class="sxs-lookup"><span data-stu-id="7425c-125">The CLR calculates and returns only those statistics that are specified by the `Flags` field of `pStats`.</span></span>  
  
 <span data-ttu-id="7425c-126">Defina o `Flags` campo como um ou mais valores da enumeração [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) para especificar quais estatísticas na estrutura [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) devem ser definidas.</span><span class="sxs-lookup"><span data-stu-id="7425c-126">Set the `Flags` field to one or more values of the [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) enumeration to specify which statistics in the [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) structure are to be set.</span></span>  
  
 <span data-ttu-id="7425c-127">Um exemplo de uso é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="7425c-127">An example of the usage is as follows:</span></span>  
  
```cpp  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a><span data-ttu-id="7425c-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7425c-128">Requirements</span></span>  
 <span data-ttu-id="7425c-129">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7425c-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7425c-130">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7425c-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7425c-131">**Biblioteca** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7425c-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7425c-132">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7425c-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7425c-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7425c-133">See also</span></span>

- [<span data-ttu-id="7425c-134">Gerenciamento Automático de Memória</span><span class="sxs-lookup"><span data-stu-id="7425c-134">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="7425c-135">Estrutura COR_GC_STATS</span><span class="sxs-lookup"><span data-stu-id="7425c-135">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)
- [<span data-ttu-id="7425c-136">Enumeração COR_GC_STAT_TYPES</span><span class="sxs-lookup"><span data-stu-id="7425c-136">COR_GC_STAT_TYPES Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md)
- [<span data-ttu-id="7425c-137">Coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="7425c-137">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="7425c-138">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="7425c-138">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="7425c-139">Interface ICLRGCManager</span><span class="sxs-lookup"><span data-stu-id="7425c-139">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)
- [<span data-ttu-id="7425c-140">Interfaces de hospedagem CLR</span><span class="sxs-lookup"><span data-stu-id="7425c-140">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [<span data-ttu-id="7425c-141">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="7425c-141">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="7425c-142">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="7425c-142">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
