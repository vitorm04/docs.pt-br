---
title: Método ICLRTask::YieldTask
ms.date: 03/30/2017
api_name:
- ICLRTask.YieldTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::YieldTask
helpviewer_keywords:
- ICLRTask::YieldTask method [.NET Framework hosting]
- YieldTask method [.NET Framework hosting]
ms.assetid: b8eb4095-3a8f-4be3-9446-63e9893dce7d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 44716e0c763fe71fe94c8c0ec247cd37379561ec
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54682885"
---
# <a name="iclrtaskyieldtask-method"></a><span data-ttu-id="d26d2-102">Método ICLRTask::YieldTask</span><span class="sxs-lookup"><span data-stu-id="d26d2-102">ICLRTask::YieldTask Method</span></span>
<span data-ttu-id="d26d2-103">Solicitações que o common language runtime (CLR) deixados de lado a tarefa que o atual [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instância representa e tornar o tempo de processador disponíveis para outras tarefas.</span><span class="sxs-lookup"><span data-stu-id="d26d2-103">Requests that the common language runtime (CLR) put aside the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents, and make the processor time available to other tasks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d26d2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d26d2-104">Syntax</span></span>  
  
```  
HRESULT YieldTask ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="d26d2-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="d26d2-105">Return Value</span></span>  
  
|<span data-ttu-id="d26d2-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d26d2-106">HRESULT</span></span>|<span data-ttu-id="d26d2-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="d26d2-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d26d2-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="d26d2-108">S_OK</span></span>|<span data-ttu-id="d26d2-109">`YieldTask` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="d26d2-109">`YieldTask` returned successfully.</span></span>|  
|<span data-ttu-id="d26d2-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d26d2-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d26d2-111">O CLR não tenha sido carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="d26d2-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d26d2-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d26d2-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d26d2-113">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="d26d2-113">The call timed out.</span></span>|  
|<span data-ttu-id="d26d2-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d26d2-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d26d2-115">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="d26d2-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d26d2-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d26d2-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d26d2-117">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="d26d2-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d26d2-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d26d2-118">E_FAIL</span></span>|<span data-ttu-id="d26d2-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="d26d2-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d26d2-120">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="d26d2-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d26d2-121">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d26d2-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d26d2-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="d26d2-122">Remarks</span></span>  
 <span data-ttu-id="d26d2-123">Um host chama `YieldTask` para solicitar recursos do processador para outros processos ou tarefas.</span><span class="sxs-lookup"><span data-stu-id="d26d2-123">A host calls `YieldTask` to request processor resources for other tasks or processes.</span></span> <span data-ttu-id="d26d2-124">Este método destina-se principalmente para permitir que o código de execução longa dar tempo de CPU.</span><span class="sxs-lookup"><span data-stu-id="d26d2-124">This method is primarily intended to allow long-running code to give up CPU time.</span></span> <span data-ttu-id="d26d2-125">O tempo de execução tenta colocar a tarefa que atual `ICLRTask` instância representa em um estado em que ele pode gerar o tempo de processamento, mas não faz nenhuma garantia de êxito.</span><span class="sxs-lookup"><span data-stu-id="d26d2-125">The runtime attempts to put the task that the current `ICLRTask` instance represents in a state where it can yield processing time, but makes no guarantee of success.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d26d2-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d26d2-126">Requirements</span></span>  
 <span data-ttu-id="d26d2-127">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d26d2-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d26d2-128">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d26d2-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d26d2-129">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="d26d2-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d26d2-130">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d26d2-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d26d2-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d26d2-131">See also</span></span>
- [<span data-ttu-id="d26d2-132">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="d26d2-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="d26d2-133">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="d26d2-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="d26d2-134">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="d26d2-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="d26d2-135">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="d26d2-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
