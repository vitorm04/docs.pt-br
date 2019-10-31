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
ms.openlocfilehash: 9ef906ed5e8a6985c084741bf06b683da79c546e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140795"
---
# <a name="iclrpolicymanagersetactionontimeout-method"></a><span data-ttu-id="f668b-102">Método ICLRPolicyManager::SetActionOnTimeout</span><span class="sxs-lookup"><span data-stu-id="f668b-102">ICLRPolicyManager::SetActionOnTimeout Method</span></span>
<span data-ttu-id="f668b-103">Especifica a ação de política que o Common Language Runtime (CLR) deve executar quando a operação especificada atingir o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="f668b-103">Specifies the policy action the common language runtime (CLR) should take when the specified operation times out.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f668b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f668b-104">Syntax</span></span>  
  
```cpp  
HRESULT SetActionOnTimeout (  
    [in] EClrOperation operation,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f668b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f668b-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="f668b-106">no Um dos valores de [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) , que indica a operação para a qual especificar a ação de tempo limite.</span><span class="sxs-lookup"><span data-stu-id="f668b-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the operation for which to specify the timeout action.</span></span> <span data-ttu-id="f668b-107">Há suporte para os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="f668b-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="f668b-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="f668b-108">OPR_AppDomainUnload</span></span>  
  
- <span data-ttu-id="f668b-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="f668b-109">OPR_ProcessExit</span></span>  
  
- <span data-ttu-id="f668b-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="f668b-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
- <span data-ttu-id="f668b-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="f668b-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `action`  
 <span data-ttu-id="f668b-112">no Um dos valores de [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) , indicando a ação da política a ser executada quando a operação atingir o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="f668b-112">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the policy action to be taken when the operation times out.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f668b-113">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="f668b-113">Return Value</span></span>  
  
|<span data-ttu-id="f668b-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f668b-114">HRESULT</span></span>|<span data-ttu-id="f668b-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="f668b-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f668b-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="f668b-116">S_OK</span></span>|<span data-ttu-id="f668b-117">`SetActionOnTimeout` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="f668b-117">`SetActionOnTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="f668b-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f668b-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f668b-119">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="f668b-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f668b-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f668b-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f668b-121">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="f668b-121">The call timed out.</span></span>|  
|<span data-ttu-id="f668b-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f668b-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f668b-123">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="f668b-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f668b-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f668b-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f668b-125">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="f668b-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f668b-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f668b-126">E_FAIL</span></span>|<span data-ttu-id="f668b-127">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="f668b-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f668b-128">Depois que um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="f668b-128">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f668b-129">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f668b-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="f668b-130">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="f668b-130">E_INVALIDARG</span></span>|<span data-ttu-id="f668b-131">Não é possível definir um tempo limite para o `operation`especificado ou um valor inválido foi fornecido para `operation`.</span><span class="sxs-lookup"><span data-stu-id="f668b-131">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f668b-132">Comentários</span><span class="sxs-lookup"><span data-stu-id="f668b-132">Remarks</span></span>  
 <span data-ttu-id="f668b-133">O valor de tempo limite pode ser o tempo limite padrão definido pelo CLR ou um valor especificado pelo host em uma chamada para o método [ICLRPolicyManager:: SetTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) .</span><span class="sxs-lookup"><span data-stu-id="f668b-133">The timeout value can be either the default timeout set by the CLR, or a value specified by the host in a call to the [ICLRPolicyManager::SetTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) method.</span></span>  
  
 <span data-ttu-id="f668b-134">Nem todos os valores de ação de política podem ser especificados como o comportamento de tempo limite para operações de CLR.</span><span class="sxs-lookup"><span data-stu-id="f668b-134">Not all policy action values can be specified as the timeout behavior for CLR operations.</span></span> <span data-ttu-id="f668b-135">`SetActionOnTimeout` normalmente é usado apenas para escalonar o comportamento.</span><span class="sxs-lookup"><span data-stu-id="f668b-135">`SetActionOnTimeout` is typically used only to escalate behavior.</span></span> <span data-ttu-id="f668b-136">Por exemplo, um host pode especificar que as anulações de thread sejam transformadas em anulações de thread rudes, mas não podem especificar o oposto.</span><span class="sxs-lookup"><span data-stu-id="f668b-136">For example, a host can specify that thread aborts be turned into rude thread aborts, but cannot specify the opposite.</span></span> <span data-ttu-id="f668b-137">A tabela a seguir descreve os valores de `action` válidos para valores de `operation` válidos.</span><span class="sxs-lookup"><span data-stu-id="f668b-137">The table below describes the valid `action` values for valid `operation` values.</span></span>  
  
|<span data-ttu-id="f668b-138">Valor para `operation`</span><span class="sxs-lookup"><span data-stu-id="f668b-138">Value for `operation`</span></span>|<span data-ttu-id="f668b-139">Valores válidos para `action`</span><span class="sxs-lookup"><span data-stu-id="f668b-139">Valid values for `action`</span></span>|  
|---------------------------|-------------------------------|  
|<span data-ttu-id="f668b-140">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="f668b-140">OPR_ThreadRudeAbortInNonCriticalRegion</span></span><br /><br /> <span data-ttu-id="f668b-141">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="f668b-141">OPR_ThreadRudeAbortInCriticalRegion</span></span>|<span data-ttu-id="f668b-142">- eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="f668b-142">-   eRudeAbortThread</span></span><br /><span data-ttu-id="f668b-143">- eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="f668b-143">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="f668b-144">- eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="f668b-144">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="f668b-145">- eExitProcess</span><span class="sxs-lookup"><span data-stu-id="f668b-145">-   eExitProcess</span></span><br /><span data-ttu-id="f668b-146">- eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="f668b-146">-   eFastExitProcess</span></span><br /><span data-ttu-id="f668b-147">- eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="f668b-147">-   eRudeExitProcess</span></span><br /><span data-ttu-id="f668b-148">- eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="f668b-148">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="f668b-149">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="f668b-149">OPR_AppDomainUnload</span></span>|<span data-ttu-id="f668b-150">- eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="f668b-150">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="f668b-151">- eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="f668b-151">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="f668b-152">- eExitProcess</span><span class="sxs-lookup"><span data-stu-id="f668b-152">-   eExitProcess</span></span><br /><span data-ttu-id="f668b-153">- eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="f668b-153">-   eFastExitProcess</span></span><br /><span data-ttu-id="f668b-154">- eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="f668b-154">-   eRudeExitProcess</span></span><br /><span data-ttu-id="f668b-155">- eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="f668b-155">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="f668b-156">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="f668b-156">OPR_ProcessExit</span></span>|<span data-ttu-id="f668b-157">- eExitProcess</span><span class="sxs-lookup"><span data-stu-id="f668b-157">-   eExitProcess</span></span><br /><span data-ttu-id="f668b-158">- eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="f668b-158">-   eFastExitProcess</span></span><br /><span data-ttu-id="f668b-159">- eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="f668b-159">-   eRudeExitProcess</span></span><br /><span data-ttu-id="f668b-160">- eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="f668b-160">-   eDisableRuntime</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f668b-161">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f668b-161">Requirements</span></span>  
 <span data-ttu-id="f668b-162">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f668b-162">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f668b-163">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f668b-163">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f668b-164">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f668b-164">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f668b-165">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f668b-165">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f668b-166">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f668b-166">See also</span></span>

- [<span data-ttu-id="f668b-167">Enumeração EClrOperation</span><span class="sxs-lookup"><span data-stu-id="f668b-167">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="f668b-168">Enumeração EPolicyAction</span><span class="sxs-lookup"><span data-stu-id="f668b-168">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="f668b-169">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="f668b-169">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="f668b-170">Interface ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="f668b-170">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
