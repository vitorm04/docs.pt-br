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
ms.openlocfilehash: cc1d16a2d57fea27c1c26fc55fbbfa9b74c25495
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435832"
---
# <a name="iclrpolicymanagersetactionontimeout-method"></a><span data-ttu-id="526b5-102">Método ICLRPolicyManager::SetActionOnTimeout</span><span class="sxs-lookup"><span data-stu-id="526b5-102">ICLRPolicyManager::SetActionOnTimeout Method</span></span>
<span data-ttu-id="526b5-103">Especifica a ação de política, que o common language runtime (CLR) deve ser executada quando a operação especificada expire.</span><span class="sxs-lookup"><span data-stu-id="526b5-103">Specifies the policy action the common language runtime (CLR) should take when the specified operation times out.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="526b5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="526b5-104">Syntax</span></span>  
  
```  
HRESULT SetActionOnTimeout (  
    [in] EClrOperation operation,  
    [in] EPolicyAction action  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="526b5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="526b5-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="526b5-106">[in] Uma da [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) valores, indicando que a operação para o qual especificar a ação de tempo limite.</span><span class="sxs-lookup"><span data-stu-id="526b5-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the operation for which to specify the timeout action.</span></span> <span data-ttu-id="526b5-107">Há suporte para os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="526b5-107">The following values are supported:</span></span>  
  
-   <span data-ttu-id="526b5-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="526b5-108">OPR_AppDomainUnload</span></span>  
  
-   <span data-ttu-id="526b5-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="526b5-109">OPR_ProcessExit</span></span>  
  
-   <span data-ttu-id="526b5-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="526b5-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
-   <span data-ttu-id="526b5-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="526b5-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `action`  
 <span data-ttu-id="526b5-112">[in] Uma da [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) valores, que indica a ação a ser tomada quando a operação de tempo limite da política.</span><span class="sxs-lookup"><span data-stu-id="526b5-112">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the policy action to be taken when the operation times out.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="526b5-113">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="526b5-113">Return Value</span></span>  
  
|<span data-ttu-id="526b5-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="526b5-114">HRESULT</span></span>|<span data-ttu-id="526b5-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="526b5-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="526b5-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="526b5-116">S_OK</span></span>|<span data-ttu-id="526b5-117">`SetActionOnTimeout` retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="526b5-117">`SetActionOnTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="526b5-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="526b5-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="526b5-119">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="526b5-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="526b5-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="526b5-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="526b5-121">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="526b5-121">The call timed out.</span></span>|  
|<span data-ttu-id="526b5-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="526b5-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="526b5-123">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="526b5-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="526b5-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="526b5-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="526b5-125">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="526b5-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="526b5-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="526b5-126">E_FAIL</span></span>|<span data-ttu-id="526b5-127">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="526b5-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="526b5-128">Depois que um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="526b5-128">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="526b5-129">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="526b5-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="526b5-130">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="526b5-130">E_INVALIDARG</span></span>|<span data-ttu-id="526b5-131">Não é possível definir um tempo limite especificado `operation`, ou um valor inválido foi fornecido para `operation`.</span><span class="sxs-lookup"><span data-stu-id="526b5-131">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="526b5-132">Comentários</span><span class="sxs-lookup"><span data-stu-id="526b5-132">Remarks</span></span>  
 <span data-ttu-id="526b5-133">O valor de tempo limite pode ser o tempo de limite padrão definido pelo CLR ou um valor especificado pelo host em uma chamada para o [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="526b5-133">The timeout value can be either the default timeout set by the CLR, or a value specified by the host in a call to the [ICLRPolicyManager::SetTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) method.</span></span>  
  
 <span data-ttu-id="526b5-134">Nem todos os valores da política de ação podem ser especificados como o comportamento de tempo limite para operações de CLR.</span><span class="sxs-lookup"><span data-stu-id="526b5-134">Not all policy action values can be specified as the timeout behavior for CLR operations.</span></span> <span data-ttu-id="526b5-135">`SetActionOnTimeout` normalmente é usado somente para escalonar o comportamento.</span><span class="sxs-lookup"><span data-stu-id="526b5-135">`SetActionOnTimeout` is typically used only to escalate behavior.</span></span> <span data-ttu-id="526b5-136">Por exemplo, um host pode especificar que anulações de thread se tornar educado anulações de thread, mas não é possível especificar o oposto.</span><span class="sxs-lookup"><span data-stu-id="526b5-136">For example, a host can specify that thread aborts be turned into rude thread aborts, but cannot specify the opposite.</span></span> <span data-ttu-id="526b5-137">A tabela a seguir descreve o válido `action` valores para válido `operation` valores.</span><span class="sxs-lookup"><span data-stu-id="526b5-137">The table below describes the valid `action` values for valid `operation` values.</span></span>  
  
|<span data-ttu-id="526b5-138">Valor para `operation`</span><span class="sxs-lookup"><span data-stu-id="526b5-138">Value for `operation`</span></span>|<span data-ttu-id="526b5-139">Valores válidos para `action`</span><span class="sxs-lookup"><span data-stu-id="526b5-139">Valid values for `action`</span></span>|  
|---------------------------|-------------------------------|  
|<span data-ttu-id="526b5-140">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="526b5-140">OPR_ThreadRudeAbortInNonCriticalRegion</span></span><br /><br /> <span data-ttu-id="526b5-141">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="526b5-141">OPR_ThreadRudeAbortInCriticalRegion</span></span>|<span data-ttu-id="526b5-142">-eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="526b5-142">-   eRudeAbortThread</span></span><br /><span data-ttu-id="526b5-143">-eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="526b5-143">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="526b5-144">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="526b5-144">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="526b5-145">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="526b5-145">-   eExitProcess</span></span><br /><span data-ttu-id="526b5-146">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="526b5-146">-   eFastExitProcess</span></span><br /><span data-ttu-id="526b5-147">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="526b5-147">-   eRudeExitProcess</span></span><br /><span data-ttu-id="526b5-148">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="526b5-148">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="526b5-149">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="526b5-149">OPR_AppDomainUnload</span></span>|<span data-ttu-id="526b5-150">-eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="526b5-150">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="526b5-151">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="526b5-151">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="526b5-152">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="526b5-152">-   eExitProcess</span></span><br /><span data-ttu-id="526b5-153">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="526b5-153">-   eFastExitProcess</span></span><br /><span data-ttu-id="526b5-154">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="526b5-154">-   eRudeExitProcess</span></span><br /><span data-ttu-id="526b5-155">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="526b5-155">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="526b5-156">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="526b5-156">OPR_ProcessExit</span></span>|<span data-ttu-id="526b5-157">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="526b5-157">-   eExitProcess</span></span><br /><span data-ttu-id="526b5-158">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="526b5-158">-   eFastExitProcess</span></span><br /><span data-ttu-id="526b5-159">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="526b5-159">-   eRudeExitProcess</span></span><br /><span data-ttu-id="526b5-160">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="526b5-160">-   eDisableRuntime</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="526b5-161">Requisitos</span><span class="sxs-lookup"><span data-stu-id="526b5-161">Requirements</span></span>  
 <span data-ttu-id="526b5-162">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="526b5-162">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="526b5-163">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="526b5-163">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="526b5-164">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="526b5-164">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="526b5-165">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="526b5-165">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="526b5-166">Consulte também</span><span class="sxs-lookup"><span data-stu-id="526b5-166">See Also</span></span>  
 [<span data-ttu-id="526b5-167">Enumeração EClrOperation</span><span class="sxs-lookup"><span data-stu-id="526b5-167">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="526b5-168">Enumeração EPolicyAction</span><span class="sxs-lookup"><span data-stu-id="526b5-168">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="526b5-169">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="526b5-169">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="526b5-170">Interface ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="526b5-170">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
