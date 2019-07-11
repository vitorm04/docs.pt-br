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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cb3044927e0d9975ed9347cd4f4896b3b75d3e29
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67749628"
---
# <a name="ihosttaskmanagergetcurrenttask-method"></a><span data-ttu-id="2048c-102">Método IHostTaskManager::GetCurrentTask</span><span class="sxs-lookup"><span data-stu-id="2048c-102">IHostTaskManager::GetCurrentTask Method</span></span>
<span data-ttu-id="2048c-103">Obtém um ponteiro de interface para a tarefa que está sendo executado no thread do sistema operacional do qual essa chamada é feita.</span><span class="sxs-lookup"><span data-stu-id="2048c-103">Gets an interface pointer to the task that is currently executing on the operating system thread from which this call is made.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2048c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2048c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentTask (  
    [out] IHostTask **pTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2048c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2048c-105">Parameters</span></span>  
 `pTask`  
 <span data-ttu-id="2048c-106">[out] Um ponteiro para o endereço de um [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instância que representa a tarefa em execução no momento, ou nulo, se nenhuma tarefa está em execução atualmente.</span><span class="sxs-lookup"><span data-stu-id="2048c-106">[out] A pointer to the address of an [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that represents the currently executing task, or null, if no task is currently executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2048c-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="2048c-107">Return Value</span></span>  
  
|<span data-ttu-id="2048c-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2048c-108">HRESULT</span></span>|<span data-ttu-id="2048c-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="2048c-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2048c-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="2048c-110">S_OK</span></span>|<span data-ttu-id="2048c-111">`GetCurrentTask` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="2048c-111">`GetCurrentTask` returned successfully.</span></span>|  
|<span data-ttu-id="2048c-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2048c-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2048c-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="2048c-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2048c-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2048c-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2048c-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="2048c-115">The call timed out.</span></span>|  
|<span data-ttu-id="2048c-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2048c-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2048c-117">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="2048c-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2048c-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2048c-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2048c-119">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="2048c-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2048c-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2048c-120">E_FAIL</span></span>|<span data-ttu-id="2048c-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="2048c-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2048c-122">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="2048c-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2048c-123">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="2048c-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="2048c-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="2048c-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="2048c-125">`GetCurrentTask` foi chamado em um thread do sistema operacional fora do controle do host.</span><span class="sxs-lookup"><span data-stu-id="2048c-125">`GetCurrentTask` was called on an operating system thread outside the control of the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2048c-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="2048c-126">Remarks</span></span>  
 <span data-ttu-id="2048c-127">O host também pode definir o `pTask` parâmetro para nulo para impedir que uma tarefa que ele não iniciou inserindo o CLR.</span><span class="sxs-lookup"><span data-stu-id="2048c-127">The host can also set the `pTask` parameter to null to prevent a task that it did not initiate from entering the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2048c-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2048c-128">Requirements</span></span>  
 <span data-ttu-id="2048c-129">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2048c-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2048c-130">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2048c-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2048c-131">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="2048c-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2048c-132">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2048c-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2048c-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2048c-133">See also</span></span>

- [<span data-ttu-id="2048c-134">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="2048c-134">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="2048c-135">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="2048c-135">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="2048c-136">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="2048c-136">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="2048c-137">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="2048c-137">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
