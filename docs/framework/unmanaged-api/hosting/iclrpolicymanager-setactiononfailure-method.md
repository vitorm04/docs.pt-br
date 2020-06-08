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
ms.openlocfilehash: 727cd82226b9a59c4879ffea5e87f93dd5fe38c9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504102"
---
# <a name="iclrpolicymanagersetactiononfailure-method"></a><span data-ttu-id="801f3-102">Método ICLRPolicyManager::SetActionOnFailure</span><span class="sxs-lookup"><span data-stu-id="801f3-102">ICLRPolicyManager::SetActionOnFailure Method</span></span>
<span data-ttu-id="801f3-103">Especifica a ação de política que o Common Language Runtime (CLR) deve executar quando a falha especificada ocorrer.</span><span class="sxs-lookup"><span data-stu-id="801f3-103">Specifies the policy action the common language runtime (CLR) should take when the specified failure occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="801f3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="801f3-104">Syntax</span></span>  
  
```cpp  
HRESULT SetActionOnFailure (  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="801f3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="801f3-105">Parameters</span></span>  
 `failure`  
 <span data-ttu-id="801f3-106">no Um dos valores de [EClrFailure](eclrfailure-enumeration.md) , indicando o tipo de falha para a qual executar a ação.</span><span class="sxs-lookup"><span data-stu-id="801f3-106">[in] One of the [EClrFailure](eclrfailure-enumeration.md) values, indicating the type of failure for which to take action.</span></span>  
  
 `action`  
 <span data-ttu-id="801f3-107">no Um dos valores de [EPolicyAction](epolicyaction-enumeration.md) , indicando a ação a ser executada quando ocorrer uma falha.</span><span class="sxs-lookup"><span data-stu-id="801f3-107">[in] One of the [EPolicyAction](epolicyaction-enumeration.md) values, indicating the action to be taken when a failure occurs.</span></span> <span data-ttu-id="801f3-108">Para obter uma lista de valores com suporte, consulte a seção comentários.</span><span class="sxs-lookup"><span data-stu-id="801f3-108">For a list of supported values, see the Remarks section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="801f3-109">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="801f3-109">Return Value</span></span>  
  
|<span data-ttu-id="801f3-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="801f3-110">HRESULT</span></span>|<span data-ttu-id="801f3-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="801f3-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="801f3-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="801f3-112">S_OK</span></span>|<span data-ttu-id="801f3-113">`SetActionOnFailure`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="801f3-113">`SetActionOnFailure` returned successfully.</span></span>|  
|<span data-ttu-id="801f3-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="801f3-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="801f3-115">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="801f3-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="801f3-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="801f3-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="801f3-117">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="801f3-117">The call timed out.</span></span>|  
|<span data-ttu-id="801f3-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="801f3-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="801f3-119">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="801f3-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="801f3-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="801f3-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="801f3-121">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="801f3-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="801f3-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="801f3-122">E_FAIL</span></span>|<span data-ttu-id="801f3-123">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="801f3-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="801f3-124">Depois que um método retorna E_FAIL, o CLR não pode mais ser usado no processo.</span><span class="sxs-lookup"><span data-stu-id="801f3-124">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="801f3-125">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="801f3-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="801f3-126">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="801f3-126">E_INVALIDARG</span></span>|<span data-ttu-id="801f3-127">Uma ação de política não pode ser definida para a operação especificada ou uma ação de política inválida foi especificada para a operação.</span><span class="sxs-lookup"><span data-stu-id="801f3-127">A policy action cannot be set for the specified operation, or an invalid policy action was specified for the operation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="801f3-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="801f3-128">Remarks</span></span>  
 <span data-ttu-id="801f3-129">Por padrão, o CLR gera uma exceção quando ele falha ao alocar um recurso, como memória.</span><span class="sxs-lookup"><span data-stu-id="801f3-129">By default, the CLR throws an exception when it fails to allocate a resource such as memory.</span></span> <span data-ttu-id="801f3-130">`SetActionOnFailure`permite que o host Substitua esse comportamento especificando a ação da política a ser tomada após a falha.</span><span class="sxs-lookup"><span data-stu-id="801f3-130">`SetActionOnFailure` allows the host to override this behavior by specifying the policy action to take upon failure.</span></span> <span data-ttu-id="801f3-131">A tabela a seguir mostra as combinações de valores [EClrFailure](eclrfailure-enumeration.md) e [EPolicyAction](epolicyaction-enumeration.md) com suporte.</span><span class="sxs-lookup"><span data-stu-id="801f3-131">The following table shows the combinations of [EClrFailure](eclrfailure-enumeration.md) and [EPolicyAction](epolicyaction-enumeration.md) values that are supported.</span></span> <span data-ttu-id="801f3-132">(O prefixo de FAIL_ é omitido dos valores de [EClrFailure](eclrfailure-enumeration.md) .)</span><span class="sxs-lookup"><span data-stu-id="801f3-132">(The FAIL_ prefix is omitted from [EClrFailure](eclrfailure-enumeration.md) values.)</span></span>  
  
||<span data-ttu-id="801f3-133">NonCriticalResource</span><span class="sxs-lookup"><span data-stu-id="801f3-133">NonCriticalResource</span></span>|<span data-ttu-id="801f3-134">CriticalResource</span><span class="sxs-lookup"><span data-stu-id="801f3-134">CriticalResource</span></span>|<span data-ttu-id="801f3-135">FatalRuntime</span><span class="sxs-lookup"><span data-stu-id="801f3-135">FatalRuntime</span></span>|<span data-ttu-id="801f3-136">OrphanedLock</span><span class="sxs-lookup"><span data-stu-id="801f3-136">OrphanedLock</span></span>|<span data-ttu-id="801f3-137">StackOverflow</span><span class="sxs-lookup"><span data-stu-id="801f3-137">StackOverflow</span></span>|<span data-ttu-id="801f3-138">AccessViolation</span><span class="sxs-lookup"><span data-stu-id="801f3-138">AccessViolation</span></span>|<span data-ttu-id="801f3-139">CodeContract</span><span class="sxs-lookup"><span data-stu-id="801f3-139">CodeContract</span></span>|  
|-|-------------------------|----------------------|------------------|------------------|-------------------|---------------------|------------------|  
|`eNoAction`|<span data-ttu-id="801f3-140">X</span><span class="sxs-lookup"><span data-stu-id="801f3-140">X</span></span>|<span data-ttu-id="801f3-141">X</span><span class="sxs-lookup"><span data-stu-id="801f3-141">X</span></span>||||<span data-ttu-id="801f3-142">N/D</span><span class="sxs-lookup"><span data-stu-id="801f3-142">N/A</span></span>||  
|<span data-ttu-id="801f3-143">eThrowException</span><span class="sxs-lookup"><span data-stu-id="801f3-143">eThrowException</span></span>|<span data-ttu-id="801f3-144">X</span><span class="sxs-lookup"><span data-stu-id="801f3-144">X</span></span>|<span data-ttu-id="801f3-145">X</span><span class="sxs-lookup"><span data-stu-id="801f3-145">X</span></span>||||<span data-ttu-id="801f3-146">N/D</span><span class="sxs-lookup"><span data-stu-id="801f3-146">N/A</span></span>||  
|`eAbortThread`|<span data-ttu-id="801f3-147">X</span><span class="sxs-lookup"><span data-stu-id="801f3-147">X</span></span>|<span data-ttu-id="801f3-148">X</span><span class="sxs-lookup"><span data-stu-id="801f3-148">X</span></span>||||<span data-ttu-id="801f3-149">N/D</span><span class="sxs-lookup"><span data-stu-id="801f3-149">N/A</span></span>|<span data-ttu-id="801f3-150">X</span><span class="sxs-lookup"><span data-stu-id="801f3-150">X</span></span>|  
|`eRudeAbortThread`|<span data-ttu-id="801f3-151">X</span><span class="sxs-lookup"><span data-stu-id="801f3-151">X</span></span>|<span data-ttu-id="801f3-152">X</span><span class="sxs-lookup"><span data-stu-id="801f3-152">X</span></span>||||<span data-ttu-id="801f3-153">N/D</span><span class="sxs-lookup"><span data-stu-id="801f3-153">N/A</span></span>|<span data-ttu-id="801f3-154">X</span><span class="sxs-lookup"><span data-stu-id="801f3-154">X</span></span>|  
|`eUnloadAppDomain`|<span data-ttu-id="801f3-155">X</span><span class="sxs-lookup"><span data-stu-id="801f3-155">X</span></span>|<span data-ttu-id="801f3-156">X</span><span class="sxs-lookup"><span data-stu-id="801f3-156">X</span></span>||<span data-ttu-id="801f3-157">X</span><span class="sxs-lookup"><span data-stu-id="801f3-157">X</span></span>||<span data-ttu-id="801f3-158">N/D</span><span class="sxs-lookup"><span data-stu-id="801f3-158">N/A</span></span>|<span data-ttu-id="801f3-159">X</span><span class="sxs-lookup"><span data-stu-id="801f3-159">X</span></span>|  
|`eRudeUnloadAppDomain`|<span data-ttu-id="801f3-160">X</span><span class="sxs-lookup"><span data-stu-id="801f3-160">X</span></span>|<span data-ttu-id="801f3-161">X</span><span class="sxs-lookup"><span data-stu-id="801f3-161">X</span></span>||<span data-ttu-id="801f3-162">X</span><span class="sxs-lookup"><span data-stu-id="801f3-162">X</span></span>|<span data-ttu-id="801f3-163">X</span><span class="sxs-lookup"><span data-stu-id="801f3-163">X</span></span>|<span data-ttu-id="801f3-164">N/D</span><span class="sxs-lookup"><span data-stu-id="801f3-164">N/A</span></span>|<span data-ttu-id="801f3-165">X</span><span class="sxs-lookup"><span data-stu-id="801f3-165">X</span></span>|  
|`eExitProcess`|<span data-ttu-id="801f3-166">X</span><span class="sxs-lookup"><span data-stu-id="801f3-166">X</span></span>|<span data-ttu-id="801f3-167">X</span><span class="sxs-lookup"><span data-stu-id="801f3-167">X</span></span>||<span data-ttu-id="801f3-168">X</span><span class="sxs-lookup"><span data-stu-id="801f3-168">X</span></span>|<span data-ttu-id="801f3-169">X</span><span class="sxs-lookup"><span data-stu-id="801f3-169">X</span></span>|<span data-ttu-id="801f3-170">N/D</span><span class="sxs-lookup"><span data-stu-id="801f3-170">N/A</span></span>|<span data-ttu-id="801f3-171">X</span><span class="sxs-lookup"><span data-stu-id="801f3-171">X</span></span>|  
|<span data-ttu-id="801f3-172">eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="801f3-172">eFastExitProcess</span></span>|<span data-ttu-id="801f3-173">X</span><span class="sxs-lookup"><span data-stu-id="801f3-173">X</span></span>|<span data-ttu-id="801f3-174">X</span><span class="sxs-lookup"><span data-stu-id="801f3-174">X</span></span>||<span data-ttu-id="801f3-175">X</span><span class="sxs-lookup"><span data-stu-id="801f3-175">X</span></span>|<span data-ttu-id="801f3-176">X</span><span class="sxs-lookup"><span data-stu-id="801f3-176">X</span></span>|<span data-ttu-id="801f3-177">N/D</span><span class="sxs-lookup"><span data-stu-id="801f3-177">N/A</span></span>||  
|`eRudeExitProcess`|<span data-ttu-id="801f3-178">X</span><span class="sxs-lookup"><span data-stu-id="801f3-178">X</span></span>|<span data-ttu-id="801f3-179">X</span><span class="sxs-lookup"><span data-stu-id="801f3-179">X</span></span>|<span data-ttu-id="801f3-180">X</span><span class="sxs-lookup"><span data-stu-id="801f3-180">X</span></span>|<span data-ttu-id="801f3-181">X</span><span class="sxs-lookup"><span data-stu-id="801f3-181">X</span></span>|<span data-ttu-id="801f3-182">X</span><span class="sxs-lookup"><span data-stu-id="801f3-182">X</span></span>|<span data-ttu-id="801f3-183">N/D</span><span class="sxs-lookup"><span data-stu-id="801f3-183">N/A</span></span>||  
|`eDisableRuntime`|<span data-ttu-id="801f3-184">X</span><span class="sxs-lookup"><span data-stu-id="801f3-184">X</span></span>|<span data-ttu-id="801f3-185">X</span><span class="sxs-lookup"><span data-stu-id="801f3-185">X</span></span>|<span data-ttu-id="801f3-186">X</span><span class="sxs-lookup"><span data-stu-id="801f3-186">X</span></span>|<span data-ttu-id="801f3-187">X</span><span class="sxs-lookup"><span data-stu-id="801f3-187">X</span></span>|<span data-ttu-id="801f3-188">X</span><span class="sxs-lookup"><span data-stu-id="801f3-188">X</span></span>|<span data-ttu-id="801f3-189">N/D</span><span class="sxs-lookup"><span data-stu-id="801f3-189">N/A</span></span>||  
  
## <a name="requirements"></a><span data-ttu-id="801f3-190">Requisitos</span><span class="sxs-lookup"><span data-stu-id="801f3-190">Requirements</span></span>  
 <span data-ttu-id="801f3-191">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="801f3-191">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="801f3-192">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="801f3-192">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="801f3-193">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="801f3-193">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="801f3-194">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="801f3-194">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="801f3-195">Confira também</span><span class="sxs-lookup"><span data-stu-id="801f3-195">See also</span></span>

- [<span data-ttu-id="801f3-196">Enumeração EClrFailure</span><span class="sxs-lookup"><span data-stu-id="801f3-196">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="801f3-197">Enumeração EPolicyAction</span><span class="sxs-lookup"><span data-stu-id="801f3-197">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="801f3-198">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="801f3-198">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="801f3-199">Interface ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="801f3-199">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
