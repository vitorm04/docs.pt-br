---
title: Método ICLRPolicyManager::SetTimeoutAndAction
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetTimeoutAndAction
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetTimeoutAndAction
helpviewer_keywords:
- ICLRPolicyManager::SetTimeoutAndAction method [.NET Framework hosting]
- SetTimeoutAndAction method [.NET Framework hosting]
ms.assetid: 60454f91-d855-4ddf-bb6d-60a02f5eabab
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7ea97084351bdc0a9dbd85d7a6a38a34acffaac8
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57489269"
---
# <a name="iclrpolicymanagersettimeoutandaction-method"></a><span data-ttu-id="7daab-102">Método ICLRPolicyManager::SetTimeoutAndAction</span><span class="sxs-lookup"><span data-stu-id="7daab-102">ICLRPolicyManager::SetTimeoutAndAction Method</span></span>
<span data-ttu-id="7daab-103">Define um valor de tempo limite para a operação especificada e especifica a ação de política, que o common language runtime (CLR) deve tomar quando a operação ocorre.</span><span class="sxs-lookup"><span data-stu-id="7daab-103">Sets a timeout value for the specified operation, and specifies the policy action the common language runtime (CLR) should take when the operation occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7daab-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7daab-104">Syntax</span></span>  
  
```  
HRESULT SetTimeoutAndAction (  
    [in] EClrOperation operation,  
    [in] DWORD dwMilliseconds,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7daab-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7daab-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="7daab-106">[in] Um dos [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) valores, indicando que a operação para o qual definir o tempo limite e a política `action`.</span><span class="sxs-lookup"><span data-stu-id="7daab-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the operation for which to set the timeout and policy `action`.</span></span> <span data-ttu-id="7daab-107">Há suporte para os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="7daab-107">The following values are supported:</span></span>  
  
-   <span data-ttu-id="7daab-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="7daab-108">OPR_AppDomainUnload</span></span>  
  
-   <span data-ttu-id="7daab-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="7daab-109">OPR_ProcessExit</span></span>  
  
-   <span data-ttu-id="7daab-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="7daab-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
-   <span data-ttu-id="7daab-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="7daab-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `dwMilliseconds`  
 <span data-ttu-id="7daab-112">[in] O novo valor de tempo limite, em milissegundos.</span><span class="sxs-lookup"><span data-stu-id="7daab-112">[in] The new timeout value, in milliseconds.</span></span> <span data-ttu-id="7daab-113">Um valor infinito causas `operation` nunca para atingir o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="7daab-113">A value of INFINITE causes `operation` never to time out.</span></span>  
  
 `action`  
 <span data-ttu-id="7daab-114">[in] Um dos [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) valores, indicando que o CLR deve tomar quando a ação da política `operation` ocorre.</span><span class="sxs-lookup"><span data-stu-id="7daab-114">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the policy action that the CLR should take when `operation` occurs.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7daab-115">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="7daab-115">Return Value</span></span>  
  
|<span data-ttu-id="7daab-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7daab-116">HRESULT</span></span>|<span data-ttu-id="7daab-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="7daab-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7daab-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="7daab-118">S_OK</span></span>|<span data-ttu-id="7daab-119">`SetTimeoutAndAction` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="7daab-119">`SetTimeoutAndAction` returned successfully.</span></span>|  
|<span data-ttu-id="7daab-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7daab-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7daab-121">O CLR não tenha sido carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="7daab-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7daab-122">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7daab-122">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7daab-123">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="7daab-123">The call timed out.</span></span>|  
|<span data-ttu-id="7daab-124">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7daab-124">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7daab-125">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="7daab-125">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7daab-126">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7daab-126">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7daab-127">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="7daab-127">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7daab-128">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7daab-128">E_FAIL</span></span>|<span data-ttu-id="7daab-129">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="7daab-129">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7daab-130">Depois que um método retorna E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="7daab-130">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7daab-131">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7daab-131">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="7daab-132">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="7daab-132">E_INVALIDARG</span></span>|<span data-ttu-id="7daab-133">Não é possível definir um tempo limite especificado `operation`, ou um valor inválido foi fornecido para `action`.</span><span class="sxs-lookup"><span data-stu-id="7daab-133">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `action`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7daab-134">Comentários</span><span class="sxs-lookup"><span data-stu-id="7daab-134">Remarks</span></span>  
 <span data-ttu-id="7daab-135">`SetTimeoutAndAction` encapsula os recursos da [ICLRPolicyManager:: setTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) e [ICLRPolicyManager:: Setactionontimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) métodos e pode ser chamado no lugar sequenciais chamadas para esses dois métodos.</span><span class="sxs-lookup"><span data-stu-id="7daab-135">`SetTimeoutAndAction` encapsulates the capabilities of the [ICLRPolicyManager::SetTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) and [ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) methods, and can be called in place of sequential calls to these two methods.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7daab-136">Nem todos os valores de ação de política podem ser especificados como o comportamento de tempo limite para operações de CLR.</span><span class="sxs-lookup"><span data-stu-id="7daab-136">Not all policy action values can be specified as the timeout behavior for CLR operations.</span></span> <span data-ttu-id="7daab-137">Consulte as seções de comentários dos tópicos para esses dois métodos para os valores válidos.</span><span class="sxs-lookup"><span data-stu-id="7daab-137">See the Remarks sections of the topics for these two methods for valid values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7daab-138">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7daab-138">Requirements</span></span>  
 <span data-ttu-id="7daab-139">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7daab-139">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7daab-140">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7daab-140">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7daab-141">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="7daab-141">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7daab-142">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7daab-142">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7daab-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7daab-143">See also</span></span>
- [<span data-ttu-id="7daab-144">Enumeração EClrOperation</span><span class="sxs-lookup"><span data-stu-id="7daab-144">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="7daab-145">Enumeração EPolicyAction</span><span class="sxs-lookup"><span data-stu-id="7daab-145">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="7daab-146">Interface ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="7daab-146">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="7daab-147">Método SetActionOnTimeout</span><span class="sxs-lookup"><span data-stu-id="7daab-147">SetActionOnTimeout Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md)
- [<span data-ttu-id="7daab-148">ICLRPolicyManager::SetTimeoutAndAction</span><span class="sxs-lookup"><span data-stu-id="7daab-148">ICLRPolicyManager::SetTimeoutAndAction</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeoutandaction-method.md)
