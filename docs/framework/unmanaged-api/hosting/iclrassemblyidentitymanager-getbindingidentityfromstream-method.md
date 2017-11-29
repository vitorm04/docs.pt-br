---
title: "Método ICLRAssemblyIdentityManager::GetBindingIdentityFromStream"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRAssemblyIdentityManager.GetBindingIdentityFromStream
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRAssemblyIdentityManager::GetBindingIdentityFromStream
helpviewer_keywords:
- GetBindingIdentityFromStream method [.NET Framework hosting]
- ICLRAssemblyIdentityManager::GetBindingIdentityFromStream method [.NET Framework hosting]
ms.assetid: 40123b30-a589-46b3-95d3-af7b2b0baa05
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cd16f13bd77127953bdd17b258c7be518088f899
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrassemblyidentitymanagergetbindingidentityfromstream-method"></a><span data-ttu-id="842a4-102">Método ICLRAssemblyIdentityManager::GetBindingIdentityFromStream</span><span class="sxs-lookup"><span data-stu-id="842a4-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromStream Method</span></span>
<span data-ttu-id="842a4-103">Obtém os dados de identidade de assembly canônico para o assembly do fluxo especificado.</span><span class="sxs-lookup"><span data-stu-id="842a4-103">Gets the canonical assembly identity data for the assembly in the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="842a4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="842a4-104">Syntax</span></span>  
  
```  
HRESULT GetBindingIdentityFromStream (  
    [in] IStream    *pStream,  
    [in] DWORD       dwFlags,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="842a4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="842a4-105">Parameters</span></span>  
 `pStream`  
 <span data-ttu-id="842a4-106">[in] O fluxo de assembly a ser avaliada.</span><span class="sxs-lookup"><span data-stu-id="842a4-106">[in] The assembly stream to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="842a4-107">[in] Fornecido para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="842a4-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="842a4-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT é o único valor que suporta a versão atual do common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="842a4-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="842a4-109">[out] Um buffer que contém os dados de identidade de assembly opaco.</span><span class="sxs-lookup"><span data-stu-id="842a4-109">[out] A buffer containing the opaque assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="842a4-110">[out no] O tamanho de `pwzBuffer`.</span><span class="sxs-lookup"><span data-stu-id="842a4-110">[in, out] The size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="842a4-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="842a4-111">Return Value</span></span>  
  
|<span data-ttu-id="842a4-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="842a4-112">HRESULT</span></span>|<span data-ttu-id="842a4-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="842a4-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="842a4-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="842a4-114">S_OK</span></span>|<span data-ttu-id="842a4-115">O método é retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="842a4-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="842a4-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="842a4-116">E_INVALIDARG</span></span>|<span data-ttu-id="842a4-117">Fornecido `pStream` é nulo.</span><span class="sxs-lookup"><span data-stu-id="842a4-117">The supplied `pStream` is null.</span></span>|  
|<span data-ttu-id="842a4-118">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="842a4-118">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="842a4-119">O tamanho de `pwzBuffer` é muito pequeno.</span><span class="sxs-lookup"><span data-stu-id="842a4-119">The size of `pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="842a4-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="842a4-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="842a4-121">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="842a4-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="842a4-122">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="842a4-122">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="842a4-123">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="842a4-123">The call timed out.</span></span>|  
|<span data-ttu-id="842a4-124">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="842a4-124">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="842a4-125">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="842a4-125">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="842a4-126">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="842a4-126">HOST_E_ABANDONED</span></span>|<span data-ttu-id="842a4-127">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="842a4-127">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="842a4-128">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="842a4-128">E_FAIL</span></span>|<span data-ttu-id="842a4-129">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="842a4-129">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="842a4-130">Se um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="842a4-130">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="842a4-131">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="842a4-131">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="842a4-132">Requisitos</span><span class="sxs-lookup"><span data-stu-id="842a4-132">Requirements</span></span>  
 <span data-ttu-id="842a4-133">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="842a4-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="842a4-134">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="842a4-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="842a4-135">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="842a4-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="842a4-136">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="842a4-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="842a4-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="842a4-137">See Also</span></span>  
 [<span data-ttu-id="842a4-138">Interface ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="842a4-138">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="842a4-139">Interface ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="842a4-139">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
