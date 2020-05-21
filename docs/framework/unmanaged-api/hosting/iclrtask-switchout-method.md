---
title: Método ICLRTask::SwitchOut
ms.date: 03/30/2017
api_name:
- ICLRTask.SwitchOut
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::SwitchOut
helpviewer_keywords:
- ICLRTask::SwitchOut method [.NET Framework hosting]
- SwitchOut method [.NET Framework hosting]
ms.assetid: b6fb168c-b24b-4ecf-a390-2b5ba3317ae6
topic_type:
- apiref
ms.openlocfilehash: 75517ae55ebae07242f19c19c5473780ce4b0809
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762910"
---
# <a name="iclrtaskswitchout-method"></a><span data-ttu-id="37f2c-102">Método ICLRTask::SwitchOut</span><span class="sxs-lookup"><span data-stu-id="37f2c-102">ICLRTask::SwitchOut Method</span></span>
<span data-ttu-id="37f2c-103">Notifica o Common Language Runtime (CLR) que a tarefa representada pela instância [ICLRTask](iclrtask-interface.md) atual não está mais em um estado operável.</span><span class="sxs-lookup"><span data-stu-id="37f2c-103">Notifies the common language runtime (CLR) that the task represented by the current [ICLRTask](iclrtask-interface.md) instance is no longer in an operable state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37f2c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="37f2c-104">Syntax</span></span>  
  
```cpp  
HRESULT SwitchOut ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="37f2c-105">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="37f2c-105">Return Value</span></span>  
  
|<span data-ttu-id="37f2c-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="37f2c-106">HRESULT</span></span>|<span data-ttu-id="37f2c-107">Description</span><span class="sxs-lookup"><span data-stu-id="37f2c-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="37f2c-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="37f2c-108">S_OK</span></span>|<span data-ttu-id="37f2c-109">`SwitchOut`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="37f2c-109">`SwitchOut` returned successfully.</span></span>|  
|<span data-ttu-id="37f2c-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="37f2c-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="37f2c-111">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="37f2c-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="37f2c-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="37f2c-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="37f2c-113">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="37f2c-113">The call timed out.</span></span>|  
|<span data-ttu-id="37f2c-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="37f2c-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="37f2c-115">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="37f2c-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="37f2c-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="37f2c-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="37f2c-117">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="37f2c-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="37f2c-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="37f2c-118">E_FAIL</span></span>|<span data-ttu-id="37f2c-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="37f2c-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="37f2c-120">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="37f2c-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="37f2c-121">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="37f2c-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="37f2c-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="37f2c-122">Remarks</span></span>  
 <span data-ttu-id="37f2c-123">Um host chama `SwitchOut` para informar ao CLR que ele interrompeu temporariamente a execução da tarefa que a `ICLRTask` instância atual representa e reagendará a tarefa.</span><span class="sxs-lookup"><span data-stu-id="37f2c-123">A host calls `SwitchOut` to inform the CLR that it has temporarily stopped executing the task that the current `ICLRTask` instance represents, and will reschedule the task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37f2c-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="37f2c-124">Requirements</span></span>  
 <span data-ttu-id="37f2c-125">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37f2c-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37f2c-126">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="37f2c-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="37f2c-127">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="37f2c-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="37f2c-128">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37f2c-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37f2c-129">Veja também</span><span class="sxs-lookup"><span data-stu-id="37f2c-129">See also</span></span>

- [<span data-ttu-id="37f2c-130">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="37f2c-130">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="37f2c-131">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="37f2c-131">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="37f2c-132">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="37f2c-132">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="37f2c-133">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="37f2c-133">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
