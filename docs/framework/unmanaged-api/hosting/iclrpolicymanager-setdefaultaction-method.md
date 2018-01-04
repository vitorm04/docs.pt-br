---
title: "Método ICLRPolicyManager::SetDefaultAction"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRPolicyManager.SetDefaultAction
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRPolicyManager::SetDefaultAction
helpviewer_keywords:
- SetDefaultAction method [.NET Framework hosting]
- ICLRPolicyManager::SetDefaultAction method [.NET Framework hosting]
ms.assetid: f9411e7a-27df-451f-9f6c-d643d6a7a7ce
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 751853aaf4322c15b44bb9b912d293a081c24ba8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrpolicymanagersetdefaultaction-method"></a><span data-ttu-id="3a20b-102">Método ICLRPolicyManager::SetDefaultAction</span><span class="sxs-lookup"><span data-stu-id="3a20b-102">ICLRPolicyManager::SetDefaultAction Method</span></span>
<span data-ttu-id="3a20b-103">Especifica a ação de política, que o common language runtime (CLR) deve ser executada quando ocorre a operação especificada.</span><span class="sxs-lookup"><span data-stu-id="3a20b-103">Specifies the policy action the common language runtime (CLR) should take when the specified operation occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a20b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3a20b-104">Syntax</span></span>  
  
```  
HRESULT SetDefaultAction (  
    [in] EClrOperation operation,  
    [in] EPolicyAction action  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3a20b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3a20b-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="3a20b-106">[in] Uma da [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) valores, que indica a ação para o qual CLR comportamento deve ser personalizado.</span><span class="sxs-lookup"><span data-stu-id="3a20b-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the action for which CLR behavior should be customized.</span></span>  
  
 `action`  
 <span data-ttu-id="3a20b-107">[in] Uma da [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) valores, que indica a ação da política do CLR deve ser executada quando `operation` ocorre.</span><span class="sxs-lookup"><span data-stu-id="3a20b-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the policy action the CLR should take when `operation` occurs.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3a20b-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="3a20b-108">Return Value</span></span>  
  
|<span data-ttu-id="3a20b-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3a20b-109">HRESULT</span></span>|<span data-ttu-id="3a20b-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="3a20b-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3a20b-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="3a20b-111">S_OK</span></span>|<span data-ttu-id="3a20b-112">`SetDefaultAction`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="3a20b-112">`SetDefaultAction` returned successfully.</span></span>|  
|<span data-ttu-id="3a20b-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3a20b-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3a20b-114">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="3a20b-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3a20b-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3a20b-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3a20b-116">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="3a20b-116">The call timed out.</span></span>|  
|<span data-ttu-id="3a20b-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3a20b-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3a20b-118">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="3a20b-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3a20b-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3a20b-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3a20b-120">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="3a20b-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3a20b-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3a20b-121">E_FAIL</span></span>|<span data-ttu-id="3a20b-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="3a20b-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3a20b-123">Depois que um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="3a20b-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3a20b-124">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="3a20b-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="3a20b-125">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="3a20b-125">E_INVALIDARG</span></span>|<span data-ttu-id="3a20b-126">Inválido `action` foi especificado para o `operation`, ou um valor inválido foi fornecido para `operation`.</span><span class="sxs-lookup"><span data-stu-id="3a20b-126">An invalid `action` was specified for the `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3a20b-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="3a20b-127">Remarks</span></span>  
 <span data-ttu-id="3a20b-128">Nem todos os valores da política de ação podem ser especificados como o comportamento padrão para operações de CLR.</span><span class="sxs-lookup"><span data-stu-id="3a20b-128">Not all policy action values can be specified as the default behavior for CLR operations.</span></span> <span data-ttu-id="3a20b-129">`SetDefaultAction`normalmente podem ser usadas somente para escalonar o comportamento.</span><span class="sxs-lookup"><span data-stu-id="3a20b-129">`SetDefaultAction` can typically be used only to escalate behavior.</span></span> <span data-ttu-id="3a20b-130">Por exemplo, um host pode especificar que anulações de thread se tornar educado anulações de thread, mas não é possível especificar o oposto.</span><span class="sxs-lookup"><span data-stu-id="3a20b-130">For example, a host can specify that thread aborts be turned into rude thread aborts, but cannot specify the opposite.</span></span> <span data-ttu-id="3a20b-131">A tabela a seguir descreve o válido `action` valores para cada possível `operation` valor.</span><span class="sxs-lookup"><span data-stu-id="3a20b-131">The table below describes the valid `action` values for each possible `operation` value.</span></span>  
  
|<span data-ttu-id="3a20b-132">Valor para`operation`</span><span class="sxs-lookup"><span data-stu-id="3a20b-132">Value for `operation`</span></span>|<span data-ttu-id="3a20b-133">Valores válidos para`action`</span><span class="sxs-lookup"><span data-stu-id="3a20b-133">Valid values for `action`</span></span>|  
|---------------------------|-------------------------------|  
|<span data-ttu-id="3a20b-134">OPR_ThreadAbort</span><span class="sxs-lookup"><span data-stu-id="3a20b-134">OPR_ThreadAbort</span></span>|<span data-ttu-id="3a20b-135">-eAbortThread</span><span class="sxs-lookup"><span data-stu-id="3a20b-135">-   eAbortThread</span></span><br /><span data-ttu-id="3a20b-136">-eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="3a20b-136">-   eRudeAbortThread</span></span><br /><span data-ttu-id="3a20b-137">-eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="3a20b-137">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="3a20b-138">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="3a20b-138">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="3a20b-139">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="3a20b-139">-   eExitProcess</span></span><br /><span data-ttu-id="3a20b-140">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="3a20b-140">-   eFastExitProcess</span></span><br /><span data-ttu-id="3a20b-141">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="3a20b-141">-   eRudeExitProcess</span></span><br /><span data-ttu-id="3a20b-142">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="3a20b-142">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="3a20b-143">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="3a20b-143">OPR_ThreadRudeAbortInNonCriticalRegion</span></span><br /><br /> <span data-ttu-id="3a20b-144">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="3a20b-144">OPR_ThreadRudeAbortInCriticalRegion</span></span>|<span data-ttu-id="3a20b-145">-eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="3a20b-145">-   eRudeAbortThread</span></span><br /><span data-ttu-id="3a20b-146">-eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="3a20b-146">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="3a20b-147">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="3a20b-147">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="3a20b-148">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="3a20b-148">-   eExitProcess</span></span><br /><span data-ttu-id="3a20b-149">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="3a20b-149">-   eFastExitProcess</span></span><br /><span data-ttu-id="3a20b-150">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="3a20b-150">-   eRudeExitProcess</span></span><br /><span data-ttu-id="3a20b-151">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="3a20b-151">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="3a20b-152">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="3a20b-152">OPR_AppDomainUnload</span></span>|<span data-ttu-id="3a20b-153">-eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="3a20b-153">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="3a20b-154">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="3a20b-154">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="3a20b-155">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="3a20b-155">-   eExitProcess</span></span><br /><span data-ttu-id="3a20b-156">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="3a20b-156">-   eFastExitProcess</span></span><br /><span data-ttu-id="3a20b-157">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="3a20b-157">-   eRudeExitProcess</span></span><br /><span data-ttu-id="3a20b-158">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="3a20b-158">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="3a20b-159">OPR_AppDomainRudeUnload</span><span class="sxs-lookup"><span data-stu-id="3a20b-159">OPR_AppDomainRudeUnload</span></span>|<span data-ttu-id="3a20b-160">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="3a20b-160">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="3a20b-161">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="3a20b-161">-   eExitProcess</span></span><br /><span data-ttu-id="3a20b-162">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="3a20b-162">-   eFastExitProcess</span></span><br /><span data-ttu-id="3a20b-163">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="3a20b-163">-   eRudeExitProcess</span></span><br /><span data-ttu-id="3a20b-164">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="3a20b-164">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="3a20b-165">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="3a20b-165">OPR_ProcessExit</span></span>|<span data-ttu-id="3a20b-166">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="3a20b-166">-   eExitProcess</span></span><br /><span data-ttu-id="3a20b-167">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="3a20b-167">-   eFastExitProcess</span></span><br /><span data-ttu-id="3a20b-168">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="3a20b-168">-   eRudeExitProcess</span></span><br /><span data-ttu-id="3a20b-169">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="3a20b-169">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="3a20b-170">OPR_FinalizerRun</span><span class="sxs-lookup"><span data-stu-id="3a20b-170">OPR_FinalizerRun</span></span>|<span data-ttu-id="3a20b-171">-eNoAction</span><span class="sxs-lookup"><span data-stu-id="3a20b-171">-   eNoAction</span></span><br /><span data-ttu-id="3a20b-172">-eAbortThread</span><span class="sxs-lookup"><span data-stu-id="3a20b-172">-   eAbortThread</span></span><br /><span data-ttu-id="3a20b-173">-eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="3a20b-173">-   eRudeAbortThread</span></span><br /><span data-ttu-id="3a20b-174">-eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="3a20b-174">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="3a20b-175">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="3a20b-175">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="3a20b-176">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="3a20b-176">-   eExitProcess</span></span><br /><span data-ttu-id="3a20b-177">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="3a20b-177">-   eFastExitProcess</span></span><br /><span data-ttu-id="3a20b-178">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="3a20b-178">-   eRudeExitProcess</span></span><br /><span data-ttu-id="3a20b-179">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="3a20b-179">-   eDisableRuntime</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3a20b-180">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3a20b-180">Requirements</span></span>  
 <span data-ttu-id="3a20b-181">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a20b-181">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a20b-182">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3a20b-182">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3a20b-183">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="3a20b-183">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3a20b-184">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a20b-184">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a20b-185">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3a20b-185">See Also</span></span>  
 [<span data-ttu-id="3a20b-186">Enumeração EClrOperation</span><span class="sxs-lookup"><span data-stu-id="3a20b-186">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="3a20b-187">Enumeração EPolicyAction</span><span class="sxs-lookup"><span data-stu-id="3a20b-187">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="3a20b-188">Interface ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="3a20b-188">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
