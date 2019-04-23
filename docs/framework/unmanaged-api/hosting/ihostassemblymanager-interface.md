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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2e300d4645939a131ceb8206999d95056b96a678
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59118944"
---
# <a name="ihostassemblymanager-interface"></a><span data-ttu-id="3bcec-102">Interface IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="3bcec-102">IHostAssemblyManager Interface</span></span>
<span data-ttu-id="3bcec-103">Fornece métodos que permitem que um host ao especificar conjuntos de módulos (assemblies) que deve ser carregado pelo common language runtime (CLR) ou pelo host.</span><span class="sxs-lookup"><span data-stu-id="3bcec-103">Provides methods that allow a host to specify sets of assemblies that should be loaded by the common language runtime (CLR) or by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3bcec-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="3bcec-104">Methods</span></span>  
  
|<span data-ttu-id="3bcec-105">Método</span><span class="sxs-lookup"><span data-stu-id="3bcec-105">Method</span></span>|<span data-ttu-id="3bcec-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="3bcec-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3bcec-107">Método GetAssemblyStore</span><span class="sxs-lookup"><span data-stu-id="3bcec-107">GetAssemblyStore Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getassemblystore-method.md)|<span data-ttu-id="3bcec-108">Obtém um ponteiro de interface para um [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) que representa a lista de assemblies carregados pelo host.</span><span class="sxs-lookup"><span data-stu-id="3bcec-108">Gets an interface pointer to an [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) that represents the list of assemblies loaded by the host.</span></span>|  
|[<span data-ttu-id="3bcec-109">Método GetNonHostStoreAssemblies</span><span class="sxs-lookup"><span data-stu-id="3bcec-109">GetNonHostStoreAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md)|<span data-ttu-id="3bcec-110">Obtém um ponteiro de interface para um [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) que representa a lista de assemblies que o host espera para carregar o CLR.</span><span class="sxs-lookup"><span data-stu-id="3bcec-110">Gets an interface pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) that represents the list of assemblies that the host expects the CLR to load.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3bcec-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="3bcec-111">Remarks</span></span>  
 <span data-ttu-id="3bcec-112">O host não é necessário para implementar `IHostAssemblyManager` ou `IHostAssemblyStore`.</span><span class="sxs-lookup"><span data-stu-id="3bcec-112">The host is not required to implement `IHostAssemblyManager` or `IHostAssemblyStore`.</span></span> <span data-ttu-id="3bcec-113">Se o host implementa `IHostAssemblyManager`, também deve implementar `IHostAssemblyStore`.</span><span class="sxs-lookup"><span data-stu-id="3bcec-113">If the host does implement `IHostAssemblyManager`, it must also implement `IHostAssemblyStore`.</span></span>  
  
 <span data-ttu-id="3bcec-114">O tempo de execução de consulta para um `IHostAssemblyManager` chamando [ihostcontrol:: Gethostmanager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) após a inicialização com um `IID` de IID_IHostAssemblyManager.</span><span class="sxs-lookup"><span data-stu-id="3bcec-114">The runtime queries for an `IHostAssemblyManager` by calling [IHostControl::GetHostManager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) upon initialization with an `IID` of IID_IHostAssemblyManager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3bcec-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3bcec-115">Requirements</span></span>  
 <span data-ttu-id="3bcec-116">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3bcec-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3bcec-117">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3bcec-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3bcec-118">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="3bcec-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3bcec-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3bcec-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bcec-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3bcec-120">See also</span></span>

- [<span data-ttu-id="3bcec-121">Interface ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="3bcec-121">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="3bcec-122">Interface IHostAssemblyStore</span><span class="sxs-lookup"><span data-stu-id="3bcec-122">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
- [<span data-ttu-id="3bcec-123">Interface IHostControl</span><span class="sxs-lookup"><span data-stu-id="3bcec-123">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
- [<span data-ttu-id="3bcec-124">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="3bcec-124">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
