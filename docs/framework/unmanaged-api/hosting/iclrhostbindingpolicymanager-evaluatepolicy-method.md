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
ms.openlocfilehash: ad7856a9376880f867e35f1e63bc2cac1ca216fa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59130126"
---
# <a name="iclrhostbindingpolicymanagerevaluatepolicy-method"></a><span data-ttu-id="e47d4-102">Método ICLRHostBindingPolicyManager::EvaluatePolicy</span><span class="sxs-lookup"><span data-stu-id="e47d4-102">ICLRHostBindingPolicyManager::EvaluatePolicy Method</span></span>
<span data-ttu-id="e47d4-103">Avalia a política de associação em nome do host.</span><span class="sxs-lookup"><span data-stu-id="e47d4-103">Evaluates binding policy on behalf of the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e47d4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e47d4-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="e47d4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e47d4-105">Parameters</span></span>  
 `pwzReferenceIdentity`  
 <span data-ttu-id="e47d4-106">[in] Uma referência ao assembly antes da avaliação da política.</span><span class="sxs-lookup"><span data-stu-id="e47d4-106">[in] A reference to the assembly before the policy evaluation.</span></span>  
  
 `pbApplicationPolicy`  
 <span data-ttu-id="e47d4-107">[in] Um ponteiro para um buffer que contém os dados de política.</span><span class="sxs-lookup"><span data-stu-id="e47d4-107">[in] A pointer to a buffer that contains the policy data.</span></span>  
  
 `cbAppPolicySize`  
 <span data-ttu-id="e47d4-108">[in] O tamanho do `pbApplicationPolicy` buffer.</span><span class="sxs-lookup"><span data-stu-id="e47d4-108">[in] The size of the `pbApplicationPolicy` buffer.</span></span>  
  
 `pwzPostPolicyReferenceIdentity`  
 <span data-ttu-id="e47d4-109">[out] Uma referência ao assembly após a avaliação dos novos dados de política.</span><span class="sxs-lookup"><span data-stu-id="e47d4-109">[out] A reference to the assembly after the evaluation of the new policy data.</span></span>  
  
 `pcchPostPolicyReferenceIdentity`  
 <span data-ttu-id="e47d4-110">[no, out] Um ponteiro para o tamanho do buffer de referência de identidade de assembly após a avaliação dos novos dados de política.</span><span class="sxs-lookup"><span data-stu-id="e47d4-110">[in, out] A pointer to the size of the assembly identity reference buffer after the evaluation of the new policy data.</span></span>  
  
 `pdwPoliciesApplied`  
 <span data-ttu-id="e47d4-111">[out] Um ponteiro para uma combinação OR lógico de [EBindPolicyLevels](../../../../docs/framework/unmanaged-api/hosting/ebindpolicylevels-enumeration.md) valores, que indica quais diretivas foram aplicadas.</span><span class="sxs-lookup"><span data-stu-id="e47d4-111">[out] A pointer to a logical OR combination of [EBindPolicyLevels](../../../../docs/framework/unmanaged-api/hosting/ebindpolicylevels-enumeration.md) values, indicating which policies have been applied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e47d4-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="e47d4-112">Return Value</span></span>  
  
|<span data-ttu-id="e47d4-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e47d4-113">HRESULT</span></span>|<span data-ttu-id="e47d4-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="e47d4-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e47d4-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="e47d4-115">S_OK</span></span>|<span data-ttu-id="e47d4-116">A avaliação foi concluída com êxito.</span><span class="sxs-lookup"><span data-stu-id="e47d4-116">The evaluation completed successfully.</span></span>|  
|<span data-ttu-id="e47d4-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="e47d4-117">E_INVALIDARG</span></span>|<span data-ttu-id="e47d4-118">Tanto `pwzReferenceIdentity` ou `pbApplicationPolicy` é uma referência nula.</span><span class="sxs-lookup"><span data-stu-id="e47d4-118">Either `pwzReferenceIdentity` or `pbApplicationPolicy` is a null reference.</span></span>|  
|<span data-ttu-id="e47d4-119">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="e47d4-119">ERROR_INSUFFICIENT_BUFFER</span></span>|`cbAppPolicySize` <span data-ttu-id="e47d4-120">é muito pequeno.</span><span class="sxs-lookup"><span data-stu-id="e47d4-120">is too small.</span></span>|  
|<span data-ttu-id="e47d4-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e47d4-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e47d4-122">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="e47d4-122">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e47d4-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e47d4-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e47d4-124">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="e47d4-124">The call timed out.</span></span>|  
|<span data-ttu-id="e47d4-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e47d4-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e47d4-126">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="e47d4-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e47d4-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e47d4-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e47d4-128">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="e47d4-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e47d4-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e47d4-129">E_FAIL</span></span>|<span data-ttu-id="e47d4-130">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="e47d4-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e47d4-131">Depois que um método retorna E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="e47d4-131">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e47d4-132">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e47d4-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e47d4-133">Comentários</span><span class="sxs-lookup"><span data-stu-id="e47d4-133">Remarks</span></span>  
 <span data-ttu-id="e47d4-134">O `EvaluatePolicy` método permite que o host para influenciar a política de associação de assembly específico de host de manter os requisitos de controle de versão.</span><span class="sxs-lookup"><span data-stu-id="e47d4-134">The `EvaluatePolicy` method allows the host to influence binding policy to maintain host-specific assembly versioning requirements.</span></span> <span data-ttu-id="e47d4-135">O mecanismo de políticas em si permanece dentro do CLR.</span><span class="sxs-lookup"><span data-stu-id="e47d4-135">The policy engine itself remains inside the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e47d4-136">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e47d4-136">Requirements</span></span>  
 <span data-ttu-id="e47d4-137">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e47d4-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e47d4-138">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e47d4-138">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e47d4-139">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="e47d4-139">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="e47d4-140">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="e47d4-140">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e47d4-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e47d4-141">See also</span></span>

- [<span data-ttu-id="e47d4-142">Interface ICLRHostBindingPolicyManager</span><span class="sxs-lookup"><span data-stu-id="e47d4-142">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
