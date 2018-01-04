---
title: "Método ICLRTask::YieldTask"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTask.YieldTask
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTask::YieldTask
helpviewer_keywords:
- ICLRTask::YieldTask method [.NET Framework hosting]
- YieldTask method [.NET Framework hosting]
ms.assetid: b8eb4095-3a8f-4be3-9446-63e9893dce7d
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: da84f4da9e7f7bcee48c0d6bc432ca75a001ece3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrtaskyieldtask-method"></a><span data-ttu-id="ebf58-102">Método ICLRTask::YieldTask</span><span class="sxs-lookup"><span data-stu-id="ebf58-102">ICLRTask::YieldTask Method</span></span>
<span data-ttu-id="ebf58-103">Solicitações que o common language runtime (CLR) deixados de lado a tarefa que atual [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instância representa e disponibilizar para outras tarefas de tempo do processador.</span><span class="sxs-lookup"><span data-stu-id="ebf58-103">Requests that the common language runtime (CLR) put aside the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents, and make the processor time available to other tasks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebf58-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ebf58-104">Syntax</span></span>  
  
```  
HRESULT YieldTask ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="ebf58-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="ebf58-105">Return Value</span></span>  
  
|<span data-ttu-id="ebf58-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ebf58-106">HRESULT</span></span>|<span data-ttu-id="ebf58-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="ebf58-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ebf58-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="ebf58-108">S_OK</span></span>|<span data-ttu-id="ebf58-109">`YieldTask`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="ebf58-109">`YieldTask` returned successfully.</span></span>|  
|<span data-ttu-id="ebf58-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ebf58-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ebf58-111">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="ebf58-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ebf58-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ebf58-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ebf58-113">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="ebf58-113">The call timed out.</span></span>|  
|<span data-ttu-id="ebf58-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ebf58-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ebf58-115">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="ebf58-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ebf58-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ebf58-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ebf58-117">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="ebf58-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ebf58-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ebf58-118">E_FAIL</span></span>|<span data-ttu-id="ebf58-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="ebf58-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ebf58-120">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="ebf58-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ebf58-121">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ebf58-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ebf58-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="ebf58-122">Remarks</span></span>  
 <span data-ttu-id="ebf58-123">Um host chama `YieldTask` para solicitar recursos do processador para outros processos ou tarefas.</span><span class="sxs-lookup"><span data-stu-id="ebf58-123">A host calls `YieldTask` to request processor resources for other tasks or processes.</span></span> <span data-ttu-id="ebf58-124">Esse método é usado principalmente para permitir que o código de execução longa fornecer o tempo de CPU.</span><span class="sxs-lookup"><span data-stu-id="ebf58-124">This method is primarily intended to allow long-running code to give up CPU time.</span></span> <span data-ttu-id="ebf58-125">O tempo de execução tenta colocar a tarefa que atual `ICLRTask` instância representa em um estado em que ele pode gerar o tempo de processamento, mas não dá nenhuma garantia de êxito.</span><span class="sxs-lookup"><span data-stu-id="ebf58-125">The runtime attempts to put the task that the current `ICLRTask` instance represents in a state where it can yield processing time, but makes no guarantee of success.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ebf58-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ebf58-126">Requirements</span></span>  
 <span data-ttu-id="ebf58-127">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ebf58-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ebf58-128">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ebf58-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ebf58-129">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="ebf58-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ebf58-130">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ebf58-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebf58-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ebf58-131">See Also</span></span>  
 [<span data-ttu-id="ebf58-132">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="ebf58-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="ebf58-133">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="ebf58-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="ebf58-134">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="ebf58-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="ebf58-135">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="ebf58-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
