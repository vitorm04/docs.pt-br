---
title: Método IHostTaskManager::ReverseLeaveRuntime
ms.date: 03/30/2017
api_name:
- IHostTaskManager.ReverseLeaveRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::ReverseLeaveRuntime
helpviewer_keywords:
- IHostTaskManager::ReverseLeaveRuntime method [.NET Framework hosting]
- ReverseLeaveRuntime method [.NET Framework hosting]
ms.assetid: 4837d398-16a1-4e32-902c-022cd1aad3ca
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3e462d951475cc9333dd190d96668e2c2a129872
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45512901"
---
# <a name="ihosttaskmanagerreverseleaveruntime-method"></a><span data-ttu-id="41a76-102">Método IHostTaskManager::ReverseLeaveRuntime</span><span class="sxs-lookup"><span data-stu-id="41a76-102">IHostTaskManager::ReverseLeaveRuntime Method</span></span>
<span data-ttu-id="41a76-103">Notifica o host que o controle está deixando o common language runtime (CLR) e inserir uma função não gerenciada, por sua vez, chamado do código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="41a76-103">Notifies the host that control is leaving the common language runtime (CLR) and entering an unmanaged function that was, in turn, called from managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41a76-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="41a76-104">Syntax</span></span>  
  
```  
HRESULT ReverseLeaveRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="41a76-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="41a76-105">Return Value</span></span>  
  
|<span data-ttu-id="41a76-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="41a76-106">HRESULT</span></span>|<span data-ttu-id="41a76-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="41a76-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="41a76-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="41a76-108">S_OK</span></span>|<span data-ttu-id="41a76-109">`ReverseLeaveRuntime` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="41a76-109">`ReverseLeaveRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="41a76-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="41a76-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="41a76-111">O CLR não tenha sido carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="41a76-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="41a76-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="41a76-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="41a76-113">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="41a76-113">The call timed out.</span></span>|  
|<span data-ttu-id="41a76-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="41a76-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="41a76-115">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="41a76-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="41a76-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="41a76-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="41a76-117">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="41a76-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="41a76-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="41a76-118">E_FAIL</span></span>|<span data-ttu-id="41a76-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="41a76-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="41a76-120">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="41a76-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="41a76-121">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="41a76-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="41a76-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="41a76-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="41a76-123">Não há memória suficiente está disponível para concluir a alocação de recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="41a76-123">Not enough memory is available to complete the requested resource allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="41a76-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="41a76-124">Remarks</span></span>  
 <span data-ttu-id="41a76-125">O CLR chama `ReverseLeaveRuntime` para informar o host em que a tarefa em execução no momento está retornando o controle para uma função não gerenciada, por sua vez, chamado do código gerenciado pela plataforma invocar.</span><span class="sxs-lookup"><span data-stu-id="41a76-125">The CLR calls `ReverseLeaveRuntime` to inform the host that the currently executing task is returning control to an unmanaged function that was, in turn, called from managed code through platform invoke.</span></span> <span data-ttu-id="41a76-126">Cada chamada para `ReverseLeaveRuntime` corresponde a uma chamada correspondente para [ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md).</span><span class="sxs-lookup"><span data-stu-id="41a76-126">Each call to `ReverseLeaveRuntime` matches a corresponding call to [ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41a76-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="41a76-127">Requirements</span></span>  
 <span data-ttu-id="41a76-128">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41a76-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41a76-129">**Cabeçalho:** mscoree. H</span><span class="sxs-lookup"><span data-stu-id="41a76-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="41a76-130">**Biblioteca:** incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="41a76-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="41a76-131">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41a76-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41a76-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="41a76-132">See Also</span></span>  
 [<span data-ttu-id="41a76-133">Método CallNeedsHostHook</span><span class="sxs-lookup"><span data-stu-id="41a76-133">CallNeedsHostHook Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-callneedshosthook-method.md)  
 [<span data-ttu-id="41a76-134">Método EnterRuntime</span><span class="sxs-lookup"><span data-stu-id="41a76-134">EnterRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md)  
 [<span data-ttu-id="41a76-135">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="41a76-135">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="41a76-136">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="41a76-136">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="41a76-137">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="41a76-137">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="41a76-138">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="41a76-138">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="41a76-139">Método LeaveRuntime</span><span class="sxs-lookup"><span data-stu-id="41a76-139">LeaveRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)  
 [<span data-ttu-id="41a76-140">Um olhar detalhado sobre invocação de plataforma</span><span class="sxs-lookup"><span data-stu-id="41a76-140">A Closer Look at Platform Invoke</span></span>](https://msdn.microsoft.com/library/ba9dd55b-2eaa-45cd-8afd-75cb8d64d243)
