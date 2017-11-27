---
title: "Método ICLRHostBindingPolicyManager::EvaluatePolicy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRHostBindingPolicyManager.EvaluatePolicy
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRHostBindingPolicyManager::EvaluatePolicy
helpviewer_keywords:
- ICLRHostBindingPolicyManager::EvaluatePolicy method [.NET Framework hosting]
- EvaluatePolicy method [.NET Framework hosting]
ms.assetid: 3a3a9446-7a4e-4836-9b27-5c536c15993d
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7471b77deca7b66ba0a30b08ccf934704a7ac61d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="iclrhostbindingpolicymanagerevaluatepolicy-method"></a><span data-ttu-id="d171e-102">Método ICLRHostBindingPolicyManager::EvaluatePolicy</span><span class="sxs-lookup"><span data-stu-id="d171e-102">ICLRHostBindingPolicyManager::EvaluatePolicy Method</span></span>
<span data-ttu-id="d171e-103">Avalia a política de associação em nome de host.</span><span class="sxs-lookup"><span data-stu-id="d171e-103">Evaluates binding policy on behalf of the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d171e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d171e-104">Syntax</span></span>  
  
```  
HRESULT EvaluatePolicy (  
    [in] LPCWSTR     pwzReferenceIdentity,  
    [in] BYTE       *pbApplicationPolicy,  
    [in] DWORD       cbAppPolicySize,  
    [out, size_is(*pcchPostPolicyReferenceIdentity)] LPWSTR pwzPostPolicyReferenceIdentity,  
    [in, out] DWORD *pcchPostPolicyReferenceIdentity,  
    [out] DWORD     *pdwPoliciesApplied  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d171e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d171e-105">Parameters</span></span>  
 `pwzReferenceIdentity`  
 <span data-ttu-id="d171e-106">[in] Uma referência ao assembly antes da avaliação da política.</span><span class="sxs-lookup"><span data-stu-id="d171e-106">[in] A reference to the assembly before the policy evaluation.</span></span>  
  
 `pbApplicationPolicy`  
 <span data-ttu-id="d171e-107">[in] Um ponteiro para um buffer que contém os dados de política.</span><span class="sxs-lookup"><span data-stu-id="d171e-107">[in] A pointer to a buffer that contains the policy data.</span></span>  
  
 `cbAppPolicySize`  
 <span data-ttu-id="d171e-108">[in] O tamanho do `pbApplicationPolicy` buffer.</span><span class="sxs-lookup"><span data-stu-id="d171e-108">[in] The size of the `pbApplicationPolicy` buffer.</span></span>  
  
 `pwzPostPolicyReferenceIdentity`  
 <span data-ttu-id="d171e-109">[out] Uma referência ao assembly após a avaliação dos novos dados de política.</span><span class="sxs-lookup"><span data-stu-id="d171e-109">[out] A reference to the assembly after the evaluation of the new policy data.</span></span>  
  
 `pcchPostPolicyReferenceIdentity`  
 <span data-ttu-id="d171e-110">[out no] Um ponteiro para o tamanho do buffer de referência de assembly identidade após a avaliação dos novos dados de política.</span><span class="sxs-lookup"><span data-stu-id="d171e-110">[in, out] A pointer to the size of the assembly identity reference buffer after the evaluation of the new policy data.</span></span>  
  
 `pdwPoliciesApplied`  
 <span data-ttu-id="d171e-111">[out] Um ponteiro para uma combinação de OR lógico de [EBindPolicyLevels](../../../../docs/framework/unmanaged-api/hosting/ebindpolicylevels-enumeration.md) valores, indicando que foram aplicadas.</span><span class="sxs-lookup"><span data-stu-id="d171e-111">[out] A pointer to a logical OR combination of [EBindPolicyLevels](../../../../docs/framework/unmanaged-api/hosting/ebindpolicylevels-enumeration.md) values, indicating which policies have been applied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d171e-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="d171e-112">Return Value</span></span>  
  
|<span data-ttu-id="d171e-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d171e-113">HRESULT</span></span>|<span data-ttu-id="d171e-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="d171e-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d171e-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="d171e-115">S_OK</span></span>|<span data-ttu-id="d171e-116">A avaliação foi concluída com êxito.</span><span class="sxs-lookup"><span data-stu-id="d171e-116">The evaluation completed successfully.</span></span>|  
|<span data-ttu-id="d171e-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="d171e-117">E_INVALIDARG</span></span>|<span data-ttu-id="d171e-118">O `pwzReferenceIdentity` ou `pbApplicationPolicy` é uma referência nula.</span><span class="sxs-lookup"><span data-stu-id="d171e-118">Either `pwzReferenceIdentity` or `pbApplicationPolicy` is a null reference.</span></span>|  
|<span data-ttu-id="d171e-119">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="d171e-119">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="d171e-120">`cbAppPolicySize` é pequeno demais.</span><span class="sxs-lookup"><span data-stu-id="d171e-120">`cbAppPolicySize` is too small.</span></span>|  
|<span data-ttu-id="d171e-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d171e-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d171e-122">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="d171e-122">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d171e-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d171e-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d171e-124">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="d171e-124">The call timed out.</span></span>|  
|<span data-ttu-id="d171e-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d171e-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d171e-126">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="d171e-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d171e-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d171e-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d171e-128">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="d171e-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d171e-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d171e-129">E_FAIL</span></span>|<span data-ttu-id="d171e-130">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="d171e-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d171e-131">Depois que um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="d171e-131">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d171e-132">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d171e-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d171e-133">Comentários</span><span class="sxs-lookup"><span data-stu-id="d171e-133">Remarks</span></span>  
 <span data-ttu-id="d171e-134">O `EvaluatePolicy` método permite que o host para influenciar a política de associação para manter o assembly de host específico requisitos de controle de versão.</span><span class="sxs-lookup"><span data-stu-id="d171e-134">The `EvaluatePolicy` method allows the host to influence binding policy to maintain host-specific assembly versioning requirements.</span></span> <span data-ttu-id="d171e-135">O mecanismo de políticas em si permanece dentro do CLR.</span><span class="sxs-lookup"><span data-stu-id="d171e-135">The policy engine itself remains inside the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d171e-136">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d171e-136">Requirements</span></span>  
 <span data-ttu-id="d171e-137">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d171e-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d171e-138">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d171e-138">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d171e-139">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="d171e-139">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d171e-140">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d171e-140">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d171e-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d171e-141">See Also</span></span>  
 [<span data-ttu-id="d171e-142">Interface ICLRHostBindingPolicyManager</span><span class="sxs-lookup"><span data-stu-id="d171e-142">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
