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
ms.openlocfilehash: 615637813b08629aaea74b23fa2737f52d61bafb
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616912"
---
# <a name="assemblybindinfo-structure"></a><span data-ttu-id="80adc-102">Estrutura AssemblyBindInfo</span><span class="sxs-lookup"><span data-stu-id="80adc-102">AssemblyBindInfo Structure</span></span>
<span data-ttu-id="80adc-103">Fornece informações detalhadas sobre o assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="80adc-103">Provides detailed information about the referenced assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80adc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="80adc-104">Syntax</span></span>  
  
```cpp  
typedef struct _AssemblyBindInfo {  
    DWORD       dwAppDomainId;  
    LPCWSTR     lpReferencedIdentity;  
    LPCWSTR     lpPostPolicyIdentity;  
    DWORD       ePolicyLevel;  
} AssemblyBindInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="80adc-105">Membros</span><span class="sxs-lookup"><span data-stu-id="80adc-105">Members</span></span>  
  
|<span data-ttu-id="80adc-106">Membro</span><span class="sxs-lookup"><span data-stu-id="80adc-106">Member</span></span>|<span data-ttu-id="80adc-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="80adc-107">Description</span></span>|  
|------------|-----------------|  
|`dwAppDomainId`|<span data-ttu-id="80adc-108">Um identificador exclusivo para o `IStream` retornado por uma chamada para [IHostAssemblyStore::P rovideassembly](ihostassemblystore-provideassembly-method.md), da qual o assembly referenciado deve ser carregado.</span><span class="sxs-lookup"><span data-stu-id="80adc-108">A unique identifier for the `IStream` returned by a call to [IHostAssemblyStore::ProvideAssembly](ihostassemblystore-provideassembly-method.md), from which the referenced assembly is to be loaded.</span></span>|  
|`lpReferencedIdentity`|<span data-ttu-id="80adc-109">Um identificador exclusivo para o assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="80adc-109">A unique identifier for the referenced assembly.</span></span>|  
|`lpPostPolicyIdentity`|<span data-ttu-id="80adc-110">O identificador para o assembly referenciado após a aplicação de qualquer valor de política de associação.</span><span class="sxs-lookup"><span data-stu-id="80adc-110">The identifier for the referenced assembly after the application of any binding policy values.</span></span>|  
|`ePolicyLevel`|<span data-ttu-id="80adc-111">Um dos valores de [EPolicyAction](epolicyaction-enumeration.md) que indicam quais políticas de controle de versão, se houver, deve ser aplicado ao assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="80adc-111">One of the [EPolicyAction](epolicyaction-enumeration.md) values that indicate which versioning policies, if any, should be applied to the referenced assembly.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="80adc-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="80adc-112">Remarks</span></span>  
 <span data-ttu-id="80adc-113">O host fornece o identificador exclusivo `dwAppDomainId` para o Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="80adc-113">The host supplies the unique identifier `dwAppDomainId` to the common language runtime (CLR).</span></span> <span data-ttu-id="80adc-114">Depois de uma chamada para `IHostAssemblyStore::ProvideAssembly` retornar, o tempo de execução usa o identificador para determinar se o conteúdo do `IStream` foi mapeado.</span><span class="sxs-lookup"><span data-stu-id="80adc-114">After a call to `IHostAssemblyStore::ProvideAssembly` returns, the runtime uses the identifier to determine whether the contents of the `IStream` have been mapped.</span></span> <span data-ttu-id="80adc-115">Nesse caso, o tempo de execução carrega a cópia existente em vez de remapear o fluxo.</span><span class="sxs-lookup"><span data-stu-id="80adc-115">If so, the runtime loads the existing copy rather than remapping the stream.</span></span> <span data-ttu-id="80adc-116">O tempo de execução também usa esse identificador como uma chave de pesquisa para fluxos retornados de chamadas para [IHostAssemblyStore::P rovidemodule](ihostassemblystore-providemodule-method.md).</span><span class="sxs-lookup"><span data-stu-id="80adc-116">The runtime also uses this identifier as a lookup key for streams returned from calls to [IHostAssemblyStore::ProvideModule](ihostassemblystore-providemodule-method.md).</span></span> <span data-ttu-id="80adc-117">Portanto, o identificador deve ser exclusivo para solicitações de módulo e para solicitações de assembly.</span><span class="sxs-lookup"><span data-stu-id="80adc-117">Therefore, the identifier must be unique for module requests and for assembly requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80adc-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="80adc-118">Requirements</span></span>  
 <span data-ttu-id="80adc-119">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80adc-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80adc-120">**Cabeçalho:** MSCorEE. idl</span><span class="sxs-lookup"><span data-stu-id="80adc-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="80adc-121">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="80adc-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="80adc-122">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80adc-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80adc-123">Veja também</span><span class="sxs-lookup"><span data-stu-id="80adc-123">See also</span></span>

- [<span data-ttu-id="80adc-124">Estruturas de hospedagem</span><span class="sxs-lookup"><span data-stu-id="80adc-124">Hosting Structures</span></span>](hosting-structures.md)
- [<span data-ttu-id="80adc-125">Interface ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="80adc-125">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="80adc-126">Interface ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="80adc-126">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="80adc-127">Interface IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="80adc-127">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
- [<span data-ttu-id="80adc-128">Interface IHostAssemblyStore</span><span class="sxs-lookup"><span data-stu-id="80adc-128">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
- [<span data-ttu-id="80adc-129">Estrutura ModuleBindInfo</span><span class="sxs-lookup"><span data-stu-id="80adc-129">ModuleBindInfo Structure</span></span>](modulebindinfo-structure.md)
