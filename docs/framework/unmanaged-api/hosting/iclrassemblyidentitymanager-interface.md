---
title: Interface ICLRAssemblyIdentityManager
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 168c67eb701d7dfc461553cfe32ed43dcea5e844
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrassemblyidentitymanager-interface"></a><span data-ttu-id="7eb5d-102">Interface ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="7eb5d-102">ICLRAssemblyIdentityManager Interface</span></span>
<span data-ttu-id="7eb5d-103">Fornece métodos que oferecem suporte a comunicação entre o host e o common language runtime (CLR) sobre assemblies.</span><span class="sxs-lookup"><span data-stu-id="7eb5d-103">Provides methods that support communication between the host and the common language runtime (CLR) about assemblies.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7eb5d-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="7eb5d-104">Methods</span></span>  
  
|<span data-ttu-id="7eb5d-105">Método</span><span class="sxs-lookup"><span data-stu-id="7eb5d-105">Method</span></span>|<span data-ttu-id="7eb5d-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="7eb5d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7eb5d-107">Método GetBindingIdentityFromFile</span><span class="sxs-lookup"><span data-stu-id="7eb5d-107">GetBindingIdentityFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromfile-method.md)|<span data-ttu-id="7eb5d-108">Obtém a identidade de assembly a associação de dados para o assembly no caminho de arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="7eb5d-108">Gets the assembly identity binding data for the assembly at the specified file path.</span></span>|  
|[<span data-ttu-id="7eb5d-109">Método GetBindingIdentityFromStream</span><span class="sxs-lookup"><span data-stu-id="7eb5d-109">GetBindingIdentityFromStream Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromstream-method.md)|<span data-ttu-id="7eb5d-110">Obtém os dados de identidade de assembly canônico para o assembly do fluxo especificado.</span><span class="sxs-lookup"><span data-stu-id="7eb5d-110">Gets the canonical assembly identity data for the assembly in the specified stream.</span></span>|  
|[<span data-ttu-id="7eb5d-111">Método GetCLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="7eb5d-111">GetCLRAssemblyReferenceList Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md)|<span data-ttu-id="7eb5d-112">Obtém um [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) instância na lista fornecida de identidades de assembly parcial.</span><span class="sxs-lookup"><span data-stu-id="7eb5d-112">Gets an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) instance from the supplied list of partial assembly identities.</span></span>|  
|[<span data-ttu-id="7eb5d-113">Método GetProbingAssembliesFromReference</span><span class="sxs-lookup"><span data-stu-id="7eb5d-113">GetProbingAssembliesFromReference Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md)|<span data-ttu-id="7eb5d-114">Obtém um [ICLRProbingAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md) enumerador para as identidades de assembly referenciado pelo assembly com a identidade especificada.</span><span class="sxs-lookup"><span data-stu-id="7eb5d-114">Gets an [ICLRProbingAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md) enumerator for the assembly identities referenced by the assembly with the specified identity.</span></span>|  
|[<span data-ttu-id="7eb5d-115">Método GetReferencedAssembliesFromFile</span><span class="sxs-lookup"><span data-stu-id="7eb5d-115">GetReferencedAssembliesFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getreferencedassembliesfromfile-method.md)|<span data-ttu-id="7eb5d-116">Obtém um [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) instância que contém uma lista de assemblies referenciados pelo assembly no caminho de arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="7eb5d-116">Gets an [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) instance that contains a list of assemblies referenced by the assembly at the specified file path.</span></span>|  
|[<span data-ttu-id="7eb5d-117">Método GetReferencedAssembliesFromStream</span><span class="sxs-lookup"><span data-stu-id="7eb5d-117">GetReferencedAssembliesFromStream Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getreferencedassembliesfromstream-method.md)|<span data-ttu-id="7eb5d-118">Obtém um ponteiro para um `ICLRReferenceAssemblyEnum` objeto que contém dados de identidade de assembly para os assemblies referenciados pelo assembly do fluxo especificado.</span><span class="sxs-lookup"><span data-stu-id="7eb5d-118">Gets a pointer to an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly in the specified stream.</span></span>|  
|[<span data-ttu-id="7eb5d-119">Método IsStronglyNamed</span><span class="sxs-lookup"><span data-stu-id="7eb5d-119">IsStronglyNamed Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-isstronglynamed-method.md)|<span data-ttu-id="7eb5d-120">Obtém um valor que indica se o assembly especificado tem um nome forte.</span><span class="sxs-lookup"><span data-stu-id="7eb5d-120">Gets a value that indicates whether the specified assembly is strongly named.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7eb5d-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="7eb5d-121">Remarks</span></span>  
 <span data-ttu-id="7eb5d-122">Use `ICLRAssemblyIdentityManager` obter instâncias de `ICLRAssemblyReferenceList` e enumerar identidades de assembly.</span><span class="sxs-lookup"><span data-stu-id="7eb5d-122">Use `ICLRAssemblyIdentityManager` to get instances of `ICLRAssemblyReferenceList` and to enumerate assembly identities.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7eb5d-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7eb5d-123">Requirements</span></span>  
 <span data-ttu-id="7eb5d-124">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7eb5d-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7eb5d-125">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7eb5d-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7eb5d-126">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="7eb5d-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7eb5d-127">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7eb5d-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7eb5d-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7eb5d-128">See Also</span></span>  
 [<span data-ttu-id="7eb5d-129">Interface ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="7eb5d-129">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="7eb5d-130">Interface ICLRProbingAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="7eb5d-130">ICLRProbingAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)  
 [<span data-ttu-id="7eb5d-131">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="7eb5d-131">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
