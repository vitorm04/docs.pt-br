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
ms.openlocfilehash: aacf9de36dc39b63ed36b672e31f40704413d608
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176325"
---
# <a name="iclrtaskrudeabort-method"></a><span data-ttu-id="7ef74-102">Método ICLRTask::RudeAbort</span><span class="sxs-lookup"><span data-stu-id="7ef74-102">ICLRTask::RudeAbort Method</span></span>
<span data-ttu-id="7ef74-103">Instrui o tempo de execução do idioma comum (CLR) a abortar a tarefa representada pela atual ocorrência de [Interface ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) imediatamente e incondicionalmente.</span><span class="sxs-lookup"><span data-stu-id="7ef74-103">Instructs the common language runtime (CLR) to abort the task represented by the current [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance immediately and unconditionally.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ef74-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7ef74-104">Syntax</span></span>  
  
```cpp  
HRESULT RudeAbort ();
```  
  
## <a name="return-value"></a><span data-ttu-id="7ef74-105">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="7ef74-105">Return Value</span></span>  
  
|<span data-ttu-id="7ef74-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7ef74-106">HRESULT</span></span>|<span data-ttu-id="7ef74-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="7ef74-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7ef74-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="7ef74-108">S_OK</span></span>|<span data-ttu-id="7ef74-109">`RudeAbort`retornou com sucesso.</span><span class="sxs-lookup"><span data-stu-id="7ef74-109">`RudeAbort` returned successfully.</span></span>|  
|<span data-ttu-id="7ef74-110">Host_e_clrnotavailable</span><span class="sxs-lookup"><span data-stu-id="7ef74-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7ef74-111">A CLR não foi carregada em um processo, ou a CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com sucesso.</span><span class="sxs-lookup"><span data-stu-id="7ef74-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7ef74-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7ef74-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7ef74-113">A chamada acabou.</span><span class="sxs-lookup"><span data-stu-id="7ef74-113">The call timed out.</span></span>|  
|<span data-ttu-id="7ef74-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7ef74-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7ef74-115">O interlocutor não é dono da fechadura.</span><span class="sxs-lookup"><span data-stu-id="7ef74-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7ef74-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7ef74-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7ef74-117">Um evento foi cancelado enquanto um fio ou fibra bloqueado estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="7ef74-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7ef74-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7ef74-118">E_FAIL</span></span>|<span data-ttu-id="7ef74-119">Uma falha catastrófica desconhecida ocorreu.</span><span class="sxs-lookup"><span data-stu-id="7ef74-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7ef74-120">Quando um método retorna E_FAIL, a CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="7ef74-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7ef74-121">Chamadas subseqüentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7ef74-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7ef74-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="7ef74-122">Remarks</span></span>  
 <span data-ttu-id="7ef74-123">Um host `RudeAbort` chama para abortar uma tarefa imediatamente.</span><span class="sxs-lookup"><span data-stu-id="7ef74-123">A host calls `RudeAbort` to abort a task immediately.</span></span> <span data-ttu-id="7ef74-124">Finalizadores e rotinas de manipulação de exceções não são garantidos para serem executados.</span><span class="sxs-lookup"><span data-stu-id="7ef74-124">Finalizers and exception handling routines are not guaranteed to be executed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ef74-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7ef74-125">Requirements</span></span>  
 <span data-ttu-id="7ef74-126">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ef74-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ef74-127">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7ef74-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7ef74-128">**Biblioteca:** Incluído como um recurso em MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7ef74-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7ef74-129">**.NET Framework Versions:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ef74-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ef74-130">Confira também</span><span class="sxs-lookup"><span data-stu-id="7ef74-130">See also</span></span>

- [<span data-ttu-id="7ef74-131">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="7ef74-131">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="7ef74-132">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="7ef74-132">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="7ef74-133">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="7ef74-133">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="7ef74-134">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="7ef74-134">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
