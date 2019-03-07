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
ms.openlocfilehash: 3e92707e7b24709d64915e29823196bb0f827175
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485221"
---
# <a name="iclrgcmanagergetstats-method"></a><span data-ttu-id="e1ad6-102">Método ICLRGCManager::GetStats</span><span class="sxs-lookup"><span data-stu-id="e1ad6-102">ICLRGCManager::GetStats Method</span></span>
<span data-ttu-id="e1ad6-103">Obtém um conjunto de estatísticas atuais sobre o sistema de coleta de lixo do common language runtime.</span><span class="sxs-lookup"><span data-stu-id="e1ad6-103">Gets a set of current statistics about the common language runtime's garbage collection system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1ad6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e1ad6-104">Syntax</span></span>  
  
```  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e1ad6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e1ad6-105">Parameters</span></span>  
 `pStats`  
 <span data-ttu-id="e1ad6-106">[no, out] Um [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) instância que contém as estatísticas solicitadas.</span><span class="sxs-lookup"><span data-stu-id="e1ad6-106">[in, out] A [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) instance that contains the requested statistics.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e1ad6-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="e1ad6-107">Return Value</span></span>  
  
|<span data-ttu-id="e1ad6-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e1ad6-108">HRESULT</span></span>|<span data-ttu-id="e1ad6-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="e1ad6-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e1ad6-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="e1ad6-110">S_OK</span></span>|<span data-ttu-id="e1ad6-111">`GetStats` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="e1ad6-111">`GetStats` returned successfully.</span></span>|  
|<span data-ttu-id="e1ad6-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e1ad6-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e1ad6-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="e1ad6-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e1ad6-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e1ad6-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e1ad6-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="e1ad6-115">The call timed out.</span></span>|  
|<span data-ttu-id="e1ad6-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e1ad6-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e1ad6-117">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="e1ad6-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e1ad6-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e1ad6-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e1ad6-119">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="e1ad6-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e1ad6-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e1ad6-120">E_FAIL</span></span>|<span data-ttu-id="e1ad6-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="e1ad6-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e1ad6-122">Depois que um método retorna E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="e1ad6-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e1ad6-123">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e1ad6-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e1ad6-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="e1ad6-124">Remarks</span></span>  
 <span data-ttu-id="e1ad6-125">O CLR calcula e retorna somente as estatísticas que são especificadas pela `Flags` campo de `pStats`.</span><span class="sxs-lookup"><span data-stu-id="e1ad6-125">The CLR calculates and returns only those statistics that are specified by the `Flags` field of `pStats`.</span></span>  
  
 <span data-ttu-id="e1ad6-126">Defina a `Flags` campo para um ou mais valores da [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) enumeração para especificar quais estatísticas no [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) estrutura devem ser definidas.</span><span class="sxs-lookup"><span data-stu-id="e1ad6-126">Set the `Flags` field to one or more values of the [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) enumeration to specify which statistics in the [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) structure are to be set.</span></span>  
  
 <span data-ttu-id="e1ad6-127">Um exemplo do uso é da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="e1ad6-127">An example of the usage is as follows:</span></span>  
  
```  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a><span data-ttu-id="e1ad6-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e1ad6-128">Requirements</span></span>  
 <span data-ttu-id="e1ad6-129">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1ad6-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1ad6-130">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e1ad6-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e1ad6-131">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="e1ad6-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e1ad6-132">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1ad6-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1ad6-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e1ad6-133">See also</span></span>
- [<span data-ttu-id="e1ad6-134">Gerenciamento Automático de Memória</span><span class="sxs-lookup"><span data-stu-id="e1ad6-134">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)
- [<span data-ttu-id="e1ad6-135">Estrutura COR_GC_STATS</span><span class="sxs-lookup"><span data-stu-id="e1ad6-135">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)
- [<span data-ttu-id="e1ad6-136">Enumeração COR_GC_STAT_TYPES</span><span class="sxs-lookup"><span data-stu-id="e1ad6-136">COR_GC_STAT_TYPES Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md)
- [<span data-ttu-id="e1ad6-137">Coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="e1ad6-137">Garbage Collection</span></span>](../../../../docs/standard/garbage-collection/index.md)
- [<span data-ttu-id="e1ad6-138">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="e1ad6-138">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="e1ad6-139">Interface ICLRGCManager</span><span class="sxs-lookup"><span data-stu-id="e1ad6-139">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)
- [<span data-ttu-id="e1ad6-140">Interfaces de hospedagem CLR</span><span class="sxs-lookup"><span data-stu-id="e1ad6-140">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [<span data-ttu-id="e1ad6-141">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="e1ad6-141">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="e1ad6-142">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="e1ad6-142">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
