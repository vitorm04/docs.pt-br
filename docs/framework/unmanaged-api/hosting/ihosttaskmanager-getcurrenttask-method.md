---
title: Método IHostTaskManager::GetCurrentTask
ms.date: 03/30/2017
api_name:
- IHostTaskManager.GetCurrentTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::GetCurrentTask
helpviewer_keywords:
- GetCurrentTask method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::GetCurrentTask method [.NET Framework hosting]
ms.assetid: f17bca49-90bd-4dee-a5e1-b9a57ea46f85
topic_type:
- apiref
ms.openlocfilehash: 874951d6b5efed0dc08e6d0e166962767e295c3e
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842043"
---
# <a name="ihosttaskmanagergetcurrenttask-method"></a><span data-ttu-id="3b78a-102">Método IHostTaskManager::GetCurrentTask</span><span class="sxs-lookup"><span data-stu-id="3b78a-102">IHostTaskManager::GetCurrentTask Method</span></span>
<span data-ttu-id="3b78a-103">Obtém um ponteiro de interface para a tarefa que está atualmente em execução no thread do sistema operacional do qual essa chamada é feita.</span><span class="sxs-lookup"><span data-stu-id="3b78a-103">Gets an interface pointer to the task that is currently executing on the operating system thread from which this call is made.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b78a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3b78a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentTask (  
    [out] IHostTask **pTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3b78a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3b78a-105">Parameters</span></span>  
 `pTask`  
 <span data-ttu-id="3b78a-106">fora Um ponteiro para o endereço de uma instância de [IHostTask](ihosttask-interface.md) que representa a tarefa em execução no momento, ou NULL, se nenhuma tarefa estiver em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="3b78a-106">[out] A pointer to the address of an [IHostTask](ihosttask-interface.md) instance that represents the currently executing task, or null, if no task is currently executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3b78a-107">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="3b78a-107">Return Value</span></span>  
  
|<span data-ttu-id="3b78a-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3b78a-108">HRESULT</span></span>|<span data-ttu-id="3b78a-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="3b78a-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3b78a-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="3b78a-110">S_OK</span></span>|<span data-ttu-id="3b78a-111">`GetCurrentTask`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="3b78a-111">`GetCurrentTask` returned successfully.</span></span>|  
|<span data-ttu-id="3b78a-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3b78a-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3b78a-113">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="3b78a-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3b78a-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3b78a-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3b78a-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="3b78a-115">The call timed out.</span></span>|  
|<span data-ttu-id="3b78a-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3b78a-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3b78a-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="3b78a-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3b78a-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3b78a-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3b78a-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="3b78a-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3b78a-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3b78a-120">E_FAIL</span></span>|<span data-ttu-id="3b78a-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="3b78a-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3b78a-122">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="3b78a-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3b78a-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="3b78a-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="3b78a-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="3b78a-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="3b78a-125">`GetCurrentTask`foi chamado em um thread do sistema operacional fora do controle do host.</span><span class="sxs-lookup"><span data-stu-id="3b78a-125">`GetCurrentTask` was called on an operating system thread outside the control of the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3b78a-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="3b78a-126">Remarks</span></span>  
 <span data-ttu-id="3b78a-127">O host também pode definir o `pTask` parâmetro como nulo para impedir que uma tarefa que não foi iniciada Insira o CLR.</span><span class="sxs-lookup"><span data-stu-id="3b78a-127">The host can also set the `pTask` parameter to null to prevent a task that it did not initiate from entering the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b78a-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3b78a-128">Requirements</span></span>  
 <span data-ttu-id="3b78a-129">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3b78a-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b78a-130">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3b78a-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3b78a-131">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3b78a-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3b78a-132">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b78a-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b78a-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3b78a-133">See also</span></span>

- [<span data-ttu-id="3b78a-134">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="3b78a-134">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="3b78a-135">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="3b78a-135">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="3b78a-136">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="3b78a-136">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="3b78a-137">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="3b78a-137">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
