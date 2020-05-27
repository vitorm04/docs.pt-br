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
ms.openlocfilehash: 7d1511924fc70c42252881a46f8aebb437a3f4f7
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83841939"
---
# <a name="ihosttaskmanagerswitchtotask-method"></a><span data-ttu-id="0168d-102">Método IHostTaskManager::SwitchToTask</span><span class="sxs-lookup"><span data-stu-id="0168d-102">IHostTaskManager::SwitchToTask Method</span></span>
<span data-ttu-id="0168d-103">Notifica o host de que ele deve desativar a tarefa atual.</span><span class="sxs-lookup"><span data-stu-id="0168d-103">Notifies the host that it should switch out the current task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0168d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0168d-104">Syntax</span></span>  
  
```cpp  
HRESULT SwitchToTask (  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0168d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0168d-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="0168d-106">no Um dos [WAIT_OPTION](wait-option-enumeration.md) valores de enumeração, indicando a ação que o host deve executar se a operação solicitada for bloqueada.</span><span class="sxs-lookup"><span data-stu-id="0168d-106">[in] One of the [WAIT_OPTION](wait-option-enumeration.md) enumeration values, indicating the action the host should take if the requested operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0168d-107">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="0168d-107">Return Value</span></span>  
  
|<span data-ttu-id="0168d-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0168d-108">HRESULT</span></span>|<span data-ttu-id="0168d-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="0168d-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0168d-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="0168d-110">S_OK</span></span>|<span data-ttu-id="0168d-111">`SwitchToTask`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="0168d-111">`SwitchToTask` returned successfully.</span></span>|  
|<span data-ttu-id="0168d-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0168d-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0168d-113">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="0168d-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0168d-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0168d-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0168d-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="0168d-115">The call timed out.</span></span>|  
|<span data-ttu-id="0168d-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0168d-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0168d-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="0168d-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0168d-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0168d-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0168d-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="0168d-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0168d-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0168d-120">E_FAIL</span></span>|<span data-ttu-id="0168d-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="0168d-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0168d-122">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="0168d-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0168d-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0168d-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0168d-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="0168d-124">Remarks</span></span>  
 <span data-ttu-id="0168d-125">O host pode alternar em outra tarefa conforme desejado ou necessário.</span><span class="sxs-lookup"><span data-stu-id="0168d-125">The host can switch in another task as desired or needed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0168d-126">`SwitchToTask`não especifica a qual tarefa o host deve mudar; Ele especifica apenas a tarefa da qual ele deve mudar.</span><span class="sxs-lookup"><span data-stu-id="0168d-126">`SwitchToTask` does not specify which task the host should switch to; it specifies only the task that it should switch from.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0168d-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0168d-127">Requirements</span></span>  
 <span data-ttu-id="0168d-128">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0168d-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0168d-129">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0168d-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0168d-130">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0168d-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0168d-131">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0168d-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0168d-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0168d-132">See also</span></span>

- [<span data-ttu-id="0168d-133">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="0168d-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="0168d-134">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="0168d-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="0168d-135">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="0168d-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="0168d-136">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="0168d-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
