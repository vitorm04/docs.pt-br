---
title: Interface IHostAssemblyManager
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 351824c1b915183a8e157f5bb2e01a414027a178
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostassemblymanager-interface"></a><span data-ttu-id="69a99-102">Interface IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="69a99-102">IHostAssemblyManager Interface</span></span>
<span data-ttu-id="69a99-103">Fornece métodos que permitem que um host ao especificar conjuntos de módulos (assemblies) que deve ser carregado pelo common language runtime (CLR) ou pelo host.</span><span class="sxs-lookup"><span data-stu-id="69a99-103">Provides methods that allow a host to specify sets of assemblies that should be loaded by the common language runtime (CLR) or by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="69a99-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="69a99-104">Methods</span></span>  
  
|<span data-ttu-id="69a99-105">Método</span><span class="sxs-lookup"><span data-stu-id="69a99-105">Method</span></span>|<span data-ttu-id="69a99-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="69a99-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="69a99-107">Método GetAssemblyStore</span><span class="sxs-lookup"><span data-stu-id="69a99-107">GetAssemblyStore Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getassemblystore-method.md)|<span data-ttu-id="69a99-108">Obtém um ponteiro de interface para um [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) que representa a lista de assemblies carregados pelo host.</span><span class="sxs-lookup"><span data-stu-id="69a99-108">Gets an interface pointer to an [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) that represents the list of assemblies loaded by the host.</span></span>|  
|[<span data-ttu-id="69a99-109">Método GetNonHostStoreAssemblies</span><span class="sxs-lookup"><span data-stu-id="69a99-109">GetNonHostStoreAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md)|<span data-ttu-id="69a99-110">Obtém um ponteiro de interface para um [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) que representa a lista de assemblies para carregar o CLR espera que o host.</span><span class="sxs-lookup"><span data-stu-id="69a99-110">Gets an interface pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) that represents the list of assemblies that the host expects the CLR to load.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="69a99-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="69a99-111">Remarks</span></span>  
 <span data-ttu-id="69a99-112">O host não é necessário para implementar `IHostAssemblyManager` ou `IHostAssemblyStore`.</span><span class="sxs-lookup"><span data-stu-id="69a99-112">The host is not required to implement `IHostAssemblyManager` or `IHostAssemblyStore`.</span></span> <span data-ttu-id="69a99-113">Se o host implementar `IHostAssemblyManager`, também deve implementar `IHostAssemblyStore`.</span><span class="sxs-lookup"><span data-stu-id="69a99-113">If the host does implement `IHostAssemblyManager`, it must also implement `IHostAssemblyStore`.</span></span>  
  
 <span data-ttu-id="69a99-114">O tempo de execução de consulta para um `IHostAssemblyManager` chamando [Ihostcontrol](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) na inicialização com um `IID` de IID_IHostAssemblyManager.</span><span class="sxs-lookup"><span data-stu-id="69a99-114">The runtime queries for an `IHostAssemblyManager` by calling [IHostControl::GetHostManager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) upon initialization with an `IID` of IID_IHostAssemblyManager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69a99-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="69a99-115">Requirements</span></span>  
 <span data-ttu-id="69a99-116">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69a99-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69a99-117">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="69a99-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="69a99-118">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="69a99-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="69a99-119">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69a99-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69a99-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="69a99-120">See Also</span></span>  
 [<span data-ttu-id="69a99-121">Interface ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="69a99-121">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="69a99-122">Interface IHostAssemblyStore</span><span class="sxs-lookup"><span data-stu-id="69a99-122">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)  
 [<span data-ttu-id="69a99-123">Interface IHostControl</span><span class="sxs-lookup"><span data-stu-id="69a99-123">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)  
 [<span data-ttu-id="69a99-124">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="69a99-124">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
