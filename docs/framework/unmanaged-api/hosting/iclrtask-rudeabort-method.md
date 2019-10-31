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
ms.openlocfilehash: 69e3ecfc82985d52bd5b14e9faf2566e395b622b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124649"
---
# <a name="iclrtaskrudeabort-method"></a><span data-ttu-id="a615e-102">Método ICLRTask::RudeAbort</span><span class="sxs-lookup"><span data-stu-id="a615e-102">ICLRTask::RudeAbort Method</span></span>
<span data-ttu-id="a615e-103">Instrui o Common Language Runtime (CLR) a anular a tarefa representada pela instância de [interface ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) atual imediatamente e incondicionalmente.</span><span class="sxs-lookup"><span data-stu-id="a615e-103">Instructs the common language runtime (CLR) to abort the task represented by the current [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance immediately and unconditionally.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a615e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a615e-104">Syntax</span></span>  
  
```cpp  
HRESULT RudeAbort ();   
```  
  
## <a name="return-value"></a><span data-ttu-id="a615e-105">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="a615e-105">Return Value</span></span>  
  
|<span data-ttu-id="a615e-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a615e-106">HRESULT</span></span>|<span data-ttu-id="a615e-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="a615e-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a615e-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="a615e-108">S_OK</span></span>|<span data-ttu-id="a615e-109">`RudeAbort` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="a615e-109">`RudeAbort` returned successfully.</span></span>|  
|<span data-ttu-id="a615e-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a615e-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a615e-111">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="a615e-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a615e-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a615e-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a615e-113">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="a615e-113">The call timed out.</span></span>|  
|<span data-ttu-id="a615e-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a615e-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a615e-115">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="a615e-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a615e-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a615e-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a615e-117">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="a615e-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a615e-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a615e-118">E_FAIL</span></span>|<span data-ttu-id="a615e-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="a615e-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a615e-120">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="a615e-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a615e-121">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a615e-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a615e-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="a615e-122">Remarks</span></span>  
 <span data-ttu-id="a615e-123">Um host chama `RudeAbort` para anular uma tarefa imediatamente.</span><span class="sxs-lookup"><span data-stu-id="a615e-123">A host calls `RudeAbort` to abort a task immediately.</span></span> <span data-ttu-id="a615e-124">Os finalizadores e as rotinas de manipulação de exceção não têm garantia de serem executadas.</span><span class="sxs-lookup"><span data-stu-id="a615e-124">Finalizers and exception handling routines are not guaranteed to be executed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a615e-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a615e-125">Requirements</span></span>  
 <span data-ttu-id="a615e-126">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a615e-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a615e-127">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a615e-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a615e-128">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a615e-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a615e-129">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a615e-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a615e-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a615e-130">See also</span></span>

- [<span data-ttu-id="a615e-131">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="a615e-131">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="a615e-132">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="a615e-132">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="a615e-133">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="a615e-133">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="a615e-134">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="a615e-134">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
