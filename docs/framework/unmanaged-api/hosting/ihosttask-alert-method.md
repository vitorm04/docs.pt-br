---
title: Método IHostTask::Alert
ms.date: 03/30/2017
api_name:
- IHostTask.Alert
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::Alert
helpviewer_keywords:
- IHostTask::Alert method [.NET Framework hosting]
- Alert method, IHostTask interface [.NET Framework hosting]
ms.assetid: 5245d4b5-b6c3-48df-9cb9-8caf059f43fb
topic_type:
- apiref
ms.openlocfilehash: c95b787101d4d0302ce4d2a5cd3bdc7e11f9cd63
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501424"
---
# <a name="ihosttaskalert-method"></a><span data-ttu-id="55baf-102">Método IHostTask::Alert</span><span class="sxs-lookup"><span data-stu-id="55baf-102">IHostTask::Alert Method</span></span>
<span data-ttu-id="55baf-103">Solicita que o host ative a tarefa representada pela instância [IHostTask](ihosttask-interface.md) atual, para que a tarefa possa ser anulada.</span><span class="sxs-lookup"><span data-stu-id="55baf-103">Requests that the host wake the task represented by the current [IHostTask](ihosttask-interface.md) instance, so the task can be aborted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55baf-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="55baf-104">Syntax</span></span>  
  
```cpp  
HRESULT Alert ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="55baf-105">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="55baf-105">Return Value</span></span>  
  
|<span data-ttu-id="55baf-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="55baf-106">HRESULT</span></span>|<span data-ttu-id="55baf-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="55baf-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="55baf-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="55baf-108">S_OK</span></span>|<span data-ttu-id="55baf-109">O método foi retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="55baf-109">The method returned successfully.</span></span>|  
|<span data-ttu-id="55baf-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="55baf-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="55baf-111">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="55baf-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="55baf-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="55baf-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="55baf-113">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="55baf-113">The call timed out.</span></span>|  
|<span data-ttu-id="55baf-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="55baf-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="55baf-115">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="55baf-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="55baf-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="55baf-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="55baf-117">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="55baf-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="55baf-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="55baf-118">E_FAIL</span></span>|<span data-ttu-id="55baf-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="55baf-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="55baf-120">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="55baf-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="55baf-121">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="55baf-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="55baf-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="55baf-122">Remarks</span></span>  
 <span data-ttu-id="55baf-123">O CLR chama o `Alert` método quando <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> é chamado a partir do código do usuário ou quando o <xref:System.AppDomain> associado ao atual é <xref:System.Threading.Thread> desligado.</span><span class="sxs-lookup"><span data-stu-id="55baf-123">The CLR calls the `Alert` method when <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> is called from user code, or when the <xref:System.AppDomain> associated with the current <xref:System.Threading.Thread> shuts down.</span></span> <span data-ttu-id="55baf-124">O host deve retornar imediatamente, pois a chamada é feita de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="55baf-124">The host must return immediately, because the call is made asynchronously.</span></span> <span data-ttu-id="55baf-125">Se o host não puder alertar a tarefa imediatamente, ele deverá ser ativado na próxima vez que entrar em um estado no qual possa ser alertado.</span><span class="sxs-lookup"><span data-stu-id="55baf-125">If the host cannot alert the task immediately, it must wake up the next time it enters a state in which it can be alerted.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="55baf-126">`Alert`afeta apenas as tarefas para as quais o tempo de execução passou um valor [WAIT_OPTION](wait-option-enumeration.md) de WAIT_ALERTABLE para métodos como [Join](ihosttask-join-method.md).</span><span class="sxs-lookup"><span data-stu-id="55baf-126">`Alert` affects only those tasks to which the runtime has passed a [WAIT_OPTION](wait-option-enumeration.md) value of WAIT_ALERTABLE to methods such as [Join](ihosttask-join-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55baf-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="55baf-127">Requirements</span></span>  
 <span data-ttu-id="55baf-128">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="55baf-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55baf-129">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="55baf-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="55baf-130">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="55baf-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="55baf-131">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55baf-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55baf-132">Confira também</span><span class="sxs-lookup"><span data-stu-id="55baf-132">See also</span></span>

- [<span data-ttu-id="55baf-133">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="55baf-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="55baf-134">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="55baf-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="55baf-135">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="55baf-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="55baf-136">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="55baf-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
