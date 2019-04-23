---
title: Método ICLRTask::GetMemStats
ms.date: 03/30/2017
api_name:
- ICLRTask.GetMemStats
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::GetMemStats
helpviewer_keywords:
- ICLRTask::GetMemStats method [.NET Framework hosting]
- GetMemStats method [.NET Framework hosting]
ms.assetid: c9e07657-1682-4c30-a336-f8658ff1a125
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 668e570c315f5473f222905a061f05ac94afa81a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59183398"
---
# <a name="iclrtaskgetmemstats-method"></a><span data-ttu-id="d6cf0-102">Método ICLRTask::GetMemStats</span><span class="sxs-lookup"><span data-stu-id="d6cf0-102">ICLRTask::GetMemStats Method</span></span>
<span data-ttu-id="d6cf0-103">Obtém informações de uso de memória estatísticas relacionadas à tarefa que atual [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instância representa.</span><span class="sxs-lookup"><span data-stu-id="d6cf0-103">Gets statistical memory usage information related to the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6cf0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d6cf0-104">Syntax</span></span>  
  
```  
HRESULT GetMemStats (  
    [out] COR_GC_THREAD_STATS *pMemUsage  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d6cf0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d6cf0-105">Parameters</span></span>  
 `pMemUsage`  
 <span data-ttu-id="d6cf0-106">[out] Um ponteiro para um [COR_GC_THREAD_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md) instância que contém detalhes sobre o uso de memória da tarefa, incluindo o número de bytes alocados.</span><span class="sxs-lookup"><span data-stu-id="d6cf0-106">[out] A pointer to a [COR_GC_THREAD_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md) instance that contains details about the memory usage of the task, including the number of bytes allocated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d6cf0-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="d6cf0-107">Return Value</span></span>  
  
|<span data-ttu-id="d6cf0-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d6cf0-108">HRESULT</span></span>|<span data-ttu-id="d6cf0-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="d6cf0-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d6cf0-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="d6cf0-110">S_OK</span></span>|<span data-ttu-id="d6cf0-111">`GetMemStats` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="d6cf0-111">`GetMemStats` returned successfully.</span></span>|  
|<span data-ttu-id="d6cf0-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d6cf0-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d6cf0-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="d6cf0-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d6cf0-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d6cf0-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d6cf0-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="d6cf0-115">The call timed out.</span></span>|  
|<span data-ttu-id="d6cf0-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d6cf0-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d6cf0-117">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="d6cf0-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d6cf0-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d6cf0-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d6cf0-119">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="d6cf0-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d6cf0-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d6cf0-120">E_FAIL</span></span>|<span data-ttu-id="d6cf0-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="d6cf0-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d6cf0-122">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="d6cf0-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d6cf0-123">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d6cf0-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d6cf0-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d6cf0-124">Requirements</span></span>  
 <span data-ttu-id="d6cf0-125">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6cf0-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6cf0-126">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d6cf0-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d6cf0-127">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="d6cf0-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d6cf0-128">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6cf0-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6cf0-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d6cf0-129">See also</span></span>

- [<span data-ttu-id="d6cf0-130">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="d6cf0-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="d6cf0-131">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="d6cf0-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="d6cf0-132">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="d6cf0-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="d6cf0-133">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="d6cf0-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
