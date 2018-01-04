---
title: "Método IHostTaskManager::LeaveRuntime"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTaskManager.LeaveRuntime
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTaskManager::LeaveRuntime
helpviewer_keywords:
- IHostTaskManager::LeaveRuntime method [.NET Framework hosting]
- LeaveRuntime method [.NET Framework hosting]
ms.assetid: 43689cc4-e48e-46e5-a22d-bafd768b8759
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a4c168cffba44a21d6705e8abd921ecbf8a9da6b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ihosttaskmanagerleaveruntime-method"></a><span data-ttu-id="a4fc8-102">Método IHostTaskManager::LeaveRuntime</span><span class="sxs-lookup"><span data-stu-id="a4fc8-102">IHostTaskManager::LeaveRuntime Method</span></span>
<span data-ttu-id="a4fc8-103">Notifica o host que a tarefa em execução no momento está prestes a deixar o common language runtime (CLR) e insira o código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="a4fc8-103">Notifies the host that the currently executing task is about to leave the common language runtime (CLR) and enter unmanaged code.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a4fc8-104">Uma chamada correspondente para [Enterruntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md) notifica o host que a tarefa em execução no momento é precisar reinserir o código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="a4fc8-104">A corresponding call to [IHostTaskManager::EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md) notifies the host that the currently executing task is reentering managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4fc8-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a4fc8-105">Syntax</span></span>  
  
```  
HRESULT LeaveRuntime (  
    [in] SIZE_T target  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a4fc8-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a4fc8-106">Parameters</span></span>  
 `target`  
 <span data-ttu-id="a4fc8-107">[in] O endereço dentro do arquivo executável portátil mapeado de função não gerenciada a ser chamado.</span><span class="sxs-lookup"><span data-stu-id="a4fc8-107">[in] The address within the mapped portable executable file of the unmanaged function to be called.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a4fc8-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="a4fc8-108">Return Value</span></span>  
  
|<span data-ttu-id="a4fc8-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a4fc8-109">HRESULT</span></span>|<span data-ttu-id="a4fc8-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="a4fc8-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a4fc8-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="a4fc8-111">S_OK</span></span>|<span data-ttu-id="a4fc8-112">`LeaveRuntime`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="a4fc8-112">`LeaveRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="a4fc8-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a4fc8-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a4fc8-114">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="a4fc8-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a4fc8-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a4fc8-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a4fc8-116">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="a4fc8-116">The call timed out.</span></span>|  
|<span data-ttu-id="a4fc8-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a4fc8-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a4fc8-118">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="a4fc8-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a4fc8-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a4fc8-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a4fc8-120">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="a4fc8-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a4fc8-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a4fc8-121">E_FAIL</span></span>|<span data-ttu-id="a4fc8-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="a4fc8-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a4fc8-123">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="a4fc8-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a4fc8-124">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a4fc8-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a4fc8-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="a4fc8-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="a4fc8-126">Não há memória suficiente está disponível para concluir a alocação solicitada.</span><span class="sxs-lookup"><span data-stu-id="a4fc8-126">Not enough memory is available to complete the requested allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a4fc8-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="a4fc8-127">Remarks</span></span>  
 <span data-ttu-id="a4fc8-128">Sequências de chamada de código não gerenciado e podem ser aninhadas.</span><span class="sxs-lookup"><span data-stu-id="a4fc8-128">Call sequences to and from unmanaged code can be nested.</span></span> <span data-ttu-id="a4fc8-129">Por exemplo, a lista a seguir descreve uma situação hipotética no qual a sequência de chamadas para `LeaveRuntime`, [Ihosttaskmanager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), [Ihosttaskmanager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md), e `IHostTaskManager::EnterRuntime` permite que o host identificar as camadas aninhadas.</span><span class="sxs-lookup"><span data-stu-id="a4fc8-129">For example, the list below describes a hypothetical situation in which the sequence of calls to `LeaveRuntime`, [IHostTaskManager::ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), [IHostTaskManager::ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md), and `IHostTaskManager::EnterRuntime` allows the host to identify the nested layers.</span></span>  
  
|<span data-ttu-id="a4fc8-130">Ação</span><span class="sxs-lookup"><span data-stu-id="a4fc8-130">Action</span></span>|<span data-ttu-id="a4fc8-131">Chamada de método correspondente</span><span class="sxs-lookup"><span data-stu-id="a4fc8-131">Corresponding Method Call</span></span>|  
|------------|-------------------------------|  
|<span data-ttu-id="a4fc8-132">Invocação de uma função não gerenciada, escrita em C usando a plataforma um chamadas executável gerenciado do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a4fc8-132">A managed Visual Basic executable calls an unmanaged function written in C by using platform invoke.</span></span>|`IHostTaskManager::LeaveRuntime`|  
|<span data-ttu-id="a4fc8-133">A função não gerenciada de C chama um método em uma DLL gerenciada, escrita em c#.</span><span class="sxs-lookup"><span data-stu-id="a4fc8-133">The unmanaged C function calls a method in a managed DLL written in C#.</span></span>|`IHostTaskManager::ReverseEnterRuntime`|  
|<span data-ttu-id="a4fc8-134">A função c# gerenciada chama outra função não gerenciada, escrita em C, também usando invocação de plataforma.</span><span class="sxs-lookup"><span data-stu-id="a4fc8-134">The managed C# function calls another unmanaged function written in C, also using platform invoke.</span></span>|`IHostTaskManager::LeaveRuntime`|  
|<span data-ttu-id="a4fc8-135">A segunda função não gerenciada retorna a execução para a função c#.</span><span class="sxs-lookup"><span data-stu-id="a4fc8-135">The second unmanaged function returns execution to the C# function.</span></span>|`IHostTaskManager::EnterRuntime`|  
|<span data-ttu-id="a4fc8-136">A função c# retorna a execução para a primeira função não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="a4fc8-136">The C# function returns execution to the first unmanaged function.</span></span>|`IHostTaskManager::ReverseLeaveRuntime`|  
|<span data-ttu-id="a4fc8-137">A função não gerenciada primeiro retorna a execução para o programa do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a4fc8-137">The first unmanaged function returns execution to the Visual Basic program.</span></span>|`IHostTaskManager::EnterRuntime`|  
  
## <a name="requirements"></a><span data-ttu-id="a4fc8-138">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a4fc8-138">Requirements</span></span>  
 <span data-ttu-id="a4fc8-139">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a4fc8-139">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4fc8-140">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a4fc8-140">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a4fc8-141">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="a4fc8-141">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a4fc8-142">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4fc8-142">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4fc8-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a4fc8-143">See Also</span></span>  
 [<span data-ttu-id="a4fc8-144">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="a4fc8-144">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="a4fc8-145">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="a4fc8-145">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="a4fc8-146">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="a4fc8-146">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="a4fc8-147">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="a4fc8-147">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
