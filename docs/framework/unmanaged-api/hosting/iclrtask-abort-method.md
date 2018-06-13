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
ms.openlocfilehash: 46d60ff6ab64d57ca5c7020877758657b61125ad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434831"
---
# <a name="iclrtaskabort-method"></a><span data-ttu-id="0ea23-102">Método ICLRTask::Abort</span><span class="sxs-lookup"><span data-stu-id="0ea23-102">ICLRTask::Abort Method</span></span>
<span data-ttu-id="0ea23-103">O common language runtime (CLR) anular a tarefa de solicitações que atual [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instância representa.</span><span class="sxs-lookup"><span data-stu-id="0ea23-103">Requests that the common language runtime (CLR) abort the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ea23-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0ea23-104">Syntax</span></span>  
  
```  
HRESULT Abort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="0ea23-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="0ea23-105">Return Value</span></span>  
  
|<span data-ttu-id="0ea23-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0ea23-106">HRESULT</span></span>|<span data-ttu-id="0ea23-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ea23-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0ea23-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="0ea23-108">S_OK</span></span>|<span data-ttu-id="0ea23-109">`Abort` retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="0ea23-109">`Abort` returned successfully.</span></span>|  
|<span data-ttu-id="0ea23-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0ea23-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0ea23-111">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="0ea23-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0ea23-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0ea23-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0ea23-113">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="0ea23-113">The call timed out.</span></span>|  
|<span data-ttu-id="0ea23-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0ea23-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0ea23-115">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="0ea23-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0ea23-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0ea23-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0ea23-117">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="0ea23-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0ea23-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0ea23-118">E_FAIL</span></span>|<span data-ttu-id="0ea23-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="0ea23-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0ea23-120">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="0ea23-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0ea23-121">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0ea23-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0ea23-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="0ea23-122">Remarks</span></span>  
 <span data-ttu-id="0ea23-123">O CLR gera um <xref:System.Threading.ThreadAbortException> quando o host chama `Abort`.</span><span class="sxs-lookup"><span data-stu-id="0ea23-123">The CLR raises a <xref:System.Threading.ThreadAbortException> when the host calls `Abort`.</span></span> <span data-ttu-id="0ea23-124">Ele retorna imediatamente depois que as informações de exceção são inicializadas, sem esperar por código de usuário, como finalizadores ou mecanismos, de manipulação de exceção para executar.</span><span class="sxs-lookup"><span data-stu-id="0ea23-124">It returns immediately after the exception information is initialized, without waiting for user code, such as finalizers or exception handling mechanisms, to execute.</span></span> <span data-ttu-id="0ea23-125">Chamadas para `Abort` , portanto, retornar rapidamente.</span><span class="sxs-lookup"><span data-stu-id="0ea23-125">Calls to `Abort` thus return quickly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ea23-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0ea23-126">Requirements</span></span>  
 <span data-ttu-id="0ea23-127">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ea23-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ea23-128">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0ea23-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0ea23-129">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="0ea23-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0ea23-130">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ea23-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ea23-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ea23-131">See Also</span></span>  
 [<span data-ttu-id="0ea23-132">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="0ea23-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="0ea23-133">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="0ea23-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="0ea23-134">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="0ea23-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="0ea23-135">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="0ea23-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
