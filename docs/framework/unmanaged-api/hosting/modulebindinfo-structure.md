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
ms.openlocfilehash: 31be0525c637e50c1161129277d651b56dadfaa3
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84006747"
---
# <a name="modulebindinfo-structure"></a><span data-ttu-id="b02b6-102">Estrutura ModuleBindInfo</span><span class="sxs-lookup"><span data-stu-id="b02b6-102">ModuleBindInfo Structure</span></span>
<span data-ttu-id="b02b6-103">Fornece informações detalhadas sobre o módulo referenciado e o assembly que o contém.</span><span class="sxs-lookup"><span data-stu-id="b02b6-103">Provides detailed information about the referenced module and the assembly that contains it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b02b6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b02b6-104">Syntax</span></span>  
  
```cpp  
typedef struct _ModuleBindInfo {  
    DWORD    dwAppDomainId;  
    LPCWSTR  lpAssemblyIdentity;  
    LPCWSTR  lpModuleName  
} ModuleBindInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="b02b6-105">Membros</span><span class="sxs-lookup"><span data-stu-id="b02b6-105">Members</span></span>  
  
|<span data-ttu-id="b02b6-106">Membro</span><span class="sxs-lookup"><span data-stu-id="b02b6-106">Member</span></span>|<span data-ttu-id="b02b6-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="b02b6-107">Description</span></span>|  
|------------|-----------------|  
|`dwAppDomainId`|<span data-ttu-id="b02b6-108">Um identificador exclusivo para o `IStream` que é retornado por uma chamada para o método [IHostAssemblyStore::P rovidemodule](ihostassemblystore-providemodule-method.md) do qual o módulo referenciado deve ser carregado.</span><span class="sxs-lookup"><span data-stu-id="b02b6-108">A unique identifier for the `IStream` that is returned by a call to the [IHostAssemblyStore::ProvideModule](ihostassemblystore-providemodule-method.md) method from which the referenced module is to be loaded.</span></span>|  
|`lpAssemblyIdentity`|<span data-ttu-id="b02b6-109">Um identificador exclusivo para o assembly que contém o módulo referenciado.</span><span class="sxs-lookup"><span data-stu-id="b02b6-109">A unique identifier for the assembly that contains the referenced module.</span></span>|  
|`lpModuleName`|<span data-ttu-id="b02b6-110">O nome do módulo referenciado.</span><span class="sxs-lookup"><span data-stu-id="b02b6-110">The name of the referenced module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b02b6-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="b02b6-111">Remarks</span></span>  
 <span data-ttu-id="b02b6-112">`ModuleBindInfo`é passado como um parâmetro para `IHostAssemblyStore::ProvideModule` .</span><span class="sxs-lookup"><span data-stu-id="b02b6-112">`ModuleBindInfo` is passed as a parameter to `IHostAssemblyStore::ProvideModule`.</span></span> <span data-ttu-id="b02b6-113">O host fornece o identificador exclusivo `dwAppDomainId` para o Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="b02b6-113">The host supplies the unique identifier `dwAppDomainId` to the common language runtime (CLR).</span></span> <span data-ttu-id="b02b6-114">Após uma chamada para o método [IHostAssemblyStore::P rovideassembly](ihostassemblystore-provideassembly-method.md) retorna, o tempo de execução usa o identificador para determinar se o conteúdo do `IStream` foi mapeado.</span><span class="sxs-lookup"><span data-stu-id="b02b6-114">After a call to the [IHostAssemblyStore::ProvideAssembly](ihostassemblystore-provideassembly-method.md) method returns, the runtime uses the identifier to determine whether the contents of the `IStream` have been mapped.</span></span> <span data-ttu-id="b02b6-115">Nesse caso, o tempo de execução carrega a cópia existente em vez de remapear o fluxo.</span><span class="sxs-lookup"><span data-stu-id="b02b6-115">If so, the runtime loads the existing copy rather than remapping the stream.</span></span> <span data-ttu-id="b02b6-116">O tempo de execução também usa esse identificador como uma chave de pesquisa para fluxos que são retornados de chamadas para o `IHostAssemblyStore::ProvideAssembly` método.</span><span class="sxs-lookup"><span data-stu-id="b02b6-116">The runtime also uses this identifier as a lookup key for streams that are returned from calls to the `IHostAssemblyStore::ProvideAssembly` method.</span></span> <span data-ttu-id="b02b6-117">Portanto, o identificador deve ser exclusivo para solicitações de módulo, bem como para solicitações de assembly.</span><span class="sxs-lookup"><span data-stu-id="b02b6-117">Therefore, the identifier must be unique for module requests as well as for assembly requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b02b6-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b02b6-118">Requirements</span></span>  
 <span data-ttu-id="b02b6-119">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b02b6-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b02b6-120">**Cabeçalho:** MSCorEE. idl</span><span class="sxs-lookup"><span data-stu-id="b02b6-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="b02b6-121">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b02b6-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b02b6-122">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b02b6-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b02b6-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="b02b6-123">See also</span></span>

- [<span data-ttu-id="b02b6-124">Estruturas de hospedagem</span><span class="sxs-lookup"><span data-stu-id="b02b6-124">Hosting Structures</span></span>](hosting-structures.md)
- [<span data-ttu-id="b02b6-125">Estrutura AssemblyBindInfo</span><span class="sxs-lookup"><span data-stu-id="b02b6-125">AssemblyBindInfo Structure</span></span>](assemblybindinfo-structure.md)
- [<span data-ttu-id="b02b6-126">Interface ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="b02b6-126">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="b02b6-127">Interface ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="b02b6-127">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="b02b6-128">Interface IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="b02b6-128">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
