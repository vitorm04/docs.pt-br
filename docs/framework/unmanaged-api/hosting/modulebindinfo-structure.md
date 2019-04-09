---
title: Estrutura ModuleBindInfo
ms.date: 03/30/2017
api_name:
- ModuleBindInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ModuleBindInfo
helpviewer_keywords:
- ModuleBindInfo structure [.NET Framework hosting]
ms.assetid: 632d4adc-dbc9-4ce8-9397-abc3285c1c69
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f14d3dcaad1cc8cac11599b1647d61df3a793301
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59124443"
---
# <a name="modulebindinfo-structure"></a><span data-ttu-id="8428b-102">Estrutura ModuleBindInfo</span><span class="sxs-lookup"><span data-stu-id="8428b-102">ModuleBindInfo Structure</span></span>
<span data-ttu-id="8428b-103">Fornece informações detalhadas sobre o módulo referenciado e o assembly que o contém.</span><span class="sxs-lookup"><span data-stu-id="8428b-103">Provides detailed information about the referenced module and the assembly that contains it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8428b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8428b-104">Syntax</span></span>  
  
```  
typedef struct _ModuleBindInfo {  
    DWORD    dwAppDomainId;  
    LPCWSTR  lpAssemblyIdentity;  
    LPCWSTR  lpModuleName  
} ModuleBindInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="8428b-105">Membros</span><span class="sxs-lookup"><span data-stu-id="8428b-105">Members</span></span>  
  
|<span data-ttu-id="8428b-106">Membro</span><span class="sxs-lookup"><span data-stu-id="8428b-106">Member</span></span>|<span data-ttu-id="8428b-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="8428b-107">Description</span></span>|  
|------------|-----------------|  
|`dwAppDomainId`|<span data-ttu-id="8428b-108">Um identificador exclusivo para o `IStream` que é retornado por uma chamada para o [ihostassemblystore:: Providemodule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md) método do qual o módulo referenciado deve ser carregado.</span><span class="sxs-lookup"><span data-stu-id="8428b-108">A unique identifier for the `IStream` that is returned by a call to the [IHostAssemblyStore::ProvideModule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md) method from which the referenced module is to be loaded.</span></span>|  
|`lpAssemblyIdentity`|<span data-ttu-id="8428b-109">Um identificador exclusivo para o assembly que contém o módulo referenciado.</span><span class="sxs-lookup"><span data-stu-id="8428b-109">A unique identifier for the assembly that contains the referenced module.</span></span>|  
|`lpModuleName`|<span data-ttu-id="8428b-110">O nome do módulo referenciado.</span><span class="sxs-lookup"><span data-stu-id="8428b-110">The name of the referenced module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8428b-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="8428b-111">Remarks</span></span>  
 `ModuleBindInfo` <span data-ttu-id="8428b-112">é passado como um parâmetro para `IHostAssemblyStore::ProvideModule`.</span><span class="sxs-lookup"><span data-stu-id="8428b-112">is passed as a parameter to `IHostAssemblyStore::ProvideModule`.</span></span> <span data-ttu-id="8428b-113">O host fornece o identificador exclusivo `dwAppDomainId` para o common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="8428b-113">The host supplies the unique identifier `dwAppDomainId` to the common language runtime (CLR).</span></span> <span data-ttu-id="8428b-114">Após uma chamada para o [ihostassemblystore:: Provideassembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) método retorna, o tempo de execução usa o identificador para determinar se o conteúdo do `IStream` foram mapeados.</span><span class="sxs-lookup"><span data-stu-id="8428b-114">After a call to the [IHostAssemblyStore::ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) method returns, the runtime uses the identifier to determine whether the contents of the `IStream` have been mapped.</span></span> <span data-ttu-id="8428b-115">Nesse caso, o tempo de execução carrega a cópia existente em vez de remapeamento de fluxo.</span><span class="sxs-lookup"><span data-stu-id="8428b-115">If so, the runtime loads the existing copy rather than remapping the stream.</span></span> <span data-ttu-id="8428b-116">O tempo de execução também usa esse identificador como uma chave de pesquisa para fluxos que são retornados de chamadas para o `IHostAssemblyStore::ProvideAssembly` método.</span><span class="sxs-lookup"><span data-stu-id="8428b-116">The runtime also uses this identifier as a lookup key for streams that are returned from calls to the `IHostAssemblyStore::ProvideAssembly` method.</span></span> <span data-ttu-id="8428b-117">Portanto, o identificador deve ser exclusivo para solicitações do módulo, bem como para solicitações de assembly.</span><span class="sxs-lookup"><span data-stu-id="8428b-117">Therefore, the identifier must be unique for module requests as well as for assembly requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8428b-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8428b-118">Requirements</span></span>  
 <span data-ttu-id="8428b-119">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8428b-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8428b-120">**Cabeçalho:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="8428b-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="8428b-121">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="8428b-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="8428b-122">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="8428b-122">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8428b-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8428b-123">See also</span></span>

- [<span data-ttu-id="8428b-124">Estruturas de hospedagem</span><span class="sxs-lookup"><span data-stu-id="8428b-124">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [<span data-ttu-id="8428b-125">Estrutura AssemblyBindInfo</span><span class="sxs-lookup"><span data-stu-id="8428b-125">AssemblyBindInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md)
- [<span data-ttu-id="8428b-126">Interface ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="8428b-126">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="8428b-127">Interface ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="8428b-127">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="8428b-128">Interface IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="8428b-128">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
