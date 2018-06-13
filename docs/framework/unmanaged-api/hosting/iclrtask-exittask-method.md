---
title: Método ICLRTask::ExitTask
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3391ed2be03c965807a1c6cad89579cea4015693
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434558"
---
# <a name="iclrtaskexittask-method"></a><span data-ttu-id="fb2a9-102">Método ICLRTask::ExitTask</span><span class="sxs-lookup"><span data-stu-id="fb2a9-102">ICLRTask::ExitTask Method</span></span>
<span data-ttu-id="fb2a9-103">Notifica o common language runtime (CLR) que a tarefa representada pela atual [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instância está terminando e tenta desligar a tarefa normalmente.</span><span class="sxs-lookup"><span data-stu-id="fb2a9-103">Notifies the common language runtime (CLR) that the task represented by the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance is ending, and attempts to shut the task down gracefully.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb2a9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fb2a9-104">Syntax</span></span>  
  
```  
HRESULT ExitTask ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="fb2a9-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="fb2a9-105">Return Value</span></span>  
  
|<span data-ttu-id="fb2a9-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fb2a9-106">HRESULT</span></span>|<span data-ttu-id="fb2a9-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="fb2a9-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fb2a9-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="fb2a9-108">S_OK</span></span>|<span data-ttu-id="fb2a9-109">`ExitTask` retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="fb2a9-109">`ExitTask` returned successfully.</span></span>|  
|<span data-ttu-id="fb2a9-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fb2a9-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fb2a9-111">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="fb2a9-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fb2a9-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fb2a9-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fb2a9-113">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="fb2a9-113">The call timed out.</span></span>|  
|<span data-ttu-id="fb2a9-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fb2a9-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fb2a9-115">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="fb2a9-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fb2a9-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fb2a9-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fb2a9-117">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="fb2a9-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fb2a9-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fb2a9-118">E_FAIL</span></span>|<span data-ttu-id="fb2a9-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="fb2a9-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fb2a9-120">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="fb2a9-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fb2a9-121">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="fb2a9-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fb2a9-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="fb2a9-122">Remarks</span></span>  
 <span data-ttu-id="fb2a9-123">`ExitTask` as tentativas de um desligamento normal de uma tarefa, de modo semelhante a desanexação de um segmento de uma biblioteca de tipo não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="fb2a9-123">`ExitTask` attempts a clean shutdown of a task, in a manner analogous to detaching a thread from an unmanaged type library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb2a9-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fb2a9-124">Requirements</span></span>  
 <span data-ttu-id="fb2a9-125">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb2a9-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb2a9-126">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fb2a9-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fb2a9-127">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="fb2a9-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fb2a9-128">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb2a9-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb2a9-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fb2a9-129">See Also</span></span>  
 [<span data-ttu-id="fb2a9-130">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="fb2a9-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="fb2a9-131">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="fb2a9-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="fb2a9-132">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="fb2a9-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="fb2a9-133">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="fb2a9-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
