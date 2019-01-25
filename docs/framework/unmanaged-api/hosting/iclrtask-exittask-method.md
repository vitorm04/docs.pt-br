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
ms.openlocfilehash: b9913618f597d8e456d8db4d13883ee049c21fb4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54726371"
---
# <a name="iclrtaskexittask-method"></a><span data-ttu-id="5710b-102">Método ICLRTask::ExitTask</span><span class="sxs-lookup"><span data-stu-id="5710b-102">ICLRTask::ExitTask Method</span></span>
<span data-ttu-id="5710b-103">Notifica o common language runtime (CLR) que a tarefa representada por atual [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instância está terminando e tenta desligar a tarefa normalmente.</span><span class="sxs-lookup"><span data-stu-id="5710b-103">Notifies the common language runtime (CLR) that the task represented by the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance is ending, and attempts to shut the task down gracefully.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5710b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5710b-104">Syntax</span></span>  
  
```  
HRESULT ExitTask ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="5710b-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="5710b-105">Return Value</span></span>  
  
|<span data-ttu-id="5710b-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5710b-106">HRESULT</span></span>|<span data-ttu-id="5710b-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="5710b-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5710b-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="5710b-108">S_OK</span></span>|<span data-ttu-id="5710b-109">`ExitTask` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="5710b-109">`ExitTask` returned successfully.</span></span>|  
|<span data-ttu-id="5710b-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5710b-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5710b-111">O CLR não tenha sido carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="5710b-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5710b-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5710b-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5710b-113">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="5710b-113">The call timed out.</span></span>|  
|<span data-ttu-id="5710b-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5710b-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5710b-115">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="5710b-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5710b-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5710b-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5710b-117">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="5710b-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5710b-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5710b-118">E_FAIL</span></span>|<span data-ttu-id="5710b-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="5710b-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5710b-120">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="5710b-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5710b-121">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="5710b-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5710b-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="5710b-122">Remarks</span></span>  
 <span data-ttu-id="5710b-123">`ExitTask` tentativas de um desligamento normal de uma tarefa, de maneira análoga a desanexação de um thread de uma biblioteca de tipos não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="5710b-123">`ExitTask` attempts a clean shutdown of a task, in a manner analogous to detaching a thread from an unmanaged type library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5710b-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5710b-124">Requirements</span></span>  
 <span data-ttu-id="5710b-125">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5710b-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5710b-126">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5710b-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5710b-127">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="5710b-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5710b-128">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5710b-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5710b-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5710b-129">See also</span></span>
- [<span data-ttu-id="5710b-130">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="5710b-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="5710b-131">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="5710b-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="5710b-132">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="5710b-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="5710b-133">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="5710b-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
