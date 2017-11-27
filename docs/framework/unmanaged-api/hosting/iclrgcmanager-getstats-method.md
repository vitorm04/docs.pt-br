---
title: "Método ICLRGCManager::GetStats"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRGCManager.GetStats
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRGCManager::GetStats
helpviewer_keywords:
- GetStats method, ICLRGCManager interface [.NET Framework hosting]
- ICLRGCManager::GetStats method [.NET Framework hosting]
ms.assetid: ce259d1d-cd81-4490-a7a1-0d0ea0804872
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 06d52bd0348e4667f1e3ec43a371021922f12ded
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrgcmanagergetstats-method"></a><span data-ttu-id="08f8c-102">Método ICLRGCManager::GetStats</span><span class="sxs-lookup"><span data-stu-id="08f8c-102">ICLRGCManager::GetStats Method</span></span>
<span data-ttu-id="08f8c-103">Obtém um conjunto de estatísticas atuais sobre o sistema de coleta de lixo do common language runtime.</span><span class="sxs-lookup"><span data-stu-id="08f8c-103">Gets a set of current statistics about the common language runtime's garbage collection system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08f8c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="08f8c-104">Syntax</span></span>  
  
```  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="08f8c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="08f8c-105">Parameters</span></span>  
 `pStats`  
 <span data-ttu-id="08f8c-106">[out no] Um [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) instância que contém as estatísticas solicitadas.</span><span class="sxs-lookup"><span data-stu-id="08f8c-106">[in, out] A [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) instance that contains the requested statistics.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="08f8c-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="08f8c-107">Return Value</span></span>  
  
|<span data-ttu-id="08f8c-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="08f8c-108">HRESULT</span></span>|<span data-ttu-id="08f8c-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="08f8c-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="08f8c-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="08f8c-110">S_OK</span></span>|<span data-ttu-id="08f8c-111">`GetStats`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="08f8c-111">`GetStats` returned successfully.</span></span>|  
|<span data-ttu-id="08f8c-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="08f8c-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="08f8c-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="08f8c-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="08f8c-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="08f8c-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="08f8c-115">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="08f8c-115">The call timed out.</span></span>|  
|<span data-ttu-id="08f8c-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="08f8c-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="08f8c-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="08f8c-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="08f8c-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="08f8c-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="08f8c-119">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="08f8c-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="08f8c-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="08f8c-120">E_FAIL</span></span>|<span data-ttu-id="08f8c-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="08f8c-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="08f8c-122">Depois que um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="08f8c-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="08f8c-123">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="08f8c-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="08f8c-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="08f8c-124">Remarks</span></span>  
 <span data-ttu-id="08f8c-125">O CLR calcula e retorna somente as estatísticas que são especificadas pelo `Flags` campo de `pStats`.</span><span class="sxs-lookup"><span data-stu-id="08f8c-125">The CLR calculates and returns only those statistics that are specified by the `Flags` field of `pStats`.</span></span>  
  
 <span data-ttu-id="08f8c-126">Definir o `Flags` para um ou mais valores de campo a [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) enumeração para especificar quais estatísticas no [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) estrutura devem ser definidas.</span><span class="sxs-lookup"><span data-stu-id="08f8c-126">Set the `Flags` field to one or more values of the [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) enumeration to specify which statistics in the [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) structure are to be set.</span></span>  
  
 <span data-ttu-id="08f8c-127">Um exemplo de uso é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="08f8c-127">An example of the usage is as follows:</span></span>  
  
```  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a><span data-ttu-id="08f8c-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="08f8c-128">Requirements</span></span>  
 <span data-ttu-id="08f8c-129">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08f8c-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08f8c-130">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="08f8c-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="08f8c-131">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="08f8c-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="08f8c-132">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08f8c-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08f8c-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="08f8c-133">See Also</span></span>  
 [<span data-ttu-id="08f8c-134">Gerenciamento Automático de Memória</span><span class="sxs-lookup"><span data-stu-id="08f8c-134">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)  
 [<span data-ttu-id="08f8c-135">Estrutura COR_GC_STATS</span><span class="sxs-lookup"><span data-stu-id="08f8c-135">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)  
 [<span data-ttu-id="08f8c-136">Enumeração COR_GC_STAT_TYPES</span><span class="sxs-lookup"><span data-stu-id="08f8c-136">COR_GC_STAT_TYPES Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md)  
 [<span data-ttu-id="08f8c-137">Coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="08f8c-137">Garbage Collection</span></span>](../../../../docs/standard/garbage-collection/index.md)  
 [<span data-ttu-id="08f8c-138">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="08f8c-138">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="08f8c-139">Interface ICLRGCManager</span><span class="sxs-lookup"><span data-stu-id="08f8c-139">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)  
 [<span data-ttu-id="08f8c-140">Interfaces de hospedagem CLR</span><span class="sxs-lookup"><span data-stu-id="08f8c-140">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 [<span data-ttu-id="08f8c-141">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="08f8c-141">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="08f8c-142">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="08f8c-142">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
