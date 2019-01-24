---
title: Método ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetReferencedAssembliesFromStream
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream
helpviewer_keywords:
- ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream method [.NET Framework hosting]
- GetReferencedAssembliesFromStream method [.NET Framework hosting]
ms.assetid: fe9849c1-c3fc-477b-a31f-e8619f5516f5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 35f7e168f143d9427bf6905e9b4c383d9a40cd1b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54514446"
---
# <a name="iclrassemblyidentitymanagergetreferencedassembliesfromstream-method"></a><span data-ttu-id="dcb2a-102">Método ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream</span><span class="sxs-lookup"><span data-stu-id="dcb2a-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream Method</span></span>
<span data-ttu-id="dcb2a-103">Obtém um ponteiro para um [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) objeto que contém os dados de identidade do assembly para os assemblies referenciados pelo assembly no fluxo especificado.</span><span class="sxs-lookup"><span data-stu-id="dcb2a-103">Gets a pointer to an [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) object that contains assembly identity data for the assemblies referenced by the assembly in the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcb2a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dcb2a-104">Syntax</span></span>  
  
```  
HRESULT GetReferencedAssembliesFromStream (  
    [in]  IStream *pStream,  
    [in]  DWORD    dwFlags,  
    [in]  ICLRAssemblyReferenceList  *pExcludeAssembliesList,  
    [out] ICLRReferenceAssemblyEnum **ppReferenceEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dcb2a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dcb2a-105">Parameters</span></span>  
 `pStream`  
 <span data-ttu-id="dcb2a-106">[in] Um ponteiro de interface para um `IStream` que contém o assembly a ser avaliada.</span><span class="sxs-lookup"><span data-stu-id="dcb2a-106">[in] An interface pointer to an `IStream` containing the assembly to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="dcb2a-107">[in] Fornecido para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="dcb2a-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="dcb2a-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT é o único valor que a versão atual do common language runtime (CLR) dá suporte.</span><span class="sxs-lookup"><span data-stu-id="dcb2a-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pExcludeAssembliesList`  
 <span data-ttu-id="dcb2a-109">[in] Um ponteiro para um [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) objeto que contém dados de identidade de assembly para os assemblies a serem excluídos da `ppReferenceEnum`.</span><span class="sxs-lookup"><span data-stu-id="dcb2a-109">[in] A pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) object that contains assembly identity data for the assemblies to be excluded from `ppReferenceEnum`.</span></span>  
  
 `ppReferenceEnum`  
 <span data-ttu-id="dcb2a-110">[out] Um ponteiro para o endereço de um `ICLRReferenceAssemblyEnum` objeto que contém os dados de identidade do assembly para os assemblies referenciados pelo assembly no `pStream`, exceto os assemblies no `pExcludeAssembliesList`.</span><span class="sxs-lookup"><span data-stu-id="dcb2a-110">[out] A pointer to the address of an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly in `pStream`, excluding the assemblies in `pExcludeAssembliesList`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dcb2a-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="dcb2a-111">Return Value</span></span>  
  
|<span data-ttu-id="dcb2a-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dcb2a-112">HRESULT</span></span>|<span data-ttu-id="dcb2a-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="dcb2a-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dcb2a-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="dcb2a-114">S_OK</span></span>|<span data-ttu-id="dcb2a-115">O método é retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="dcb2a-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="dcb2a-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="dcb2a-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="dcb2a-117">O CLR não tenha sido carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="dcb2a-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="dcb2a-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="dcb2a-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="dcb2a-119">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="dcb2a-119">The call timed out.</span></span>|  
|<span data-ttu-id="dcb2a-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="dcb2a-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="dcb2a-121">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="dcb2a-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="dcb2a-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="dcb2a-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="dcb2a-123">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="dcb2a-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="dcb2a-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="dcb2a-124">E_FAIL</span></span>|<span data-ttu-id="dcb2a-125">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="dcb2a-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="dcb2a-126">Se um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="dcb2a-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="dcb2a-127">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="dcb2a-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dcb2a-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="dcb2a-128">Remarks</span></span>  
 <span data-ttu-id="dcb2a-129">O chamador pode optar por excluir um conjunto de referências de assembly conhecidos na lista retornada.</span><span class="sxs-lookup"><span data-stu-id="dcb2a-129">The caller can choose to exclude a set of known assembly references from the returned list.</span></span> <span data-ttu-id="dcb2a-130">Este conjunto é definido pela `pExcludeAssembliesList`.</span><span class="sxs-lookup"><span data-stu-id="dcb2a-130">This set is defined by `pExcludeAssembliesList`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dcb2a-131">Requisitos</span><span class="sxs-lookup"><span data-stu-id="dcb2a-131">Requirements</span></span>  
 <span data-ttu-id="dcb2a-132">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dcb2a-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dcb2a-133">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="dcb2a-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dcb2a-134">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="dcb2a-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dcb2a-135">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dcb2a-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcb2a-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dcb2a-136">See also</span></span>
- [<span data-ttu-id="dcb2a-137">Interface ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="dcb2a-137">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="dcb2a-138">Interface ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="dcb2a-138">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="dcb2a-139">Interface ICLRReferenceAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="dcb2a-139">ICLRReferenceAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)
