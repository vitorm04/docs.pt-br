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
ms.workload: dotnet
ms.openlocfilehash: 4440b36485ed900b5e64adcead2525dbb7d5206e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrpolicymanagersetactiononfailure-method"></a><span data-ttu-id="bfd69-102">Método ICLRPolicyManager::SetActionOnFailure</span><span class="sxs-lookup"><span data-stu-id="bfd69-102">ICLRPolicyManager::SetActionOnFailure Method</span></span>
<span data-ttu-id="bfd69-103">Especifica a ação de política, que o common language runtime (CLR) deve ser executada quando ocorre a falha especificada.</span><span class="sxs-lookup"><span data-stu-id="bfd69-103">Specifies the policy action the common language runtime (CLR) should take when the specified failure occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bfd69-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bfd69-104">Syntax</span></span>  
  
```  
HRESULT SetActionOnFailure (  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bfd69-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bfd69-105">Parameters</span></span>  
 `failure`  
 <span data-ttu-id="bfd69-106">[in] Uma da [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) valores, que indica o tipo de falha para o qual agir.</span><span class="sxs-lookup"><span data-stu-id="bfd69-106">[in] One of the [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) values, indicating the type of failure for which to take action.</span></span>  
  
 `action`  
 <span data-ttu-id="bfd69-107">[in] Uma da [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) valores, que indica a ação a ser executada quando ocorre uma falha.</span><span class="sxs-lookup"><span data-stu-id="bfd69-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action to be taken when a failure occurs.</span></span> <span data-ttu-id="bfd69-108">Para obter uma lista de valores com suporte, consulte a seção comentários.</span><span class="sxs-lookup"><span data-stu-id="bfd69-108">For a list of supported values, see the Remarks section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bfd69-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="bfd69-109">Return Value</span></span>  
  
|<span data-ttu-id="bfd69-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bfd69-110">HRESULT</span></span>|<span data-ttu-id="bfd69-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="bfd69-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bfd69-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="bfd69-112">S_OK</span></span>|<span data-ttu-id="bfd69-113">`SetActionOnFailure`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="bfd69-113">`SetActionOnFailure` returned successfully.</span></span>|  
|<span data-ttu-id="bfd69-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bfd69-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bfd69-115">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="bfd69-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="bfd69-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bfd69-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bfd69-117">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="bfd69-117">The call timed out.</span></span>|  
|<span data-ttu-id="bfd69-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bfd69-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bfd69-119">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="bfd69-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bfd69-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bfd69-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bfd69-121">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="bfd69-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bfd69-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bfd69-122">E_FAIL</span></span>|<span data-ttu-id="bfd69-123">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="bfd69-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bfd69-124">Depois que um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="bfd69-124">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bfd69-125">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="bfd69-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="bfd69-126">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="bfd69-126">E_INVALIDARG</span></span>|<span data-ttu-id="bfd69-127">Uma ação de política não pode ser definida para a operação especificada ou uma ação de política inválida foi especificada para a operação.</span><span class="sxs-lookup"><span data-stu-id="bfd69-127">A policy action cannot be set for the specified operation, or an invalid policy action was specified for the operation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bfd69-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="bfd69-128">Remarks</span></span>  
 <span data-ttu-id="bfd69-129">Por padrão, o CLR lança uma exceção quando ele não consegue alocar um recurso, como memória.</span><span class="sxs-lookup"><span data-stu-id="bfd69-129">By default, the CLR throws an exception when it fails to allocate a resource such as memory.</span></span> <span data-ttu-id="bfd69-130">`SetActionOnFailure`permite que o host substituir esse comportamento especificando a ação a tomar em caso de falha da política.</span><span class="sxs-lookup"><span data-stu-id="bfd69-130">`SetActionOnFailure` allows the host to override this behavior by specifying the policy action to take upon failure.</span></span> <span data-ttu-id="bfd69-131">A tabela a seguir mostra as combinações de [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) e [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) valores que têm suporte.</span><span class="sxs-lookup"><span data-stu-id="bfd69-131">The following table shows the combinations of [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) and [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values that are supported.</span></span> <span data-ttu-id="bfd69-132">(O prefixo FAIL_ é omitido do [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) valores.)</span><span class="sxs-lookup"><span data-stu-id="bfd69-132">(The FAIL_ prefix is omitted from [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) values.)</span></span>  
  
||<span data-ttu-id="bfd69-133">NonCriticalResource</span><span class="sxs-lookup"><span data-stu-id="bfd69-133">NonCriticalResource</span></span>|<span data-ttu-id="bfd69-134">CriticalResource</span><span class="sxs-lookup"><span data-stu-id="bfd69-134">CriticalResource</span></span>|<span data-ttu-id="bfd69-135">FatalRuntime</span><span class="sxs-lookup"><span data-stu-id="bfd69-135">FatalRuntime</span></span>|<span data-ttu-id="bfd69-136">OrphanedLock</span><span class="sxs-lookup"><span data-stu-id="bfd69-136">OrphanedLock</span></span>|<span data-ttu-id="bfd69-137">StackOverflow</span><span class="sxs-lookup"><span data-stu-id="bfd69-137">StackOverflow</span></span>|<span data-ttu-id="bfd69-138">AccessViolation</span><span class="sxs-lookup"><span data-stu-id="bfd69-138">AccessViolation</span></span>|<span data-ttu-id="bfd69-139">CodeContract</span><span class="sxs-lookup"><span data-stu-id="bfd69-139">CodeContract</span></span>|  
|-|-------------------------|----------------------|------------------|------------------|-------------------|---------------------|------------------|  
|`eNoAction`|<span data-ttu-id="bfd69-140">X</span><span class="sxs-lookup"><span data-stu-id="bfd69-140">X</span></span>|<span data-ttu-id="bfd69-141">X</span><span class="sxs-lookup"><span data-stu-id="bfd69-141">X</span></span>||||<span data-ttu-id="bfd69-142">N/D</span><span class="sxs-lookup"><span data-stu-id="bfd69-142">N/A</span></span>||  
|<span data-ttu-id="bfd69-143">eThrowException</span><span class="sxs-lookup"><span data-stu-id="bfd69-143">eThrowException</span></span>|<span data-ttu-id="bfd69-144">X</span><span class="sxs-lookup"><span data-stu-id="bfd69-144">X</span></span>|<span data-ttu-id="bfd69-145">X</span><span class="sxs-lookup"><span data-stu-id="bfd69-145">X</span></span>||||<span data-ttu-id="bfd69-146">N/D</span><span class="sxs-lookup"><span data-stu-id="bfd69-146">N/A</span></span>||  
|`eAbortThread`|<span data-ttu-id="bfd69-147">X</span><span class="sxs-lookup"><span data-stu-id="bfd69-147">X</span></span>|<span data-ttu-id="bfd69-148">X</span><span class="sxs-lookup"><span data-stu-id="bfd69-148">X</span></span>||||<span data-ttu-id="bfd69-149">N/D</span><span class="sxs-lookup"><span data-stu-id="bfd69-149">N/A</span></span>|<span data-ttu-id="bfd69-150">X</span><span class="sxs-lookup"><span data-stu-id="bfd69-150">X</span></span>|  
|`eRudeAbortThread`|<span data-ttu-id="bfd69-151">X</span><span class="sxs-lookup"><span data-stu-id="bfd69-151">X</span></span>|<span data-ttu-id="bfd69-152">X</span><span class="sxs-lookup"><span data-stu-id="bfd69-152">X</span></span>||||<span data-ttu-id="bfd69-153">N/D</span><span class="sxs-lookup"><span data-stu-id="bfd69-153">N/A</span></span>|<span data-ttu-id="bfd69-154">X</span><span class="sxs-lookup"><span data-stu-id="bfd69-154">X</span></span>|  
|`eUnloadAppDomain`|<span data-ttu-id="bfd69-155">X</span><span class="sxs-lookup"><span data-stu-id="bfd69-155">X</span></span>|<span data-ttu-id="bfd69-156">X</span><span class="sxs-lookup"><span data-stu-id="bfd69-156">X</span></span>||<span data-ttu-id="bfd69-157">X</span><span class="sxs-lookup"><span data-stu-id="bfd69-157">X</span></span>||<span data-ttu-id="bfd69-158">N/D</span><span class="sxs-lookup"><span data-stu-id="bfd69-158">N/A</span></span>|<span data-ttu-id="bfd69-159">X</span><span class="sxs-lookup"><span data-stu-id="bfd69-159">X</span></span>|  
|`eRudeUnloadAppDomain`|<span data-ttu-id="bfd69-160">X</span><span class="sxs-lookup"><span data-stu-id="bfd69-160">X</span></span>|<span data-ttu-id="bfd69-161">X</span><span class="sxs-lookup"><span data-stu-id="bfd69-161">X</span></span>||<span data-ttu-id="bfd69-162">X</span><span class="sxs-lookup"><span data-stu-id="bfd69-162">X</span></span>|<span data-ttu-id="bfd69-163">X</span><span class="sxs-lookup"><span data-stu-id="bfd69-163">X</span></span>|<span data-ttu-id="bfd69-164">N/D</span><span class="sxs-lookup"><span data-stu-id="bfd69-164">N/A</span></span>|<span data-ttu-id="bfd69-165">X</span><span class="sxs-lookup"><span data-stu-id="bfd69-165">X</span></span>|  
|`eExitProcess`|<span data-ttu-id="bfd69-166">X</span><span class="sxs-lookup"><span data-stu-id="bfd69-166">X</span></span>|<span data-ttu-id="bfd69-167">X</span><span class="sxs-lookup"><span data-stu-id="bfd69-167">X</span></span>||<span data-ttu-id="bfd69-168">X</span><span class="sxs-lookup"><span data-stu-id="bfd69-168">X</span></span>|<span data-ttu-id="bfd69-169">X</span><span class="sxs-lookup"><span data-stu-id="bfd69-169">X</span></span>|<span data-ttu-id="bfd69-170">N/D</span><span class="sxs-lookup"><span data-stu-id="bfd69-170">N/A</span></span>|<span data-ttu-id="bfd69-171">X</span><span class="sxs-lookup"><span data-stu-id="bfd69-171">X</span></span>|  
|<span data-ttu-id="bfd69-172">eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="bfd69-172">eFastExitProcess</span></span>|<span data-ttu-id="bfd69-173">X</span><span class="sxs-lookup"><span data-stu-id="bfd69-173">X</span></span>|<span data-ttu-id="bfd69-174">X</span><span class="sxs-lookup"><span data-stu-id="bfd69-174">X</span></span>||<span data-ttu-id="bfd69-175">X</span><span class="sxs-lookup"><span data-stu-id="bfd69-175">X</span></span>|<span data-ttu-id="bfd69-176">X</span><span class="sxs-lookup"><span data-stu-id="bfd69-176">X</span></span>|<span data-ttu-id="bfd69-177">N/D</span><span class="sxs-lookup"><span data-stu-id="bfd69-177">N/A</span></span>||  
|`eRudeExitProcess`|<span data-ttu-id="bfd69-178">X</span><span class="sxs-lookup"><span data-stu-id="bfd69-178">X</span></span>|<span data-ttu-id="bfd69-179">X</span><span class="sxs-lookup"><span data-stu-id="bfd69-179">X</span></span>|<span data-ttu-id="bfd69-180">X</span><span class="sxs-lookup"><span data-stu-id="bfd69-180">X</span></span>|<span data-ttu-id="bfd69-181">X</span><span class="sxs-lookup"><span data-stu-id="bfd69-181">X</span></span>|<span data-ttu-id="bfd69-182">X</span><span class="sxs-lookup"><span data-stu-id="bfd69-182">X</span></span>|<span data-ttu-id="bfd69-183">N/D</span><span class="sxs-lookup"><span data-stu-id="bfd69-183">N/A</span></span>||  
|`eDisableRuntime`|<span data-ttu-id="bfd69-184">X</span><span class="sxs-lookup"><span data-stu-id="bfd69-184">X</span></span>|<span data-ttu-id="bfd69-185">X</span><span class="sxs-lookup"><span data-stu-id="bfd69-185">X</span></span>|<span data-ttu-id="bfd69-186">X</span><span class="sxs-lookup"><span data-stu-id="bfd69-186">X</span></span>|<span data-ttu-id="bfd69-187">X</span><span class="sxs-lookup"><span data-stu-id="bfd69-187">X</span></span>|<span data-ttu-id="bfd69-188">X</span><span class="sxs-lookup"><span data-stu-id="bfd69-188">X</span></span>|<span data-ttu-id="bfd69-189">N/D</span><span class="sxs-lookup"><span data-stu-id="bfd69-189">N/A</span></span>||  
  
## <a name="requirements"></a><span data-ttu-id="bfd69-190">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bfd69-190">Requirements</span></span>  
 <span data-ttu-id="bfd69-191">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bfd69-191">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bfd69-192">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bfd69-192">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bfd69-193">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="bfd69-193">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bfd69-194">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bfd69-194">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfd69-195">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bfd69-195">See Also</span></span>  
 [<span data-ttu-id="bfd69-196">Enumeração EClrFailure</span><span class="sxs-lookup"><span data-stu-id="bfd69-196">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [<span data-ttu-id="bfd69-197">Enumeração EPolicyAction</span><span class="sxs-lookup"><span data-stu-id="bfd69-197">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="bfd69-198">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="bfd69-198">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="bfd69-199">Interface ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="bfd69-199">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
