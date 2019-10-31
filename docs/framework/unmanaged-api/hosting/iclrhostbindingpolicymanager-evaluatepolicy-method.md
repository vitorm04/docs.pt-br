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
ms.openlocfilehash: 9600573a0a730cee10247d5644d587e75856cdd9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141183"
---
# <a name="iclrhostbindingpolicymanagerevaluatepolicy-method"></a><span data-ttu-id="af308-102">Método ICLRHostBindingPolicyManager::EvaluatePolicy</span><span class="sxs-lookup"><span data-stu-id="af308-102">ICLRHostBindingPolicyManager::EvaluatePolicy Method</span></span>
<span data-ttu-id="af308-103">Avalia a política de associação em nome do host.</span><span class="sxs-lookup"><span data-stu-id="af308-103">Evaluates binding policy on behalf of the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af308-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="af308-104">Syntax</span></span>  
  
```cpp  
HRESULT EvaluatePolicy (  
    [in] LPCWSTR     pwzReferenceIdentity,  
    [in] BYTE       *pbApplicationPolicy,  
    [in] DWORD       cbAppPolicySize,  
    [out, size_is(*pcchPostPolicyReferenceIdentity)] LPWSTR pwzPostPolicyReferenceIdentity,  
    [in, out] DWORD *pcchPostPolicyReferenceIdentity,  
    [out] DWORD     *pdwPoliciesApplied  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="af308-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="af308-105">Parameters</span></span>  
 `pwzReferenceIdentity`  
 <span data-ttu-id="af308-106">no Uma referência ao assembly antes da avaliação da política.</span><span class="sxs-lookup"><span data-stu-id="af308-106">[in] A reference to the assembly before the policy evaluation.</span></span>  
  
 `pbApplicationPolicy`  
 <span data-ttu-id="af308-107">no Um ponteiro para um buffer que contém os dados da política.</span><span class="sxs-lookup"><span data-stu-id="af308-107">[in] A pointer to a buffer that contains the policy data.</span></span>  
  
 `cbAppPolicySize`  
 <span data-ttu-id="af308-108">no O tamanho do buffer de `pbApplicationPolicy`.</span><span class="sxs-lookup"><span data-stu-id="af308-108">[in] The size of the `pbApplicationPolicy` buffer.</span></span>  
  
 `pwzPostPolicyReferenceIdentity`  
 <span data-ttu-id="af308-109">fora Uma referência ao assembly após a avaliação dos novos dados de política.</span><span class="sxs-lookup"><span data-stu-id="af308-109">[out] A reference to the assembly after the evaluation of the new policy data.</span></span>  
  
 `pcchPostPolicyReferenceIdentity`  
 <span data-ttu-id="af308-110">[entrada, saída] Um ponteiro para o tamanho do buffer de referência de identidade do assembly após a avaliação dos novos dados de política.</span><span class="sxs-lookup"><span data-stu-id="af308-110">[in, out] A pointer to the size of the assembly identity reference buffer after the evaluation of the new policy data.</span></span>  
  
 `pdwPoliciesApplied`  
 <span data-ttu-id="af308-111">fora Um ponteiro para uma combinação lógica ou de valores [EBindPolicyLevels](../../../../docs/framework/unmanaged-api/hosting/ebindpolicylevels-enumeration.md) , indicando quais políticas foram aplicadas.</span><span class="sxs-lookup"><span data-stu-id="af308-111">[out] A pointer to a logical OR combination of [EBindPolicyLevels](../../../../docs/framework/unmanaged-api/hosting/ebindpolicylevels-enumeration.md) values, indicating which policies have been applied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="af308-112">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="af308-112">Return Value</span></span>  
  
|<span data-ttu-id="af308-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="af308-113">HRESULT</span></span>|<span data-ttu-id="af308-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="af308-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="af308-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="af308-115">S_OK</span></span>|<span data-ttu-id="af308-116">A avaliação foi concluída com êxito.</span><span class="sxs-lookup"><span data-stu-id="af308-116">The evaluation completed successfully.</span></span>|  
|<span data-ttu-id="af308-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="af308-117">E_INVALIDARG</span></span>|<span data-ttu-id="af308-118">O `pwzReferenceIdentity` ou `pbApplicationPolicy` é uma referência nula.</span><span class="sxs-lookup"><span data-stu-id="af308-118">Either `pwzReferenceIdentity` or `pbApplicationPolicy` is a null reference.</span></span>|  
|<span data-ttu-id="af308-119">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="af308-119">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="af308-120">`cbAppPolicySize` é pequeno demais.</span><span class="sxs-lookup"><span data-stu-id="af308-120">`cbAppPolicySize` is too small.</span></span>|  
|<span data-ttu-id="af308-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="af308-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="af308-122">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="af308-122">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="af308-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="af308-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="af308-124">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="af308-124">The call timed out.</span></span>|  
|<span data-ttu-id="af308-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="af308-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="af308-126">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="af308-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="af308-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="af308-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="af308-128">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="af308-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="af308-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="af308-129">E_FAIL</span></span>|<span data-ttu-id="af308-130">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="af308-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="af308-131">Depois que um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="af308-131">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="af308-132">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="af308-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="af308-133">Comentários</span><span class="sxs-lookup"><span data-stu-id="af308-133">Remarks</span></span>  
 <span data-ttu-id="af308-134">O método `EvaluatePolicy` permite que o host influencie a diretiva de associação para manter os requisitos de controle de versão de assembly específicos do host.</span><span class="sxs-lookup"><span data-stu-id="af308-134">The `EvaluatePolicy` method allows the host to influence binding policy to maintain host-specific assembly versioning requirements.</span></span> <span data-ttu-id="af308-135">O próprio mecanismo de política permanece dentro do CLR.</span><span class="sxs-lookup"><span data-stu-id="af308-135">The policy engine itself remains inside the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af308-136">Requisitos</span><span class="sxs-lookup"><span data-stu-id="af308-136">Requirements</span></span>  
 <span data-ttu-id="af308-137">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af308-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af308-138">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="af308-138">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="af308-139">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="af308-139">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="af308-140">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af308-140">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af308-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="af308-141">See also</span></span>

- [<span data-ttu-id="af308-142">Interface ICLRHostBindingPolicyManager</span><span class="sxs-lookup"><span data-stu-id="af308-142">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
