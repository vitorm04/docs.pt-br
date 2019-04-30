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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2b209e568b1e65ed785155d045cd48d1248672da
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61985030"
---
# <a name="iclrassemblyidentitymanager-interface"></a><span data-ttu-id="e21f3-102">Interface ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="e21f3-102">ICLRAssemblyIdentityManager Interface</span></span>
<span data-ttu-id="e21f3-103">Fornece métodos que oferecem suporte à comunicação entre o host e o common language runtime (CLR) sobre assemblies.</span><span class="sxs-lookup"><span data-stu-id="e21f3-103">Provides methods that support communication between the host and the common language runtime (CLR) about assemblies.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e21f3-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="e21f3-104">Methods</span></span>  
  
|<span data-ttu-id="e21f3-105">Método</span><span class="sxs-lookup"><span data-stu-id="e21f3-105">Method</span></span>|<span data-ttu-id="e21f3-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="e21f3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e21f3-107">Método GetBindingIdentityFromFile</span><span class="sxs-lookup"><span data-stu-id="e21f3-107">GetBindingIdentityFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromfile-method.md)|<span data-ttu-id="e21f3-108">Obtém a identidade do assembly a associação de dados para o assembly no caminho de arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="e21f3-108">Gets the assembly identity binding data for the assembly at the specified file path.</span></span>|  
|[<span data-ttu-id="e21f3-109">Método GetBindingIdentityFromStream</span><span class="sxs-lookup"><span data-stu-id="e21f3-109">GetBindingIdentityFromStream Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromstream-method.md)|<span data-ttu-id="e21f3-110">Obtém os dados de identidade do assembly canônico para o assembly no fluxo especificado.</span><span class="sxs-lookup"><span data-stu-id="e21f3-110">Gets the canonical assembly identity data for the assembly in the specified stream.</span></span>|  
|[<span data-ttu-id="e21f3-111">Método GetCLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="e21f3-111">GetCLRAssemblyReferenceList Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md)|<span data-ttu-id="e21f3-112">Obtém uma [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) instância na lista fornecida de identidades de assembly parcial.</span><span class="sxs-lookup"><span data-stu-id="e21f3-112">Gets an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) instance from the supplied list of partial assembly identities.</span></span>|  
|[<span data-ttu-id="e21f3-113">Método GetProbingAssembliesFromReference</span><span class="sxs-lookup"><span data-stu-id="e21f3-113">GetProbingAssembliesFromReference Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md)|<span data-ttu-id="e21f3-114">Obtém uma [ICLRProbingAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md) enumerador para as identidades de assembly referenciados pelo assembly com a identidade especificada.</span><span class="sxs-lookup"><span data-stu-id="e21f3-114">Gets an [ICLRProbingAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md) enumerator for the assembly identities referenced by the assembly with the specified identity.</span></span>|  
|[<span data-ttu-id="e21f3-115">Método GetReferencedAssembliesFromFile</span><span class="sxs-lookup"><span data-stu-id="e21f3-115">GetReferencedAssembliesFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getreferencedassembliesfromfile-method.md)|<span data-ttu-id="e21f3-116">Obtém uma [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) instância que contém uma lista de assemblies referenciados pelo assembly no caminho de arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="e21f3-116">Gets an [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) instance that contains a list of assemblies referenced by the assembly at the specified file path.</span></span>|  
|[<span data-ttu-id="e21f3-117">Método GetReferencedAssembliesFromStream</span><span class="sxs-lookup"><span data-stu-id="e21f3-117">GetReferencedAssembliesFromStream Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getreferencedassembliesfromstream-method.md)|<span data-ttu-id="e21f3-118">Obtém um ponteiro para um `ICLRReferenceAssemblyEnum` objeto que contém os dados de identidade do assembly para os assemblies referenciados pelo assembly no fluxo especificado.</span><span class="sxs-lookup"><span data-stu-id="e21f3-118">Gets a pointer to an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly in the specified stream.</span></span>|  
|[<span data-ttu-id="e21f3-119">Método IsStronglyNamed</span><span class="sxs-lookup"><span data-stu-id="e21f3-119">IsStronglyNamed Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-isstronglynamed-method.md)|<span data-ttu-id="e21f3-120">Obtém um valor que indica se o assembly especificado forte.</span><span class="sxs-lookup"><span data-stu-id="e21f3-120">Gets a value that indicates whether the specified assembly is strongly named.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e21f3-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="e21f3-121">Remarks</span></span>  
 <span data-ttu-id="e21f3-122">Use `ICLRAssemblyIdentityManager` para obter instâncias de `ICLRAssemblyReferenceList` e enumerar identidades de assembly.</span><span class="sxs-lookup"><span data-stu-id="e21f3-122">Use `ICLRAssemblyIdentityManager` to get instances of `ICLRAssemblyReferenceList` and to enumerate assembly identities.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e21f3-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e21f3-123">Requirements</span></span>  
 <span data-ttu-id="e21f3-124">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e21f3-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e21f3-125">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e21f3-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e21f3-126">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="e21f3-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e21f3-127">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e21f3-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e21f3-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e21f3-128">See also</span></span>

- [<span data-ttu-id="e21f3-129">Interface ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="e21f3-129">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="e21f3-130">Interface ICLRProbingAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="e21f3-130">ICLRProbingAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)
- [<span data-ttu-id="e21f3-131">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="e21f3-131">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
