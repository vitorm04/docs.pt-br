---
title: "Método ICLRTask::RudeAbort"
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
- ICLRTask.RudeAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::RudeAbort
helpviewer_keywords:
- RudeAbort method, ICLRTask interface [.NET Framework hosting]
- ICLRTask::RudeAbort method [.NET Framework hosting]
ms.assetid: b5785468-fcd7-4cc3-8a5d-8796337b53fc
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f48de1fb44d978b1d9c8960c3e44c360b0801e27
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrtaskrudeabort-method"></a><span data-ttu-id="34633-102">Método ICLRTask::RudeAbort</span><span class="sxs-lookup"><span data-stu-id="34633-102">ICLRTask::RudeAbort Method</span></span>
<span data-ttu-id="34633-103">Instrui o common language runtime (CLR) para anular a tarefa representada por atual [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instância imediatamente e incondicionalmente.</span><span class="sxs-lookup"><span data-stu-id="34633-103">Instructs the common language runtime (CLR) to abort the task represented by the current [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance immediately and unconditionally.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34633-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="34633-104">Syntax</span></span>  
  
```  
HRESULT RudeAbort ();   
```  
  
## <a name="return-value"></a><span data-ttu-id="34633-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="34633-105">Return Value</span></span>  
  
|<span data-ttu-id="34633-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="34633-106">HRESULT</span></span>|<span data-ttu-id="34633-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="34633-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="34633-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="34633-108">S_OK</span></span>|<span data-ttu-id="34633-109">`RudeAbort`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="34633-109">`RudeAbort` returned successfully.</span></span>|  
|<span data-ttu-id="34633-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="34633-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="34633-111">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="34633-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="34633-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="34633-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="34633-113">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="34633-113">The call timed out.</span></span>|  
|<span data-ttu-id="34633-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="34633-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="34633-115">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="34633-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="34633-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="34633-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="34633-117">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="34633-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="34633-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="34633-118">E_FAIL</span></span>|<span data-ttu-id="34633-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="34633-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="34633-120">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="34633-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="34633-121">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="34633-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="34633-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="34633-122">Remarks</span></span>  
 <span data-ttu-id="34633-123">Um host chama `RudeAbort` para anular uma tarefa imediatamente.</span><span class="sxs-lookup"><span data-stu-id="34633-123">A host calls `RudeAbort` to abort a task immediately.</span></span> <span data-ttu-id="34633-124">Não há garantia finalizadores e as rotinas de tratamento de exceção a ser executado.</span><span class="sxs-lookup"><span data-stu-id="34633-124">Finalizers and exception handling routines are not guaranteed to be executed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34633-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="34633-125">Requirements</span></span>  
 <span data-ttu-id="34633-126">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34633-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34633-127">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="34633-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="34633-128">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="34633-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="34633-129">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34633-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34633-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34633-130">See Also</span></span>  
 [<span data-ttu-id="34633-131">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="34633-131">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="34633-132">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="34633-132">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="34633-133">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="34633-133">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="34633-134">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="34633-134">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
