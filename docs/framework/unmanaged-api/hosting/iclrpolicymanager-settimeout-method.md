---
title: Método ICLRPolicyManager::SetTimeout
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetTimeout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetTimeout
helpviewer_keywords:
- SetTimeout method [.NET Framework hosting]
- ICLRPolicyManager::SetTimeout method [.NET Framework hosting]
ms.assetid: 954404fd-d52d-4e68-b582-8692f3a5f608
topic_type:
- apiref
ms.openlocfilehash: 516ba1325404e757af8e38de239864b21b1640f1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140751"
---
# <a name="iclrpolicymanagersettimeout-method"></a><span data-ttu-id="8aed2-102">Método ICLRPolicyManager::SetTimeout</span><span class="sxs-lookup"><span data-stu-id="8aed2-102">ICLRPolicyManager::SetTimeout Method</span></span>
<span data-ttu-id="8aed2-103">Define um valor de tempo limite para a operação especificada.</span><span class="sxs-lookup"><span data-stu-id="8aed2-103">Sets a timeout value for the specified operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8aed2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8aed2-104">Syntax</span></span>  
  
```cpp  
HRESULT SetTimeout (  
    [in] EClrOperation operation,  
    [in] DWORD dsMilliseconds  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8aed2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8aed2-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="8aed2-106">no Um dos valores de [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) , que indica a operação Common Language Runtime (CLR) para a qual definir um tempo limite.</span><span class="sxs-lookup"><span data-stu-id="8aed2-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the common language runtime (CLR) operation for which to set a timeout.</span></span> <span data-ttu-id="8aed2-107">Há suporte para os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="8aed2-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="8aed2-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="8aed2-108">OPR_AppDomainUnload</span></span>  
  
- <span data-ttu-id="8aed2-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="8aed2-109">OPR_ProcessExit</span></span>  
  
- <span data-ttu-id="8aed2-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="8aed2-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
- <span data-ttu-id="8aed2-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="8aed2-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `dwMilliseconds`  
 <span data-ttu-id="8aed2-112">no O novo valor de tempo limite, em milissegundos.</span><span class="sxs-lookup"><span data-stu-id="8aed2-112">[in] The new timeout value, in milliseconds.</span></span> <span data-ttu-id="8aed2-113">Um valor infinito faz com que a operação nunca expire.</span><span class="sxs-lookup"><span data-stu-id="8aed2-113">A value of INFINITE causes the operation never to time out.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8aed2-114">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="8aed2-114">Return Value</span></span>  
  
|<span data-ttu-id="8aed2-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8aed2-115">HRESULT</span></span>|<span data-ttu-id="8aed2-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="8aed2-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8aed2-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="8aed2-117">S_OK</span></span>|<span data-ttu-id="8aed2-118">`SetTimeout` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="8aed2-118">`SetTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="8aed2-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8aed2-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8aed2-120">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="8aed2-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8aed2-121">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8aed2-121">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8aed2-122">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="8aed2-122">The call timed out.</span></span>|  
|<span data-ttu-id="8aed2-123">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8aed2-123">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8aed2-124">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="8aed2-124">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8aed2-125">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8aed2-125">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8aed2-126">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="8aed2-126">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8aed2-127">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8aed2-127">E_FAIL</span></span>|<span data-ttu-id="8aed2-128">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="8aed2-128">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8aed2-129">Depois que um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="8aed2-129">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8aed2-130">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8aed2-130">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="8aed2-131">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="8aed2-131">E_INVALIDARG</span></span>|<span data-ttu-id="8aed2-132">Não é possível definir um tempo limite para o `operation`especificado ou um valor inválido foi fornecido para `operation`.</span><span class="sxs-lookup"><span data-stu-id="8aed2-132">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8aed2-133">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8aed2-133">Requirements</span></span>  
 <span data-ttu-id="8aed2-134">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8aed2-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8aed2-135">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8aed2-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8aed2-136">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8aed2-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8aed2-137">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8aed2-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8aed2-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8aed2-138">See also</span></span>

- [<span data-ttu-id="8aed2-139">Enumeração EClrOperation</span><span class="sxs-lookup"><span data-stu-id="8aed2-139">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="8aed2-140">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="8aed2-140">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="8aed2-141">Interface ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="8aed2-141">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
