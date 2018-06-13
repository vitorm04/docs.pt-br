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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 983cad5ed87d0666ed71a805a3b3f7a3c7e7c091
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444298"
---
# <a name="ihosttaskmanagercallneedshosthook-method"></a><span data-ttu-id="28c40-102">Método IHostTaskManager::CallNeedsHostHook</span><span class="sxs-lookup"><span data-stu-id="28c40-102">IHostTaskManager::CallNeedsHostHook Method</span></span>
<span data-ttu-id="28c40-103">Permite que o host especificar se o common language runtime (CLR) pode embutido chamada especificado para uma função não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="28c40-103">Enables the host to specify whether the common language runtime (CLR) can inline the specified call to an unmanaged function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28c40-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="28c40-104">Syntax</span></span>  
  
```  
HRESULT CallNeedsHostHook (  
    [in]  SIZE_T target,   
    [out] BOOL   *pbCallNeedsHostHook  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="28c40-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="28c40-105">Parameters</span></span>  
 `target`  
 <span data-ttu-id="28c40-106">[in] O endereço dentro do arquivo mapeado PE (executável portátil) da função não gerenciada que deve ser chamado.</span><span class="sxs-lookup"><span data-stu-id="28c40-106">[in] The address within the mapped portable executable (PE) file of the unmanaged function that is to be called.</span></span>  
  
 `pbCallNeedsHostHook`  
 <span data-ttu-id="28c40-107">[out] Um ponteiro para um valor booliano que indica se o host requer a chamada a ser vinculada.</span><span class="sxs-lookup"><span data-stu-id="28c40-107">[out] A pointer to a Boolean value that indicates whether the host requires the call to be hooked.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="28c40-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="28c40-108">Return Value</span></span>  
  
|<span data-ttu-id="28c40-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="28c40-109">HRESULT</span></span>|<span data-ttu-id="28c40-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="28c40-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="28c40-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="28c40-111">S_OK</span></span>|<span data-ttu-id="28c40-112">`CallNeedsHostHook` retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="28c40-112">`CallNeedsHostHook` returned successfully.</span></span>|  
|<span data-ttu-id="28c40-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="28c40-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="28c40-114">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="28c40-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="28c40-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="28c40-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="28c40-116">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="28c40-116">The call timed out.</span></span>|  
|<span data-ttu-id="28c40-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="28c40-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="28c40-118">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="28c40-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="28c40-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="28c40-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="28c40-120">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="28c40-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="28c40-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="28c40-121">E_FAIL</span></span>|<span data-ttu-id="28c40-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="28c40-122">An unknown catastrophic failure has occurred.</span></span> <span data-ttu-id="28c40-123">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="28c40-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="28c40-124">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="28c40-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="28c40-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="28c40-125">Remarks</span></span>  
 <span data-ttu-id="28c40-126">Para ajudar a otimizar a execução de código, o CLR realiza uma análise de cada plataforma chamar invoke durante a compilação para determinar se a chamada pode ser embutida.</span><span class="sxs-lookup"><span data-stu-id="28c40-126">To help optimize code execution, the CLR performs an analysis of each platform invoke call during compilation to determine whether the call can be inlined.</span></span> <span data-ttu-id="28c40-127">`CallNeedsHostHook` permite que o host substituir essa decisão, exigindo que uma chamada para uma função não gerenciada ser vinculada.</span><span class="sxs-lookup"><span data-stu-id="28c40-127">`CallNeedsHostHook` enables the host to override that decision by requiring that a call to an unmanaged function be hooked.</span></span> <span data-ttu-id="28c40-128">Se o host requer um gancho, o tempo de execução não embutido não a chamada.</span><span class="sxs-lookup"><span data-stu-id="28c40-128">If the host requires a hook, the runtime does not inline the call.</span></span>  
  
 <span data-ttu-id="28c40-129">O host geralmente exigem um gancho onde ele deve ajustar o estado de ponto flutuante, ou depois de receber a notificação de que uma chamada é entrar em um estado em que o host não pode controlar as solicitações do runtime memória ou qualquer bloqueios.</span><span class="sxs-lookup"><span data-stu-id="28c40-129">The host typically would require a hook where it must adjust a floating-point state, or upon receiving notification that a call is entering a state where the host cannot track the runtime's requests for memory or any locks taken.</span></span> <span data-ttu-id="28c40-130">Quando o host requer que a chamada ser conectado, o tempo de execução notifica o host de transições de e para código gerenciado por meio de chamadas para [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), [ ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), e [ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span><span class="sxs-lookup"><span data-stu-id="28c40-130">When the host requires that the call be hooked, the runtime notifies the host of transitions to and from managed code by using calls to [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), [ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), and [ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28c40-131">Requisitos</span><span class="sxs-lookup"><span data-stu-id="28c40-131">Requirements</span></span>  
 <span data-ttu-id="28c40-132">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="28c40-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28c40-133">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="28c40-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="28c40-134">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="28c40-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="28c40-135">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28c40-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28c40-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="28c40-136">See Also</span></span>  
 [<span data-ttu-id="28c40-137">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="28c40-137">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="28c40-138">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="28c40-138">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="28c40-139">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="28c40-139">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="28c40-140">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="28c40-140">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
