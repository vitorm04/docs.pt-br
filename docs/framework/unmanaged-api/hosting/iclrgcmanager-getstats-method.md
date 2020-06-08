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
ms.openlocfilehash: 8622920a81f4b469361ffa879f7a4eeda697cab9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504219"
---
# <a name="iclrgcmanagergetstats-method"></a><span data-ttu-id="304a7-102">Método ICLRGCManager::GetStats</span><span class="sxs-lookup"><span data-stu-id="304a7-102">ICLRGCManager::GetStats Method</span></span>
<span data-ttu-id="304a7-103">Obtém um conjunto de estatísticas atuais sobre o sistema de coleta de lixo do Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="304a7-103">Gets a set of current statistics about the common language runtime's garbage collection system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="304a7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="304a7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="304a7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="304a7-105">Parameters</span></span>  
 `pStats`  
 <span data-ttu-id="304a7-106">[entrada, saída] Uma instância de [COR_GC_STATS](cor-gc-stats-structure.md) que contém as estatísticas solicitadas.</span><span class="sxs-lookup"><span data-stu-id="304a7-106">[in, out] A [COR_GC_STATS](cor-gc-stats-structure.md) instance that contains the requested statistics.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="304a7-107">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="304a7-107">Return Value</span></span>  
  
|<span data-ttu-id="304a7-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="304a7-108">HRESULT</span></span>|<span data-ttu-id="304a7-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="304a7-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="304a7-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="304a7-110">S_OK</span></span>|<span data-ttu-id="304a7-111">`GetStats`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="304a7-111">`GetStats` returned successfully.</span></span>|  
|<span data-ttu-id="304a7-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="304a7-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="304a7-113">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="304a7-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="304a7-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="304a7-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="304a7-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="304a7-115">The call timed out.</span></span>|  
|<span data-ttu-id="304a7-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="304a7-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="304a7-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="304a7-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="304a7-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="304a7-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="304a7-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="304a7-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="304a7-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="304a7-120">E_FAIL</span></span>|<span data-ttu-id="304a7-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="304a7-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="304a7-122">Depois que um método retorna E_FAIL, o CLR não pode mais ser usado no processo.</span><span class="sxs-lookup"><span data-stu-id="304a7-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="304a7-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="304a7-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="304a7-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="304a7-124">Remarks</span></span>  
 <span data-ttu-id="304a7-125">O CLR calcula e retorna somente as estatísticas que são especificadas pelo `Flags` campo de `pStats` .</span><span class="sxs-lookup"><span data-stu-id="304a7-125">The CLR calculates and returns only those statistics that are specified by the `Flags` field of `pStats`.</span></span>  
  
 <span data-ttu-id="304a7-126">Defina o `Flags` campo como um ou mais valores da enumeração [COR_GC_STAT_TYPES](cor-gc-stat-types-enumeration.md) para especificar quais estatísticas na estrutura de [COR_GC_STATS](cor-gc-stats-structure.md) devem ser definidas.</span><span class="sxs-lookup"><span data-stu-id="304a7-126">Set the `Flags` field to one or more values of the [COR_GC_STAT_TYPES](cor-gc-stat-types-enumeration.md) enumeration to specify which statistics in the [COR_GC_STATS](cor-gc-stats-structure.md) structure are to be set.</span></span>  
  
 <span data-ttu-id="304a7-127">Um exemplo de uso é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="304a7-127">An example of the usage is as follows:</span></span>  
  
```cpp  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a><span data-ttu-id="304a7-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="304a7-128">Requirements</span></span>  
 <span data-ttu-id="304a7-129">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="304a7-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="304a7-130">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="304a7-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="304a7-131">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="304a7-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="304a7-132">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="304a7-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="304a7-133">Confira também</span><span class="sxs-lookup"><span data-stu-id="304a7-133">See also</span></span>

- [<span data-ttu-id="304a7-134">Gerenciamento automático de memória</span><span class="sxs-lookup"><span data-stu-id="304a7-134">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="304a7-135">Estrutura COR_GC_STATS</span><span class="sxs-lookup"><span data-stu-id="304a7-135">COR_GC_STATS Structure</span></span>](cor-gc-stats-structure.md)
- [<span data-ttu-id="304a7-136">Enumeração COR_GC_STAT_TYPES</span><span class="sxs-lookup"><span data-stu-id="304a7-136">COR_GC_STAT_TYPES Enumeration</span></span>](cor-gc-stat-types-enumeration.md)
- [<span data-ttu-id="304a7-137">Coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="304a7-137">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="304a7-138">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="304a7-138">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="304a7-139">Interface ICLRGCManager</span><span class="sxs-lookup"><span data-stu-id="304a7-139">ICLRGCManager Interface</span></span>](iclrgcmanager-interface.md)
- [<span data-ttu-id="304a7-140">Interfaces de hospedagem CLR</span><span class="sxs-lookup"><span data-stu-id="304a7-140">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)
- [<span data-ttu-id="304a7-141">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="304a7-141">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="304a7-142">Hosting</span><span class="sxs-lookup"><span data-stu-id="304a7-142">Hosting</span></span>](index.md)
