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
ms.openlocfilehash: a50c9f7fc5921d3e5c21dd3566de81ac2249f3dd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59110554"
---
# <a name="ihosttaskmanagerswitchtotask-method"></a><span data-ttu-id="e6a98-102">Método IHostTaskManager::SwitchToTask</span><span class="sxs-lookup"><span data-stu-id="e6a98-102">IHostTaskManager::SwitchToTask Method</span></span>
<span data-ttu-id="e6a98-103">Notifica o host que ele deve alternar a tarefa atual.</span><span class="sxs-lookup"><span data-stu-id="e6a98-103">Notifies the host that it should switch out the current task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6a98-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e6a98-104">Syntax</span></span>  
  
```  
HRESULT SwitchToTask (  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e6a98-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e6a98-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="e6a98-106">[in] Um dos [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) valores de enumeração que indica a ação que o host deve executar se os blocos de operação solicitada.</span><span class="sxs-lookup"><span data-stu-id="e6a98-106">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) enumeration values, indicating the action the host should take if the requested operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e6a98-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="e6a98-107">Return Value</span></span>  
  
|<span data-ttu-id="e6a98-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e6a98-108">HRESULT</span></span>|<span data-ttu-id="e6a98-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="e6a98-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e6a98-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="e6a98-110">S_OK</span></span>|`SwitchToTask` <span data-ttu-id="e6a98-111">retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="e6a98-111">returned successfully.</span></span>|  
|<span data-ttu-id="e6a98-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e6a98-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e6a98-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="e6a98-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e6a98-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e6a98-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e6a98-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="e6a98-115">The call timed out.</span></span>|  
|<span data-ttu-id="e6a98-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e6a98-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e6a98-117">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="e6a98-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e6a98-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e6a98-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e6a98-119">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="e6a98-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e6a98-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e6a98-120">E_FAIL</span></span>|<span data-ttu-id="e6a98-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="e6a98-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e6a98-122">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="e6a98-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e6a98-123">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e6a98-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e6a98-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="e6a98-124">Remarks</span></span>  
 <span data-ttu-id="e6a98-125">O host pode mudar em outra tarefa como necessária ou desejada.</span><span class="sxs-lookup"><span data-stu-id="e6a98-125">The host can switch in another task as desired or needed.</span></span>  
  
> [!NOTE]
>  `SwitchToTask` <span data-ttu-id="e6a98-126">não especifica qual tarefa o host deve mudar para; Ele especifica apenas a tarefa que ele deve alternar do.</span><span class="sxs-lookup"><span data-stu-id="e6a98-126">does not specify which task the host should switch to; it specifies only the task that it should switch from.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6a98-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e6a98-127">Requirements</span></span>  
 <span data-ttu-id="e6a98-128">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6a98-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6a98-129">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e6a98-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e6a98-130">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="e6a98-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="e6a98-131">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="e6a98-131">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e6a98-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e6a98-132">See also</span></span>

- [<span data-ttu-id="e6a98-133">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="e6a98-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="e6a98-134">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="e6a98-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="e6a98-135">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="e6a98-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="e6a98-136">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="e6a98-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
