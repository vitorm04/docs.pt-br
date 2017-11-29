---
title: "Método IHostTaskManager::EnterRuntime"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTaskManager.EnterRuntime
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTaskManager::EnterRuntime
helpviewer_keywords:
- IHostTaskManager::EnterRuntime method [.NET Framework hosting]
- EnterRuntime method [.NET Framework hosting]
ms.assetid: 1aa7a4b1-636a-4f5e-b834-b406d72f7120
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2a4c0304047246c912be965d80a26b26ec2344ad
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ihosttaskmanagerenterruntime-method"></a><span data-ttu-id="aeb3c-102">Método IHostTaskManager::EnterRuntime</span><span class="sxs-lookup"><span data-stu-id="aeb3c-102">IHostTaskManager::EnterRuntime Method</span></span>
<span data-ttu-id="aeb3c-103">Notifica o host que uma chamada para um método não gerenciado, como uma plataforma de invocação de método, está retornando o controle de execução para o common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="aeb3c-103">Notifies the host that a call to an unmanaged method, such as a platform invoke method, is returning execution control to the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aeb3c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="aeb3c-104">Syntax</span></span>  
  
```  
HRESULT EnterRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="aeb3c-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="aeb3c-105">Return Value</span></span>  
  
|<span data-ttu-id="aeb3c-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="aeb3c-106">HRESULT</span></span>|<span data-ttu-id="aeb3c-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="aeb3c-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="aeb3c-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="aeb3c-108">S_OK</span></span>|<span data-ttu-id="aeb3c-109">`EnterRuntime`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="aeb3c-109">`EnterRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="aeb3c-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="aeb3c-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="aeb3c-111">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="aeb3c-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="aeb3c-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="aeb3c-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="aeb3c-113">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="aeb3c-113">The call timed out.</span></span>|  
|<span data-ttu-id="aeb3c-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="aeb3c-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="aeb3c-115">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="aeb3c-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="aeb3c-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="aeb3c-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="aeb3c-117">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="aeb3c-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="aeb3c-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="aeb3c-118">E_FAIL</span></span>|<span data-ttu-id="aeb3c-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="aeb3c-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="aeb3c-120">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="aeb3c-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="aeb3c-121">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="aeb3c-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="aeb3c-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="aeb3c-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="aeb3c-123">Não havia memória suficiente disponível para concluir a alocação solicitada.</span><span class="sxs-lookup"><span data-stu-id="aeb3c-123">Not enough memory was available to complete the requested allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aeb3c-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="aeb3c-124">Remarks</span></span>  
 <span data-ttu-id="aeb3c-125">`EnterRuntime`é chamado para notificar o host que uma função não gerenciada, para que uma chamada anterior para o [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md) método foi feito, concluiu a execução e está retornando o controle de execução para o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="aeb3c-125">`EnterRuntime` is called to notify the host that an unmanaged function, for which an earlier call to the [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md) method was made, has finished executing, and is returning execution control to the runtime.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aeb3c-126">[ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md) é chamado para notificar o host que uma função não gerenciada, para que uma chamada anterior para `LeaveRuntime` foi feita, está fazendo uma chamada para código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="aeb3c-126">[ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md) is called to notify the host that an unmanaged function, for which an earlier call to `LeaveRuntime` was made, is making a call into managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aeb3c-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="aeb3c-127">Requirements</span></span>  
 <span data-ttu-id="aeb3c-128">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aeb3c-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aeb3c-129">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="aeb3c-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="aeb3c-130">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="aeb3c-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aeb3c-131">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aeb3c-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aeb3c-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aeb3c-132">See Also</span></span>  
 [<span data-ttu-id="aeb3c-133">Interoperabilidade COM avançada</span><span class="sxs-lookup"><span data-stu-id="aeb3c-133">Advanced COM Interoperability</span></span>](http://msdn.microsoft.com/en-us/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 [<span data-ttu-id="aeb3c-134">Como chamar DLLs nativas de código gerenciado usando PInvoke</span><span class="sxs-lookup"><span data-stu-id="aeb3c-134">How to: Call Native DLLs from Managed Code Using PInvoke</span></span>](/cpp/dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke)  
 [<span data-ttu-id="aeb3c-135">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="aeb3c-135">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="aeb3c-136">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="aeb3c-136">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="aeb3c-137">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="aeb3c-137">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="aeb3c-138">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="aeb3c-138">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="aeb3c-139">Método LeaveRuntime</span><span class="sxs-lookup"><span data-stu-id="aeb3c-139">LeaveRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)
