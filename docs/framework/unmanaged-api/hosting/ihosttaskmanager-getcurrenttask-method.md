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
ms.openlocfilehash: 2436288e2f2f241cab15b16abf4df99c73caec25
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59093716"
---
# <a name="ihosttaskmanagergetcurrenttask-method"></a><span data-ttu-id="251a3-102">Método IHostTaskManager::GetCurrentTask</span><span class="sxs-lookup"><span data-stu-id="251a3-102">IHostTaskManager::GetCurrentTask Method</span></span>
<span data-ttu-id="251a3-103">Obtém um ponteiro de interface para a tarefa que está sendo executado no thread do sistema operacional do qual essa chamada é feita.</span><span class="sxs-lookup"><span data-stu-id="251a3-103">Gets an interface pointer to the task that is currently executing on the operating system thread from which this call is made.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="251a3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="251a3-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentTask (  
    [out] IHostTask **pTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="251a3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="251a3-105">Parameters</span></span>  
 `pTask`  
 <span data-ttu-id="251a3-106">[out] Um ponteiro para o endereço de um [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instância que representa a tarefa em execução no momento, ou nulo, se nenhuma tarefa está em execução atualmente.</span><span class="sxs-lookup"><span data-stu-id="251a3-106">[out] A pointer to the address of an [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that represents the currently executing task, or null, if no task is currently executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="251a3-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="251a3-107">Return Value</span></span>  
  
|<span data-ttu-id="251a3-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="251a3-108">HRESULT</span></span>|<span data-ttu-id="251a3-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="251a3-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="251a3-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="251a3-110">S_OK</span></span>|`GetCurrentTask` <span data-ttu-id="251a3-111">retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="251a3-111">returned successfully.</span></span>|  
|<span data-ttu-id="251a3-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="251a3-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="251a3-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="251a3-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="251a3-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="251a3-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="251a3-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="251a3-115">The call timed out.</span></span>|  
|<span data-ttu-id="251a3-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="251a3-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="251a3-117">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="251a3-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="251a3-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="251a3-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="251a3-119">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="251a3-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="251a3-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="251a3-120">E_FAIL</span></span>|<span data-ttu-id="251a3-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="251a3-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="251a3-122">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="251a3-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="251a3-123">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="251a3-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="251a3-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="251a3-124">HOST_E_INVALIDOPERATION</span></span>|`GetCurrentTask` <span data-ttu-id="251a3-125">foi chamado em um thread do sistema operacional fora do controle do host.</span><span class="sxs-lookup"><span data-stu-id="251a3-125">was called on an operating system thread outside the control of the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="251a3-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="251a3-126">Remarks</span></span>  
 <span data-ttu-id="251a3-127">O host também pode definir o `pTask` parâmetro para nulo para impedir que uma tarefa que ele não iniciou inserindo o CLR.</span><span class="sxs-lookup"><span data-stu-id="251a3-127">The host can also set the `pTask` parameter to null to prevent a task that it did not initiate from entering the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="251a3-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="251a3-128">Requirements</span></span>  
 <span data-ttu-id="251a3-129">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="251a3-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="251a3-130">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="251a3-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="251a3-131">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="251a3-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="251a3-132">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="251a3-132">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="251a3-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="251a3-133">See also</span></span>

- [<span data-ttu-id="251a3-134">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="251a3-134">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="251a3-135">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="251a3-135">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="251a3-136">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="251a3-136">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="251a3-137">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="251a3-137">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
