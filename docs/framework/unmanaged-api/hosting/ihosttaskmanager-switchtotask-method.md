---
title: "Método IHostTaskManager::SwitchToTask"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTaskManager.SwitchToTask
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTaskManager::SwitchToTask
helpviewer_keywords:
- IHostTaskManager::SwitchToTask method [.NET Framework hosting]
- SwitchToTask method [.NET Framework hosting]
ms.assetid: 35d0c27e-4b14-49ce-810d-7ab2120177e8
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9b85c762bd2d10baddfa013a8310e3b542a94af6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ihosttaskmanagerswitchtotask-method"></a><span data-ttu-id="19562-102">Método IHostTaskManager::SwitchToTask</span><span class="sxs-lookup"><span data-stu-id="19562-102">IHostTaskManager::SwitchToTask Method</span></span>
<span data-ttu-id="19562-103">Notifica o host que ele deve alternar a tarefa atual.</span><span class="sxs-lookup"><span data-stu-id="19562-103">Notifies the host that it should switch out the current task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19562-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="19562-104">Syntax</span></span>  
  
```  
HRESULT SwitchToTask (  
    [in] DWORD option  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="19562-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="19562-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="19562-106">[in] Uma da [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) valores de enumeração, que indica a ação que o host deve executar se os blocos da operação solicitada.</span><span class="sxs-lookup"><span data-stu-id="19562-106">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) enumeration values, indicating the action the host should take if the requested operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="19562-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="19562-107">Return Value</span></span>  
  
|<span data-ttu-id="19562-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="19562-108">HRESULT</span></span>|<span data-ttu-id="19562-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="19562-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="19562-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="19562-110">S_OK</span></span>|<span data-ttu-id="19562-111">`SwitchToTask`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="19562-111">`SwitchToTask` returned successfully.</span></span>|  
|<span data-ttu-id="19562-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="19562-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="19562-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="19562-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="19562-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="19562-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="19562-115">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="19562-115">The call timed out.</span></span>|  
|<span data-ttu-id="19562-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="19562-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="19562-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="19562-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="19562-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="19562-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="19562-119">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="19562-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="19562-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="19562-120">E_FAIL</span></span>|<span data-ttu-id="19562-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="19562-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="19562-122">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="19562-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="19562-123">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="19562-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="19562-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="19562-124">Remarks</span></span>  
 <span data-ttu-id="19562-125">O host pode mudar em outra tarefa como necessário ou desejado.</span><span class="sxs-lookup"><span data-stu-id="19562-125">The host can switch in another task as desired or needed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="19562-126">`SwitchToTask`não especifica quais tarefas o host deve alternar Ele especifica apenas a tarefa que ele deve alternar entre.</span><span class="sxs-lookup"><span data-stu-id="19562-126">`SwitchToTask` does not specify which task the host should switch to; it specifies only the task that it should switch from.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19562-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="19562-127">Requirements</span></span>  
 <span data-ttu-id="19562-128">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19562-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19562-129">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="19562-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="19562-130">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="19562-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="19562-131">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19562-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19562-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="19562-132">See Also</span></span>  
 [<span data-ttu-id="19562-133">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="19562-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="19562-134">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="19562-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="19562-135">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="19562-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="19562-136">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="19562-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
