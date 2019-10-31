---
title: Método IHostTaskManager::CallNeedsHostHook
ms.date: 03/30/2017
api_name:
- IHostTaskManager.CallNeedsHostHook
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::CallNeedsHostHook
helpviewer_keywords:
- CallNeedsHostHook method [.NET Framework hosting]
- IHostTaskManager::CallNeedsHostHook method [.NET Framework hosting]
ms.assetid: b60f1f59-9825-4b57-961f-d2979518e6a7
topic_type:
- apiref
ms.openlocfilehash: f5a595651baa48553997c2cba138f4f61bd530f0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133097"
---
# <a name="ihosttaskmanagercallneedshosthook-method"></a><span data-ttu-id="38783-102">Método IHostTaskManager::CallNeedsHostHook</span><span class="sxs-lookup"><span data-stu-id="38783-102">IHostTaskManager::CallNeedsHostHook Method</span></span>
<span data-ttu-id="38783-103">Permite que o host especifique se o Common Language Runtime (CLR) pode embutir a chamada especificada para uma função não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="38783-103">Enables the host to specify whether the common language runtime (CLR) can inline the specified call to an unmanaged function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38783-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="38783-104">Syntax</span></span>  
  
```cpp  
HRESULT CallNeedsHostHook (  
    [in]  SIZE_T target,   
    [out] BOOL   *pbCallNeedsHostHook  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="38783-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="38783-105">Parameters</span></span>  
 `target`  
 <span data-ttu-id="38783-106">no O endereço dentro do arquivo PE (executável portátil) mapeado da função não gerenciada que deve ser chamada.</span><span class="sxs-lookup"><span data-stu-id="38783-106">[in] The address within the mapped portable executable (PE) file of the unmanaged function that is to be called.</span></span>  
  
 `pbCallNeedsHostHook`  
 <span data-ttu-id="38783-107">fora Um ponteiro para um valor booliano que indica se o host requer que a chamada seja conectada.</span><span class="sxs-lookup"><span data-stu-id="38783-107">[out] A pointer to a Boolean value that indicates whether the host requires the call to be hooked.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="38783-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="38783-108">Return Value</span></span>  
  
|<span data-ttu-id="38783-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="38783-109">HRESULT</span></span>|<span data-ttu-id="38783-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="38783-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="38783-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="38783-111">S_OK</span></span>|<span data-ttu-id="38783-112">`CallNeedsHostHook` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="38783-112">`CallNeedsHostHook` returned successfully.</span></span>|  
|<span data-ttu-id="38783-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="38783-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="38783-114">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="38783-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="38783-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="38783-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="38783-116">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="38783-116">The call timed out.</span></span>|  
|<span data-ttu-id="38783-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="38783-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="38783-118">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="38783-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="38783-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="38783-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="38783-120">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="38783-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="38783-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="38783-121">E_FAIL</span></span>|<span data-ttu-id="38783-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="38783-122">An unknown catastrophic failure has occurred.</span></span> <span data-ttu-id="38783-123">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="38783-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="38783-124">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="38783-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="38783-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="38783-125">Remarks</span></span>  
 <span data-ttu-id="38783-126">Para ajudar a otimizar a execução de código, o CLR executa uma análise de cada chamada de invocação de plataforma durante a compilação para determinar se a chamada pode ser embutida.</span><span class="sxs-lookup"><span data-stu-id="38783-126">To help optimize code execution, the CLR performs an analysis of each platform invoke call during compilation to determine whether the call can be inlined.</span></span> <span data-ttu-id="38783-127">`CallNeedsHostHook` permite que o host Substitua essa decisão exigindo que uma chamada para uma função não gerenciada seja conectada.</span><span class="sxs-lookup"><span data-stu-id="38783-127">`CallNeedsHostHook` enables the host to override that decision by requiring that a call to an unmanaged function be hooked.</span></span> <span data-ttu-id="38783-128">Se o host exigir um gancho, o tempo de execução não embuti a chamada.</span><span class="sxs-lookup"><span data-stu-id="38783-128">If the host requires a hook, the runtime does not inline the call.</span></span>  
  
 <span data-ttu-id="38783-129">O host normalmente exigiria um gancho no qual ele deve ajustar um estado de ponto flutuante ou ao receber a notificação de que uma chamada está entrando em um estado em que o host não pode rastrear as solicitações do tempo de execução para a memória ou quaisquer bloqueios tirados.</span><span class="sxs-lookup"><span data-stu-id="38783-129">The host typically would require a hook where it must adjust a floating-point state, or upon receiving notification that a call is entering a state where the host cannot track the runtime's requests for memory or any locks taken.</span></span> <span data-ttu-id="38783-130">Quando o host exige que a chamada seja conectada, o tempo de execução notifica o host de transições de e para código gerenciado usando chamadas para [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), [ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md)e [ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span><span class="sxs-lookup"><span data-stu-id="38783-130">When the host requires that the call be hooked, the runtime notifies the host of transitions to and from managed code by using calls to [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), [ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), and [ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38783-131">Requisitos</span><span class="sxs-lookup"><span data-stu-id="38783-131">Requirements</span></span>  
 <span data-ttu-id="38783-132">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38783-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38783-133">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="38783-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="38783-134">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="38783-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="38783-135">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38783-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38783-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="38783-136">See also</span></span>

- [<span data-ttu-id="38783-137">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="38783-137">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="38783-138">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="38783-138">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="38783-139">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="38783-139">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="38783-140">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="38783-140">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
