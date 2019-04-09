---
title: Estrutura AssemblyBindInfo
ms.date: 03/30/2017
api_name:
- AssemblyBindInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- AssemblyBindInfo
helpviewer_keywords:
- AssemblyBindInfo structure [.NET Framework hosting]
ms.assetid: 6fc01e98-c2e7-49de-ab9f-95937cc89017
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ce79987c7fcf45b8d10dcc4613e053ee735941de
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59112808"
---
# <a name="assemblybindinfo-structure"></a><span data-ttu-id="d5607-102">Estrutura AssemblyBindInfo</span><span class="sxs-lookup"><span data-stu-id="d5607-102">AssemblyBindInfo Structure</span></span>
<span data-ttu-id="d5607-103">Fornece informações detalhadas sobre o assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="d5607-103">Provides detailed information about the referenced assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5607-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d5607-104">Syntax</span></span>  
  
```  
typedef struct _AssemblyBindInfo {  
    DWORD       dwAppDomainId;  
    LPCWSTR     lpReferencedIdentity;  
    LPCWSTR     lpPostPolicyIdentity;  
    DWORD       ePolicyLevel;  
} AssemblyBindInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="d5607-105">Membros</span><span class="sxs-lookup"><span data-stu-id="d5607-105">Members</span></span>  
  
|<span data-ttu-id="d5607-106">Membro</span><span class="sxs-lookup"><span data-stu-id="d5607-106">Member</span></span>|<span data-ttu-id="d5607-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="d5607-107">Description</span></span>|  
|------------|-----------------|  
|`dwAppDomainId`|<span data-ttu-id="d5607-108">Um identificador exclusivo para o `IStream` retornado por uma chamada para [ihostassemblystore:: Provideassembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md), da qual o assembly referenciado deve ser carregado.</span><span class="sxs-lookup"><span data-stu-id="d5607-108">A unique identifier for the `IStream` returned by a call to [IHostAssemblyStore::ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md), from which the referenced assembly is to be loaded.</span></span>|  
|`lpReferencedIdentity`|<span data-ttu-id="d5607-109">Um identificador exclusivo para o assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="d5607-109">A unique identifier for the referenced assembly.</span></span>|  
|`lpPostPolicyIdentity`|<span data-ttu-id="d5607-110">O identificador para o assembly referenciado após a aplicação de quaisquer valores de política de associação.</span><span class="sxs-lookup"><span data-stu-id="d5607-110">The identifier for the referenced assembly after the application of any binding policy values.</span></span>|  
|`ePolicyLevel`|<span data-ttu-id="d5607-111">Um dos [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) valores que indicam quais políticas de controle de versão, se houver, devem ser aplicadas para o assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="d5607-111">One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values that indicate which versioning policies, if any, should be applied to the referenced assembly.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d5607-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="d5607-112">Remarks</span></span>  
 <span data-ttu-id="d5607-113">O host fornece o identificador exclusivo `dwAppDomainId` para o common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="d5607-113">The host supplies the unique identifier `dwAppDomainId` to the common language runtime (CLR).</span></span> <span data-ttu-id="d5607-114">Após uma chamada para `IHostAssemblyStore::ProvideAssembly` retorna, o tempo de execução usa o identificador para determinar se o conteúdo do `IStream` foram mapeados.</span><span class="sxs-lookup"><span data-stu-id="d5607-114">After a call to `IHostAssemblyStore::ProvideAssembly` returns, the runtime uses the identifier to determine whether the contents of the `IStream` have been mapped.</span></span> <span data-ttu-id="d5607-115">Nesse caso, o tempo de execução carrega a cópia existente em vez de remapeamento de fluxo.</span><span class="sxs-lookup"><span data-stu-id="d5607-115">If so, the runtime loads the existing copy rather than remapping the stream.</span></span> <span data-ttu-id="d5607-116">O tempo de execução também usa esse identificador como uma chave de pesquisa para fluxos retornados de chamadas para [ihostassemblystore:: Providemodule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md).</span><span class="sxs-lookup"><span data-stu-id="d5607-116">The runtime also uses this identifier as a lookup key for streams returned from calls to [IHostAssemblyStore::ProvideModule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md).</span></span> <span data-ttu-id="d5607-117">Portanto, o identificador deve ser exclusivo para solicitações do módulo e para solicitações de assembly.</span><span class="sxs-lookup"><span data-stu-id="d5607-117">Therefore, the identifier must be unique for module requests and for assembly requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5607-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d5607-118">Requirements</span></span>  
 <span data-ttu-id="d5607-119">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5607-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5607-120">**Cabeçalho:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="d5607-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="d5607-121">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="d5607-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="d5607-122">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="d5607-122">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d5607-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d5607-123">See also</span></span>

- [<span data-ttu-id="d5607-124">Estruturas de hospedagem</span><span class="sxs-lookup"><span data-stu-id="d5607-124">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [<span data-ttu-id="d5607-125">Interface ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="d5607-125">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="d5607-126">Interface ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="d5607-126">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="d5607-127">Interface IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="d5607-127">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="d5607-128">Interface IHostAssemblyStore</span><span class="sxs-lookup"><span data-stu-id="d5607-128">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
- [<span data-ttu-id="d5607-129">Estrutura ModuleBindInfo</span><span class="sxs-lookup"><span data-stu-id="d5607-129">ModuleBindInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md)
