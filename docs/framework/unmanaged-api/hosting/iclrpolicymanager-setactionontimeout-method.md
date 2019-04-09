---
title: Método ICLRPolicyManager::SetActionOnTimeout
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetActionOnTimeout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetActionOnTimeout
helpviewer_keywords:
- SetActionOnTimeout method [.NET Framework hosting]
- ICLRPolicyManager::SetActionOnTimeout method [.NET Framework hosting]
ms.assetid: 38439fa1-2b99-4fa8-a6ec-08afc0f83b9c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 30ab869ed6b06f5c9e53d819e20d3307ccc0e8f1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59109922"
---
# <a name="iclrpolicymanagersetactionontimeout-method"></a><span data-ttu-id="3e3a8-102">Método ICLRPolicyManager::SetActionOnTimeout</span><span class="sxs-lookup"><span data-stu-id="3e3a8-102">ICLRPolicyManager::SetActionOnTimeout Method</span></span>
<span data-ttu-id="3e3a8-103">Especifica a ação de política, que o common language runtime (CLR) deve tomar quando a operação especificada expira.</span><span class="sxs-lookup"><span data-stu-id="3e3a8-103">Specifies the policy action the common language runtime (CLR) should take when the specified operation times out.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e3a8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3e3a8-104">Syntax</span></span>  
  
```  
HRESULT SetActionOnTimeout (  
    [in] EClrOperation operation,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3e3a8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3e3a8-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="3e3a8-106">[in] Um dos [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) valores, indicando que a operação para o qual especificar a ação de tempo limite.</span><span class="sxs-lookup"><span data-stu-id="3e3a8-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the operation for which to specify the timeout action.</span></span> <span data-ttu-id="3e3a8-107">Há suporte para os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="3e3a8-107">The following values are supported:</span></span>  
  
-   <span data-ttu-id="3e3a8-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="3e3a8-108">OPR_AppDomainUnload</span></span>  
  
-   <span data-ttu-id="3e3a8-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="3e3a8-109">OPR_ProcessExit</span></span>  
  
-   <span data-ttu-id="3e3a8-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="3e3a8-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
-   <span data-ttu-id="3e3a8-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="3e3a8-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `action`  
 <span data-ttu-id="3e3a8-112">[in] Um dos [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) valores, que indica a ação a ser tomada quando a operação de tempo limite da política.</span><span class="sxs-lookup"><span data-stu-id="3e3a8-112">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the policy action to be taken when the operation times out.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3e3a8-113">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="3e3a8-113">Return Value</span></span>  
  
|<span data-ttu-id="3e3a8-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3e3a8-114">HRESULT</span></span>|<span data-ttu-id="3e3a8-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="3e3a8-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3e3a8-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="3e3a8-116">S_OK</span></span>|`SetActionOnTimeout` <span data-ttu-id="3e3a8-117">retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="3e3a8-117">returned successfully.</span></span>|  
|<span data-ttu-id="3e3a8-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3e3a8-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3e3a8-119">O CLR não tenha sido carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="3e3a8-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3e3a8-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3e3a8-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3e3a8-121">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="3e3a8-121">The call timed out.</span></span>|  
|<span data-ttu-id="3e3a8-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3e3a8-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3e3a8-123">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="3e3a8-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3e3a8-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3e3a8-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3e3a8-125">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="3e3a8-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3e3a8-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3e3a8-126">E_FAIL</span></span>|<span data-ttu-id="3e3a8-127">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="3e3a8-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3e3a8-128">Depois que um método retorna E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="3e3a8-128">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3e3a8-129">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="3e3a8-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="3e3a8-130">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="3e3a8-130">E_INVALIDARG</span></span>|<span data-ttu-id="3e3a8-131">Não é possível definir um tempo limite especificado `operation`, ou um valor inválido foi fornecido para `operation`.</span><span class="sxs-lookup"><span data-stu-id="3e3a8-131">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3e3a8-132">Comentários</span><span class="sxs-lookup"><span data-stu-id="3e3a8-132">Remarks</span></span>  
 <span data-ttu-id="3e3a8-133">O valor de tempo limite pode ser o tempo de limite padrão definido pelo CLR, ou um valor especificado pelo host em uma chamada para o [ICLRPolicyManager:: setTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="3e3a8-133">The timeout value can be either the default timeout set by the CLR, or a value specified by the host in a call to the [ICLRPolicyManager::SetTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) method.</span></span>  
  
 <span data-ttu-id="3e3a8-134">Nem todos os valores de ação de política podem ser especificados como o comportamento de tempo limite para operações de CLR.</span><span class="sxs-lookup"><span data-stu-id="3e3a8-134">Not all policy action values can be specified as the timeout behavior for CLR operations.</span></span> `SetActionOnTimeout` <span data-ttu-id="3e3a8-135">normalmente é usado apenas para escalonar o comportamento.</span><span class="sxs-lookup"><span data-stu-id="3e3a8-135">is typically used only to escalate behavior.</span></span> <span data-ttu-id="3e3a8-136">Por exemplo, um host pode especificar que as anulações de thread ser transformado em rude anulações de thread, mas não é possível especificar o oposto.</span><span class="sxs-lookup"><span data-stu-id="3e3a8-136">For example, a host can specify that thread aborts be turned into rude thread aborts, but cannot specify the opposite.</span></span> <span data-ttu-id="3e3a8-137">A tabela abaixo descreve válidos `action` os valores para válido `operation` valores.</span><span class="sxs-lookup"><span data-stu-id="3e3a8-137">The table below describes the valid `action` values for valid `operation` values.</span></span>  
  
|<span data-ttu-id="3e3a8-138">Valor para</span><span class="sxs-lookup"><span data-stu-id="3e3a8-138">Value for</span></span> `operation`|<span data-ttu-id="3e3a8-139">Valores válidos para</span><span class="sxs-lookup"><span data-stu-id="3e3a8-139">Valid values for</span></span> `action`|  
|---------------------------|-------------------------------|  
|<span data-ttu-id="3e3a8-140">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="3e3a8-140">OPR_ThreadRudeAbortInNonCriticalRegion</span></span><br /><br /> <span data-ttu-id="3e3a8-141">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="3e3a8-141">OPR_ThreadRudeAbortInCriticalRegion</span></span>|<span data-ttu-id="3e3a8-142">-   eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="3e3a8-142">-   eRudeAbortThread</span></span><br /><span data-ttu-id="3e3a8-143">-   eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="3e3a8-143">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="3e3a8-144">-   eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="3e3a8-144">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="3e3a8-145">-   eExitProcess</span><span class="sxs-lookup"><span data-stu-id="3e3a8-145">-   eExitProcess</span></span><br /><span data-ttu-id="3e3a8-146">-   eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="3e3a8-146">-   eFastExitProcess</span></span><br /><span data-ttu-id="3e3a8-147">-   eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="3e3a8-147">-   eRudeExitProcess</span></span><br /><span data-ttu-id="3e3a8-148">-   eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="3e3a8-148">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="3e3a8-149">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="3e3a8-149">OPR_AppDomainUnload</span></span>|<span data-ttu-id="3e3a8-150">-   eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="3e3a8-150">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="3e3a8-151">-   eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="3e3a8-151">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="3e3a8-152">-   eExitProcess</span><span class="sxs-lookup"><span data-stu-id="3e3a8-152">-   eExitProcess</span></span><br /><span data-ttu-id="3e3a8-153">-   eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="3e3a8-153">-   eFastExitProcess</span></span><br /><span data-ttu-id="3e3a8-154">-   eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="3e3a8-154">-   eRudeExitProcess</span></span><br /><span data-ttu-id="3e3a8-155">-   eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="3e3a8-155">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="3e3a8-156">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="3e3a8-156">OPR_ProcessExit</span></span>|<span data-ttu-id="3e3a8-157">-   eExitProcess</span><span class="sxs-lookup"><span data-stu-id="3e3a8-157">-   eExitProcess</span></span><br /><span data-ttu-id="3e3a8-158">-   eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="3e3a8-158">-   eFastExitProcess</span></span><br /><span data-ttu-id="3e3a8-159">-   eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="3e3a8-159">-   eRudeExitProcess</span></span><br /><span data-ttu-id="3e3a8-160">-   eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="3e3a8-160">-   eDisableRuntime</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3e3a8-161">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3e3a8-161">Requirements</span></span>  
 <span data-ttu-id="3e3a8-162">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e3a8-162">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e3a8-163">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3e3a8-163">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3e3a8-164">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="3e3a8-164">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="3e3a8-165">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="3e3a8-165">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3e3a8-166">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3e3a8-166">See also</span></span>

- [<span data-ttu-id="3e3a8-167">Enumeração EClrOperation</span><span class="sxs-lookup"><span data-stu-id="3e3a8-167">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="3e3a8-168">Enumeração EPolicyAction</span><span class="sxs-lookup"><span data-stu-id="3e3a8-168">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="3e3a8-169">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="3e3a8-169">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="3e3a8-170">Interface ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="3e3a8-170">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
