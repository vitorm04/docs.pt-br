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
ms.openlocfilehash: 9c7bf550985b5177348541aaa148c88c7c205258
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54490711"
---
# <a name="ihosttaskmanagerswitchtotask-method"></a><span data-ttu-id="9ff3e-102">Método IHostTaskManager::SwitchToTask</span><span class="sxs-lookup"><span data-stu-id="9ff3e-102">IHostTaskManager::SwitchToTask Method</span></span>
<span data-ttu-id="9ff3e-103">Notifica o host que ele deve alternar a tarefa atual.</span><span class="sxs-lookup"><span data-stu-id="9ff3e-103">Notifies the host that it should switch out the current task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ff3e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9ff3e-104">Syntax</span></span>  
  
```  
HRESULT SwitchToTask (  
    [in] DWORD option  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9ff3e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9ff3e-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="9ff3e-106">[in] Um dos [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) valores de enumeração que indica a ação que o host deve executar se os blocos de operação solicitada.</span><span class="sxs-lookup"><span data-stu-id="9ff3e-106">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) enumeration values, indicating the action the host should take if the requested operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9ff3e-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="9ff3e-107">Return Value</span></span>  
  
|<span data-ttu-id="9ff3e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9ff3e-108">HRESULT</span></span>|<span data-ttu-id="9ff3e-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="9ff3e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9ff3e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="9ff3e-110">S_OK</span></span>|<span data-ttu-id="9ff3e-111">`SwitchToTask` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="9ff3e-111">`SwitchToTask` returned successfully.</span></span>|  
|<span data-ttu-id="9ff3e-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9ff3e-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9ff3e-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="9ff3e-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9ff3e-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9ff3e-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9ff3e-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="9ff3e-115">The call timed out.</span></span>|  
|<span data-ttu-id="9ff3e-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9ff3e-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9ff3e-117">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="9ff3e-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9ff3e-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9ff3e-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9ff3e-119">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="9ff3e-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9ff3e-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9ff3e-120">E_FAIL</span></span>|<span data-ttu-id="9ff3e-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="9ff3e-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9ff3e-122">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="9ff3e-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9ff3e-123">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9ff3e-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9ff3e-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="9ff3e-124">Remarks</span></span>  
 <span data-ttu-id="9ff3e-125">O host pode mudar em outra tarefa como necessária ou desejada.</span><span class="sxs-lookup"><span data-stu-id="9ff3e-125">The host can switch in another task as desired or needed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9ff3e-126">`SwitchToTask` não especifica qual tarefa o host deve mudar para; Ele especifica apenas a tarefa que ele deve alternar do.</span><span class="sxs-lookup"><span data-stu-id="9ff3e-126">`SwitchToTask` does not specify which task the host should switch to; it specifies only the task that it should switch from.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ff3e-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9ff3e-127">Requirements</span></span>  
 <span data-ttu-id="9ff3e-128">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ff3e-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ff3e-129">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9ff3e-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9ff3e-130">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="9ff3e-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9ff3e-131">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ff3e-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ff3e-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9ff3e-132">See also</span></span>
- [<span data-ttu-id="9ff3e-133">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="9ff3e-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="9ff3e-134">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="9ff3e-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="9ff3e-135">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="9ff3e-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="9ff3e-136">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="9ff3e-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
