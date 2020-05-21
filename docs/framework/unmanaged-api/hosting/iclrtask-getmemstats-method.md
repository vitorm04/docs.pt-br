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
ms.openlocfilehash: 0d2975d6247cd9ecdb07b564d77518151404c7d0
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762450"
---
# <a name="iclrtaskgetmemstats-method"></a><span data-ttu-id="388b2-102">Método ICLRTask::GetMemStats</span><span class="sxs-lookup"><span data-stu-id="388b2-102">ICLRTask::GetMemStats Method</span></span>
<span data-ttu-id="388b2-103">Obtém informações de uso de memória estatística relacionadas à tarefa que a instância [ICLRTask](iclrtask-interface.md) atual representa.</span><span class="sxs-lookup"><span data-stu-id="388b2-103">Gets statistical memory usage information related to the task that the current [ICLRTask](iclrtask-interface.md) instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="388b2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="388b2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMemStats (  
    [out] COR_GC_THREAD_STATS *pMemUsage  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="388b2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="388b2-105">Parameters</span></span>  
 `pMemUsage`  
 <span data-ttu-id="388b2-106">fora Um ponteiro para uma instância de [COR_GC_THREAD_STATS](cor-gc-thread-stats-structure.md) que contém detalhes sobre o uso de memória da tarefa, incluindo o número de bytes alocados.</span><span class="sxs-lookup"><span data-stu-id="388b2-106">[out] A pointer to a [COR_GC_THREAD_STATS](cor-gc-thread-stats-structure.md) instance that contains details about the memory usage of the task, including the number of bytes allocated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="388b2-107">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="388b2-107">Return Value</span></span>  
  
|<span data-ttu-id="388b2-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="388b2-108">HRESULT</span></span>|<span data-ttu-id="388b2-109">Description</span><span class="sxs-lookup"><span data-stu-id="388b2-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="388b2-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="388b2-110">S_OK</span></span>|<span data-ttu-id="388b2-111">`GetMemStats`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="388b2-111">`GetMemStats` returned successfully.</span></span>|  
|<span data-ttu-id="388b2-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="388b2-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="388b2-113">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="388b2-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="388b2-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="388b2-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="388b2-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="388b2-115">The call timed out.</span></span>|  
|<span data-ttu-id="388b2-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="388b2-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="388b2-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="388b2-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="388b2-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="388b2-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="388b2-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="388b2-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="388b2-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="388b2-120">E_FAIL</span></span>|<span data-ttu-id="388b2-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="388b2-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="388b2-122">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="388b2-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="388b2-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="388b2-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="388b2-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="388b2-124">Requirements</span></span>  
 <span data-ttu-id="388b2-125">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="388b2-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="388b2-126">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="388b2-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="388b2-127">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="388b2-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="388b2-128">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="388b2-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="388b2-129">Veja também</span><span class="sxs-lookup"><span data-stu-id="388b2-129">See also</span></span>

- [<span data-ttu-id="388b2-130">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="388b2-130">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="388b2-131">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="388b2-131">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="388b2-132">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="388b2-132">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="388b2-133">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="388b2-133">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
