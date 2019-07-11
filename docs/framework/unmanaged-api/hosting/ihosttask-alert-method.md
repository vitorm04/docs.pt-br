---
title: Método IHostTask::Alert
ms.date: 03/30/2017
api_name:
- IHostTask.Alert
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::Alert
helpviewer_keywords:
- IHostTask::Alert method [.NET Framework hosting]
- Alert method, IHostTask interface [.NET Framework hosting]
ms.assetid: 5245d4b5-b6c3-48df-9cb9-8caf059f43fb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3a5e3b82645456ffa574f63931abbf60a2194540
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764541"
---
# <a name="ihosttaskalert-method"></a><span data-ttu-id="e37ec-102">Método IHostTask::Alert</span><span class="sxs-lookup"><span data-stu-id="e37ec-102">IHostTask::Alert Method</span></span>
<span data-ttu-id="e37ec-103">Solicitações que o host da tarefa representada pela atual wake [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) da instância, portanto, a tarefa pode ser anulada.</span><span class="sxs-lookup"><span data-stu-id="e37ec-103">Requests that the host wake the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance, so the task can be aborted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e37ec-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e37ec-104">Syntax</span></span>  
  
```cpp  
HRESULT Alert ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="e37ec-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="e37ec-105">Return Value</span></span>  
  
|<span data-ttu-id="e37ec-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e37ec-106">HRESULT</span></span>|<span data-ttu-id="e37ec-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="e37ec-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e37ec-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="e37ec-108">S_OK</span></span>|<span data-ttu-id="e37ec-109">O método é retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="e37ec-109">The method returned successfully.</span></span>|  
|<span data-ttu-id="e37ec-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e37ec-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e37ec-111">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="e37ec-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e37ec-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e37ec-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e37ec-113">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="e37ec-113">The call timed out.</span></span>|  
|<span data-ttu-id="e37ec-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e37ec-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e37ec-115">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="e37ec-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e37ec-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e37ec-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e37ec-117">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="e37ec-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e37ec-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e37ec-118">E_FAIL</span></span>|<span data-ttu-id="e37ec-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="e37ec-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e37ec-120">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="e37ec-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e37ec-121">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e37ec-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e37ec-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="e37ec-122">Remarks</span></span>  
 <span data-ttu-id="e37ec-123">O CLR chama o `Alert` método quando <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> é chamado do código do usuário, ou quando o <xref:System.AppDomain> associados ao atual <xref:System.Threading.Thread> é desligado.</span><span class="sxs-lookup"><span data-stu-id="e37ec-123">The CLR calls the `Alert` method when <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> is called from user code, or when the <xref:System.AppDomain> associated with the current <xref:System.Threading.Thread> shuts down.</span></span> <span data-ttu-id="e37ec-124">O host deve retornar imediatamente, porque a chamada é feita de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="e37ec-124">The host must return immediately, because the call is made asynchronously.</span></span> <span data-ttu-id="e37ec-125">Se o host não é possível alertar a tarefa imediatamente, ele deve ativar na próxima vez que ele entra em um estado em que ele pode ser alertado.</span><span class="sxs-lookup"><span data-stu-id="e37ec-125">If the host cannot alert the task immediately, it must wake up the next time it enters a state in which it can be alerted.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e37ec-126">`Alert` afeta somente as tarefas para o qual o tempo de execução passou uma [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) valor de WAIT_ALERTABLE para métodos, tais como [ingressar](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md).</span><span class="sxs-lookup"><span data-stu-id="e37ec-126">`Alert` affects only those tasks to which the runtime has passed a [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) value of WAIT_ALERTABLE to methods such as [Join](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e37ec-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e37ec-127">Requirements</span></span>  
 <span data-ttu-id="e37ec-128">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e37ec-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e37ec-129">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e37ec-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e37ec-130">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="e37ec-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e37ec-131">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e37ec-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e37ec-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e37ec-132">See also</span></span>

- [<span data-ttu-id="e37ec-133">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="e37ec-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="e37ec-134">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="e37ec-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="e37ec-135">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="e37ec-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="e37ec-136">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="e37ec-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
