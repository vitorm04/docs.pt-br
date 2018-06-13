---
title: Método ICLRTask::RudeAbort
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a99bda7a6d21fea159c8f616f2db7d12b1f27579
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435408"
---
# <a name="iclrtaskrudeabort-method"></a><span data-ttu-id="12b64-102">Método ICLRTask::RudeAbort</span><span class="sxs-lookup"><span data-stu-id="12b64-102">ICLRTask::RudeAbort Method</span></span>
<span data-ttu-id="12b64-103">Instrui o common language runtime (CLR) para anular a tarefa representada por atual [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instância imediatamente e incondicionalmente.</span><span class="sxs-lookup"><span data-stu-id="12b64-103">Instructs the common language runtime (CLR) to abort the task represented by the current [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance immediately and unconditionally.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12b64-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="12b64-104">Syntax</span></span>  
  
```  
HRESULT RudeAbort ();   
```  
  
## <a name="return-value"></a><span data-ttu-id="12b64-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="12b64-105">Return Value</span></span>  
  
|<span data-ttu-id="12b64-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="12b64-106">HRESULT</span></span>|<span data-ttu-id="12b64-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="12b64-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="12b64-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="12b64-108">S_OK</span></span>|<span data-ttu-id="12b64-109">`RudeAbort` retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="12b64-109">`RudeAbort` returned successfully.</span></span>|  
|<span data-ttu-id="12b64-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="12b64-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="12b64-111">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="12b64-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="12b64-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="12b64-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="12b64-113">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="12b64-113">The call timed out.</span></span>|  
|<span data-ttu-id="12b64-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="12b64-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="12b64-115">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="12b64-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="12b64-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="12b64-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="12b64-117">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="12b64-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="12b64-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="12b64-118">E_FAIL</span></span>|<span data-ttu-id="12b64-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="12b64-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="12b64-120">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="12b64-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="12b64-121">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="12b64-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="12b64-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="12b64-122">Remarks</span></span>  
 <span data-ttu-id="12b64-123">Um host chama `RudeAbort` para anular uma tarefa imediatamente.</span><span class="sxs-lookup"><span data-stu-id="12b64-123">A host calls `RudeAbort` to abort a task immediately.</span></span> <span data-ttu-id="12b64-124">Não há garantia finalizadores e as rotinas de tratamento de exceção a ser executado.</span><span class="sxs-lookup"><span data-stu-id="12b64-124">Finalizers and exception handling routines are not guaranteed to be executed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12b64-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="12b64-125">Requirements</span></span>  
 <span data-ttu-id="12b64-126">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12b64-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12b64-127">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="12b64-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="12b64-128">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="12b64-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="12b64-129">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12b64-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12b64-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="12b64-130">See Also</span></span>  
 [<span data-ttu-id="12b64-131">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="12b64-131">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="12b64-132">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="12b64-132">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="12b64-133">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="12b64-133">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="12b64-134">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="12b64-134">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
