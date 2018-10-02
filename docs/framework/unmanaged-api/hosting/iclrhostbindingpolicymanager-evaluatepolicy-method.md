---
title: Método ICLRHostBindingPolicyManager::EvaluatePolicy
ms.date: 03/30/2017
api_name:
- ICLRHostBindingPolicyManager.EvaluatePolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostBindingPolicyManager::EvaluatePolicy
helpviewer_keywords:
- ICLRHostBindingPolicyManager::EvaluatePolicy method [.NET Framework hosting]
- EvaluatePolicy method [.NET Framework hosting]
ms.assetid: 3a3a9446-7a4e-4836-9b27-5c536c15993d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9e37d56a321e6529812045e37c4f1929818b38a7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33433601"
---
# <a name="iclrhostbindingpolicymanagerevaluatepolicy-method"></a><span data-ttu-id="ecfbb-102">Método ICLRHostBindingPolicyManager::EvaluatePolicy</span><span class="sxs-lookup"><span data-stu-id="ecfbb-102">ICLRHostBindingPolicyManager::EvaluatePolicy Method</span></span>
<span data-ttu-id="ecfbb-103">Avalia a política de associação em nome de host.</span><span class="sxs-lookup"><span data-stu-id="ecfbb-103">Evaluates binding policy on behalf of the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecfbb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ecfbb-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="ecfbb-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ecfbb-105">Parameters</span></span>  
 `pwzReferenceIdentity`  
 <span data-ttu-id="ecfbb-106">[in] Uma referência ao assembly antes da avaliação da política.</span><span class="sxs-lookup"><span data-stu-id="ecfbb-106">[in] A reference to the assembly before the policy evaluation.</span></span>  
  
 `pbApplicationPolicy`  
 <span data-ttu-id="ecfbb-107">[in] Um ponteiro para um buffer que contém os dados de política.</span><span class="sxs-lookup"><span data-stu-id="ecfbb-107">[in] A pointer to a buffer that contains the policy data.</span></span>  
  
 `cbAppPolicySize`  
 <span data-ttu-id="ecfbb-108">[in] O tamanho do `pbApplicationPolicy` buffer.</span><span class="sxs-lookup"><span data-stu-id="ecfbb-108">[in] The size of the `pbApplicationPolicy` buffer.</span></span>  
  
 `pwzPostPolicyReferenceIdentity`  
 <span data-ttu-id="ecfbb-109">[out] Uma referência ao assembly após a avaliação dos novos dados de política.</span><span class="sxs-lookup"><span data-stu-id="ecfbb-109">[out] A reference to the assembly after the evaluation of the new policy data.</span></span>  
  
 `pcchPostPolicyReferenceIdentity`  
 <span data-ttu-id="ecfbb-110">[out no] Um ponteiro para o tamanho do buffer de referência de assembly identidade após a avaliação dos novos dados de política.</span><span class="sxs-lookup"><span data-stu-id="ecfbb-110">[in, out] A pointer to the size of the assembly identity reference buffer after the evaluation of the new policy data.</span></span>  
  
 `pdwPoliciesApplied`  
 <span data-ttu-id="ecfbb-111">[out] Um ponteiro para uma combinação de OR lógico de [EBindPolicyLevels](../../../../docs/framework/unmanaged-api/hosting/ebindpolicylevels-enumeration.md) valores, indicando que foram aplicadas.</span><span class="sxs-lookup"><span data-stu-id="ecfbb-111">[out] A pointer to a logical OR combination of [EBindPolicyLevels](../../../../docs/framework/unmanaged-api/hosting/ebindpolicylevels-enumeration.md) values, indicating which policies have been applied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ecfbb-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="ecfbb-112">Return Value</span></span>  
  
|<span data-ttu-id="ecfbb-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ecfbb-113">HRESULT</span></span>|<span data-ttu-id="ecfbb-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="ecfbb-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ecfbb-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="ecfbb-115">S_OK</span></span>|<span data-ttu-id="ecfbb-116">A avaliação foi concluída com êxito.</span><span class="sxs-lookup"><span data-stu-id="ecfbb-116">The evaluation completed successfully.</span></span>|  
|<span data-ttu-id="ecfbb-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="ecfbb-117">E_INVALIDARG</span></span>|<span data-ttu-id="ecfbb-118">O `pwzReferenceIdentity` ou `pbApplicationPolicy` é uma referência nula.</span><span class="sxs-lookup"><span data-stu-id="ecfbb-118">Either `pwzReferenceIdentity` or `pbApplicationPolicy` is a null reference.</span></span>|  
|<span data-ttu-id="ecfbb-119">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="ecfbb-119">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="ecfbb-120">`cbAppPolicySize` é pequeno demais.</span><span class="sxs-lookup"><span data-stu-id="ecfbb-120">`cbAppPolicySize` is too small.</span></span>|  
|<span data-ttu-id="ecfbb-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ecfbb-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ecfbb-122">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="ecfbb-122">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ecfbb-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ecfbb-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ecfbb-124">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="ecfbb-124">The call timed out.</span></span>|  
|<span data-ttu-id="ecfbb-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ecfbb-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ecfbb-126">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="ecfbb-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ecfbb-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ecfbb-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ecfbb-128">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="ecfbb-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ecfbb-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ecfbb-129">E_FAIL</span></span>|<span data-ttu-id="ecfbb-130">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="ecfbb-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ecfbb-131">Depois que um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="ecfbb-131">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ecfbb-132">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ecfbb-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ecfbb-133">Comentários</span><span class="sxs-lookup"><span data-stu-id="ecfbb-133">Remarks</span></span>  
 <span data-ttu-id="ecfbb-134">O `EvaluatePolicy` método permite que o host para influenciar a política de associação para manter o assembly de host específico requisitos de controle de versão.</span><span class="sxs-lookup"><span data-stu-id="ecfbb-134">The `EvaluatePolicy` method allows the host to influence binding policy to maintain host-specific assembly versioning requirements.</span></span> <span data-ttu-id="ecfbb-135">O mecanismo de políticas em si permanece dentro do CLR.</span><span class="sxs-lookup"><span data-stu-id="ecfbb-135">The policy engine itself remains inside the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ecfbb-136">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ecfbb-136">Requirements</span></span>  
 <span data-ttu-id="ecfbb-137">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ecfbb-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ecfbb-138">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ecfbb-138">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ecfbb-139">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="ecfbb-139">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ecfbb-140">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ecfbb-140">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecfbb-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ecfbb-141">See Also</span></span>  
 [<span data-ttu-id="ecfbb-142">Interface ICLRHostBindingPolicyManager</span><span class="sxs-lookup"><span data-stu-id="ecfbb-142">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
