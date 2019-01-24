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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9164e64c56a8a4ae908a3d06f878b399550703f9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54715394"
---
# <a name="iclrtaskabort-method"></a><span data-ttu-id="3e08e-102">Método ICLRTask::Abort</span><span class="sxs-lookup"><span data-stu-id="3e08e-102">ICLRTask::Abort Method</span></span>
<span data-ttu-id="3e08e-103">Solicitações que o common language runtime (CLR) anular a tarefa que o atual [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instância representa.</span><span class="sxs-lookup"><span data-stu-id="3e08e-103">Requests that the common language runtime (CLR) abort the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e08e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3e08e-104">Syntax</span></span>  
  
```  
HRESULT Abort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="3e08e-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="3e08e-105">Return Value</span></span>  
  
|<span data-ttu-id="3e08e-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3e08e-106">HRESULT</span></span>|<span data-ttu-id="3e08e-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="3e08e-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3e08e-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="3e08e-108">S_OK</span></span>|<span data-ttu-id="3e08e-109">`Abort` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="3e08e-109">`Abort` returned successfully.</span></span>|  
|<span data-ttu-id="3e08e-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3e08e-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3e08e-111">O CLR não tenha sido carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="3e08e-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3e08e-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3e08e-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3e08e-113">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="3e08e-113">The call timed out.</span></span>|  
|<span data-ttu-id="3e08e-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3e08e-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3e08e-115">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="3e08e-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3e08e-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3e08e-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3e08e-117">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="3e08e-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3e08e-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3e08e-118">E_FAIL</span></span>|<span data-ttu-id="3e08e-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="3e08e-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3e08e-120">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="3e08e-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3e08e-121">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="3e08e-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3e08e-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="3e08e-122">Remarks</span></span>  
 <span data-ttu-id="3e08e-123">O CLR aciona uma <xref:System.Threading.ThreadAbortException> quando o host chama `Abort`.</span><span class="sxs-lookup"><span data-stu-id="3e08e-123">The CLR raises a <xref:System.Threading.ThreadAbortException> when the host calls `Abort`.</span></span> <span data-ttu-id="3e08e-124">Ele retorna imediatamente depois que as informações de exceção são inicializadas, sem aguardar o código do usuário, como os finalizadores ou mecanismos de manipulação de exceção a ser executado.</span><span class="sxs-lookup"><span data-stu-id="3e08e-124">It returns immediately after the exception information is initialized, without waiting for user code, such as finalizers or exception handling mechanisms, to execute.</span></span> <span data-ttu-id="3e08e-125">Chamadas para `Abort` , assim, retornar rapidamente.</span><span class="sxs-lookup"><span data-stu-id="3e08e-125">Calls to `Abort` thus return quickly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e08e-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3e08e-126">Requirements</span></span>  
 <span data-ttu-id="3e08e-127">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e08e-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e08e-128">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3e08e-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3e08e-129">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="3e08e-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3e08e-130">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e08e-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e08e-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3e08e-131">See also</span></span>
- [<span data-ttu-id="3e08e-132">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="3e08e-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="3e08e-133">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="3e08e-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="3e08e-134">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="3e08e-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="3e08e-135">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="3e08e-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
