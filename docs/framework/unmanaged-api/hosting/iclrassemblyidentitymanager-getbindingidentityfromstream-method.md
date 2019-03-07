---
title: Método ICLRAssemblyIdentityManager::GetBindingIdentityFromStream
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetBindingIdentityFromStream
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetBindingIdentityFromStream
helpviewer_keywords:
- GetBindingIdentityFromStream method [.NET Framework hosting]
- ICLRAssemblyIdentityManager::GetBindingIdentityFromStream method [.NET Framework hosting]
ms.assetid: 40123b30-a589-46b3-95d3-af7b2b0baa05
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6590b455717dfdb3ea43e3622b494e2169047337
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57469607"
---
# <a name="iclrassemblyidentitymanagergetbindingidentityfromstream-method"></a><span data-ttu-id="dae51-102">Método ICLRAssemblyIdentityManager::GetBindingIdentityFromStream</span><span class="sxs-lookup"><span data-stu-id="dae51-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromStream Method</span></span>
<span data-ttu-id="dae51-103">Obtém os dados de identidade do assembly canônico para o assembly no fluxo especificado.</span><span class="sxs-lookup"><span data-stu-id="dae51-103">Gets the canonical assembly identity data for the assembly in the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dae51-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dae51-104">Syntax</span></span>  
  
```  
HRESULT GetBindingIdentityFromStream (  
    [in] IStream    *pStream,  
    [in] DWORD       dwFlags,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dae51-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dae51-105">Parameters</span></span>  
 `pStream`  
 <span data-ttu-id="dae51-106">[in] O fluxo de assembly a ser avaliada.</span><span class="sxs-lookup"><span data-stu-id="dae51-106">[in] The assembly stream to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="dae51-107">[in] Fornecido para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="dae51-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="dae51-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT é o único valor que a versão atual do common language runtime (CLR) dá suporte.</span><span class="sxs-lookup"><span data-stu-id="dae51-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="dae51-109">[out] Um buffer que contém os dados de identidade do assembly opaco.</span><span class="sxs-lookup"><span data-stu-id="dae51-109">[out] A buffer containing the opaque assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="dae51-110">[no, out] O tamanho do `pwzBuffer`.</span><span class="sxs-lookup"><span data-stu-id="dae51-110">[in, out] The size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dae51-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="dae51-111">Return Value</span></span>  
  
|<span data-ttu-id="dae51-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dae51-112">HRESULT</span></span>|<span data-ttu-id="dae51-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="dae51-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dae51-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="dae51-114">S_OK</span></span>|<span data-ttu-id="dae51-115">O método é retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="dae51-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="dae51-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="dae51-116">E_INVALIDARG</span></span>|<span data-ttu-id="dae51-117">Fornecido `pStream` é nulo.</span><span class="sxs-lookup"><span data-stu-id="dae51-117">The supplied `pStream` is null.</span></span>|  
|<span data-ttu-id="dae51-118">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="dae51-118">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="dae51-119">O tamanho de `pwzBuffer` é muito pequeno.</span><span class="sxs-lookup"><span data-stu-id="dae51-119">The size of `pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="dae51-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="dae51-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="dae51-121">O CLR não tenha sido carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="dae51-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="dae51-122">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="dae51-122">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="dae51-123">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="dae51-123">The call timed out.</span></span>|  
|<span data-ttu-id="dae51-124">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="dae51-124">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="dae51-125">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="dae51-125">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="dae51-126">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="dae51-126">HOST_E_ABANDONED</span></span>|<span data-ttu-id="dae51-127">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="dae51-127">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="dae51-128">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="dae51-128">E_FAIL</span></span>|<span data-ttu-id="dae51-129">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="dae51-129">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="dae51-130">Se um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="dae51-130">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="dae51-131">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="dae51-131">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dae51-132">Requisitos</span><span class="sxs-lookup"><span data-stu-id="dae51-132">Requirements</span></span>  
 <span data-ttu-id="dae51-133">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dae51-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dae51-134">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="dae51-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dae51-135">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="dae51-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dae51-136">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dae51-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dae51-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dae51-137">See also</span></span>
- [<span data-ttu-id="dae51-138">Interface ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="dae51-138">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="dae51-139">Interface ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="dae51-139">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
