---
title: "Método ICLRTask::ExitTask"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRTask.ExitTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::ExitTask
helpviewer_keywords:
- ExitTask method [.NET Framework hosting]
- ICLRTask::ExitTask method [.NET Framework hosting]
ms.assetid: 746c85a6-4b33-4f72-a2e9-379fdf2e96af
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ff2adafa41ce68a824f6b01888c3565bf054c031
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrtaskexittask-method"></a><span data-ttu-id="db259-102">Método ICLRTask::ExitTask</span><span class="sxs-lookup"><span data-stu-id="db259-102">ICLRTask::ExitTask Method</span></span>
<span data-ttu-id="db259-103">Notifica o common language runtime (CLR) que a tarefa representada pela atual [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instância está terminando e tenta desligar a tarefa normalmente.</span><span class="sxs-lookup"><span data-stu-id="db259-103">Notifies the common language runtime (CLR) that the task represented by the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance is ending, and attempts to shut the task down gracefully.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db259-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="db259-104">Syntax</span></span>  
  
```  
HRESULT ExitTask ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="db259-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="db259-105">Return Value</span></span>  
  
|<span data-ttu-id="db259-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="db259-106">HRESULT</span></span>|<span data-ttu-id="db259-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="db259-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="db259-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="db259-108">S_OK</span></span>|<span data-ttu-id="db259-109">`ExitTask`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="db259-109">`ExitTask` returned successfully.</span></span>|  
|<span data-ttu-id="db259-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="db259-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="db259-111">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="db259-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="db259-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="db259-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="db259-113">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="db259-113">The call timed out.</span></span>|  
|<span data-ttu-id="db259-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="db259-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="db259-115">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="db259-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="db259-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="db259-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="db259-117">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="db259-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="db259-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="db259-118">E_FAIL</span></span>|<span data-ttu-id="db259-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="db259-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="db259-120">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="db259-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="db259-121">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="db259-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="db259-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="db259-122">Remarks</span></span>  
 <span data-ttu-id="db259-123">`ExitTask`as tentativas de um desligamento normal de uma tarefa, de modo semelhante a desanexação de um segmento de uma biblioteca de tipo não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="db259-123">`ExitTask` attempts a clean shutdown of a task, in a manner analogous to detaching a thread from an unmanaged type library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db259-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="db259-124">Requirements</span></span>  
 <span data-ttu-id="db259-125">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db259-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db259-126">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="db259-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="db259-127">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="db259-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="db259-128">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db259-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db259-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="db259-129">See Also</span></span>  
 [<span data-ttu-id="db259-130">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="db259-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="db259-131">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="db259-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="db259-132">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="db259-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="db259-133">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="db259-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
