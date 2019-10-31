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
ms.openlocfilehash: f4c200ad23ff7a71298e84fda857912da53978a5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126694"
---
# <a name="iclrassemblyidentitymanagergetreferencedassembliesfromstream-method"></a><span data-ttu-id="0b74a-102">Método ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream</span><span class="sxs-lookup"><span data-stu-id="0b74a-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream Method</span></span>
<span data-ttu-id="0b74a-103">Obtém um ponteiro para um objeto [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) que contém dados de identidade de assembly para os assemblies referenciados pelo assembly no fluxo especificado.</span><span class="sxs-lookup"><span data-stu-id="0b74a-103">Gets a pointer to an [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) object that contains assembly identity data for the assemblies referenced by the assembly in the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b74a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0b74a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReferencedAssembliesFromStream (  
    [in]  IStream *pStream,  
    [in]  DWORD    dwFlags,  
    [in]  ICLRAssemblyReferenceList  *pExcludeAssembliesList,  
    [out] ICLRReferenceAssemblyEnum **ppReferenceEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0b74a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0b74a-105">Parameters</span></span>  
 `pStream`  
 <span data-ttu-id="0b74a-106">no Um ponteiro de interface para um `IStream` que contém o assembly a ser avaliado.</span><span class="sxs-lookup"><span data-stu-id="0b74a-106">[in] An interface pointer to an `IStream` containing the assembly to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="0b74a-107">no Fornecido para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="0b74a-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="0b74a-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT é o único valor para o qual a versão atual do Common Language Runtime (CLR) dá suporte.</span><span class="sxs-lookup"><span data-stu-id="0b74a-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pExcludeAssembliesList`  
 <span data-ttu-id="0b74a-109">no Um ponteiro para um objeto [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) que contém dados de identidade de assembly para os assemblies a serem excluídos do `ppReferenceEnum`.</span><span class="sxs-lookup"><span data-stu-id="0b74a-109">[in] A pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) object that contains assembly identity data for the assemblies to be excluded from `ppReferenceEnum`.</span></span>  
  
 `ppReferenceEnum`  
 <span data-ttu-id="0b74a-110">fora Um ponteiro para o endereço de um objeto de `ICLRReferenceAssemblyEnum` que contém dados de identidade de assembly para os assemblies referenciados pelo assembly no `pStream`, excluindo os assemblies no `pExcludeAssembliesList`.</span><span class="sxs-lookup"><span data-stu-id="0b74a-110">[out] A pointer to the address of an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly in `pStream`, excluding the assemblies in `pExcludeAssembliesList`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0b74a-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="0b74a-111">Return Value</span></span>  
  
|<span data-ttu-id="0b74a-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0b74a-112">HRESULT</span></span>|<span data-ttu-id="0b74a-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="0b74a-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0b74a-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="0b74a-114">S_OK</span></span>|<span data-ttu-id="0b74a-115">O método retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="0b74a-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="0b74a-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0b74a-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0b74a-117">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="0b74a-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0b74a-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0b74a-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0b74a-119">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="0b74a-119">The call timed out.</span></span>|  
|<span data-ttu-id="0b74a-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0b74a-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0b74a-121">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="0b74a-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0b74a-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0b74a-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0b74a-123">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="0b74a-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0b74a-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0b74a-124">E_FAIL</span></span>|<span data-ttu-id="0b74a-125">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="0b74a-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0b74a-126">Se um método retornar E_FAIL, o CLR não poderá mais ser usado no processo.</span><span class="sxs-lookup"><span data-stu-id="0b74a-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0b74a-127">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0b74a-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0b74a-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="0b74a-128">Remarks</span></span>  
 <span data-ttu-id="0b74a-129">O chamador pode optar por excluir um conjunto de referências de assembly conhecidas da lista retornada.</span><span class="sxs-lookup"><span data-stu-id="0b74a-129">The caller can choose to exclude a set of known assembly references from the returned list.</span></span> <span data-ttu-id="0b74a-130">Esse conjunto é definido por `pExcludeAssembliesList`.</span><span class="sxs-lookup"><span data-stu-id="0b74a-130">This set is defined by `pExcludeAssembliesList`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b74a-131">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0b74a-131">Requirements</span></span>  
 <span data-ttu-id="0b74a-132">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b74a-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b74a-133">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0b74a-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0b74a-134">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0b74a-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0b74a-135">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b74a-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b74a-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0b74a-136">See also</span></span>

- [<span data-ttu-id="0b74a-137">Interface ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="0b74a-137">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="0b74a-138">Interface ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="0b74a-138">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="0b74a-139">Interface ICLRReferenceAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="0b74a-139">ICLRReferenceAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)
