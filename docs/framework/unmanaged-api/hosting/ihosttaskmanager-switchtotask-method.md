---
title: Método IHostTaskManager::SwitchToTask
ms.date: 03/30/2017
api_name:
- IHostTaskManager.SwitchToTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::SwitchToTask
helpviewer_keywords:
- IHostTaskManager::SwitchToTask method [.NET Framework hosting]
- SwitchToTask method [.NET Framework hosting]
ms.assetid: 35d0c27e-4b14-49ce-810d-7ab2120177e8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7c4b6780b9784c5d02499224e6787f2cda6cc8e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33442822"
---
# <a name="ihosttaskmanagerswitchtotask-method"></a><span data-ttu-id="f48c5-102">Método IHostTaskManager::SwitchToTask</span><span class="sxs-lookup"><span data-stu-id="f48c5-102">IHostTaskManager::SwitchToTask Method</span></span>
<span data-ttu-id="f48c5-103">Notifica o host que ele deve alternar a tarefa atual.</span><span class="sxs-lookup"><span data-stu-id="f48c5-103">Notifies the host that it should switch out the current task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f48c5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f48c5-104">Syntax</span></span>  
  
```  
HRESULT SwitchToTask (  
    [in] DWORD option  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f48c5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f48c5-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="f48c5-106">[in] Uma da [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) valores de enumeração, que indica a ação que o host deve executar se os blocos da operação solicitada.</span><span class="sxs-lookup"><span data-stu-id="f48c5-106">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) enumeration values, indicating the action the host should take if the requested operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f48c5-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="f48c5-107">Return Value</span></span>  
  
|<span data-ttu-id="f48c5-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f48c5-108">HRESULT</span></span>|<span data-ttu-id="f48c5-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="f48c5-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f48c5-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="f48c5-110">S_OK</span></span>|<span data-ttu-id="f48c5-111">`SwitchToTask` retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="f48c5-111">`SwitchToTask` returned successfully.</span></span>|  
|<span data-ttu-id="f48c5-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f48c5-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f48c5-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="f48c5-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f48c5-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f48c5-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f48c5-115">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="f48c5-115">The call timed out.</span></span>|  
|<span data-ttu-id="f48c5-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f48c5-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f48c5-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="f48c5-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f48c5-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f48c5-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f48c5-119">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="f48c5-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f48c5-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f48c5-120">E_FAIL</span></span>|<span data-ttu-id="f48c5-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="f48c5-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f48c5-122">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="f48c5-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f48c5-123">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f48c5-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f48c5-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="f48c5-124">Remarks</span></span>  
 <span data-ttu-id="f48c5-125">O host pode mudar em outra tarefa como necessário ou desejado.</span><span class="sxs-lookup"><span data-stu-id="f48c5-125">The host can switch in another task as desired or needed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f48c5-126">`SwitchToTask` não especifica quais tarefas o host deve alternar Ele especifica apenas a tarefa que ele deve alternar entre.</span><span class="sxs-lookup"><span data-stu-id="f48c5-126">`SwitchToTask` does not specify which task the host should switch to; it specifies only the task that it should switch from.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f48c5-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f48c5-127">Requirements</span></span>  
 <span data-ttu-id="f48c5-128">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f48c5-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f48c5-129">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f48c5-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f48c5-130">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="f48c5-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f48c5-131">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f48c5-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f48c5-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f48c5-132">See Also</span></span>  
 [<span data-ttu-id="f48c5-133">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="f48c5-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="f48c5-134">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="f48c5-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="f48c5-135">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="f48c5-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="f48c5-136">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="f48c5-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
