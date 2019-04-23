---
title: Método ICLRPolicyManager::SetActionOnFailure
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetActionOnFailure
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetActionOnFailure
helpviewer_keywords:
- SetActionOnFailure method [.NET Framework hosting]
- ICLRPolicyManager::SetActionOnFailure method [.NET Framework hosting]
ms.assetid: 4664033f-db97-4388-b988-2ec470796e58
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 34d9e1a3747ecf3dffc925d7883599b773dd51f1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59117424"
---
# <a name="iclrpolicymanagersetactiononfailure-method"></a><span data-ttu-id="505bd-102">Método ICLRPolicyManager::SetActionOnFailure</span><span class="sxs-lookup"><span data-stu-id="505bd-102">ICLRPolicyManager::SetActionOnFailure Method</span></span>
<span data-ttu-id="505bd-103">Especifica a ação de política, que o common language runtime (CLR) deve tomar quando ocorre a falha especificada.</span><span class="sxs-lookup"><span data-stu-id="505bd-103">Specifies the policy action the common language runtime (CLR) should take when the specified failure occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="505bd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="505bd-104">Syntax</span></span>  
  
```  
HRESULT SetActionOnFailure (  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="505bd-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="505bd-105">Parameters</span></span>  
 `failure`  
 <span data-ttu-id="505bd-106">[in] Um dos [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) valores, que indica o tipo de falha para o qual agir.</span><span class="sxs-lookup"><span data-stu-id="505bd-106">[in] One of the [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) values, indicating the type of failure for which to take action.</span></span>  
  
 `action`  
 <span data-ttu-id="505bd-107">[in] Um dos [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) valores, que indica a ação a ser executada quando ocorre uma falha.</span><span class="sxs-lookup"><span data-stu-id="505bd-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action to be taken when a failure occurs.</span></span> <span data-ttu-id="505bd-108">Para obter uma lista de valores com suporte, consulte a seção comentários.</span><span class="sxs-lookup"><span data-stu-id="505bd-108">For a list of supported values, see the Remarks section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="505bd-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="505bd-109">Return Value</span></span>  
  
|<span data-ttu-id="505bd-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="505bd-110">HRESULT</span></span>|<span data-ttu-id="505bd-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="505bd-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="505bd-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="505bd-112">S_OK</span></span>|<span data-ttu-id="505bd-113">`SetActionOnFailure` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="505bd-113">`SetActionOnFailure` returned successfully.</span></span>|  
|<span data-ttu-id="505bd-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="505bd-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="505bd-115">O CLR não tenha sido carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="505bd-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="505bd-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="505bd-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="505bd-117">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="505bd-117">The call timed out.</span></span>|  
|<span data-ttu-id="505bd-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="505bd-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="505bd-119">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="505bd-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="505bd-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="505bd-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="505bd-121">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="505bd-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="505bd-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="505bd-122">E_FAIL</span></span>|<span data-ttu-id="505bd-123">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="505bd-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="505bd-124">Depois que um método retorna E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="505bd-124">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="505bd-125">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="505bd-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="505bd-126">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="505bd-126">E_INVALIDARG</span></span>|<span data-ttu-id="505bd-127">Uma ação de política não pode ser definida para a operação especificada ou uma ação de política inválida foi especificada para a operação.</span><span class="sxs-lookup"><span data-stu-id="505bd-127">A policy action cannot be set for the specified operation, or an invalid policy action was specified for the operation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="505bd-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="505bd-128">Remarks</span></span>  
 <span data-ttu-id="505bd-129">Por padrão, o CLR lança uma exceção quando ele falha ao alocar um recurso como a memória.</span><span class="sxs-lookup"><span data-stu-id="505bd-129">By default, the CLR throws an exception when it fails to allocate a resource such as memory.</span></span> <span data-ttu-id="505bd-130">`SetActionOnFailure` permite que o host substituir esse comportamento especificando a ação de política a tomar em caso de falha.</span><span class="sxs-lookup"><span data-stu-id="505bd-130">`SetActionOnFailure` allows the host to override this behavior by specifying the policy action to take upon failure.</span></span> <span data-ttu-id="505bd-131">A tabela a seguir mostra as combinações de [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) e [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) valores que têm suporte.</span><span class="sxs-lookup"><span data-stu-id="505bd-131">The following table shows the combinations of [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) and [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values that are supported.</span></span> <span data-ttu-id="505bd-132">(O prefixo FAIL_ for omitido da [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) valores.)</span><span class="sxs-lookup"><span data-stu-id="505bd-132">(The FAIL_ prefix is omitted from [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) values.)</span></span>  
  
||<span data-ttu-id="505bd-133">NonCriticalResource</span><span class="sxs-lookup"><span data-stu-id="505bd-133">NonCriticalResource</span></span>|<span data-ttu-id="505bd-134">CriticalResource</span><span class="sxs-lookup"><span data-stu-id="505bd-134">CriticalResource</span></span>|<span data-ttu-id="505bd-135">FatalRuntime</span><span class="sxs-lookup"><span data-stu-id="505bd-135">FatalRuntime</span></span>|<span data-ttu-id="505bd-136">OrphanedLock</span><span class="sxs-lookup"><span data-stu-id="505bd-136">OrphanedLock</span></span>|<span data-ttu-id="505bd-137">StackOverflow</span><span class="sxs-lookup"><span data-stu-id="505bd-137">StackOverflow</span></span>|<span data-ttu-id="505bd-138">AccessViolation</span><span class="sxs-lookup"><span data-stu-id="505bd-138">AccessViolation</span></span>|<span data-ttu-id="505bd-139">CodeContract</span><span class="sxs-lookup"><span data-stu-id="505bd-139">CodeContract</span></span>|  
|-|-------------------------|----------------------|------------------|------------------|-------------------|---------------------|------------------|  
|`eNoAction`|<span data-ttu-id="505bd-140">X</span><span class="sxs-lookup"><span data-stu-id="505bd-140">X</span></span>|<span data-ttu-id="505bd-141">X</span><span class="sxs-lookup"><span data-stu-id="505bd-141">X</span></span>||||<span data-ttu-id="505bd-142">N/D</span><span class="sxs-lookup"><span data-stu-id="505bd-142">N/A</span></span>||  
|<span data-ttu-id="505bd-143">eThrowException</span><span class="sxs-lookup"><span data-stu-id="505bd-143">eThrowException</span></span>|<span data-ttu-id="505bd-144">X</span><span class="sxs-lookup"><span data-stu-id="505bd-144">X</span></span>|<span data-ttu-id="505bd-145">X</span><span class="sxs-lookup"><span data-stu-id="505bd-145">X</span></span>||||<span data-ttu-id="505bd-146">N/D</span><span class="sxs-lookup"><span data-stu-id="505bd-146">N/A</span></span>||  
|`eAbortThread`|<span data-ttu-id="505bd-147">X</span><span class="sxs-lookup"><span data-stu-id="505bd-147">X</span></span>|<span data-ttu-id="505bd-148">X</span><span class="sxs-lookup"><span data-stu-id="505bd-148">X</span></span>||||<span data-ttu-id="505bd-149">N/D</span><span class="sxs-lookup"><span data-stu-id="505bd-149">N/A</span></span>|<span data-ttu-id="505bd-150">X</span><span class="sxs-lookup"><span data-stu-id="505bd-150">X</span></span>|  
|`eRudeAbortThread`|<span data-ttu-id="505bd-151">X</span><span class="sxs-lookup"><span data-stu-id="505bd-151">X</span></span>|<span data-ttu-id="505bd-152">X</span><span class="sxs-lookup"><span data-stu-id="505bd-152">X</span></span>||||<span data-ttu-id="505bd-153">N/D</span><span class="sxs-lookup"><span data-stu-id="505bd-153">N/A</span></span>|<span data-ttu-id="505bd-154">X</span><span class="sxs-lookup"><span data-stu-id="505bd-154">X</span></span>|  
|`eUnloadAppDomain`|<span data-ttu-id="505bd-155">X</span><span class="sxs-lookup"><span data-stu-id="505bd-155">X</span></span>|<span data-ttu-id="505bd-156">X</span><span class="sxs-lookup"><span data-stu-id="505bd-156">X</span></span>||<span data-ttu-id="505bd-157">X</span><span class="sxs-lookup"><span data-stu-id="505bd-157">X</span></span>||<span data-ttu-id="505bd-158">N/D</span><span class="sxs-lookup"><span data-stu-id="505bd-158">N/A</span></span>|<span data-ttu-id="505bd-159">X</span><span class="sxs-lookup"><span data-stu-id="505bd-159">X</span></span>|  
|`eRudeUnloadAppDomain`|<span data-ttu-id="505bd-160">X</span><span class="sxs-lookup"><span data-stu-id="505bd-160">X</span></span>|<span data-ttu-id="505bd-161">X</span><span class="sxs-lookup"><span data-stu-id="505bd-161">X</span></span>||<span data-ttu-id="505bd-162">X</span><span class="sxs-lookup"><span data-stu-id="505bd-162">X</span></span>|<span data-ttu-id="505bd-163">X</span><span class="sxs-lookup"><span data-stu-id="505bd-163">X</span></span>|<span data-ttu-id="505bd-164">N/D</span><span class="sxs-lookup"><span data-stu-id="505bd-164">N/A</span></span>|<span data-ttu-id="505bd-165">X</span><span class="sxs-lookup"><span data-stu-id="505bd-165">X</span></span>|  
|`eExitProcess`|<span data-ttu-id="505bd-166">X</span><span class="sxs-lookup"><span data-stu-id="505bd-166">X</span></span>|<span data-ttu-id="505bd-167">X</span><span class="sxs-lookup"><span data-stu-id="505bd-167">X</span></span>||<span data-ttu-id="505bd-168">X</span><span class="sxs-lookup"><span data-stu-id="505bd-168">X</span></span>|<span data-ttu-id="505bd-169">X</span><span class="sxs-lookup"><span data-stu-id="505bd-169">X</span></span>|<span data-ttu-id="505bd-170">N/D</span><span class="sxs-lookup"><span data-stu-id="505bd-170">N/A</span></span>|<span data-ttu-id="505bd-171">X</span><span class="sxs-lookup"><span data-stu-id="505bd-171">X</span></span>|  
|<span data-ttu-id="505bd-172">eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="505bd-172">eFastExitProcess</span></span>|<span data-ttu-id="505bd-173">X</span><span class="sxs-lookup"><span data-stu-id="505bd-173">X</span></span>|<span data-ttu-id="505bd-174">X</span><span class="sxs-lookup"><span data-stu-id="505bd-174">X</span></span>||<span data-ttu-id="505bd-175">X</span><span class="sxs-lookup"><span data-stu-id="505bd-175">X</span></span>|<span data-ttu-id="505bd-176">X</span><span class="sxs-lookup"><span data-stu-id="505bd-176">X</span></span>|<span data-ttu-id="505bd-177">N/D</span><span class="sxs-lookup"><span data-stu-id="505bd-177">N/A</span></span>||  
|`eRudeExitProcess`|<span data-ttu-id="505bd-178">X</span><span class="sxs-lookup"><span data-stu-id="505bd-178">X</span></span>|<span data-ttu-id="505bd-179">X</span><span class="sxs-lookup"><span data-stu-id="505bd-179">X</span></span>|<span data-ttu-id="505bd-180">X</span><span class="sxs-lookup"><span data-stu-id="505bd-180">X</span></span>|<span data-ttu-id="505bd-181">X</span><span class="sxs-lookup"><span data-stu-id="505bd-181">X</span></span>|<span data-ttu-id="505bd-182">X</span><span class="sxs-lookup"><span data-stu-id="505bd-182">X</span></span>|<span data-ttu-id="505bd-183">N/D</span><span class="sxs-lookup"><span data-stu-id="505bd-183">N/A</span></span>||  
|`eDisableRuntime`|<span data-ttu-id="505bd-184">X</span><span class="sxs-lookup"><span data-stu-id="505bd-184">X</span></span>|<span data-ttu-id="505bd-185">X</span><span class="sxs-lookup"><span data-stu-id="505bd-185">X</span></span>|<span data-ttu-id="505bd-186">X</span><span class="sxs-lookup"><span data-stu-id="505bd-186">X</span></span>|<span data-ttu-id="505bd-187">X</span><span class="sxs-lookup"><span data-stu-id="505bd-187">X</span></span>|<span data-ttu-id="505bd-188">X</span><span class="sxs-lookup"><span data-stu-id="505bd-188">X</span></span>|<span data-ttu-id="505bd-189">N/D</span><span class="sxs-lookup"><span data-stu-id="505bd-189">N/A</span></span>||  
  
## <a name="requirements"></a><span data-ttu-id="505bd-190">Requisitos</span><span class="sxs-lookup"><span data-stu-id="505bd-190">Requirements</span></span>  
 <span data-ttu-id="505bd-191">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="505bd-191">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="505bd-192">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="505bd-192">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="505bd-193">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="505bd-193">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="505bd-194">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="505bd-194">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="505bd-195">Consulte também</span><span class="sxs-lookup"><span data-stu-id="505bd-195">See also</span></span>

- [<span data-ttu-id="505bd-196">Enumeração EClrFailure</span><span class="sxs-lookup"><span data-stu-id="505bd-196">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [<span data-ttu-id="505bd-197">Enumeração EPolicyAction</span><span class="sxs-lookup"><span data-stu-id="505bd-197">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="505bd-198">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="505bd-198">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="505bd-199">Interface ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="505bd-199">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
