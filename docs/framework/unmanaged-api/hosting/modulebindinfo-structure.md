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
ms.openlocfilehash: ae40d8adaae70ccff6e8058858a506267d58873f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133742"
---
# <a name="modulebindinfo-structure"></a><span data-ttu-id="5b49e-102">Estrutura ModuleBindInfo</span><span class="sxs-lookup"><span data-stu-id="5b49e-102">ModuleBindInfo Structure</span></span>
<span data-ttu-id="5b49e-103">Fornece informações detalhadas sobre o módulo referenciado e o assembly que o contém.</span><span class="sxs-lookup"><span data-stu-id="5b49e-103">Provides detailed information about the referenced module and the assembly that contains it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b49e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5b49e-104">Syntax</span></span>  
  
```cpp  
typedef struct _ModuleBindInfo {  
    DWORD    dwAppDomainId;  
    LPCWSTR  lpAssemblyIdentity;  
    LPCWSTR  lpModuleName  
} ModuleBindInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="5b49e-105">Membros</span><span class="sxs-lookup"><span data-stu-id="5b49e-105">Members</span></span>  
  
|<span data-ttu-id="5b49e-106">Membro</span><span class="sxs-lookup"><span data-stu-id="5b49e-106">Member</span></span>|<span data-ttu-id="5b49e-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="5b49e-107">Description</span></span>|  
|------------|-----------------|  
|`dwAppDomainId`|<span data-ttu-id="5b49e-108">Um identificador exclusivo para o `IStream` retornado por uma chamada para o método [IHostAssemblyStore::P rovidemodule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md) do qual o módulo referenciado deve ser carregado.</span><span class="sxs-lookup"><span data-stu-id="5b49e-108">A unique identifier for the `IStream` that is returned by a call to the [IHostAssemblyStore::ProvideModule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md) method from which the referenced module is to be loaded.</span></span>|  
|`lpAssemblyIdentity`|<span data-ttu-id="5b49e-109">Um identificador exclusivo para o assembly que contém o módulo referenciado.</span><span class="sxs-lookup"><span data-stu-id="5b49e-109">A unique identifier for the assembly that contains the referenced module.</span></span>|  
|`lpModuleName`|<span data-ttu-id="5b49e-110">O nome do módulo referenciado.</span><span class="sxs-lookup"><span data-stu-id="5b49e-110">The name of the referenced module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5b49e-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="5b49e-111">Remarks</span></span>  
 <span data-ttu-id="5b49e-112">`ModuleBindInfo` é passado como um parâmetro para `IHostAssemblyStore::ProvideModule`.</span><span class="sxs-lookup"><span data-stu-id="5b49e-112">`ModuleBindInfo` is passed as a parameter to `IHostAssemblyStore::ProvideModule`.</span></span> <span data-ttu-id="5b49e-113">O host fornece o identificador exclusivo `dwAppDomainId` para o Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="5b49e-113">The host supplies the unique identifier `dwAppDomainId` to the common language runtime (CLR).</span></span> <span data-ttu-id="5b49e-114">Após uma chamada para o método [IHostAssemblyStore::P rovideassembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) retorna, o tempo de execução usa o identificador para determinar se o conteúdo do `IStream` foi mapeado.</span><span class="sxs-lookup"><span data-stu-id="5b49e-114">After a call to the [IHostAssemblyStore::ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) method returns, the runtime uses the identifier to determine whether the contents of the `IStream` have been mapped.</span></span> <span data-ttu-id="5b49e-115">Nesse caso, o tempo de execução carrega a cópia existente em vez de remapear o fluxo.</span><span class="sxs-lookup"><span data-stu-id="5b49e-115">If so, the runtime loads the existing copy rather than remapping the stream.</span></span> <span data-ttu-id="5b49e-116">O tempo de execução também usa esse identificador como uma chave de pesquisa para fluxos que são retornados de chamadas para o método `IHostAssemblyStore::ProvideAssembly`.</span><span class="sxs-lookup"><span data-stu-id="5b49e-116">The runtime also uses this identifier as a lookup key for streams that are returned from calls to the `IHostAssemblyStore::ProvideAssembly` method.</span></span> <span data-ttu-id="5b49e-117">Portanto, o identificador deve ser exclusivo para solicitações de módulo, bem como para solicitações de assembly.</span><span class="sxs-lookup"><span data-stu-id="5b49e-117">Therefore, the identifier must be unique for module requests as well as for assembly requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b49e-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5b49e-118">Requirements</span></span>  
 <span data-ttu-id="5b49e-119">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b49e-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b49e-120">**Cabeçalho:** MSCorEE. idl</span><span class="sxs-lookup"><span data-stu-id="5b49e-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="5b49e-121">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="5b49e-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5b49e-122">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b49e-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b49e-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5b49e-123">See also</span></span>

- [<span data-ttu-id="5b49e-124">Estruturas de hospedagem</span><span class="sxs-lookup"><span data-stu-id="5b49e-124">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [<span data-ttu-id="5b49e-125">Estrutura AssemblyBindInfo</span><span class="sxs-lookup"><span data-stu-id="5b49e-125">AssemblyBindInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md)
- [<span data-ttu-id="5b49e-126">Interface ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="5b49e-126">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="5b49e-127">Interface ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="5b49e-127">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="5b49e-128">Interface IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="5b49e-128">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
