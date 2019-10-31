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
ms.openlocfilehash: 26de2ebf1364981d8b8f1fb38c8fa1045191114f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126622"
---
# <a name="iclrassemblyidentitymanager-interface"></a><span data-ttu-id="6ebe5-102">Interface ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="6ebe5-102">ICLRAssemblyIdentityManager Interface</span></span>
<span data-ttu-id="6ebe5-103">Fornece métodos que dão suporte à comunicação entre o host e o Common Language Runtime (CLR) sobre assemblies.</span><span class="sxs-lookup"><span data-stu-id="6ebe5-103">Provides methods that support communication between the host and the common language runtime (CLR) about assemblies.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6ebe5-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="6ebe5-104">Methods</span></span>  
  
|<span data-ttu-id="6ebe5-105">Método</span><span class="sxs-lookup"><span data-stu-id="6ebe5-105">Method</span></span>|<span data-ttu-id="6ebe5-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="6ebe5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6ebe5-107">Método GetBindingIdentityFromFile</span><span class="sxs-lookup"><span data-stu-id="6ebe5-107">GetBindingIdentityFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromfile-method.md)|<span data-ttu-id="6ebe5-108">Obtém os dados de associação de identidade do assembly para o assembly no caminho de arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="6ebe5-108">Gets the assembly identity binding data for the assembly at the specified file path.</span></span>|  
|[<span data-ttu-id="6ebe5-109">Método GetBindingIdentityFromStream</span><span class="sxs-lookup"><span data-stu-id="6ebe5-109">GetBindingIdentityFromStream Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromstream-method.md)|<span data-ttu-id="6ebe5-110">Obtém os dados de identidade do assembly canônico para o assembly no fluxo especificado.</span><span class="sxs-lookup"><span data-stu-id="6ebe5-110">Gets the canonical assembly identity data for the assembly in the specified stream.</span></span>|  
|[<span data-ttu-id="6ebe5-111">Método GetCLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="6ebe5-111">GetCLRAssemblyReferenceList Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md)|<span data-ttu-id="6ebe5-112">Obtém uma instância de [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) da lista fornecida de identidades de assembly parciais.</span><span class="sxs-lookup"><span data-stu-id="6ebe5-112">Gets an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) instance from the supplied list of partial assembly identities.</span></span>|  
|[<span data-ttu-id="6ebe5-113">Método GetProbingAssembliesFromReference</span><span class="sxs-lookup"><span data-stu-id="6ebe5-113">GetProbingAssembliesFromReference Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md)|<span data-ttu-id="6ebe5-114">Obtém um enumerador [ICLRProbingAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md) para as identidades de assembly referenciadas pelo assembly com a identidade especificada.</span><span class="sxs-lookup"><span data-stu-id="6ebe5-114">Gets an [ICLRProbingAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md) enumerator for the assembly identities referenced by the assembly with the specified identity.</span></span>|  
|[<span data-ttu-id="6ebe5-115">Método GetReferencedAssembliesFromFile</span><span class="sxs-lookup"><span data-stu-id="6ebe5-115">GetReferencedAssembliesFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getreferencedassembliesfromfile-method.md)|<span data-ttu-id="6ebe5-116">Obtém uma instância de [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) que contém uma lista de assemblies referenciados pelo assembly no caminho de arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="6ebe5-116">Gets an [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) instance that contains a list of assemblies referenced by the assembly at the specified file path.</span></span>|  
|[<span data-ttu-id="6ebe5-117">Método GetReferencedAssembliesFromStream</span><span class="sxs-lookup"><span data-stu-id="6ebe5-117">GetReferencedAssembliesFromStream Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getreferencedassembliesfromstream-method.md)|<span data-ttu-id="6ebe5-118">Obtém um ponteiro para um objeto `ICLRReferenceAssemblyEnum` que contém dados de identidade de assembly para os assemblies referenciados pelo assembly no fluxo especificado.</span><span class="sxs-lookup"><span data-stu-id="6ebe5-118">Gets a pointer to an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly in the specified stream.</span></span>|  
|[<span data-ttu-id="6ebe5-119">Método IsStronglyNamed</span><span class="sxs-lookup"><span data-stu-id="6ebe5-119">IsStronglyNamed Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-isstronglynamed-method.md)|<span data-ttu-id="6ebe5-120">Obtém um valor que indica se o assembly especificado tem um nome forte.</span><span class="sxs-lookup"><span data-stu-id="6ebe5-120">Gets a value that indicates whether the specified assembly is strongly named.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6ebe5-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="6ebe5-121">Remarks</span></span>  
 <span data-ttu-id="6ebe5-122">Use `ICLRAssemblyIdentityManager` para obter instâncias de `ICLRAssemblyReferenceList` e enumerar identidades de assembly.</span><span class="sxs-lookup"><span data-stu-id="6ebe5-122">Use `ICLRAssemblyIdentityManager` to get instances of `ICLRAssemblyReferenceList` and to enumerate assembly identities.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ebe5-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6ebe5-123">Requirements</span></span>  
 <span data-ttu-id="6ebe5-124">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ebe5-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ebe5-125">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6ebe5-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6ebe5-126">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6ebe5-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6ebe5-127">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ebe5-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ebe5-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6ebe5-128">See also</span></span>

- [<span data-ttu-id="6ebe5-129">Interface ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="6ebe5-129">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="6ebe5-130">Interface ICLRProbingAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="6ebe5-130">ICLRProbingAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)
- [<span data-ttu-id="6ebe5-131">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="6ebe5-131">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
