---
title: Método IHostTaskManager::LeaveRuntime
ms.date: 03/30/2017
api_name:
- IHostTaskManager.LeaveRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::LeaveRuntime
helpviewer_keywords:
- IHostTaskManager::LeaveRuntime method [.NET Framework hosting]
- LeaveRuntime method [.NET Framework hosting]
ms.assetid: 43689cc4-e48e-46e5-a22d-bafd768b8759
topic_type:
- apiref
ms.openlocfilehash: 2939f13933c4681e7e2220e5290e019e10c2844e
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83841911"
---
# <a name="ihosttaskmanagerleaveruntime-method"></a><span data-ttu-id="64f5d-102">Método IHostTaskManager::LeaveRuntime</span><span class="sxs-lookup"><span data-stu-id="64f5d-102">IHostTaskManager::LeaveRuntime Method</span></span>
<span data-ttu-id="64f5d-103">Notifica o host de que a tarefa em execução no momento está prestes a sair do Common Language Runtime (CLR) e inserir código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="64f5d-103">Notifies the host that the currently executing task is about to leave the common language runtime (CLR) and enter unmanaged code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="64f5d-104">Uma chamada correspondente para [IHostTaskManager:: EnterRuntime](ihosttaskmanager-enterruntime-method.md) notifica o host que a tarefa em execução no momento está reinserindo o código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="64f5d-104">A corresponding call to [IHostTaskManager::EnterRuntime](ihosttaskmanager-enterruntime-method.md) notifies the host that the currently executing task is reentering managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64f5d-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="64f5d-105">Syntax</span></span>  
  
```cpp  
HRESULT LeaveRuntime (  
    [in] SIZE_T target  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="64f5d-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="64f5d-106">Parameters</span></span>  
 `target`  
 <span data-ttu-id="64f5d-107">no O endereço dentro do arquivo executável portátil mapeado da função não gerenciada a ser chamada.</span><span class="sxs-lookup"><span data-stu-id="64f5d-107">[in] The address within the mapped portable executable file of the unmanaged function to be called.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="64f5d-108">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="64f5d-108">Return Value</span></span>  
  
|<span data-ttu-id="64f5d-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="64f5d-109">HRESULT</span></span>|<span data-ttu-id="64f5d-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="64f5d-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="64f5d-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="64f5d-111">S_OK</span></span>|<span data-ttu-id="64f5d-112">`LeaveRuntime`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="64f5d-112">`LeaveRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="64f5d-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="64f5d-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="64f5d-114">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="64f5d-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="64f5d-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="64f5d-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="64f5d-116">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="64f5d-116">The call timed out.</span></span>|  
|<span data-ttu-id="64f5d-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="64f5d-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="64f5d-118">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="64f5d-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="64f5d-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="64f5d-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="64f5d-120">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="64f5d-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="64f5d-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="64f5d-121">E_FAIL</span></span>|<span data-ttu-id="64f5d-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="64f5d-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="64f5d-123">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="64f5d-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="64f5d-124">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="64f5d-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="64f5d-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="64f5d-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="64f5d-126">Não há memória suficiente disponível para concluir a alocação solicitada.</span><span class="sxs-lookup"><span data-stu-id="64f5d-126">Not enough memory is available to complete the requested allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="64f5d-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="64f5d-127">Remarks</span></span>  
 <span data-ttu-id="64f5d-128">Seqüências de chamadas de e para código não gerenciado podem ser aninhadas.</span><span class="sxs-lookup"><span data-stu-id="64f5d-128">Call sequences to and from unmanaged code can be nested.</span></span> <span data-ttu-id="64f5d-129">Por exemplo, a lista a seguir descreve uma situação hipotética na qual a sequência de chamadas para `LeaveRuntime` , [IHostTaskManager:: ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), [IHostTaskManager:: ReverseLeaveRuntime](ihosttaskmanager-reverseleaveruntime-method.md)e `IHostTaskManager::EnterRuntime` permite que o host identifique as camadas aninhadas.</span><span class="sxs-lookup"><span data-stu-id="64f5d-129">For example, the list below describes a hypothetical situation in which the sequence of calls to `LeaveRuntime`, [IHostTaskManager::ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), [IHostTaskManager::ReverseLeaveRuntime](ihosttaskmanager-reverseleaveruntime-method.md), and `IHostTaskManager::EnterRuntime` allows the host to identify the nested layers.</span></span>  
  
|<span data-ttu-id="64f5d-130">Ação</span><span class="sxs-lookup"><span data-stu-id="64f5d-130">Action</span></span>|<span data-ttu-id="64f5d-131">Chamada de método correspondente</span><span class="sxs-lookup"><span data-stu-id="64f5d-131">Corresponding Method Call</span></span>|  
|------------|-------------------------------|  
|<span data-ttu-id="64f5d-132">Um executável gerenciado Visual Basic chama uma função não gerenciada escrita em C usando a invocação de plataforma.</span><span class="sxs-lookup"><span data-stu-id="64f5d-132">A managed Visual Basic executable calls an unmanaged function written in C by using platform invoke.</span></span>|`IHostTaskManager::LeaveRuntime`|  
|<span data-ttu-id="64f5d-133">A função C não gerenciada chama um método em uma DLL gerenciada escrita em C#.</span><span class="sxs-lookup"><span data-stu-id="64f5d-133">The unmanaged C function calls a method in a managed DLL written in C#.</span></span>|`IHostTaskManager::ReverseEnterRuntime`|  
|<span data-ttu-id="64f5d-134">A função C# gerenciada chama outra função não gerenciada escrita em C, também usando a invocação de plataforma.</span><span class="sxs-lookup"><span data-stu-id="64f5d-134">The managed C# function calls another unmanaged function written in C, also using platform invoke.</span></span>|`IHostTaskManager::LeaveRuntime`|  
|<span data-ttu-id="64f5d-135">A segunda função não gerenciada retorna a execução para a função C#.</span><span class="sxs-lookup"><span data-stu-id="64f5d-135">The second unmanaged function returns execution to the C# function.</span></span>|`IHostTaskManager::EnterRuntime`|  
|<span data-ttu-id="64f5d-136">A função C# retorna a execução para a primeira função não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="64f5d-136">The C# function returns execution to the first unmanaged function.</span></span>|`IHostTaskManager::ReverseLeaveRuntime`|  
|<span data-ttu-id="64f5d-137">A primeira função não gerenciada retorna a execução para o programa de Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="64f5d-137">The first unmanaged function returns execution to the Visual Basic program.</span></span>|`IHostTaskManager::EnterRuntime`|  
  
## <a name="requirements"></a><span data-ttu-id="64f5d-138">Requisitos</span><span class="sxs-lookup"><span data-stu-id="64f5d-138">Requirements</span></span>  
 <span data-ttu-id="64f5d-139">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64f5d-139">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64f5d-140">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="64f5d-140">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="64f5d-141">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="64f5d-141">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="64f5d-142">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64f5d-142">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64f5d-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="64f5d-143">See also</span></span>

- [<span data-ttu-id="64f5d-144">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="64f5d-144">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="64f5d-145">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="64f5d-145">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="64f5d-146">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="64f5d-146">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="64f5d-147">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="64f5d-147">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
