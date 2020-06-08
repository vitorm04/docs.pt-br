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
ms.openlocfilehash: 4e32a36a4cf751bf7c5a2c918fde0122f21b7878
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501580"
---
# <a name="ihostassemblymanager-interface"></a><span data-ttu-id="2e3a2-102">Interface IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="2e3a2-102">IHostAssemblyManager Interface</span></span>
<span data-ttu-id="2e3a2-103">Fornece métodos que permitem que um host especifique conjuntos de assemblies que devem ser carregados pelo Common Language Runtime (CLR) ou pelo host.</span><span class="sxs-lookup"><span data-stu-id="2e3a2-103">Provides methods that allow a host to specify sets of assemblies that should be loaded by the common language runtime (CLR) or by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2e3a2-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="2e3a2-104">Methods</span></span>  
  
|<span data-ttu-id="2e3a2-105">Método</span><span class="sxs-lookup"><span data-stu-id="2e3a2-105">Method</span></span>|<span data-ttu-id="2e3a2-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="2e3a2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2e3a2-107">Método GetAssemblyStore</span><span class="sxs-lookup"><span data-stu-id="2e3a2-107">GetAssemblyStore Method</span></span>](ihostassemblymanager-getassemblystore-method.md)|<span data-ttu-id="2e3a2-108">Obtém um ponteiro de interface para um [IHostAssemblyStore](ihostassemblystore-interface.md) que representa a lista de assemblies carregados pelo host.</span><span class="sxs-lookup"><span data-stu-id="2e3a2-108">Gets an interface pointer to an [IHostAssemblyStore](ihostassemblystore-interface.md) that represents the list of assemblies loaded by the host.</span></span>|  
|[<span data-ttu-id="2e3a2-109">Método GetNonHostStoreAssemblies</span><span class="sxs-lookup"><span data-stu-id="2e3a2-109">GetNonHostStoreAssemblies Method</span></span>](ihostassemblymanager-getnonhoststoreassemblies-method.md)|<span data-ttu-id="2e3a2-110">Obtém um ponteiro de interface para um [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) que representa a lista de assemblies que o host espera que o CLR carregue.</span><span class="sxs-lookup"><span data-stu-id="2e3a2-110">Gets an interface pointer to an [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) that represents the list of assemblies that the host expects the CLR to load.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2e3a2-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="2e3a2-111">Remarks</span></span>  
 <span data-ttu-id="2e3a2-112">Não é necessário que o host implemente `IHostAssemblyManager` ou `IHostAssemblyStore` .</span><span class="sxs-lookup"><span data-stu-id="2e3a2-112">The host is not required to implement `IHostAssemblyManager` or `IHostAssemblyStore`.</span></span> <span data-ttu-id="2e3a2-113">Se o host implementar `IHostAssemblyManager` , ele também deverá implementar `IHostAssemblyStore` .</span><span class="sxs-lookup"><span data-stu-id="2e3a2-113">If the host does implement `IHostAssemblyManager`, it must also implement `IHostAssemblyStore`.</span></span>  
  
 <span data-ttu-id="2e3a2-114">As consultas de tempo de execução para um `IHostAssemblyManager` chamando [IHostControl:: GetHostManager](ihostcontrol-gethostmanager-method.md) na inicialização com um `IID` de IID_IHostAssemblyManager.</span><span class="sxs-lookup"><span data-stu-id="2e3a2-114">The runtime queries for an `IHostAssemblyManager` by calling [IHostControl::GetHostManager](ihostcontrol-gethostmanager-method.md) upon initialization with an `IID` of IID_IHostAssemblyManager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e3a2-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2e3a2-115">Requirements</span></span>  
 <span data-ttu-id="2e3a2-116">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e3a2-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e3a2-117">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2e3a2-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2e3a2-118">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2e3a2-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2e3a2-119">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e3a2-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e3a2-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="2e3a2-120">See also</span></span>

- [<span data-ttu-id="2e3a2-121">Interface ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="2e3a2-121">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="2e3a2-122">Interface IHostAssemblyStore</span><span class="sxs-lookup"><span data-stu-id="2e3a2-122">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
- [<span data-ttu-id="2e3a2-123">Interface IHostControl</span><span class="sxs-lookup"><span data-stu-id="2e3a2-123">IHostControl Interface</span></span>](ihostcontrol-interface.md)
- [<span data-ttu-id="2e3a2-124">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="2e3a2-124">Hosting Interfaces</span></span>](hosting-interfaces.md)
