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
ms.openlocfilehash: e4ef2971d9835070e9db72a5e5d370ff35c8edfe
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61984263"
---
# <a name="ihosttaskmanagerenterruntime-method"></a><span data-ttu-id="92b62-102">Método IHostTaskManager::EnterRuntime</span><span class="sxs-lookup"><span data-stu-id="92b62-102">IHostTaskManager::EnterRuntime Method</span></span>
<span data-ttu-id="92b62-103">Notifica o host que uma chamada para um método não gerenciado, como uma plataforma de invocação de método, está retornando o controle de execução para o common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="92b62-103">Notifies the host that a call to an unmanaged method, such as a platform invoke method, is returning execution control to the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92b62-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="92b62-104">Syntax</span></span>  
  
```  
HRESULT EnterRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="92b62-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="92b62-105">Return Value</span></span>  
  
|<span data-ttu-id="92b62-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="92b62-106">HRESULT</span></span>|<span data-ttu-id="92b62-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="92b62-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="92b62-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="92b62-108">S_OK</span></span>|<span data-ttu-id="92b62-109">`EnterRuntime` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="92b62-109">`EnterRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="92b62-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="92b62-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="92b62-111">O CLR não tenha sido carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="92b62-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="92b62-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="92b62-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="92b62-113">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="92b62-113">The call timed out.</span></span>|  
|<span data-ttu-id="92b62-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="92b62-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="92b62-115">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="92b62-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="92b62-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="92b62-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="92b62-117">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="92b62-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="92b62-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="92b62-118">E_FAIL</span></span>|<span data-ttu-id="92b62-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="92b62-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="92b62-120">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="92b62-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="92b62-121">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="92b62-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="92b62-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="92b62-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="92b62-123">Não havia memória suficiente disponível para concluir a alocação solicitada.</span><span class="sxs-lookup"><span data-stu-id="92b62-123">Not enough memory was available to complete the requested allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="92b62-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="92b62-124">Remarks</span></span>  
 <span data-ttu-id="92b62-125">`EnterRuntime` é chamado para notificar o host que uma função não gerenciada, para o qual uma chamada anterior para o [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md) método foi feito, execução foi concluída e está retornando o controle de execução para o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="92b62-125">`EnterRuntime` is called to notify the host that an unmanaged function, for which an earlier call to the [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md) method was made, has finished executing, and is returning execution control to the runtime.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="92b62-126">[ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md) é chamado para notificar o host que uma função não gerenciada, para o qual uma chamada anterior para `LeaveRuntime` foi feita, está fazendo uma chamada para o código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="92b62-126">[ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md) is called to notify the host that an unmanaged function, for which an earlier call to `LeaveRuntime` was made, is making a call into managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92b62-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="92b62-127">Requirements</span></span>  
 <span data-ttu-id="92b62-128">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92b62-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92b62-129">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="92b62-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="92b62-130">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="92b62-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="92b62-131">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92b62-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92b62-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="92b62-132">See also</span></span>

- [<span data-ttu-id="92b62-133">Interoperabilidade COM avançada</span><span class="sxs-lookup"><span data-stu-id="92b62-133">Advanced COM Interoperability</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx)
- [<span data-ttu-id="92b62-134">Como: chamar DLLs nativas de código gerenciado usando o PInvoke</span><span class="sxs-lookup"><span data-stu-id="92b62-134">How to: Call Native DLLs from Managed Code Using PInvoke</span></span>](/cpp/dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke)
- [<span data-ttu-id="92b62-135">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="92b62-135">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="92b62-136">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="92b62-136">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="92b62-137">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="92b62-137">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="92b62-138">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="92b62-138">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="92b62-139">Método LeaveRuntime</span><span class="sxs-lookup"><span data-stu-id="92b62-139">LeaveRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)
