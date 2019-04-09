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
ms.openlocfilehash: 9300f67e75d40f041a4fba52f6742741ec9f91de
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59187311"
---
# <a name="iclrgcmanagergetstats-method"></a><span data-ttu-id="798df-102">Método ICLRGCManager::GetStats</span><span class="sxs-lookup"><span data-stu-id="798df-102">ICLRGCManager::GetStats Method</span></span>
<span data-ttu-id="798df-103">Obtém um conjunto de estatísticas atuais sobre o sistema de coleta de lixo do common language runtime.</span><span class="sxs-lookup"><span data-stu-id="798df-103">Gets a set of current statistics about the common language runtime's garbage collection system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="798df-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="798df-104">Syntax</span></span>  
  
```  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="798df-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="798df-105">Parameters</span></span>  
 `pStats`  
 <span data-ttu-id="798df-106">[no, out] Um [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) instância que contém as estatísticas solicitadas.</span><span class="sxs-lookup"><span data-stu-id="798df-106">[in, out] A [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) instance that contains the requested statistics.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="798df-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="798df-107">Return Value</span></span>  
  
|<span data-ttu-id="798df-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="798df-108">HRESULT</span></span>|<span data-ttu-id="798df-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="798df-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="798df-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="798df-110">S_OK</span></span>|`GetStats` <span data-ttu-id="798df-111">retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="798df-111">returned successfully.</span></span>|  
|<span data-ttu-id="798df-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="798df-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="798df-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="798df-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="798df-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="798df-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="798df-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="798df-115">The call timed out.</span></span>|  
|<span data-ttu-id="798df-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="798df-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="798df-117">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="798df-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="798df-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="798df-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="798df-119">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="798df-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="798df-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="798df-120">E_FAIL</span></span>|<span data-ttu-id="798df-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="798df-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="798df-122">Depois que um método retorna E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="798df-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="798df-123">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="798df-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="798df-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="798df-124">Remarks</span></span>  
 <span data-ttu-id="798df-125">O CLR calcula e retorna somente as estatísticas que são especificadas pela `Flags` campo de `pStats`.</span><span class="sxs-lookup"><span data-stu-id="798df-125">The CLR calculates and returns only those statistics that are specified by the `Flags` field of `pStats`.</span></span>  
  
 <span data-ttu-id="798df-126">Defina a `Flags` campo para um ou mais valores da [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) enumeração para especificar quais estatísticas no [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) estrutura devem ser definidas.</span><span class="sxs-lookup"><span data-stu-id="798df-126">Set the `Flags` field to one or more values of the [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) enumeration to specify which statistics in the [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) structure are to be set.</span></span>  
  
 <span data-ttu-id="798df-127">Um exemplo do uso é da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="798df-127">An example of the usage is as follows:</span></span>  
  
```  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a><span data-ttu-id="798df-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="798df-128">Requirements</span></span>  
 <span data-ttu-id="798df-129">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="798df-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="798df-130">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="798df-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="798df-131">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="798df-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="798df-132">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="798df-132">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="798df-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="798df-133">See also</span></span>

- [<span data-ttu-id="798df-134">Gerenciamento automático de memória</span><span class="sxs-lookup"><span data-stu-id="798df-134">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)
- [<span data-ttu-id="798df-135">Estrutura COR_GC_STATS</span><span class="sxs-lookup"><span data-stu-id="798df-135">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)
- [<span data-ttu-id="798df-136">Enumeração COR_GC_STAT_TYPES</span><span class="sxs-lookup"><span data-stu-id="798df-136">COR_GC_STAT_TYPES Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md)
- [<span data-ttu-id="798df-137">Coleta de Lixo</span><span class="sxs-lookup"><span data-stu-id="798df-137">Garbage Collection</span></span>](../../../../docs/standard/garbage-collection/index.md)
- [<span data-ttu-id="798df-138">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="798df-138">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="798df-139">Interface ICLRGCManager</span><span class="sxs-lookup"><span data-stu-id="798df-139">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)
- [<span data-ttu-id="798df-140">Interfaces de hospedagem CLR</span><span class="sxs-lookup"><span data-stu-id="798df-140">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [<span data-ttu-id="798df-141">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="798df-141">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="798df-142">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="798df-142">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
