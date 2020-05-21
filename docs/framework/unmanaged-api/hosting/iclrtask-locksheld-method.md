---
title: Método ICLRTask::LocksHeld
ms.date: 03/30/2017
api_name:
- ICLRTask.LocksHeld
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::LocksHeld
helpviewer_keywords:
- LocksHeld method [.NET Framework hosting]
- ICLRTask::LocksHeld method [.NET Framework hosting]
ms.assetid: e88a4dc3-02cc-4703-a474-292b71c40657
topic_type:
- apiref
ms.openlocfilehash: c67f00acd61d6e0cdf3adfa0d3d0fda2a06a6f31
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762972"
---
# <a name="iclrtasklocksheld-method"></a><span data-ttu-id="1e055-102">Método ICLRTask::LocksHeld</span><span class="sxs-lookup"><span data-stu-id="1e055-102">ICLRTask::LocksHeld Method</span></span>
<span data-ttu-id="1e055-103">Obtém o número de bloqueios atualmente mantidos na tarefa.</span><span class="sxs-lookup"><span data-stu-id="1e055-103">Gets the number of locks currently held on the task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e055-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1e055-104">Syntax</span></span>  
  
```cpp  
HRESULT LocksHeld (  
    [out] SIZE_T *pLockCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1e055-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1e055-105">Parameters</span></span>  
 `pLockCount`  
 <span data-ttu-id="1e055-106">fora O número de bloqueios mantidos na tarefa no momento da chamada do método.</span><span class="sxs-lookup"><span data-stu-id="1e055-106">[out] The number of locks held on the task at the time of the method call.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1e055-107">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="1e055-107">Return Value</span></span>  
  
|<span data-ttu-id="1e055-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1e055-108">HRESULT</span></span>|<span data-ttu-id="1e055-109">Description</span><span class="sxs-lookup"><span data-stu-id="1e055-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1e055-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="1e055-110">S_OK</span></span>|<span data-ttu-id="1e055-111">`LocksHeld`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="1e055-111">`LocksHeld` returned successfully.</span></span>|  
|<span data-ttu-id="1e055-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1e055-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1e055-113">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="1e055-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1e055-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1e055-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1e055-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="1e055-115">The call timed out.</span></span>|  
|<span data-ttu-id="1e055-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1e055-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1e055-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="1e055-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1e055-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1e055-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1e055-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="1e055-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1e055-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1e055-120">E_FAIL</span></span>|<span data-ttu-id="1e055-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="1e055-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1e055-122">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="1e055-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1e055-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1e055-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1e055-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1e055-124">Requirements</span></span>  
 <span data-ttu-id="1e055-125">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1e055-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e055-126">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1e055-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1e055-127">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1e055-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1e055-128">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e055-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e055-129">Veja também</span><span class="sxs-lookup"><span data-stu-id="1e055-129">See also</span></span>

- [<span data-ttu-id="1e055-130">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="1e055-130">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="1e055-131">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="1e055-131">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="1e055-132">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="1e055-132">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="1e055-133">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="1e055-133">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
