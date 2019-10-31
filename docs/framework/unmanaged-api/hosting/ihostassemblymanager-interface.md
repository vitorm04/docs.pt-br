---
title: Interface IHostAssemblyManager
ms.date: 03/30/2017
api_name:
- IHostAssemblyManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyManager
helpviewer_keywords:
- IHostAssemblyManager interface [.NET Framework hosting]
ms.assetid: dfec05bb-3cd7-4bd5-b396-a4f097c3a636
topic_type:
- apiref
ms.openlocfilehash: d9feeaf5f85d6f84a13e74a893b82c97fdaf023c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124515"
---
# <a name="ihostassemblymanager-interface"></a><span data-ttu-id="15f15-102">Interface IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="15f15-102">IHostAssemblyManager Interface</span></span>
<span data-ttu-id="15f15-103">Fornece métodos que permitem que um host especifique conjuntos de assemblies que devem ser carregados pelo Common Language Runtime (CLR) ou pelo host.</span><span class="sxs-lookup"><span data-stu-id="15f15-103">Provides methods that allow a host to specify sets of assemblies that should be loaded by the common language runtime (CLR) or by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="15f15-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="15f15-104">Methods</span></span>  
  
|<span data-ttu-id="15f15-105">Método</span><span class="sxs-lookup"><span data-stu-id="15f15-105">Method</span></span>|<span data-ttu-id="15f15-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="15f15-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="15f15-107">Método GetAssemblyStore</span><span class="sxs-lookup"><span data-stu-id="15f15-107">GetAssemblyStore Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getassemblystore-method.md)|<span data-ttu-id="15f15-108">Obtém um ponteiro de interface para um [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) que representa a lista de assemblies carregados pelo host.</span><span class="sxs-lookup"><span data-stu-id="15f15-108">Gets an interface pointer to an [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) that represents the list of assemblies loaded by the host.</span></span>|  
|[<span data-ttu-id="15f15-109">Método GetNonHostStoreAssemblies</span><span class="sxs-lookup"><span data-stu-id="15f15-109">GetNonHostStoreAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md)|<span data-ttu-id="15f15-110">Obtém um ponteiro de interface para um [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) que representa a lista de assemblies que o host espera que o CLR carregue.</span><span class="sxs-lookup"><span data-stu-id="15f15-110">Gets an interface pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) that represents the list of assemblies that the host expects the CLR to load.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="15f15-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="15f15-111">Remarks</span></span>  
 <span data-ttu-id="15f15-112">Não é necessário que o host implemente `IHostAssemblyManager` ou `IHostAssemblyStore`.</span><span class="sxs-lookup"><span data-stu-id="15f15-112">The host is not required to implement `IHostAssemblyManager` or `IHostAssemblyStore`.</span></span> <span data-ttu-id="15f15-113">Se o host implementar `IHostAssemblyManager`, ele também deverá implementar `IHostAssemblyStore`.</span><span class="sxs-lookup"><span data-stu-id="15f15-113">If the host does implement `IHostAssemblyManager`, it must also implement `IHostAssemblyStore`.</span></span>  
  
 <span data-ttu-id="15f15-114">As consultas de tempo de execução para um `IHostAssemblyManager` chamando [IHostControl:: GetHostManager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) na inicialização com um `IID` de IID_IHostAssemblyManager.</span><span class="sxs-lookup"><span data-stu-id="15f15-114">The runtime queries for an `IHostAssemblyManager` by calling [IHostControl::GetHostManager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) upon initialization with an `IID` of IID_IHostAssemblyManager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15f15-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="15f15-115">Requirements</span></span>  
 <span data-ttu-id="15f15-116">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15f15-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15f15-117">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="15f15-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="15f15-118">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="15f15-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="15f15-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15f15-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15f15-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="15f15-120">See also</span></span>

- [<span data-ttu-id="15f15-121">Interface ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="15f15-121">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="15f15-122">Interface IHostAssemblyStore</span><span class="sxs-lookup"><span data-stu-id="15f15-122">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
- [<span data-ttu-id="15f15-123">Interface IHostControl</span><span class="sxs-lookup"><span data-stu-id="15f15-123">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
- [<span data-ttu-id="15f15-124">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="15f15-124">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
