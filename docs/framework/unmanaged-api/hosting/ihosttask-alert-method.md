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
ms.openlocfilehash: 057e2aafff726b187f36b8b52859b2f2e812e70e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33442358"
---
# <a name="ihosttaskalert-method"></a><span data-ttu-id="52b0d-102">Método IHostTask::Alert</span><span class="sxs-lookup"><span data-stu-id="52b0d-102">IHostTask::Alert Method</span></span>
<span data-ttu-id="52b0d-103">Solicitações que o host de ativação da tarefa representada pela atual [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instância, para que a tarefa pode ser anulada.</span><span class="sxs-lookup"><span data-stu-id="52b0d-103">Requests that the host wake the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance, so the task can be aborted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52b0d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="52b0d-104">Syntax</span></span>  
  
```  
HRESULT Alert ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="52b0d-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="52b0d-105">Return Value</span></span>  
  
|<span data-ttu-id="52b0d-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="52b0d-106">HRESULT</span></span>|<span data-ttu-id="52b0d-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="52b0d-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="52b0d-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="52b0d-108">S_OK</span></span>|<span data-ttu-id="52b0d-109">O método é retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="52b0d-109">The method returned successfully.</span></span>|  
|<span data-ttu-id="52b0d-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="52b0d-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="52b0d-111">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="52b0d-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="52b0d-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="52b0d-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="52b0d-113">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="52b0d-113">The call timed out.</span></span>|  
|<span data-ttu-id="52b0d-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="52b0d-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="52b0d-115">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="52b0d-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="52b0d-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="52b0d-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="52b0d-117">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="52b0d-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="52b0d-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="52b0d-118">E_FAIL</span></span>|<span data-ttu-id="52b0d-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="52b0d-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="52b0d-120">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="52b0d-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="52b0d-121">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="52b0d-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="52b0d-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="52b0d-122">Remarks</span></span>  
 <span data-ttu-id="52b0d-123">O CLR chama o `Alert` método quando <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> é chamado de código do usuário, ou quando o <xref:System.AppDomain> associado atual <xref:System.Threading.Thread> é desligado.</span><span class="sxs-lookup"><span data-stu-id="52b0d-123">The CLR calls the `Alert` method when <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> is called from user code, or when the <xref:System.AppDomain> associated with the current <xref:System.Threading.Thread> shuts down.</span></span> <span data-ttu-id="52b0d-124">O host deve retornar imediatamente, porque a chamada é feita de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="52b0d-124">The host must return immediately, because the call is made asynchronously.</span></span> <span data-ttu-id="52b0d-125">Se o host não pode alertar a tarefa imediatamente, ele deve ativar na próxima vez que ele entra em um estado em que ele pode ser alertado.</span><span class="sxs-lookup"><span data-stu-id="52b0d-125">If the host cannot alert the task immediately, it must wake up the next time it enters a state in which it can be alerted.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="52b0d-126">`Alert` afeta somente as tarefas para o qual o tempo de execução foi passado um [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) valor de WAIT_ALERTABLE métodos como [ingressar](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md).</span><span class="sxs-lookup"><span data-stu-id="52b0d-126">`Alert` affects only those tasks to which the runtime has passed a [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) value of WAIT_ALERTABLE to methods such as [Join](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52b0d-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="52b0d-127">Requirements</span></span>  
 <span data-ttu-id="52b0d-128">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52b0d-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52b0d-129">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="52b0d-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="52b0d-130">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="52b0d-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="52b0d-131">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52b0d-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52b0d-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="52b0d-132">See Also</span></span>  
 [<span data-ttu-id="52b0d-133">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="52b0d-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="52b0d-134">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="52b0d-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="52b0d-135">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="52b0d-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="52b0d-136">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="52b0d-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
