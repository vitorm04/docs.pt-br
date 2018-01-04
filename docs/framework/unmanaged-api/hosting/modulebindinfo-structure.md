---
title: Estrutura ModuleBindInfo
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ModuleBindInfo
api_location: mscoree.dll
api_type: COM
f1_keywords: ModuleBindInfo
helpviewer_keywords: ModuleBindInfo structure [.NET Framework hosting]
ms.assetid: 632d4adc-dbc9-4ce8-9397-abc3285c1c69
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 399ba2471b4dc7c5e372a56a9dcab8117068a693
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="modulebindinfo-structure"></a><span data-ttu-id="a61bc-102">Estrutura ModuleBindInfo</span><span class="sxs-lookup"><span data-stu-id="a61bc-102">ModuleBindInfo Structure</span></span>
<span data-ttu-id="a61bc-103">Fornece informações detalhadas sobre o módulo referenciado e o assembly que o contém.</span><span class="sxs-lookup"><span data-stu-id="a61bc-103">Provides detailed information about the referenced module and the assembly that contains it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a61bc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a61bc-104">Syntax</span></span>  
  
```  
typedef struct _ModuleBindInfo {  
    DWORD    dwAppDomainId;  
    LPCWSTR  lpAssemblyIdentity;  
    LPCWSTR  lpModuleName  
} ModuleBindInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="a61bc-105">Membros</span><span class="sxs-lookup"><span data-stu-id="a61bc-105">Members</span></span>  
  
|<span data-ttu-id="a61bc-106">Membro</span><span class="sxs-lookup"><span data-stu-id="a61bc-106">Member</span></span>|<span data-ttu-id="a61bc-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="a61bc-107">Description</span></span>|  
|------------|-----------------|  
|`dwAppDomainId`|<span data-ttu-id="a61bc-108">Um identificador exclusivo para o `IStream` que é retornado por uma chamada para o [Ihostassemblystore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md) método do qual o módulo referenciado está ser carregado.</span><span class="sxs-lookup"><span data-stu-id="a61bc-108">A unique identifier for the `IStream` that is returned by a call to the [IHostAssemblyStore::ProvideModule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md) method from which the referenced module is to be loaded.</span></span>|  
|`lpAssemblyIdentity`|<span data-ttu-id="a61bc-109">Um identificador exclusivo para o assembly que contém o módulo referenciado.</span><span class="sxs-lookup"><span data-stu-id="a61bc-109">A unique identifier for the assembly that contains the referenced module.</span></span>|  
|`lpModuleName`|<span data-ttu-id="a61bc-110">O nome do módulo referenciado.</span><span class="sxs-lookup"><span data-stu-id="a61bc-110">The name of the referenced module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a61bc-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="a61bc-111">Remarks</span></span>  
 <span data-ttu-id="a61bc-112">`ModuleBindInfo`é passado como um parâmetro para `IHostAssemblyStore::ProvideModule`.</span><span class="sxs-lookup"><span data-stu-id="a61bc-112">`ModuleBindInfo` is passed as a parameter to `IHostAssemblyStore::ProvideModule`.</span></span> <span data-ttu-id="a61bc-113">O host fornece o identificador exclusivo `dwAppDomainId` para o common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="a61bc-113">The host supplies the unique identifier `dwAppDomainId` to the common language runtime (CLR).</span></span> <span data-ttu-id="a61bc-114">Após uma chamada para o [Ihostassemblystore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) método retorna, o tempo de execução usa o identificador para determinar se o conteúdo do `IStream` foram mapeadas.</span><span class="sxs-lookup"><span data-stu-id="a61bc-114">After a call to the [IHostAssemblyStore::ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) method returns, the runtime uses the identifier to determine whether the contents of the `IStream` have been mapped.</span></span> <span data-ttu-id="a61bc-115">Nesse caso, o tempo de execução carrega a cópia existente em vez de remapeamento de fluxo.</span><span class="sxs-lookup"><span data-stu-id="a61bc-115">If so, the runtime loads the existing copy rather than remapping the stream.</span></span> <span data-ttu-id="a61bc-116">O tempo de execução também usa esse identificador como uma chave de pesquisa para fluxos que são retornados de chamadas para o `IHostAssemblyStore::ProvideAssembly` método.</span><span class="sxs-lookup"><span data-stu-id="a61bc-116">The runtime also uses this identifier as a lookup key for streams that are returned from calls to the `IHostAssemblyStore::ProvideAssembly` method.</span></span> <span data-ttu-id="a61bc-117">Portanto, o identificador deve ser exclusivo para solicitações do módulo, bem como para solicitações de assembly.</span><span class="sxs-lookup"><span data-stu-id="a61bc-117">Therefore, the identifier must be unique for module requests as well as for assembly requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a61bc-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a61bc-118">Requirements</span></span>  
 <span data-ttu-id="a61bc-119">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a61bc-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a61bc-120">**Cabeçalho:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="a61bc-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="a61bc-121">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="a61bc-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a61bc-122">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a61bc-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a61bc-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a61bc-123">See Also</span></span>  
 [<span data-ttu-id="a61bc-124">Estruturas de hospedagem</span><span class="sxs-lookup"><span data-stu-id="a61bc-124">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
 [<span data-ttu-id="a61bc-125">Estrutura AssemblyBindInfo</span><span class="sxs-lookup"><span data-stu-id="a61bc-125">AssemblyBindInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md)  
 [<span data-ttu-id="a61bc-126">Interface ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="a61bc-126">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="a61bc-127">Interface ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="a61bc-127">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="a61bc-128">Interface IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="a61bc-128">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
