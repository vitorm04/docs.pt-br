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
ms.openlocfilehash: 3a58664a7dc81059214246b53cf967b50cd61063
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140746"
---
# <a name="iclrpolicymanagersettimeoutandaction-method"></a><span data-ttu-id="b87b2-102">Método ICLRPolicyManager::SetTimeoutAndAction</span><span class="sxs-lookup"><span data-stu-id="b87b2-102">ICLRPolicyManager::SetTimeoutAndAction Method</span></span>
<span data-ttu-id="b87b2-103">Define um valor de tempo limite para a operação especificada e especifica a ação de política que o Common Language Runtime (CLR) deve executar quando a operação ocorre.</span><span class="sxs-lookup"><span data-stu-id="b87b2-103">Sets a timeout value for the specified operation, and specifies the policy action the common language runtime (CLR) should take when the operation occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b87b2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b87b2-104">Syntax</span></span>  
  
```cpp  
HRESULT SetTimeoutAndAction (  
    [in] EClrOperation operation,  
    [in] DWORD dwMilliseconds,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b87b2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b87b2-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="b87b2-106">no Um dos valores de [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) , indicando a operação para a qual definir o tempo limite e a política `action`.</span><span class="sxs-lookup"><span data-stu-id="b87b2-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the operation for which to set the timeout and policy `action`.</span></span> <span data-ttu-id="b87b2-107">Há suporte para os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="b87b2-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="b87b2-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="b87b2-108">OPR_AppDomainUnload</span></span>  
  
- <span data-ttu-id="b87b2-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="b87b2-109">OPR_ProcessExit</span></span>  
  
- <span data-ttu-id="b87b2-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="b87b2-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
- <span data-ttu-id="b87b2-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="b87b2-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `dwMilliseconds`  
 <span data-ttu-id="b87b2-112">no O novo valor de tempo limite, em milissegundos.</span><span class="sxs-lookup"><span data-stu-id="b87b2-112">[in] The new timeout value, in milliseconds.</span></span> <span data-ttu-id="b87b2-113">Um valor infinito causa `operation` nunca atingir o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="b87b2-113">A value of INFINITE causes `operation` never to time out.</span></span>  
  
 `action`  
 <span data-ttu-id="b87b2-114">no Um dos valores de [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) , indicando a ação de política que o CLR deve executar quando `operation` ocorre.</span><span class="sxs-lookup"><span data-stu-id="b87b2-114">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the policy action that the CLR should take when `operation` occurs.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b87b2-115">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="b87b2-115">Return Value</span></span>  
  
|<span data-ttu-id="b87b2-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b87b2-116">HRESULT</span></span>|<span data-ttu-id="b87b2-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="b87b2-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b87b2-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="b87b2-118">S_OK</span></span>|<span data-ttu-id="b87b2-119">`SetTimeoutAndAction` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="b87b2-119">`SetTimeoutAndAction` returned successfully.</span></span>|  
|<span data-ttu-id="b87b2-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b87b2-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b87b2-121">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="b87b2-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b87b2-122">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b87b2-122">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b87b2-123">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="b87b2-123">The call timed out.</span></span>|  
|<span data-ttu-id="b87b2-124">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b87b2-124">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b87b2-125">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="b87b2-125">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b87b2-126">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b87b2-126">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b87b2-127">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="b87b2-127">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b87b2-128">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b87b2-128">E_FAIL</span></span>|<span data-ttu-id="b87b2-129">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="b87b2-129">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b87b2-130">Depois que um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="b87b2-130">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b87b2-131">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b87b2-131">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="b87b2-132">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="b87b2-132">E_INVALIDARG</span></span>|<span data-ttu-id="b87b2-133">Não é possível definir um tempo limite para o `operation`especificado ou um valor inválido foi fornecido para `action`.</span><span class="sxs-lookup"><span data-stu-id="b87b2-133">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `action`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b87b2-134">Comentários</span><span class="sxs-lookup"><span data-stu-id="b87b2-134">Remarks</span></span>  
 <span data-ttu-id="b87b2-135">`SetTimeoutAndAction` encapsula os recursos dos métodos [ICLRPolicyManager:: SetTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) e [ICLRPolicyManager:: SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) e pode ser chamado no lugar de chamadas sequenciais para esses dois métodos.</span><span class="sxs-lookup"><span data-stu-id="b87b2-135">`SetTimeoutAndAction` encapsulates the capabilities of the [ICLRPolicyManager::SetTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) and [ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) methods, and can be called in place of sequential calls to these two methods.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b87b2-136">Nem todos os valores de ação de política podem ser especificados como o comportamento de tempo limite para operações de CLR.</span><span class="sxs-lookup"><span data-stu-id="b87b2-136">Not all policy action values can be specified as the timeout behavior for CLR operations.</span></span> <span data-ttu-id="b87b2-137">Consulte as seções comentários dos tópicos para esses dois métodos para obter os valores válidos.</span><span class="sxs-lookup"><span data-stu-id="b87b2-137">See the Remarks sections of the topics for these two methods for valid values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b87b2-138">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b87b2-138">Requirements</span></span>  
 <span data-ttu-id="b87b2-139">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b87b2-139">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b87b2-140">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b87b2-140">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b87b2-141">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b87b2-141">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b87b2-142">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b87b2-142">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b87b2-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b87b2-143">See also</span></span>

- [<span data-ttu-id="b87b2-144">Enumeração EClrOperation</span><span class="sxs-lookup"><span data-stu-id="b87b2-144">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="b87b2-145">Enumeração EPolicyAction</span><span class="sxs-lookup"><span data-stu-id="b87b2-145">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="b87b2-146">Interface ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="b87b2-146">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="b87b2-147">Método SetActionOnTimeout</span><span class="sxs-lookup"><span data-stu-id="b87b2-147">SetActionOnTimeout Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md)
- [<span data-ttu-id="b87b2-148">ICLRPolicyManager:: SetTimeoutAndAction</span><span class="sxs-lookup"><span data-stu-id="b87b2-148">ICLRPolicyManager::SetTimeoutAndAction</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeoutandaction-method.md)
