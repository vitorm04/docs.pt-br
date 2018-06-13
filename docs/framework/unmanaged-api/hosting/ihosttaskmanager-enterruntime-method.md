---
title: Método IHostTaskManager::EnterRuntime
ms.date: 03/30/2017
api_name:
- IHostTaskManager.EnterRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::EnterRuntime
helpviewer_keywords:
- IHostTaskManager::EnterRuntime method [.NET Framework hosting]
- EnterRuntime method [.NET Framework hosting]
ms.assetid: 1aa7a4b1-636a-4f5e-b834-b406d72f7120
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a47f51ba32a9dfc16300a8de7c2d4b380a8ba988
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445089"
---
# <a name="ihosttaskmanagerenterruntime-method"></a><span data-ttu-id="2a012-102">Método IHostTaskManager::EnterRuntime</span><span class="sxs-lookup"><span data-stu-id="2a012-102">IHostTaskManager::EnterRuntime Method</span></span>
<span data-ttu-id="2a012-103">Notifica o host que uma chamada para um método não gerenciado, como uma plataforma de invocação de método, está retornando o controle de execução para o common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="2a012-103">Notifies the host that a call to an unmanaged method, such as a platform invoke method, is returning execution control to the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a012-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2a012-104">Syntax</span></span>  
  
```  
HRESULT EnterRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="2a012-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="2a012-105">Return Value</span></span>  
  
|<span data-ttu-id="2a012-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2a012-106">HRESULT</span></span>|<span data-ttu-id="2a012-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="2a012-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2a012-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="2a012-108">S_OK</span></span>|<span data-ttu-id="2a012-109">`EnterRuntime` retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="2a012-109">`EnterRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="2a012-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2a012-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2a012-111">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="2a012-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2a012-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2a012-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2a012-113">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="2a012-113">The call timed out.</span></span>|  
|<span data-ttu-id="2a012-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2a012-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2a012-115">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="2a012-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2a012-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2a012-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2a012-117">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="2a012-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2a012-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2a012-118">E_FAIL</span></span>|<span data-ttu-id="2a012-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="2a012-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2a012-120">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="2a012-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2a012-121">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="2a012-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="2a012-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="2a012-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="2a012-123">Não havia memória suficiente disponível para concluir a alocação solicitada.</span><span class="sxs-lookup"><span data-stu-id="2a012-123">Not enough memory was available to complete the requested allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2a012-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="2a012-124">Remarks</span></span>  
 <span data-ttu-id="2a012-125">`EnterRuntime` é chamado para notificar o host que uma função não gerenciada, para que uma chamada anterior para o [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md) método foi feito, concluiu a execução e está retornando o controle de execução para o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="2a012-125">`EnterRuntime` is called to notify the host that an unmanaged function, for which an earlier call to the [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md) method was made, has finished executing, and is returning execution control to the runtime.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2a012-126">[ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md) é chamado para notificar o host que uma função não gerenciada, para que uma chamada anterior para `LeaveRuntime` foi feita, está fazendo uma chamada para código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="2a012-126">[ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md) is called to notify the host that an unmanaged function, for which an earlier call to `LeaveRuntime` was made, is making a call into managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a012-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2a012-127">Requirements</span></span>  
 <span data-ttu-id="2a012-128">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a012-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a012-129">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2a012-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2a012-130">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="2a012-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2a012-131">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a012-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a012-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2a012-132">See Also</span></span>  
 [<span data-ttu-id="2a012-133">Interoperabilidade COM avançada</span><span class="sxs-lookup"><span data-stu-id="2a012-133">Advanced COM Interoperability</span></span>](http://msdn.microsoft.com/library/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 [<span data-ttu-id="2a012-134">Como chamar DLLs nativas de código gerenciado usando PInvoke</span><span class="sxs-lookup"><span data-stu-id="2a012-134">How to: Call Native DLLs from Managed Code Using PInvoke</span></span>](/cpp/dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke)  
 [<span data-ttu-id="2a012-135">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="2a012-135">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="2a012-136">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="2a012-136">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="2a012-137">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="2a012-137">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="2a012-138">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="2a012-138">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="2a012-139">Método LeaveRuntime</span><span class="sxs-lookup"><span data-stu-id="2a012-139">LeaveRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)
