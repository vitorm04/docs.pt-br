---
title: Método IHostTask::SetCLRTask
ms.date: 03/30/2017
api_name:
- IHostTask.SetCLRTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::SetCLRTask
helpviewer_keywords:
- SetCLRTask method [.NET Framework hosting]
- IHostTask::SetCLRTask method [.NET Framework hosting]
ms.assetid: e9d39c80-41a1-49e7-bb5e-ea3433bfb5d7
topic_type:
- apiref
ms.openlocfilehash: b6eac134a4ffb1813cdc6957632ce5fb9b1a5fff
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842264"
---
# <a name="ihosttasksetclrtask-method"></a><span data-ttu-id="a8197-102">Método IHostTask::SetCLRTask</span><span class="sxs-lookup"><span data-stu-id="a8197-102">IHostTask::SetCLRTask Method</span></span>
<span data-ttu-id="a8197-103">Associa uma `ICLRTask` instância à instância de [IHostTask](ihosttask-interface.md) atual.</span><span class="sxs-lookup"><span data-stu-id="a8197-103">Associates an `ICLRTask` instance with the current [IHostTask](ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8197-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a8197-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCLRTask (  
    [in] ICLRTask *pCLRTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a8197-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a8197-105">Parameters</span></span>  
 `pCLRTask`  
 <span data-ttu-id="a8197-106">no Um ponteiro de interface para a `ICLRTask` instância a ser associada à `IHostTask` instância atual.</span><span class="sxs-lookup"><span data-stu-id="a8197-106">[in] An interface pointer to the `ICLRTask` instance to be associated with the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a8197-107">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="a8197-107">Return Value</span></span>  
  
|<span data-ttu-id="a8197-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a8197-108">HRESULT</span></span>|<span data-ttu-id="a8197-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="a8197-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a8197-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="a8197-110">S_OK</span></span>|<span data-ttu-id="a8197-111">`SetCLRTask`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="a8197-111">`SetCLRTask` returned successfully.</span></span>|  
|<span data-ttu-id="a8197-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a8197-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a8197-113">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="a8197-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a8197-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a8197-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a8197-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="a8197-115">The call timed out.</span></span>|  
|<span data-ttu-id="a8197-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a8197-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a8197-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="a8197-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a8197-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a8197-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a8197-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="a8197-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a8197-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a8197-120">E_FAIL</span></span>|<span data-ttu-id="a8197-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="a8197-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a8197-122">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="a8197-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a8197-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a8197-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a8197-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="a8197-124">Remarks</span></span>  
 <span data-ttu-id="a8197-125">O CLR chama `SetCLRTask` para associar uma `ICLRTask` instância à instância atual `IHostTask` , que foi criada por uma chamada para [IHostTaskManager:: CreateTask](ihosttaskmanager-createtask-method.md).</span><span class="sxs-lookup"><span data-stu-id="a8197-125">The CLR calls `SetCLRTask` to associate an `ICLRTask` instance with the current `IHostTask` instance, which was created by a call to [IHostTaskManager::CreateTask](ihosttaskmanager-createtask-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8197-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a8197-126">Requirements</span></span>  
 <span data-ttu-id="a8197-127">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8197-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8197-128">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a8197-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a8197-129">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a8197-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a8197-130">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8197-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8197-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a8197-131">See also</span></span>

- [<span data-ttu-id="a8197-132">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="a8197-132">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="a8197-133">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="a8197-133">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="a8197-134">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="a8197-134">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="a8197-135">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="a8197-135">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
