---
title: Método ICLRTaskManager::GetCurrentTask
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.GetCurrentTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::GetCurrentTask
helpviewer_keywords:
- GetCurrentTask method, ICLRTaskManager interface [.NET Framework hosting]
- ICLRTaskManager::GetCurrentTask method [.NET Framework hosting]
ms.assetid: c0b82a9f-edc6-4878-9c81-48de53c02142
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c2efc8e0b47e68e53858bc949e6f0d0ca1352c7e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57501572"
---
# <a name="iclrtaskmanagergetcurrenttask-method"></a><span data-ttu-id="58e69-102">Método ICLRTaskManager::GetCurrentTask</span><span class="sxs-lookup"><span data-stu-id="58e69-102">ICLRTaskManager::GetCurrentTask Method</span></span>
<span data-ttu-id="58e69-103">Obtém o [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instância que está sendo executado no thread do sistema operacional que originou a chamada de método.</span><span class="sxs-lookup"><span data-stu-id="58e69-103">Gets the [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance that is currently running on the operating system thread from which the method call originated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58e69-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="58e69-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentTask (  
    [out] ICLRTask **ppTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="58e69-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="58e69-105">Parameters</span></span>  
 `ppTask`  
 <span data-ttu-id="58e69-106">[out] Um ponteiro para o endereço de um `ICLRTask` instância que está sendo executado no thread do sistema operacional do qual a chamada foi originada, ou nulo se nenhuma tarefa está em execução nesse thread.</span><span class="sxs-lookup"><span data-stu-id="58e69-106">[out] A pointer to the address of an `ICLRTask` instance that is currently executing on the operating system thread from which the call originated, or null if no task is currently executing on this thread.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="58e69-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="58e69-107">Return Value</span></span>  
  
|<span data-ttu-id="58e69-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="58e69-108">HRESULT</span></span>|<span data-ttu-id="58e69-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="58e69-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="58e69-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="58e69-110">S_OK</span></span>|<span data-ttu-id="58e69-111">O método é retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="58e69-111">The method returned successfully.</span></span>|  
|<span data-ttu-id="58e69-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="58e69-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="58e69-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="58e69-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="58e69-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="58e69-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="58e69-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="58e69-115">The call timed out.</span></span>|  
|<span data-ttu-id="58e69-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="58e69-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="58e69-117">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="58e69-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="58e69-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="58e69-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="58e69-119">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="58e69-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="58e69-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="58e69-120">E_FAIL</span></span>|<span data-ttu-id="58e69-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="58e69-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="58e69-122">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="58e69-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="58e69-123">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="58e69-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="58e69-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="58e69-124">Remarks</span></span>  
 <span data-ttu-id="58e69-125">O `ICLRTask` da instância que o `ppTask` parâmetro aponta para representa a tarefa em execução no momento para o CLR.</span><span class="sxs-lookup"><span data-stu-id="58e69-125">The `ICLRTask` instance that the `ppTask` parameter points to represents the currently executing task for the CLR.</span></span> <span data-ttu-id="58e69-126">O `ICLRTask` instância está associada com um correspondente [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instância que representa a tarefa para o host.</span><span class="sxs-lookup"><span data-stu-id="58e69-126">The `ICLRTask` instance is associated with a corresponding [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that represents the task for the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58e69-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="58e69-127">Requirements</span></span>  
 <span data-ttu-id="58e69-128">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58e69-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58e69-129">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="58e69-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="58e69-130">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="58e69-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="58e69-131">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58e69-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58e69-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="58e69-132">See also</span></span>
- [<span data-ttu-id="58e69-133">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="58e69-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="58e69-134">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="58e69-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="58e69-135">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="58e69-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="58e69-136">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="58e69-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
