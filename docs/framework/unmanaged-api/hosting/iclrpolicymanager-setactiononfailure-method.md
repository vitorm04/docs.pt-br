---
title: "Método ICLRPolicyManager::SetActionOnFailure"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRPolicyManager.SetActionOnFailure
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRPolicyManager::SetActionOnFailure
helpviewer_keywords:
- SetActionOnFailure method [.NET Framework hosting]
- ICLRPolicyManager::SetActionOnFailure method [.NET Framework hosting]
ms.assetid: 4664033f-db97-4388-b988-2ec470796e58
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5dc8e27ed1a5701886c3583a7515e4212f490208
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrpolicymanagersetactiononfailure-method"></a><span data-ttu-id="ca2eb-102">Método ICLRPolicyManager::SetActionOnFailure</span><span class="sxs-lookup"><span data-stu-id="ca2eb-102">ICLRPolicyManager::SetActionOnFailure Method</span></span>
<span data-ttu-id="ca2eb-103">Especifica a ação de política, que o common language runtime (CLR) deve ser executada quando ocorre a falha especificada.</span><span class="sxs-lookup"><span data-stu-id="ca2eb-103">Specifies the policy action the common language runtime (CLR) should take when the specified failure occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca2eb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ca2eb-104">Syntax</span></span>  
  
```  
HRESULT SetActionOnFailure (  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ca2eb-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ca2eb-105">Parameters</span></span>  
 `failure`  
 <span data-ttu-id="ca2eb-106">[in] Uma da [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) valores, que indica o tipo de falha para o qual agir.</span><span class="sxs-lookup"><span data-stu-id="ca2eb-106">[in] One of the [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) values, indicating the type of failure for which to take action.</span></span>  
  
 `action`  
 <span data-ttu-id="ca2eb-107">[in] Uma da [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) valores, que indica a ação a ser executada quando ocorre uma falha.</span><span class="sxs-lookup"><span data-stu-id="ca2eb-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action to be taken when a failure occurs.</span></span> <span data-ttu-id="ca2eb-108">Para obter uma lista de valores com suporte, consulte a seção comentários.</span><span class="sxs-lookup"><span data-stu-id="ca2eb-108">For a list of supported values, see the Remarks section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ca2eb-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="ca2eb-109">Return Value</span></span>  
  
|<span data-ttu-id="ca2eb-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ca2eb-110">HRESULT</span></span>|<span data-ttu-id="ca2eb-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="ca2eb-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ca2eb-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="ca2eb-112">S_OK</span></span>|<span data-ttu-id="ca2eb-113">`SetActionOnFailure`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="ca2eb-113">`SetActionOnFailure` returned successfully.</span></span>|  
|<span data-ttu-id="ca2eb-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ca2eb-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ca2eb-115">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="ca2eb-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ca2eb-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ca2eb-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ca2eb-117">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="ca2eb-117">The call timed out.</span></span>|  
|<span data-ttu-id="ca2eb-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ca2eb-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ca2eb-119">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="ca2eb-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ca2eb-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ca2eb-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ca2eb-121">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="ca2eb-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ca2eb-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ca2eb-122">E_FAIL</span></span>|<span data-ttu-id="ca2eb-123">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="ca2eb-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ca2eb-124">Depois que um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="ca2eb-124">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ca2eb-125">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ca2eb-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="ca2eb-126">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="ca2eb-126">E_INVALIDARG</span></span>|<span data-ttu-id="ca2eb-127">Uma ação de política não pode ser definida para a operação especificada ou uma ação de política inválida foi especificada para a operação.</span><span class="sxs-lookup"><span data-stu-id="ca2eb-127">A policy action cannot be set for the specified operation, or an invalid policy action was specified for the operation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ca2eb-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="ca2eb-128">Remarks</span></span>  
 <span data-ttu-id="ca2eb-129">Por padrão, o CLR lança uma exceção quando ele não consegue alocar um recurso, como memória.</span><span class="sxs-lookup"><span data-stu-id="ca2eb-129">By default, the CLR throws an exception when it fails to allocate a resource such as memory.</span></span> <span data-ttu-id="ca2eb-130">`SetActionOnFailure`permite que o host substituir esse comportamento especificando a ação a tomar em caso de falha da política.</span><span class="sxs-lookup"><span data-stu-id="ca2eb-130">`SetActionOnFailure` allows the host to override this behavior by specifying the policy action to take upon failure.</span></span> <span data-ttu-id="ca2eb-131">A tabela a seguir mostra as combinações de [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) e [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) valores que têm suporte.</span><span class="sxs-lookup"><span data-stu-id="ca2eb-131">The following table shows the combinations of [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) and [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values that are supported.</span></span> <span data-ttu-id="ca2eb-132">(O prefixo FAIL_ é omitido do [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) valores.)</span><span class="sxs-lookup"><span data-stu-id="ca2eb-132">(The FAIL_ prefix is omitted from [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) values.)</span></span>  
  
||<span data-ttu-id="ca2eb-133">NonCriticalResource</span><span class="sxs-lookup"><span data-stu-id="ca2eb-133">NonCriticalResource</span></span>|<span data-ttu-id="ca2eb-134">CriticalResource</span><span class="sxs-lookup"><span data-stu-id="ca2eb-134">CriticalResource</span></span>|<span data-ttu-id="ca2eb-135">FatalRuntime</span><span class="sxs-lookup"><span data-stu-id="ca2eb-135">FatalRuntime</span></span>|<span data-ttu-id="ca2eb-136">OrphanedLock</span><span class="sxs-lookup"><span data-stu-id="ca2eb-136">OrphanedLock</span></span>|<span data-ttu-id="ca2eb-137">StackOverflow</span><span class="sxs-lookup"><span data-stu-id="ca2eb-137">StackOverflow</span></span>|<span data-ttu-id="ca2eb-138">AccessViolation</span><span class="sxs-lookup"><span data-stu-id="ca2eb-138">AccessViolation</span></span>|<span data-ttu-id="ca2eb-139">CodeContract</span><span class="sxs-lookup"><span data-stu-id="ca2eb-139">CodeContract</span></span>|  
|-|-------------------------|----------------------|------------------|------------------|-------------------|---------------------|------------------|  
|`eNoAction`|<span data-ttu-id="ca2eb-140">X</span><span class="sxs-lookup"><span data-stu-id="ca2eb-140">X</span></span>|<span data-ttu-id="ca2eb-141">X</span><span class="sxs-lookup"><span data-stu-id="ca2eb-141">X</span></span>||||<span data-ttu-id="ca2eb-142">N/D</span><span class="sxs-lookup"><span data-stu-id="ca2eb-142">N/A</span></span>||  
|<span data-ttu-id="ca2eb-143">eThrowException</span><span class="sxs-lookup"><span data-stu-id="ca2eb-143">eThrowException</span></span>|<span data-ttu-id="ca2eb-144">X</span><span class="sxs-lookup"><span data-stu-id="ca2eb-144">X</span></span>|<span data-ttu-id="ca2eb-145">X</span><span class="sxs-lookup"><span data-stu-id="ca2eb-145">X</span></span>||||<span data-ttu-id="ca2eb-146">N/D</span><span class="sxs-lookup"><span data-stu-id="ca2eb-146">N/A</span></span>||  
|`eAbortThread`|<span data-ttu-id="ca2eb-147">X</span><span class="sxs-lookup"><span data-stu-id="ca2eb-147">X</span></span>|<span data-ttu-id="ca2eb-148">X</span><span class="sxs-lookup"><span data-stu-id="ca2eb-148">X</span></span>||||<span data-ttu-id="ca2eb-149">N/D</span><span class="sxs-lookup"><span data-stu-id="ca2eb-149">N/A</span></span>|<span data-ttu-id="ca2eb-150">X</span><span class="sxs-lookup"><span data-stu-id="ca2eb-150">X</span></span>|  
|`eRudeAbortThread`|<span data-ttu-id="ca2eb-151">X</span><span class="sxs-lookup"><span data-stu-id="ca2eb-151">X</span></span>|<span data-ttu-id="ca2eb-152">X</span><span class="sxs-lookup"><span data-stu-id="ca2eb-152">X</span></span>||||<span data-ttu-id="ca2eb-153">N/D</span><span class="sxs-lookup"><span data-stu-id="ca2eb-153">N/A</span></span>|<span data-ttu-id="ca2eb-154">X</span><span class="sxs-lookup"><span data-stu-id="ca2eb-154">X</span></span>|  
|`eUnloadAppDomain`|<span data-ttu-id="ca2eb-155">X</span><span class="sxs-lookup"><span data-stu-id="ca2eb-155">X</span></span>|<span data-ttu-id="ca2eb-156">X</span><span class="sxs-lookup"><span data-stu-id="ca2eb-156">X</span></span>||<span data-ttu-id="ca2eb-157">X</span><span class="sxs-lookup"><span data-stu-id="ca2eb-157">X</span></span>||<span data-ttu-id="ca2eb-158">N/D</span><span class="sxs-lookup"><span data-stu-id="ca2eb-158">N/A</span></span>|<span data-ttu-id="ca2eb-159">X</span><span class="sxs-lookup"><span data-stu-id="ca2eb-159">X</span></span>|  
|`eRudeUnloadAppDomain`|<span data-ttu-id="ca2eb-160">X</span><span class="sxs-lookup"><span data-stu-id="ca2eb-160">X</span></span>|<span data-ttu-id="ca2eb-161">X</span><span class="sxs-lookup"><span data-stu-id="ca2eb-161">X</span></span>||<span data-ttu-id="ca2eb-162">X</span><span class="sxs-lookup"><span data-stu-id="ca2eb-162">X</span></span>|<span data-ttu-id="ca2eb-163">X</span><span class="sxs-lookup"><span data-stu-id="ca2eb-163">X</span></span>|<span data-ttu-id="ca2eb-164">N/D</span><span class="sxs-lookup"><span data-stu-id="ca2eb-164">N/A</span></span>|<span data-ttu-id="ca2eb-165">X</span><span class="sxs-lookup"><span data-stu-id="ca2eb-165">X</span></span>|  
|`eExitProcess`|<span data-ttu-id="ca2eb-166">X</span><span class="sxs-lookup"><span data-stu-id="ca2eb-166">X</span></span>|<span data-ttu-id="ca2eb-167">X</span><span class="sxs-lookup"><span data-stu-id="ca2eb-167">X</span></span>||<span data-ttu-id="ca2eb-168">X</span><span class="sxs-lookup"><span data-stu-id="ca2eb-168">X</span></span>|<span data-ttu-id="ca2eb-169">X</span><span class="sxs-lookup"><span data-stu-id="ca2eb-169">X</span></span>|<span data-ttu-id="ca2eb-170">N/D</span><span class="sxs-lookup"><span data-stu-id="ca2eb-170">N/A</span></span>|<span data-ttu-id="ca2eb-171">X</span><span class="sxs-lookup"><span data-stu-id="ca2eb-171">X</span></span>|  
|<span data-ttu-id="ca2eb-172">eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="ca2eb-172">eFastExitProcess</span></span>|<span data-ttu-id="ca2eb-173">X</span><span class="sxs-lookup"><span data-stu-id="ca2eb-173">X</span></span>|<span data-ttu-id="ca2eb-174">X</span><span class="sxs-lookup"><span data-stu-id="ca2eb-174">X</span></span>||<span data-ttu-id="ca2eb-175">X</span><span class="sxs-lookup"><span data-stu-id="ca2eb-175">X</span></span>|<span data-ttu-id="ca2eb-176">X</span><span class="sxs-lookup"><span data-stu-id="ca2eb-176">X</span></span>|<span data-ttu-id="ca2eb-177">N/D</span><span class="sxs-lookup"><span data-stu-id="ca2eb-177">N/A</span></span>||  
|`eRudeExitProcess`|<span data-ttu-id="ca2eb-178">X</span><span class="sxs-lookup"><span data-stu-id="ca2eb-178">X</span></span>|<span data-ttu-id="ca2eb-179">X</span><span class="sxs-lookup"><span data-stu-id="ca2eb-179">X</span></span>|<span data-ttu-id="ca2eb-180">X</span><span class="sxs-lookup"><span data-stu-id="ca2eb-180">X</span></span>|<span data-ttu-id="ca2eb-181">X</span><span class="sxs-lookup"><span data-stu-id="ca2eb-181">X</span></span>|<span data-ttu-id="ca2eb-182">X</span><span class="sxs-lookup"><span data-stu-id="ca2eb-182">X</span></span>|<span data-ttu-id="ca2eb-183">N/D</span><span class="sxs-lookup"><span data-stu-id="ca2eb-183">N/A</span></span>||  
|`eDisableRuntime`|<span data-ttu-id="ca2eb-184">X</span><span class="sxs-lookup"><span data-stu-id="ca2eb-184">X</span></span>|<span data-ttu-id="ca2eb-185">X</span><span class="sxs-lookup"><span data-stu-id="ca2eb-185">X</span></span>|<span data-ttu-id="ca2eb-186">X</span><span class="sxs-lookup"><span data-stu-id="ca2eb-186">X</span></span>|<span data-ttu-id="ca2eb-187">X</span><span class="sxs-lookup"><span data-stu-id="ca2eb-187">X</span></span>|<span data-ttu-id="ca2eb-188">X</span><span class="sxs-lookup"><span data-stu-id="ca2eb-188">X</span></span>|<span data-ttu-id="ca2eb-189">N/D</span><span class="sxs-lookup"><span data-stu-id="ca2eb-189">N/A</span></span>||  
  
## <a name="requirements"></a><span data-ttu-id="ca2eb-190">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ca2eb-190">Requirements</span></span>  
 <span data-ttu-id="ca2eb-191">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca2eb-191">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca2eb-192">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ca2eb-192">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ca2eb-193">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="ca2eb-193">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ca2eb-194">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca2eb-194">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca2eb-195">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ca2eb-195">See Also</span></span>  
 [<span data-ttu-id="ca2eb-196">Enumeração EClrFailure</span><span class="sxs-lookup"><span data-stu-id="ca2eb-196">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [<span data-ttu-id="ca2eb-197">Enumeração EPolicyAction</span><span class="sxs-lookup"><span data-stu-id="ca2eb-197">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="ca2eb-198">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="ca2eb-198">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="ca2eb-199">Interface ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="ca2eb-199">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
