---
title: "Método ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRAssemblyIdentityManager.GetReferencedAssembliesFromFile
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile
helpviewer_keywords:
- ICLRAssemblyIdentityManager::GetReferenceAssembliesFromFile method [.NET Framework hosting]
- GetReferenceAssembliesFromFile method [.NET Framework hosting]
ms.assetid: eed63d31-d977-4c7d-9443-f9d37a2a7d81
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: abd80676fe459bd779d5fad4cf2e9c41e140741b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrassemblyidentitymanagergetreferencedassembliesfromfile-method"></a><span data-ttu-id="bfc63-102">Método ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile</span><span class="sxs-lookup"><span data-stu-id="bfc63-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile Method</span></span>
<span data-ttu-id="bfc63-103">Obtém um [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) instância que contém uma lista de assemblies referenciados pelo assembly no caminho de arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="bfc63-103">Gets an [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) instance that contains a list of assemblies referenced by the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bfc63-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bfc63-104">Syntax</span></span>  
  
```  
HRESULT GetReferencedAssembliesFromFile (  
    [in]  LPCWSTR pwzFilePath,  
    [in]  DWORD   dwFlags,  
    [in]  ICLRAssemblyReferenceList   *pExcludeAssembliesList,  
    [out] ICLRReferenceAssemblyEnum  **ppReferenceEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bfc63-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bfc63-105">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="bfc63-106">[in] O caminho para o assembly a ser avaliada.</span><span class="sxs-lookup"><span data-stu-id="bfc63-106">[in] The path to the assembly to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="bfc63-107">[in] Fornecido para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="bfc63-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="bfc63-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT é o único valor que suporta a versão atual do common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="bfc63-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pExcludeAssembliesList`  
 <span data-ttu-id="bfc63-109">[in] Um ponteiro para um [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) objeto que representa os assemblies que devem ser excluídos da `ppReferenceEnum`.</span><span class="sxs-lookup"><span data-stu-id="bfc63-109">[in] A pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) object that represents assemblies that should be excluded from `ppReferenceEnum`.</span></span>  
  
 `ppReferenceEnum`  
 <span data-ttu-id="bfc63-110">[out] Um ponteiro para o endereço de um `ICLRReferenceAssemblyEnum` objeto que contém dados de identidade de assembly para assemblies referenciados pelo assembly em `pwzFilePath`, exceto os assemblies representados por `pExcludeAssembliesList`.</span><span class="sxs-lookup"><span data-stu-id="bfc63-110">[out] A pointer to the address of an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly at `pwzFilePath`, excluding the assemblies represented by `pExcludeAssembliesList`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bfc63-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="bfc63-111">Return Value</span></span>  
  
|<span data-ttu-id="bfc63-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bfc63-112">HRESULT</span></span>|<span data-ttu-id="bfc63-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="bfc63-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bfc63-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="bfc63-114">S_OK</span></span>|<span data-ttu-id="bfc63-115">O método é retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="bfc63-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="bfc63-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bfc63-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bfc63-117">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="bfc63-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="bfc63-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bfc63-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bfc63-119">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="bfc63-119">The call timed out.</span></span>|  
|<span data-ttu-id="bfc63-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bfc63-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bfc63-121">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="bfc63-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bfc63-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bfc63-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bfc63-123">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="bfc63-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bfc63-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bfc63-124">E_FAIL</span></span>|<span data-ttu-id="bfc63-125">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="bfc63-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bfc63-126">Se um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="bfc63-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bfc63-127">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="bfc63-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bfc63-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="bfc63-128">Remarks</span></span>  
 <span data-ttu-id="bfc63-129">O chamador pode optar por excluir um conjunto de referências de assembly conhecidos da lista retornada.</span><span class="sxs-lookup"><span data-stu-id="bfc63-129">The caller can choose to exclude a set of known assembly references from the returned list.</span></span> <span data-ttu-id="bfc63-130">Este conjunto é definido com o `pExcludeAssembliesList` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="bfc63-130">This set is defined by the `pExcludeAssembliesList` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bfc63-131">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bfc63-131">Requirements</span></span>  
 <span data-ttu-id="bfc63-132">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bfc63-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bfc63-133">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bfc63-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bfc63-134">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="bfc63-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bfc63-135">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bfc63-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfc63-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bfc63-136">See Also</span></span>  
 [<span data-ttu-id="bfc63-137">Interface ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="bfc63-137">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="bfc63-138">Interface ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="bfc63-138">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="bfc63-139">Interface ICLRReferenceAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="bfc63-139">ICLRReferenceAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)
