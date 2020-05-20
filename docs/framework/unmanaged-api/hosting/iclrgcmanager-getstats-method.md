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
ms.openlocfilehash: 1e881b4a55a99bac3f9ca0e8db1556807b888f13
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616953"
---
# <a name="iclrgcmanagergetstats-method"></a><span data-ttu-id="81d4a-102">Método ICLRGCManager::GetStats</span><span class="sxs-lookup"><span data-stu-id="81d4a-102">ICLRGCManager::GetStats Method</span></span>
<span data-ttu-id="81d4a-103">Obtém um conjunto de estatísticas atuais sobre o sistema de coleta de lixo do Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="81d4a-103">Gets a set of current statistics about the common language runtime's garbage collection system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81d4a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="81d4a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="81d4a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="81d4a-105">Parameters</span></span>  
 `pStats`  
 <span data-ttu-id="81d4a-106">[entrada, saída] Uma instância de [COR_GC_STATS](cor-gc-stats-structure.md) que contém as estatísticas solicitadas.</span><span class="sxs-lookup"><span data-stu-id="81d4a-106">[in, out] A [COR_GC_STATS](cor-gc-stats-structure.md) instance that contains the requested statistics.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="81d4a-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="81d4a-107">Return Value</span></span>  
  
|<span data-ttu-id="81d4a-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="81d4a-108">HRESULT</span></span>|<span data-ttu-id="81d4a-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="81d4a-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="81d4a-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="81d4a-110">S_OK</span></span>|<span data-ttu-id="81d4a-111">`GetStats`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="81d4a-111">`GetStats` returned successfully.</span></span>|  
|<span data-ttu-id="81d4a-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="81d4a-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="81d4a-113">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="81d4a-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="81d4a-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="81d4a-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="81d4a-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="81d4a-115">The call timed out.</span></span>|  
|<span data-ttu-id="81d4a-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="81d4a-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="81d4a-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="81d4a-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="81d4a-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="81d4a-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="81d4a-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="81d4a-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="81d4a-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="81d4a-120">E_FAIL</span></span>|<span data-ttu-id="81d4a-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="81d4a-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="81d4a-122">Depois que um método retorna E_FAIL, o CLR não pode mais ser usado no processo.</span><span class="sxs-lookup"><span data-stu-id="81d4a-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="81d4a-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="81d4a-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="81d4a-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="81d4a-124">Remarks</span></span>  
 <span data-ttu-id="81d4a-125">O CLR calcula e retorna somente as estatísticas que são especificadas pelo `Flags` campo de `pStats` .</span><span class="sxs-lookup"><span data-stu-id="81d4a-125">The CLR calculates and returns only those statistics that are specified by the `Flags` field of `pStats`.</span></span>  
  
 <span data-ttu-id="81d4a-126">Defina o `Flags` campo como um ou mais valores da enumeração [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) para especificar quais estatísticas na estrutura de [COR_GC_STATS](cor-gc-stats-structure.md) devem ser definidas.</span><span class="sxs-lookup"><span data-stu-id="81d4a-126">Set the `Flags` field to one or more values of the [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) enumeration to specify which statistics in the [COR_GC_STATS](cor-gc-stats-structure.md) structure are to be set.</span></span>  
  
 <span data-ttu-id="81d4a-127">Um exemplo de uso é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="81d4a-127">An example of the usage is as follows:</span></span>  
  
```cpp  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a><span data-ttu-id="81d4a-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="81d4a-128">Requirements</span></span>  
 <span data-ttu-id="81d4a-129">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81d4a-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81d4a-130">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="81d4a-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="81d4a-131">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="81d4a-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="81d4a-132">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81d4a-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81d4a-133">Veja também</span><span class="sxs-lookup"><span data-stu-id="81d4a-133">See also</span></span>

- [<span data-ttu-id="81d4a-134">Gerenciamento automático de memória</span><span class="sxs-lookup"><span data-stu-id="81d4a-134">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="81d4a-135">Estrutura COR_GC_STATS</span><span class="sxs-lookup"><span data-stu-id="81d4a-135">COR_GC_STATS Structure</span></span>](cor-gc-stats-structure.md)
- [<span data-ttu-id="81d4a-136">Enumeração COR_GC_STAT_TYPES</span><span class="sxs-lookup"><span data-stu-id="81d4a-136">COR_GC_STAT_TYPES Enumeration</span></span>](cor-gc-stat-types-enumeration.md)
- [<span data-ttu-id="81d4a-137">Coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="81d4a-137">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="81d4a-138">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="81d4a-138">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="81d4a-139">Interface ICLRGCManager</span><span class="sxs-lookup"><span data-stu-id="81d4a-139">ICLRGCManager Interface</span></span>](iclrgcmanager-interface.md)
- [<span data-ttu-id="81d4a-140">Interfaces de hospedagem CLR</span><span class="sxs-lookup"><span data-stu-id="81d4a-140">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)
- [<span data-ttu-id="81d4a-141">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="81d4a-141">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="81d4a-142">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="81d4a-142">Hosting</span></span>](index.md)
