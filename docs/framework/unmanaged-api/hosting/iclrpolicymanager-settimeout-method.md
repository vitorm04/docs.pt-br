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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5b5a389af718322d1e0fffebae046bf28731877b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435771"
---
# <a name="iclrpolicymanagersettimeout-method"></a><span data-ttu-id="4aa49-102">Método ICLRPolicyManager::SetTimeout</span><span class="sxs-lookup"><span data-stu-id="4aa49-102">ICLRPolicyManager::SetTimeout Method</span></span>
<span data-ttu-id="4aa49-103">Define um valor de tempo limite para a operação especificada.</span><span class="sxs-lookup"><span data-stu-id="4aa49-103">Sets a timeout value for the specified operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4aa49-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4aa49-104">Syntax</span></span>  
  
```  
HRESULT SetTimeout (  
    [in] EClrOperation operation,  
    [in] DWORD dsMilliseconds  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4aa49-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4aa49-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="4aa49-106">[in] Uma da [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) valores, indicando que a operação de runtime (CLR) de linguagem comum para o qual definir um tempo limite.</span><span class="sxs-lookup"><span data-stu-id="4aa49-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the common language runtime (CLR) operation for which to set a timeout.</span></span> <span data-ttu-id="4aa49-107">Há suporte para os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="4aa49-107">The following values are supported:</span></span>  
  
-   <span data-ttu-id="4aa49-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="4aa49-108">OPR_AppDomainUnload</span></span>  
  
-   <span data-ttu-id="4aa49-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="4aa49-109">OPR_ProcessExit</span></span>  
  
-   <span data-ttu-id="4aa49-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="4aa49-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
-   <span data-ttu-id="4aa49-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="4aa49-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `dwMilliseconds`  
 <span data-ttu-id="4aa49-112">[in] O novo valor de tempo limite, em milissegundos.</span><span class="sxs-lookup"><span data-stu-id="4aa49-112">[in] The new timeout value, in milliseconds.</span></span> <span data-ttu-id="4aa49-113">Um valor infinito faz com que a operação de nunca expirar.</span><span class="sxs-lookup"><span data-stu-id="4aa49-113">A value of INFINITE causes the operation never to time out.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4aa49-114">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="4aa49-114">Return Value</span></span>  
  
|<span data-ttu-id="4aa49-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4aa49-115">HRESULT</span></span>|<span data-ttu-id="4aa49-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="4aa49-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4aa49-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="4aa49-117">S_OK</span></span>|<span data-ttu-id="4aa49-118">`SetTimeout` retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="4aa49-118">`SetTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="4aa49-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4aa49-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4aa49-120">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="4aa49-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4aa49-121">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4aa49-121">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4aa49-122">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="4aa49-122">The call timed out.</span></span>|  
|<span data-ttu-id="4aa49-123">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4aa49-123">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4aa49-124">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="4aa49-124">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4aa49-125">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4aa49-125">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4aa49-126">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="4aa49-126">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4aa49-127">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4aa49-127">E_FAIL</span></span>|<span data-ttu-id="4aa49-128">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="4aa49-128">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4aa49-129">Depois que um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="4aa49-129">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4aa49-130">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="4aa49-130">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="4aa49-131">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="4aa49-131">E_INVALIDARG</span></span>|<span data-ttu-id="4aa49-132">Não é possível definir um tempo limite especificado `operation`, ou um valor inválido foi fornecido para `operation`.</span><span class="sxs-lookup"><span data-stu-id="4aa49-132">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4aa49-133">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4aa49-133">Requirements</span></span>  
 <span data-ttu-id="4aa49-134">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4aa49-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4aa49-135">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4aa49-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4aa49-136">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="4aa49-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4aa49-137">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4aa49-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4aa49-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4aa49-138">See Also</span></span>  
 [<span data-ttu-id="4aa49-139">Enumeração EClrOperation</span><span class="sxs-lookup"><span data-stu-id="4aa49-139">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="4aa49-140">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="4aa49-140">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="4aa49-141">Interface ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="4aa49-141">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
