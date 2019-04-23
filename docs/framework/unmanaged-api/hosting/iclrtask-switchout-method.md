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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a215189461bd22011462842bf02ff6c0109119fa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59090025"
---
# <a name="iclrtaskswitchout-method"></a><span data-ttu-id="a35ac-102">Método ICLRTask::SwitchOut</span><span class="sxs-lookup"><span data-stu-id="a35ac-102">ICLRTask::SwitchOut Method</span></span>
<span data-ttu-id="a35ac-103">Notifica o common language runtime (CLR) que a tarefa representada por atual [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instância não está mais em um estado operacional.</span><span class="sxs-lookup"><span data-stu-id="a35ac-103">Notifies the common language runtime (CLR) that the task represented by the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance is no longer in an operable state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a35ac-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a35ac-104">Syntax</span></span>  
  
```  
HRESULT SwitchOut ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="a35ac-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="a35ac-105">Return Value</span></span>  
  
|<span data-ttu-id="a35ac-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a35ac-106">HRESULT</span></span>|<span data-ttu-id="a35ac-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="a35ac-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a35ac-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="a35ac-108">S_OK</span></span>|<span data-ttu-id="a35ac-109">`SwitchOut` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="a35ac-109">`SwitchOut` returned successfully.</span></span>|  
|<span data-ttu-id="a35ac-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a35ac-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a35ac-111">O CLR não tenha sido carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="a35ac-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a35ac-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a35ac-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a35ac-113">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="a35ac-113">The call timed out.</span></span>|  
|<span data-ttu-id="a35ac-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a35ac-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a35ac-115">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="a35ac-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a35ac-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a35ac-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a35ac-117">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="a35ac-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a35ac-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a35ac-118">E_FAIL</span></span>|<span data-ttu-id="a35ac-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="a35ac-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a35ac-120">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="a35ac-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a35ac-121">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a35ac-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a35ac-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="a35ac-122">Remarks</span></span>  
 <span data-ttu-id="a35ac-123">Um host chama `SwitchOut` informe ao CLR que ele interrompeu a execução da tarefa que atual `ICLRTask` instância representa e reagendará a tarefa.</span><span class="sxs-lookup"><span data-stu-id="a35ac-123">A host calls `SwitchOut` to inform the CLR that it has temporarily stopped executing the task that the current `ICLRTask` instance represents, and will reschedule the task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a35ac-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a35ac-124">Requirements</span></span>  
 <span data-ttu-id="a35ac-125">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a35ac-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a35ac-126">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a35ac-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a35ac-127">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="a35ac-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a35ac-128">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a35ac-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a35ac-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a35ac-129">See also</span></span>

- [<span data-ttu-id="a35ac-130">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="a35ac-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="a35ac-131">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="a35ac-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="a35ac-132">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="a35ac-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="a35ac-133">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="a35ac-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
