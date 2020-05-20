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
ms.openlocfilehash: fb2ecc80f272a3fc9b63b20c5956e7a28f117784
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703467"
---
# <a name="iclrpolicymanagersetactiononfailure-method"></a><span data-ttu-id="0a072-102">Método ICLRPolicyManager::SetActionOnFailure</span><span class="sxs-lookup"><span data-stu-id="0a072-102">ICLRPolicyManager::SetActionOnFailure Method</span></span>
<span data-ttu-id="0a072-103">Especifica a ação de política que o Common Language Runtime (CLR) deve executar quando a falha especificada ocorrer.</span><span class="sxs-lookup"><span data-stu-id="0a072-103">Specifies the policy action the common language runtime (CLR) should take when the specified failure occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a072-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0a072-104">Syntax</span></span>  
  
```cpp  
HRESULT SetActionOnFailure (  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0a072-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0a072-105">Parameters</span></span>  
 `failure`  
 <span data-ttu-id="0a072-106">no Um dos valores de [EClrFailure](eclrfailure-enumeration.md) , indicando o tipo de falha para a qual executar a ação.</span><span class="sxs-lookup"><span data-stu-id="0a072-106">[in] One of the [EClrFailure](eclrfailure-enumeration.md) values, indicating the type of failure for which to take action.</span></span>  
  
 `action`  
 <span data-ttu-id="0a072-107">no Um dos valores de [EPolicyAction](epolicyaction-enumeration.md) , indicando a ação a ser executada quando ocorrer uma falha.</span><span class="sxs-lookup"><span data-stu-id="0a072-107">[in] One of the [EPolicyAction](epolicyaction-enumeration.md) values, indicating the action to be taken when a failure occurs.</span></span> <span data-ttu-id="0a072-108">Para obter uma lista de valores com suporte, consulte a seção comentários.</span><span class="sxs-lookup"><span data-stu-id="0a072-108">For a list of supported values, see the Remarks section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0a072-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="0a072-109">Return Value</span></span>  
  
|<span data-ttu-id="0a072-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0a072-110">HRESULT</span></span>|<span data-ttu-id="0a072-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="0a072-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0a072-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="0a072-112">S_OK</span></span>|<span data-ttu-id="0a072-113">`SetActionOnFailure`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="0a072-113">`SetActionOnFailure` returned successfully.</span></span>|  
|<span data-ttu-id="0a072-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0a072-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0a072-115">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="0a072-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0a072-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0a072-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0a072-117">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="0a072-117">The call timed out.</span></span>|  
|<span data-ttu-id="0a072-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0a072-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0a072-119">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="0a072-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0a072-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0a072-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0a072-121">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="0a072-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0a072-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0a072-122">E_FAIL</span></span>|<span data-ttu-id="0a072-123">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="0a072-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0a072-124">Depois que um método retorna E_FAIL, o CLR não pode mais ser usado no processo.</span><span class="sxs-lookup"><span data-stu-id="0a072-124">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0a072-125">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0a072-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0a072-126">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="0a072-126">E_INVALIDARG</span></span>|<span data-ttu-id="0a072-127">Uma ação de política não pode ser definida para a operação especificada ou uma ação de política inválida foi especificada para a operação.</span><span class="sxs-lookup"><span data-stu-id="0a072-127">A policy action cannot be set for the specified operation, or an invalid policy action was specified for the operation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0a072-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="0a072-128">Remarks</span></span>  
 <span data-ttu-id="0a072-129">Por padrão, o CLR gera uma exceção quando ele falha ao alocar um recurso, como memória.</span><span class="sxs-lookup"><span data-stu-id="0a072-129">By default, the CLR throws an exception when it fails to allocate a resource such as memory.</span></span> <span data-ttu-id="0a072-130">`SetActionOnFailure`permite que o host Substitua esse comportamento especificando a ação da política a ser tomada após a falha.</span><span class="sxs-lookup"><span data-stu-id="0a072-130">`SetActionOnFailure` allows the host to override this behavior by specifying the policy action to take upon failure.</span></span> <span data-ttu-id="0a072-131">A tabela a seguir mostra as combinações de valores [EClrFailure](eclrfailure-enumeration.md) e [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) com suporte.</span><span class="sxs-lookup"><span data-stu-id="0a072-131">The following table shows the combinations of [EClrFailure](eclrfailure-enumeration.md) and [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values that are supported.</span></span> <span data-ttu-id="0a072-132">(O prefixo de FAIL_ é omitido dos valores de [EClrFailure](eclrfailure-enumeration.md) .)</span><span class="sxs-lookup"><span data-stu-id="0a072-132">(The FAIL_ prefix is omitted from [EClrFailure](eclrfailure-enumeration.md) values.)</span></span>  
  
||<span data-ttu-id="0a072-133">NonCriticalResource</span><span class="sxs-lookup"><span data-stu-id="0a072-133">NonCriticalResource</span></span>|<span data-ttu-id="0a072-134">CriticalResource</span><span class="sxs-lookup"><span data-stu-id="0a072-134">CriticalResource</span></span>|<span data-ttu-id="0a072-135">FatalRuntime</span><span class="sxs-lookup"><span data-stu-id="0a072-135">FatalRuntime</span></span>|<span data-ttu-id="0a072-136">OrphanedLock</span><span class="sxs-lookup"><span data-stu-id="0a072-136">OrphanedLock</span></span>|<span data-ttu-id="0a072-137">StackOverflow</span><span class="sxs-lookup"><span data-stu-id="0a072-137">StackOverflow</span></span>|<span data-ttu-id="0a072-138">AccessViolation</span><span class="sxs-lookup"><span data-stu-id="0a072-138">AccessViolation</span></span>|<span data-ttu-id="0a072-139">CodeContract</span><span class="sxs-lookup"><span data-stu-id="0a072-139">CodeContract</span></span>|  
|-|-------------------------|----------------------|------------------|------------------|-------------------|---------------------|------------------|  
|`eNoAction`|<span data-ttu-id="0a072-140">X</span><span class="sxs-lookup"><span data-stu-id="0a072-140">X</span></span>|<span data-ttu-id="0a072-141">X</span><span class="sxs-lookup"><span data-stu-id="0a072-141">X</span></span>||||<span data-ttu-id="0a072-142">N/D</span><span class="sxs-lookup"><span data-stu-id="0a072-142">N/A</span></span>||  
|<span data-ttu-id="0a072-143">eThrowException</span><span class="sxs-lookup"><span data-stu-id="0a072-143">eThrowException</span></span>|<span data-ttu-id="0a072-144">X</span><span class="sxs-lookup"><span data-stu-id="0a072-144">X</span></span>|<span data-ttu-id="0a072-145">X</span><span class="sxs-lookup"><span data-stu-id="0a072-145">X</span></span>||||<span data-ttu-id="0a072-146">N/D</span><span class="sxs-lookup"><span data-stu-id="0a072-146">N/A</span></span>||  
|`eAbortThread`|<span data-ttu-id="0a072-147">X</span><span class="sxs-lookup"><span data-stu-id="0a072-147">X</span></span>|<span data-ttu-id="0a072-148">X</span><span class="sxs-lookup"><span data-stu-id="0a072-148">X</span></span>||||<span data-ttu-id="0a072-149">N/D</span><span class="sxs-lookup"><span data-stu-id="0a072-149">N/A</span></span>|<span data-ttu-id="0a072-150">X</span><span class="sxs-lookup"><span data-stu-id="0a072-150">X</span></span>|  
|`eRudeAbortThread`|<span data-ttu-id="0a072-151">X</span><span class="sxs-lookup"><span data-stu-id="0a072-151">X</span></span>|<span data-ttu-id="0a072-152">X</span><span class="sxs-lookup"><span data-stu-id="0a072-152">X</span></span>||||<span data-ttu-id="0a072-153">N/D</span><span class="sxs-lookup"><span data-stu-id="0a072-153">N/A</span></span>|<span data-ttu-id="0a072-154">X</span><span class="sxs-lookup"><span data-stu-id="0a072-154">X</span></span>|  
|`eUnloadAppDomain`|<span data-ttu-id="0a072-155">X</span><span class="sxs-lookup"><span data-stu-id="0a072-155">X</span></span>|<span data-ttu-id="0a072-156">X</span><span class="sxs-lookup"><span data-stu-id="0a072-156">X</span></span>||<span data-ttu-id="0a072-157">X</span><span class="sxs-lookup"><span data-stu-id="0a072-157">X</span></span>||<span data-ttu-id="0a072-158">N/D</span><span class="sxs-lookup"><span data-stu-id="0a072-158">N/A</span></span>|<span data-ttu-id="0a072-159">X</span><span class="sxs-lookup"><span data-stu-id="0a072-159">X</span></span>|  
|`eRudeUnloadAppDomain`|<span data-ttu-id="0a072-160">X</span><span class="sxs-lookup"><span data-stu-id="0a072-160">X</span></span>|<span data-ttu-id="0a072-161">X</span><span class="sxs-lookup"><span data-stu-id="0a072-161">X</span></span>||<span data-ttu-id="0a072-162">X</span><span class="sxs-lookup"><span data-stu-id="0a072-162">X</span></span>|<span data-ttu-id="0a072-163">X</span><span class="sxs-lookup"><span data-stu-id="0a072-163">X</span></span>|<span data-ttu-id="0a072-164">N/D</span><span class="sxs-lookup"><span data-stu-id="0a072-164">N/A</span></span>|<span data-ttu-id="0a072-165">X</span><span class="sxs-lookup"><span data-stu-id="0a072-165">X</span></span>|  
|`eExitProcess`|<span data-ttu-id="0a072-166">X</span><span class="sxs-lookup"><span data-stu-id="0a072-166">X</span></span>|<span data-ttu-id="0a072-167">X</span><span class="sxs-lookup"><span data-stu-id="0a072-167">X</span></span>||<span data-ttu-id="0a072-168">X</span><span class="sxs-lookup"><span data-stu-id="0a072-168">X</span></span>|<span data-ttu-id="0a072-169">X</span><span class="sxs-lookup"><span data-stu-id="0a072-169">X</span></span>|<span data-ttu-id="0a072-170">N/D</span><span class="sxs-lookup"><span data-stu-id="0a072-170">N/A</span></span>|<span data-ttu-id="0a072-171">X</span><span class="sxs-lookup"><span data-stu-id="0a072-171">X</span></span>|  
|<span data-ttu-id="0a072-172">eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="0a072-172">eFastExitProcess</span></span>|<span data-ttu-id="0a072-173">X</span><span class="sxs-lookup"><span data-stu-id="0a072-173">X</span></span>|<span data-ttu-id="0a072-174">X</span><span class="sxs-lookup"><span data-stu-id="0a072-174">X</span></span>||<span data-ttu-id="0a072-175">X</span><span class="sxs-lookup"><span data-stu-id="0a072-175">X</span></span>|<span data-ttu-id="0a072-176">X</span><span class="sxs-lookup"><span data-stu-id="0a072-176">X</span></span>|<span data-ttu-id="0a072-177">N/D</span><span class="sxs-lookup"><span data-stu-id="0a072-177">N/A</span></span>||  
|`eRudeExitProcess`|<span data-ttu-id="0a072-178">X</span><span class="sxs-lookup"><span data-stu-id="0a072-178">X</span></span>|<span data-ttu-id="0a072-179">X</span><span class="sxs-lookup"><span data-stu-id="0a072-179">X</span></span>|<span data-ttu-id="0a072-180">X</span><span class="sxs-lookup"><span data-stu-id="0a072-180">X</span></span>|<span data-ttu-id="0a072-181">X</span><span class="sxs-lookup"><span data-stu-id="0a072-181">X</span></span>|<span data-ttu-id="0a072-182">X</span><span class="sxs-lookup"><span data-stu-id="0a072-182">X</span></span>|<span data-ttu-id="0a072-183">N/D</span><span class="sxs-lookup"><span data-stu-id="0a072-183">N/A</span></span>||  
|`eDisableRuntime`|<span data-ttu-id="0a072-184">X</span><span class="sxs-lookup"><span data-stu-id="0a072-184">X</span></span>|<span data-ttu-id="0a072-185">X</span><span class="sxs-lookup"><span data-stu-id="0a072-185">X</span></span>|<span data-ttu-id="0a072-186">X</span><span class="sxs-lookup"><span data-stu-id="0a072-186">X</span></span>|<span data-ttu-id="0a072-187">X</span><span class="sxs-lookup"><span data-stu-id="0a072-187">X</span></span>|<span data-ttu-id="0a072-188">X</span><span class="sxs-lookup"><span data-stu-id="0a072-188">X</span></span>|<span data-ttu-id="0a072-189">N/D</span><span class="sxs-lookup"><span data-stu-id="0a072-189">N/A</span></span>||  
  
## <a name="requirements"></a><span data-ttu-id="0a072-190">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0a072-190">Requirements</span></span>  
 <span data-ttu-id="0a072-191">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a072-191">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a072-192">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0a072-192">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0a072-193">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0a072-193">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0a072-194">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a072-194">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a072-195">Confira também</span><span class="sxs-lookup"><span data-stu-id="0a072-195">See also</span></span>

- [<span data-ttu-id="0a072-196">Enumeração EClrFailure</span><span class="sxs-lookup"><span data-stu-id="0a072-196">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="0a072-197">Enumeração EPolicyAction</span><span class="sxs-lookup"><span data-stu-id="0a072-197">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="0a072-198">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="0a072-198">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="0a072-199">Interface ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="0a072-199">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
