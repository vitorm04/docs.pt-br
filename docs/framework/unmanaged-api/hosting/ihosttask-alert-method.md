---
title: "Método IHostTask::Alert"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTask.Alert
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTask::Alert
helpviewer_keywords:
- IHostTask::Alert method [.NET Framework hosting]
- Alert method, IHostTask interface [.NET Framework hosting]
ms.assetid: 5245d4b5-b6c3-48df-9cb9-8caf059f43fb
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 10dc8b9894c6f5444ccfcfd17f749df1a3fb5d05
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ihosttaskalert-method"></a><span data-ttu-id="29af1-102">Método IHostTask::Alert</span><span class="sxs-lookup"><span data-stu-id="29af1-102">IHostTask::Alert Method</span></span>
<span data-ttu-id="29af1-103">Solicitações que o host de ativação da tarefa representada pela atual [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instância, para que a tarefa pode ser anulada.</span><span class="sxs-lookup"><span data-stu-id="29af1-103">Requests that the host wake the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance, so the task can be aborted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29af1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="29af1-104">Syntax</span></span>  
  
```  
HRESULT Alert ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="29af1-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="29af1-105">Return Value</span></span>  
  
|<span data-ttu-id="29af1-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="29af1-106">HRESULT</span></span>|<span data-ttu-id="29af1-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="29af1-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="29af1-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="29af1-108">S_OK</span></span>|<span data-ttu-id="29af1-109">O método é retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="29af1-109">The method returned successfully.</span></span>|  
|<span data-ttu-id="29af1-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="29af1-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="29af1-111">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="29af1-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="29af1-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="29af1-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="29af1-113">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="29af1-113">The call timed out.</span></span>|  
|<span data-ttu-id="29af1-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="29af1-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="29af1-115">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="29af1-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="29af1-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="29af1-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="29af1-117">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="29af1-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="29af1-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="29af1-118">E_FAIL</span></span>|<span data-ttu-id="29af1-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="29af1-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="29af1-120">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="29af1-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="29af1-121">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="29af1-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="29af1-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="29af1-122">Remarks</span></span>  
 <span data-ttu-id="29af1-123">O CLR chama o `Alert` método quando <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> é chamado de código do usuário, ou quando o <xref:System.AppDomain> associado atual <xref:System.Threading.Thread> é desligado.</span><span class="sxs-lookup"><span data-stu-id="29af1-123">The CLR calls the `Alert` method when <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> is called from user code, or when the <xref:System.AppDomain> associated with the current <xref:System.Threading.Thread> shuts down.</span></span> <span data-ttu-id="29af1-124">O host deve retornar imediatamente, porque a chamada é feita de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="29af1-124">The host must return immediately, because the call is made asynchronously.</span></span> <span data-ttu-id="29af1-125">Se o host não pode alertar a tarefa imediatamente, ele deve ativar na próxima vez que ele entra em um estado em que ele pode ser alertado.</span><span class="sxs-lookup"><span data-stu-id="29af1-125">If the host cannot alert the task immediately, it must wake up the next time it enters a state in which it can be alerted.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="29af1-126">`Alert`afeta somente as tarefas para o qual o tempo de execução foi passado um [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) valor de WAIT_ALERTABLE métodos como [ingressar](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md).</span><span class="sxs-lookup"><span data-stu-id="29af1-126">`Alert` affects only those tasks to which the runtime has passed a [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) value of WAIT_ALERTABLE to methods such as [Join](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29af1-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="29af1-127">Requirements</span></span>  
 <span data-ttu-id="29af1-128">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29af1-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29af1-129">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="29af1-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="29af1-130">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="29af1-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="29af1-131">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29af1-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29af1-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="29af1-132">See Also</span></span>  
 [<span data-ttu-id="29af1-133">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="29af1-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="29af1-134">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="29af1-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="29af1-135">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="29af1-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="29af1-136">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="29af1-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
