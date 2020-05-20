---
title: Interface ICLRAssemblyIdentityManager
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager
helpviewer_keywords:
- ICLRAssemblyIdentityManager interface [.NET Framework hosting]
ms.assetid: 6a81c6fe-cc22-4062-ae27-d6eeee03a7b9
topic_type:
- apiref
ms.openlocfilehash: f06c8228d5eb850c0d5ff94d12be03d7fb75023b
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615911"
---
# <a name="iclrassemblyidentitymanager-interface"></a><span data-ttu-id="1ce60-102">Interface ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="1ce60-102">ICLRAssemblyIdentityManager Interface</span></span>
<span data-ttu-id="1ce60-103">Fornece métodos que dão suporte à comunicação entre o host e o Common Language Runtime (CLR) sobre assemblies.</span><span class="sxs-lookup"><span data-stu-id="1ce60-103">Provides methods that support communication between the host and the common language runtime (CLR) about assemblies.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1ce60-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="1ce60-104">Methods</span></span>  
  
|<span data-ttu-id="1ce60-105">Método</span><span class="sxs-lookup"><span data-stu-id="1ce60-105">Method</span></span>|<span data-ttu-id="1ce60-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="1ce60-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1ce60-107">Método GetBindingIdentityFromFile</span><span class="sxs-lookup"><span data-stu-id="1ce60-107">GetBindingIdentityFromFile Method</span></span>](iclrassemblyidentitymanager-getbindingidentityfromfile-method.md)|<span data-ttu-id="1ce60-108">Obtém os dados de associação de identidade do assembly para o assembly no caminho de arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="1ce60-108">Gets the assembly identity binding data for the assembly at the specified file path.</span></span>|  
|[<span data-ttu-id="1ce60-109">Método GetBindingIdentityFromStream</span><span class="sxs-lookup"><span data-stu-id="1ce60-109">GetBindingIdentityFromStream Method</span></span>](iclrassemblyidentitymanager-getbindingidentityfromstream-method.md)|<span data-ttu-id="1ce60-110">Obtém os dados de identidade do assembly canônico para o assembly no fluxo especificado.</span><span class="sxs-lookup"><span data-stu-id="1ce60-110">Gets the canonical assembly identity data for the assembly in the specified stream.</span></span>|  
|[<span data-ttu-id="1ce60-111">Método GetCLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="1ce60-111">GetCLRAssemblyReferenceList Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md)|<span data-ttu-id="1ce60-112">Obtém uma instância de [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) da lista fornecida de identidades de assembly parciais.</span><span class="sxs-lookup"><span data-stu-id="1ce60-112">Gets an [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) instance from the supplied list of partial assembly identities.</span></span>|  
|[<span data-ttu-id="1ce60-113">Método GetProbingAssembliesFromReference</span><span class="sxs-lookup"><span data-stu-id="1ce60-113">GetProbingAssembliesFromReference Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md)|<span data-ttu-id="1ce60-114">Obtém um enumerador [ICLRProbingAssemblyEnum](iclrprobingassemblyenum-interface.md) para as identidades de assembly referenciadas pelo assembly com a identidade especificada.</span><span class="sxs-lookup"><span data-stu-id="1ce60-114">Gets an [ICLRProbingAssemblyEnum](iclrprobingassemblyenum-interface.md) enumerator for the assembly identities referenced by the assembly with the specified identity.</span></span>|  
|[<span data-ttu-id="1ce60-115">Método GetReferencedAssembliesFromFile</span><span class="sxs-lookup"><span data-stu-id="1ce60-115">GetReferencedAssembliesFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getreferencedassembliesfromfile-method.md)|<span data-ttu-id="1ce60-116">Obtém uma instância de [ICLRReferenceAssemblyEnum](iclrreferenceassemblyenum-interface.md) que contém uma lista de assemblies referenciados pelo assembly no caminho de arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="1ce60-116">Gets an [ICLRReferenceAssemblyEnum](iclrreferenceassemblyenum-interface.md) instance that contains a list of assemblies referenced by the assembly at the specified file path.</span></span>|  
|[<span data-ttu-id="1ce60-117">Método GetReferencedAssembliesFromStream</span><span class="sxs-lookup"><span data-stu-id="1ce60-117">GetReferencedAssembliesFromStream Method</span></span>](iclrassemblyidentitymanager-getreferencedassembliesfromstream-method.md)|<span data-ttu-id="1ce60-118">Obtém um ponteiro para um `ICLRReferenceAssemblyEnum` objeto que contém dados de identidade de assembly para os assemblies referenciados pelo assembly no fluxo especificado.</span><span class="sxs-lookup"><span data-stu-id="1ce60-118">Gets a pointer to an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly in the specified stream.</span></span>|  
|[<span data-ttu-id="1ce60-119">Método IsStronglyNamed</span><span class="sxs-lookup"><span data-stu-id="1ce60-119">IsStronglyNamed Method</span></span>](iclrassemblyidentitymanager-isstronglynamed-method.md)|<span data-ttu-id="1ce60-120">Obtém um valor que indica se o assembly especificado tem um nome forte.</span><span class="sxs-lookup"><span data-stu-id="1ce60-120">Gets a value that indicates whether the specified assembly is strongly named.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1ce60-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="1ce60-121">Remarks</span></span>  
 <span data-ttu-id="1ce60-122">Use `ICLRAssemblyIdentityManager` para obter instâncias do `ICLRAssemblyReferenceList` e para enumerar identidades de assembly.</span><span class="sxs-lookup"><span data-stu-id="1ce60-122">Use `ICLRAssemblyIdentityManager` to get instances of `ICLRAssemblyReferenceList` and to enumerate assembly identities.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ce60-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1ce60-123">Requirements</span></span>  
 <span data-ttu-id="1ce60-124">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ce60-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ce60-125">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1ce60-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1ce60-126">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1ce60-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1ce60-127">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ce60-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ce60-128">Confira também</span><span class="sxs-lookup"><span data-stu-id="1ce60-128">See also</span></span>

- [<span data-ttu-id="1ce60-129">Interface ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="1ce60-129">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="1ce60-130">Interface ICLRProbingAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="1ce60-130">ICLRProbingAssemblyEnum Interface</span></span>](iclrprobingassemblyenum-interface.md)
- [<span data-ttu-id="1ce60-131">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="1ce60-131">Hosting Interfaces</span></span>](hosting-interfaces.md)
