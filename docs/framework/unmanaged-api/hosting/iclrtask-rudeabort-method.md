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
ms.openlocfilehash: 5d6e19fe307373c2920fd60b04bff482b238c5c4
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762949"
---
# <a name="iclrtaskrudeabort-method"></a><span data-ttu-id="2842c-102">Método ICLRTask::RudeAbort</span><span class="sxs-lookup"><span data-stu-id="2842c-102">ICLRTask::RudeAbort Method</span></span>
<span data-ttu-id="2842c-103">Instrui o Common Language Runtime (CLR) a anular a tarefa representada pela instância de [interface ICLRTask](iclrtask-interface.md) atual imediatamente e incondicionalmente.</span><span class="sxs-lookup"><span data-stu-id="2842c-103">Instructs the common language runtime (CLR) to abort the task represented by the current [ICLRTask Interface](iclrtask-interface.md) instance immediately and unconditionally.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2842c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2842c-104">Syntax</span></span>  
  
```cpp  
HRESULT RudeAbort ();
```  
  
## <a name="return-value"></a><span data-ttu-id="2842c-105">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="2842c-105">Return Value</span></span>  
  
|<span data-ttu-id="2842c-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2842c-106">HRESULT</span></span>|<span data-ttu-id="2842c-107">Description</span><span class="sxs-lookup"><span data-stu-id="2842c-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2842c-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="2842c-108">S_OK</span></span>|<span data-ttu-id="2842c-109">`RudeAbort`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="2842c-109">`RudeAbort` returned successfully.</span></span>|  
|<span data-ttu-id="2842c-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2842c-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2842c-111">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="2842c-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2842c-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2842c-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2842c-113">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="2842c-113">The call timed out.</span></span>|  
|<span data-ttu-id="2842c-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2842c-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2842c-115">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="2842c-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2842c-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2842c-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2842c-117">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="2842c-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2842c-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2842c-118">E_FAIL</span></span>|<span data-ttu-id="2842c-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="2842c-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2842c-120">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="2842c-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2842c-121">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="2842c-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2842c-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="2842c-122">Remarks</span></span>  
 <span data-ttu-id="2842c-123">Um host chama `RudeAbort` para anular uma tarefa imediatamente.</span><span class="sxs-lookup"><span data-stu-id="2842c-123">A host calls `RudeAbort` to abort a task immediately.</span></span> <span data-ttu-id="2842c-124">Os finalizadores e as rotinas de manipulação de exceção não têm garantia de serem executadas.</span><span class="sxs-lookup"><span data-stu-id="2842c-124">Finalizers and exception handling routines are not guaranteed to be executed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2842c-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2842c-125">Requirements</span></span>  
 <span data-ttu-id="2842c-126">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2842c-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2842c-127">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2842c-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2842c-128">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2842c-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2842c-129">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2842c-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2842c-130">Veja também</span><span class="sxs-lookup"><span data-stu-id="2842c-130">See also</span></span>

- [<span data-ttu-id="2842c-131">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="2842c-131">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="2842c-132">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="2842c-132">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="2842c-133">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="2842c-133">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="2842c-134">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="2842c-134">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
