---
title: Método ICLRTask::Abort
ms.date: 03/30/2017
api_name:
- ICLRTask.Abort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::Abort
helpviewer_keywords:
- ICLRTask::Abort method [.NET Framework hosting]
- Abort method, ICLRTask interface [.NET Framework hosting]
ms.assetid: b3594b5f-2e41-4e36-9096-3586276a138c
topic_type:
- apiref
ms.openlocfilehash: 026d4c14abed030b80e8e1b3f8363fbd59ac05e4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124912"
---
# <a name="iclrtaskabort-method"></a><span data-ttu-id="34294-102">Método ICLRTask::Abort</span><span class="sxs-lookup"><span data-stu-id="34294-102">ICLRTask::Abort Method</span></span>
<span data-ttu-id="34294-103">Solicita que o Common Language Runtime (CLR) anule a tarefa que a instância [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) atual representa.</span><span class="sxs-lookup"><span data-stu-id="34294-103">Requests that the common language runtime (CLR) abort the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34294-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="34294-104">Syntax</span></span>  
  
```cpp  
HRESULT Abort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="34294-105">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="34294-105">Return Value</span></span>  
  
|<span data-ttu-id="34294-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="34294-106">HRESULT</span></span>|<span data-ttu-id="34294-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="34294-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="34294-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="34294-108">S_OK</span></span>|<span data-ttu-id="34294-109">`Abort` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="34294-109">`Abort` returned successfully.</span></span>|  
|<span data-ttu-id="34294-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="34294-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="34294-111">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="34294-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="34294-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="34294-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="34294-113">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="34294-113">The call timed out.</span></span>|  
|<span data-ttu-id="34294-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="34294-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="34294-115">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="34294-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="34294-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="34294-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="34294-117">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="34294-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="34294-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="34294-118">E_FAIL</span></span>|<span data-ttu-id="34294-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="34294-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="34294-120">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="34294-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="34294-121">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="34294-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="34294-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="34294-122">Remarks</span></span>  
 <span data-ttu-id="34294-123">O CLR gera um <xref:System.Threading.ThreadAbortException> quando o host chama `Abort`.</span><span class="sxs-lookup"><span data-stu-id="34294-123">The CLR raises a <xref:System.Threading.ThreadAbortException> when the host calls `Abort`.</span></span> <span data-ttu-id="34294-124">Ele retorna imediatamente depois que as informações de exceção são inicializadas, sem esperar que o código do usuário, como finalizadores ou mecanismos de tratamento de exceção, seja executado.</span><span class="sxs-lookup"><span data-stu-id="34294-124">It returns immediately after the exception information is initialized, without waiting for user code, such as finalizers or exception handling mechanisms, to execute.</span></span> <span data-ttu-id="34294-125">Chamadas para `Abort`, portanto, retornam rapidamente.</span><span class="sxs-lookup"><span data-stu-id="34294-125">Calls to `Abort` thus return quickly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34294-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="34294-126">Requirements</span></span>  
 <span data-ttu-id="34294-127">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34294-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34294-128">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="34294-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="34294-129">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="34294-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="34294-130">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34294-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34294-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34294-131">See also</span></span>

- [<span data-ttu-id="34294-132">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="34294-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="34294-133">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="34294-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="34294-134">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="34294-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="34294-135">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="34294-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
