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
ms.openlocfilehash: a3af57859c5284ff45681ffc2b5aa3ea3cf8fad6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133054"
---
# <a name="ihosttaskmanagerenterruntime-method"></a><span data-ttu-id="aee36-102">Método IHostTaskManager::EnterRuntime</span><span class="sxs-lookup"><span data-stu-id="aee36-102">IHostTaskManager::EnterRuntime Method</span></span>
<span data-ttu-id="aee36-103">Notifica o host de que uma chamada para um método não gerenciado, como um método de invocação de plataforma, está retornando o controle de execução para o Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="aee36-103">Notifies the host that a call to an unmanaged method, such as a platform invoke method, is returning execution control to the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aee36-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="aee36-104">Syntax</span></span>  
  
```cpp  
HRESULT EnterRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="aee36-105">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="aee36-105">Return Value</span></span>  
  
|<span data-ttu-id="aee36-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="aee36-106">HRESULT</span></span>|<span data-ttu-id="aee36-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="aee36-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="aee36-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="aee36-108">S_OK</span></span>|<span data-ttu-id="aee36-109">`EnterRuntime` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="aee36-109">`EnterRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="aee36-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="aee36-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="aee36-111">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="aee36-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="aee36-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="aee36-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="aee36-113">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="aee36-113">The call timed out.</span></span>|  
|<span data-ttu-id="aee36-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="aee36-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="aee36-115">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="aee36-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="aee36-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="aee36-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="aee36-117">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="aee36-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="aee36-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="aee36-118">E_FAIL</span></span>|<span data-ttu-id="aee36-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="aee36-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="aee36-120">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="aee36-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="aee36-121">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="aee36-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="aee36-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="aee36-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="aee36-123">Não havia memória suficiente disponível para concluir a alocação solicitada.</span><span class="sxs-lookup"><span data-stu-id="aee36-123">Not enough memory was available to complete the requested allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aee36-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="aee36-124">Remarks</span></span>  
 <span data-ttu-id="aee36-125">`EnterRuntime` é chamado para notificar o host de que uma função não gerenciada, para a qual uma chamada anterior para o método [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md) foi feita, concluiu a execução e está retornando o controle de execução para o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="aee36-125">`EnterRuntime` is called to notify the host that an unmanaged function, for which an earlier call to the [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md) method was made, has finished executing, and is returning execution control to the runtime.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="aee36-126">[ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md) é chamado para notificar o host de que uma função não gerenciada, para a qual uma chamada anterior para `LeaveRuntime` foi feita, está fazendo uma chamada para código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="aee36-126">[ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md) is called to notify the host that an unmanaged function, for which an earlier call to `LeaveRuntime` was made, is making a call into managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aee36-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="aee36-127">Requirements</span></span>  
 <span data-ttu-id="aee36-128">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aee36-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aee36-129">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="aee36-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="aee36-130">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="aee36-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aee36-131">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aee36-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aee36-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aee36-132">See also</span></span>

- [<span data-ttu-id="aee36-133">Interoperabilidade COM avançada</span><span class="sxs-lookup"><span data-stu-id="aee36-133">Advanced COM Interoperability</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx)
- [<span data-ttu-id="aee36-134">Como chamar DLLs nativas de código gerenciado usando PInvoke</span><span class="sxs-lookup"><span data-stu-id="aee36-134">How to: Call Native DLLs from Managed Code Using PInvoke</span></span>](/cpp/dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke)
- [<span data-ttu-id="aee36-135">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="aee36-135">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="aee36-136">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="aee36-136">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="aee36-137">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="aee36-137">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="aee36-138">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="aee36-138">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="aee36-139">Método LeaveRuntime</span><span class="sxs-lookup"><span data-stu-id="aee36-139">LeaveRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)
