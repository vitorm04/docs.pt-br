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
ms.openlocfilehash: 8edb16de4c02d2589ecfb9ae5becba22e10e6be6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54609324"
---
# <a name="iclrpolicymanagersettimeout-method"></a><span data-ttu-id="0f5b1-102">Método ICLRPolicyManager::SetTimeout</span><span class="sxs-lookup"><span data-stu-id="0f5b1-102">ICLRPolicyManager::SetTimeout Method</span></span>
<span data-ttu-id="0f5b1-103">Define um valor de tempo limite para a operação especificada.</span><span class="sxs-lookup"><span data-stu-id="0f5b1-103">Sets a timeout value for the specified operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f5b1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0f5b1-104">Syntax</span></span>  
  
```  
HRESULT SetTimeout (  
    [in] EClrOperation operation,  
    [in] DWORD dsMilliseconds  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0f5b1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0f5b1-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="0f5b1-106">[in] Um dos [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) valores, indicando que a operação de runtime (CLR) de linguagem comum para o qual definir um tempo limite.</span><span class="sxs-lookup"><span data-stu-id="0f5b1-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the common language runtime (CLR) operation for which to set a timeout.</span></span> <span data-ttu-id="0f5b1-107">Há suporte para os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="0f5b1-107">The following values are supported:</span></span>  
  
-   <span data-ttu-id="0f5b1-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="0f5b1-108">OPR_AppDomainUnload</span></span>  
  
-   <span data-ttu-id="0f5b1-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="0f5b1-109">OPR_ProcessExit</span></span>  
  
-   <span data-ttu-id="0f5b1-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="0f5b1-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
-   <span data-ttu-id="0f5b1-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="0f5b1-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `dwMilliseconds`  
 <span data-ttu-id="0f5b1-112">[in] O novo valor de tempo limite, em milissegundos.</span><span class="sxs-lookup"><span data-stu-id="0f5b1-112">[in] The new timeout value, in milliseconds.</span></span> <span data-ttu-id="0f5b1-113">Um valor infinito faz com que a operação de nunca atingir o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="0f5b1-113">A value of INFINITE causes the operation never to time out.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0f5b1-114">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="0f5b1-114">Return Value</span></span>  
  
|<span data-ttu-id="0f5b1-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0f5b1-115">HRESULT</span></span>|<span data-ttu-id="0f5b1-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="0f5b1-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0f5b1-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="0f5b1-117">S_OK</span></span>|<span data-ttu-id="0f5b1-118">`SetTimeout` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="0f5b1-118">`SetTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="0f5b1-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0f5b1-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0f5b1-120">O CLR não tenha sido carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="0f5b1-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0f5b1-121">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0f5b1-121">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0f5b1-122">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="0f5b1-122">The call timed out.</span></span>|  
|<span data-ttu-id="0f5b1-123">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0f5b1-123">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0f5b1-124">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="0f5b1-124">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0f5b1-125">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0f5b1-125">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0f5b1-126">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="0f5b1-126">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0f5b1-127">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0f5b1-127">E_FAIL</span></span>|<span data-ttu-id="0f5b1-128">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="0f5b1-128">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0f5b1-129">Depois que um método retorna E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="0f5b1-129">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0f5b1-130">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0f5b1-130">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0f5b1-131">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="0f5b1-131">E_INVALIDARG</span></span>|<span data-ttu-id="0f5b1-132">Não é possível definir um tempo limite especificado `operation`, ou um valor inválido foi fornecido para `operation`.</span><span class="sxs-lookup"><span data-stu-id="0f5b1-132">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0f5b1-133">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0f5b1-133">Requirements</span></span>  
 <span data-ttu-id="0f5b1-134">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f5b1-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f5b1-135">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0f5b1-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0f5b1-136">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="0f5b1-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0f5b1-137">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f5b1-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f5b1-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0f5b1-138">See also</span></span>
- [<span data-ttu-id="0f5b1-139">Enumeração EClrOperation</span><span class="sxs-lookup"><span data-stu-id="0f5b1-139">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="0f5b1-140">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="0f5b1-140">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="0f5b1-141">Interface ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="0f5b1-141">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
