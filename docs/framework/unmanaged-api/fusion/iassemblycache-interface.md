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
ms.openlocfilehash: 4302a73f9f077c2e1bf4f66c2b80ab025ae4a62c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430577"
---
# <a name="iassemblycache-interface"></a><span data-ttu-id="36632-102">Interface IAssemblyCache</span><span class="sxs-lookup"><span data-stu-id="36632-102">IAssemblyCache Interface</span></span>
<span data-ttu-id="36632-103">Representa o cache de assembly global para uso pela tecnologia de fusão.</span><span class="sxs-lookup"><span data-stu-id="36632-103">Represents the global assembly cache for use by the fusion technology.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="36632-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="36632-104">Methods</span></span>  
  
|<span data-ttu-id="36632-105">Método</span><span class="sxs-lookup"><span data-stu-id="36632-105">Method</span></span>|<span data-ttu-id="36632-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="36632-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="36632-107">Método CreateAssemblyCacheItem</span><span class="sxs-lookup"><span data-stu-id="36632-107">CreateAssemblyCacheItem Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-createassemblycacheitem-method.md)|<span data-ttu-id="36632-108">Obtém uma referência a um novo [IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md).</span><span class="sxs-lookup"><span data-stu-id="36632-108">Gets a reference to a new [IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md).</span></span>|  
|[<span data-ttu-id="36632-109">Método CreateAssemblyScavenger</span><span class="sxs-lookup"><span data-stu-id="36632-109">CreateAssemblyScavenger Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-createassemblyscavenger-method.md)|<span data-ttu-id="36632-110">Reservado para uso interno pela tecnologia de fusão.</span><span class="sxs-lookup"><span data-stu-id="36632-110">Reserved for internal use by the fusion technology.</span></span>|  
|[<span data-ttu-id="36632-111">Método InstallAssembly</span><span class="sxs-lookup"><span data-stu-id="36632-111">InstallAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-installassembly-method.md)|<span data-ttu-id="36632-112">Instala o assembly especificado no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="36632-112">Installs the specified assembly in the global assembly cache.</span></span>|  
|[<span data-ttu-id="36632-113">Método QueryAssemblyInfo</span><span class="sxs-lookup"><span data-stu-id="36632-113">QueryAssemblyInfo Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-queryassemblyinfo-method.md)|<span data-ttu-id="36632-114">Obtém os dados solicitados sobre o assembly especificado.</span><span class="sxs-lookup"><span data-stu-id="36632-114">Gets the requested data about the specified assembly.</span></span>|  
|[<span data-ttu-id="36632-115">Método UninstallAssembly</span><span class="sxs-lookup"><span data-stu-id="36632-115">UninstallAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-uninstallassembly-method.md)|<span data-ttu-id="36632-116">Desinstala o assembly especificado do cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="36632-116">Uninstalls the specified assembly from the global assembly cache.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="36632-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="36632-117">Requirements</span></span>  
 <span data-ttu-id="36632-118">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36632-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36632-119">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="36632-119">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="36632-120">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36632-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36632-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="36632-121">See Also</span></span>  
 [<span data-ttu-id="36632-122">Interfaces de fusão</span><span class="sxs-lookup"><span data-stu-id="36632-122">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [<span data-ttu-id="36632-123">Cache de assembly global</span><span class="sxs-lookup"><span data-stu-id="36632-123">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
