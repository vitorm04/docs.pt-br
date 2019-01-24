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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bce823bd6a9ad26a705649a666aeb97dcfa0cdbc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54636541"
---
# <a name="ihosttasksetclrtask-method"></a><span data-ttu-id="3cfd5-102">Método IHostTask::SetCLRTask</span><span class="sxs-lookup"><span data-stu-id="3cfd5-102">IHostTask::SetCLRTask Method</span></span>
<span data-ttu-id="3cfd5-103">Associa um `ICLRTask` instância com atual [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instância.</span><span class="sxs-lookup"><span data-stu-id="3cfd5-103">Associates an `ICLRTask` instance with the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3cfd5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3cfd5-104">Syntax</span></span>  
  
```  
HRESULT SetCLRTask (  
    [in] ICLRTask *pCLRTask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3cfd5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3cfd5-105">Parameters</span></span>  
 `pCLRTask`  
 <span data-ttu-id="3cfd5-106">[in] Um ponteiro de interface para o `ICLRTask` instância a ser associado com a atual `IHostTask` instância.</span><span class="sxs-lookup"><span data-stu-id="3cfd5-106">[in] An interface pointer to the `ICLRTask` instance to be associated with the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3cfd5-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="3cfd5-107">Return Value</span></span>  
  
|<span data-ttu-id="3cfd5-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3cfd5-108">HRESULT</span></span>|<span data-ttu-id="3cfd5-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="3cfd5-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3cfd5-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="3cfd5-110">S_OK</span></span>|<span data-ttu-id="3cfd5-111">`SetCLRTask` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="3cfd5-111">`SetCLRTask` returned successfully.</span></span>|  
|<span data-ttu-id="3cfd5-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3cfd5-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3cfd5-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="3cfd5-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3cfd5-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3cfd5-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3cfd5-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="3cfd5-115">The call timed out.</span></span>|  
|<span data-ttu-id="3cfd5-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3cfd5-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3cfd5-117">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="3cfd5-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3cfd5-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3cfd5-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3cfd5-119">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="3cfd5-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3cfd5-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3cfd5-120">E_FAIL</span></span>|<span data-ttu-id="3cfd5-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="3cfd5-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3cfd5-122">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="3cfd5-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3cfd5-123">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="3cfd5-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3cfd5-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="3cfd5-124">Remarks</span></span>  
 <span data-ttu-id="3cfd5-125">O CLR chama `SetCLRTask` para associar uma `ICLRTask` instância com o atual `IHostTask` instância, que foi criada por uma chamada para [ihosttaskmanager:: Createtask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-createtask-method.md).</span><span class="sxs-lookup"><span data-stu-id="3cfd5-125">The CLR calls `SetCLRTask` to associate an `ICLRTask` instance with the current `IHostTask` instance, which was created by a call to [IHostTaskManager::CreateTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-createtask-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3cfd5-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3cfd5-126">Requirements</span></span>  
 <span data-ttu-id="3cfd5-127">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3cfd5-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3cfd5-128">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3cfd5-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3cfd5-129">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="3cfd5-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3cfd5-130">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3cfd5-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cfd5-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3cfd5-131">See also</span></span>
- [<span data-ttu-id="3cfd5-132">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="3cfd5-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="3cfd5-133">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="3cfd5-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="3cfd5-134">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="3cfd5-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="3cfd5-135">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="3cfd5-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
