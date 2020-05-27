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
ms.openlocfilehash: b255a1d35aa32975c879aac00f7d4edb8ea88d3b
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842030"
---
# <a name="ihosttaskmanagerenterruntime-method"></a><span data-ttu-id="9a988-102">Método IHostTaskManager::EnterRuntime</span><span class="sxs-lookup"><span data-stu-id="9a988-102">IHostTaskManager::EnterRuntime Method</span></span>
<span data-ttu-id="9a988-103">Notifica o host de que uma chamada para um método não gerenciado, como um método de invocação de plataforma, está retornando o controle de execução para o Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="9a988-103">Notifies the host that a call to an unmanaged method, such as a platform invoke method, is returning execution control to the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a988-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9a988-104">Syntax</span></span>  
  
```cpp  
HRESULT EnterRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="9a988-105">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="9a988-105">Return Value</span></span>  
  
|<span data-ttu-id="9a988-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9a988-106">HRESULT</span></span>|<span data-ttu-id="9a988-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="9a988-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9a988-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="9a988-108">S_OK</span></span>|<span data-ttu-id="9a988-109">`EnterRuntime`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="9a988-109">`EnterRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="9a988-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9a988-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9a988-111">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="9a988-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9a988-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9a988-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9a988-113">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="9a988-113">The call timed out.</span></span>|  
|<span data-ttu-id="9a988-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9a988-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9a988-115">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="9a988-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9a988-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9a988-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9a988-117">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="9a988-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9a988-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9a988-118">E_FAIL</span></span>|<span data-ttu-id="9a988-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="9a988-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9a988-120">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="9a988-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9a988-121">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9a988-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="9a988-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="9a988-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="9a988-123">Não havia memória suficiente disponível para concluir a alocação solicitada.</span><span class="sxs-lookup"><span data-stu-id="9a988-123">Not enough memory was available to complete the requested allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9a988-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="9a988-124">Remarks</span></span>  
 <span data-ttu-id="9a988-125">`EnterRuntime`é chamado para notificar o host de que uma função não gerenciada, para a qual uma chamada anterior para o método [LeaveRuntime](ihosttaskmanager-leaveruntime-method.md) foi feita, concluiu a execução e está retornando o controle de execução para o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="9a988-125">`EnterRuntime` is called to notify the host that an unmanaged function, for which an earlier call to the [LeaveRuntime](ihosttaskmanager-leaveruntime-method.md) method was made, has finished executing, and is returning execution control to the runtime.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9a988-126">[ReverseEnterRuntime](ihosttaskmanager-reverseenterruntime-method.md) é chamado para notificar o host de que uma função não gerenciada, para a qual uma chamada anterior `LeaveRuntime` foi feita, está fazendo uma chamada para código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="9a988-126">[ReverseEnterRuntime](ihosttaskmanager-reverseenterruntime-method.md) is called to notify the host that an unmanaged function, for which an earlier call to `LeaveRuntime` was made, is making a call into managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a988-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9a988-127">Requirements</span></span>  
 <span data-ttu-id="9a988-128">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a988-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a988-129">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9a988-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9a988-130">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9a988-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9a988-131">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a988-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a988-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9a988-132">See also</span></span>

- <span data-ttu-id="9a988-133">[Interoperabilidade COM avançada](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="9a988-133">[Advanced COM Interoperability](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span></span>
- [<span data-ttu-id="9a988-134">Como: chamar DLLs nativas do código gerenciado usando PInvoke</span><span class="sxs-lookup"><span data-stu-id="9a988-134">How to: Call Native DLLs from Managed Code Using PInvoke</span></span>](/cpp/dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke)
- [<span data-ttu-id="9a988-135">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="9a988-135">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="9a988-136">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="9a988-136">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="9a988-137">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="9a988-137">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="9a988-138">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="9a988-138">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="9a988-139">Método LeaveRuntime</span><span class="sxs-lookup"><span data-stu-id="9a988-139">LeaveRuntime Method</span></span>](ihosttaskmanager-leaveruntime-method.md)
