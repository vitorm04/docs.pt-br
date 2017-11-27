---
title: Estrutura AssemblyBindInfo
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: AssemblyBindInfo
api_location: mscoree.dll
api_type: COM
f1_keywords: AssemblyBindInfo
helpviewer_keywords: AssemblyBindInfo structure [.NET Framework hosting]
ms.assetid: 6fc01e98-c2e7-49de-ab9f-95937cc89017
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4f23c8269c7dd7f85ad0f848c1dee2ed0bf903c0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="assemblybindinfo-structure"></a><span data-ttu-id="baad4-102">Estrutura AssemblyBindInfo</span><span class="sxs-lookup"><span data-stu-id="baad4-102">AssemblyBindInfo Structure</span></span>
<span data-ttu-id="baad4-103">Fornece informações detalhadas sobre o assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="baad4-103">Provides detailed information about the referenced assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="baad4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="baad4-104">Syntax</span></span>  
  
```  
typedef struct _AssemblyBindInfo {  
    DWORD       dwAppDomainId;  
    LPCWSTR     lpReferencedIdentity;  
    LPCWSTR     lpPostPolicyIdentity;  
    DWORD       ePolicyLevel;  
} AssemblyBindInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="baad4-105">Membros</span><span class="sxs-lookup"><span data-stu-id="baad4-105">Members</span></span>  
  
|<span data-ttu-id="baad4-106">Membro</span><span class="sxs-lookup"><span data-stu-id="baad4-106">Member</span></span>|<span data-ttu-id="baad4-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="baad4-107">Description</span></span>|  
|------------|-----------------|  
|`dwAppDomainId`|<span data-ttu-id="baad4-108">Um identificador exclusivo para o `IStream` retornado por uma chamada para [Ihostassemblystore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md), do qual o assembly referenciado está ser carregado.</span><span class="sxs-lookup"><span data-stu-id="baad4-108">A unique identifier for the `IStream` returned by a call to [IHostAssemblyStore::ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md), from which the referenced assembly is to be loaded.</span></span>|  
|`lpReferencedIdentity`|<span data-ttu-id="baad4-109">Um identificador exclusivo para o assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="baad4-109">A unique identifier for the referenced assembly.</span></span>|  
|`lpPostPolicyIdentity`|<span data-ttu-id="baad4-110">O identificador do assembly referenciado após a aplicação de quaisquer valores de política de associação.</span><span class="sxs-lookup"><span data-stu-id="baad4-110">The identifier for the referenced assembly after the application of any binding policy values.</span></span>|  
|`ePolicyLevel`|<span data-ttu-id="baad4-111">Uma da [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) valores que indicam quais políticas de controle de versão, se houver, devem ser aplicadas para o assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="baad4-111">One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values that indicate which versioning policies, if any, should be applied to the referenced assembly.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="baad4-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="baad4-112">Remarks</span></span>  
 <span data-ttu-id="baad4-113">O host fornece o identificador exclusivo `dwAppDomainId` para o common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="baad4-113">The host supplies the unique identifier `dwAppDomainId` to the common language runtime (CLR).</span></span> <span data-ttu-id="baad4-114">Após uma chamada para `IHostAssemblyStore::ProvideAssembly` retorna, o tempo de execução usa o identificador para determinar se o conteúdo do `IStream` foram mapeadas.</span><span class="sxs-lookup"><span data-stu-id="baad4-114">After a call to `IHostAssemblyStore::ProvideAssembly` returns, the runtime uses the identifier to determine whether the contents of the `IStream` have been mapped.</span></span> <span data-ttu-id="baad4-115">Nesse caso, o tempo de execução carrega a cópia existente em vez de remapeamento de fluxo.</span><span class="sxs-lookup"><span data-stu-id="baad4-115">If so, the runtime loads the existing copy rather than remapping the stream.</span></span> <span data-ttu-id="baad4-116">O tempo de execução também usa esse identificador como uma chave de pesquisa para fluxos retornados de chamadas para [Ihostassemblystore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md).</span><span class="sxs-lookup"><span data-stu-id="baad4-116">The runtime also uses this identifier as a lookup key for streams returned from calls to [IHostAssemblyStore::ProvideModule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md).</span></span> <span data-ttu-id="baad4-117">Portanto, o identificador deve ser exclusivo para solicitações de módulo e de assembly.</span><span class="sxs-lookup"><span data-stu-id="baad4-117">Therefore, the identifier must be unique for module requests and for assembly requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="baad4-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="baad4-118">Requirements</span></span>  
 <span data-ttu-id="baad4-119">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="baad4-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="baad4-120">**Cabeçalho:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="baad4-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="baad4-121">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="baad4-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="baad4-122">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="baad4-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="baad4-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="baad4-123">See Also</span></span>  
 [<span data-ttu-id="baad4-124">Estruturas de hospedagem</span><span class="sxs-lookup"><span data-stu-id="baad4-124">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
 [<span data-ttu-id="baad4-125">Interface ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="baad4-125">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="baad4-126">Interface ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="baad4-126">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="baad4-127">Interface IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="baad4-127">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [<span data-ttu-id="baad4-128">Interface IHostAssemblyStore</span><span class="sxs-lookup"><span data-stu-id="baad4-128">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)  
 [<span data-ttu-id="baad4-129">Estrutura ModuleBindInfo</span><span class="sxs-lookup"><span data-stu-id="baad4-129">ModuleBindInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md)
