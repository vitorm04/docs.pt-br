---
title: Interface IAssemblyCache
ms.date: 03/30/2017
api_name:
- IAssemblyCache
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCache
helpviewer_keywords:
- IAssemblyCache interface [.NET Framework fusion]
ms.assetid: 71ea170f-872d-4fc5-81b6-27da1dec9b19
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9fc5f3a3d5bc5699a596bcc648a7153190c130f0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59075621"
---
# <a name="iassemblycache-interface"></a><span data-ttu-id="38704-102">Interface IAssemblyCache</span><span class="sxs-lookup"><span data-stu-id="38704-102">IAssemblyCache Interface</span></span>
<span data-ttu-id="38704-103">Representa o cache de assembly global para uso pela tecnologia de fusão.</span><span class="sxs-lookup"><span data-stu-id="38704-103">Represents the global assembly cache for use by the fusion technology.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="38704-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="38704-104">Methods</span></span>  
  
|<span data-ttu-id="38704-105">Método</span><span class="sxs-lookup"><span data-stu-id="38704-105">Method</span></span>|<span data-ttu-id="38704-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="38704-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="38704-107">Método CreateAssemblyCacheItem</span><span class="sxs-lookup"><span data-stu-id="38704-107">CreateAssemblyCacheItem Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-createassemblycacheitem-method.md)|<span data-ttu-id="38704-108">Obtém uma referência a um novo [IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md).</span><span class="sxs-lookup"><span data-stu-id="38704-108">Gets a reference to a new [IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md).</span></span>|  
|[<span data-ttu-id="38704-109">Método CreateAssemblyScavenger</span><span class="sxs-lookup"><span data-stu-id="38704-109">CreateAssemblyScavenger Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-createassemblyscavenger-method.md)|<span data-ttu-id="38704-110">Reservado para uso interno pela tecnologia de fusão.</span><span class="sxs-lookup"><span data-stu-id="38704-110">Reserved for internal use by the fusion technology.</span></span>|  
|[<span data-ttu-id="38704-111">Método InstallAssembly</span><span class="sxs-lookup"><span data-stu-id="38704-111">InstallAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-installassembly-method.md)|<span data-ttu-id="38704-112">Instala o assembly especificado no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="38704-112">Installs the specified assembly in the global assembly cache.</span></span>|  
|[<span data-ttu-id="38704-113">Método QueryAssemblyInfo</span><span class="sxs-lookup"><span data-stu-id="38704-113">QueryAssemblyInfo Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-queryassemblyinfo-method.md)|<span data-ttu-id="38704-114">Obtém os dados solicitados sobre o assembly especificado.</span><span class="sxs-lookup"><span data-stu-id="38704-114">Gets the requested data about the specified assembly.</span></span>|  
|[<span data-ttu-id="38704-115">Método UninstallAssembly</span><span class="sxs-lookup"><span data-stu-id="38704-115">UninstallAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-uninstallassembly-method.md)|<span data-ttu-id="38704-116">Desinstala o assembly especificado do cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="38704-116">Uninstalls the specified assembly from the global assembly cache.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="38704-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="38704-117">Requirements</span></span>  
 <span data-ttu-id="38704-118">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38704-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38704-119">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="38704-119">**Header:** Fusion.h</span></span>  
  
 **<span data-ttu-id="38704-120">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="38704-120">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="38704-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="38704-121">See also</span></span>

- [<span data-ttu-id="38704-122">Interfaces de fusão</span><span class="sxs-lookup"><span data-stu-id="38704-122">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [<span data-ttu-id="38704-123">Cache de assemblies global</span><span class="sxs-lookup"><span data-stu-id="38704-123">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
