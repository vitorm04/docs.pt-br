---
title: Interface IAssemblyCache
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAssemblyCache
api_location: fusion.dll
api_type: COM
f1_keywords: IAssemblyCache
helpviewer_keywords: IAssemblyCache interface [.NET Framework fusion]
ms.assetid: 71ea170f-872d-4fc5-81b6-27da1dec9b19
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6244e6c3b0cc88c50cda050a480f5af5b3996b47
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="iassemblycache-interface"></a><span data-ttu-id="c7636-102">Interface IAssemblyCache</span><span class="sxs-lookup"><span data-stu-id="c7636-102">IAssemblyCache Interface</span></span>
<span data-ttu-id="c7636-103">Representa o cache de assembly global para uso pela tecnologia de fusão.</span><span class="sxs-lookup"><span data-stu-id="c7636-103">Represents the global assembly cache for use by the fusion technology.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c7636-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="c7636-104">Methods</span></span>  
  
|<span data-ttu-id="c7636-105">Método</span><span class="sxs-lookup"><span data-stu-id="c7636-105">Method</span></span>|<span data-ttu-id="c7636-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="c7636-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c7636-107">Método CreateAssemblyCacheItem</span><span class="sxs-lookup"><span data-stu-id="c7636-107">CreateAssemblyCacheItem Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-createassemblycacheitem-method.md)|<span data-ttu-id="c7636-108">Obtém uma referência a um novo [IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md).</span><span class="sxs-lookup"><span data-stu-id="c7636-108">Gets a reference to a new [IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md).</span></span>|  
|[<span data-ttu-id="c7636-109">Método CreateAssemblyScavenger</span><span class="sxs-lookup"><span data-stu-id="c7636-109">CreateAssemblyScavenger Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-createassemblyscavenger-method.md)|<span data-ttu-id="c7636-110">Reservado para uso interno pela tecnologia de fusão.</span><span class="sxs-lookup"><span data-stu-id="c7636-110">Reserved for internal use by the fusion technology.</span></span>|  
|[<span data-ttu-id="c7636-111">Método InstallAssembly</span><span class="sxs-lookup"><span data-stu-id="c7636-111">InstallAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-installassembly-method.md)|<span data-ttu-id="c7636-112">Instala o assembly especificado no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="c7636-112">Installs the specified assembly in the global assembly cache.</span></span>|  
|[<span data-ttu-id="c7636-113">Método QueryAssemblyInfo</span><span class="sxs-lookup"><span data-stu-id="c7636-113">QueryAssemblyInfo Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-queryassemblyinfo-method.md)|<span data-ttu-id="c7636-114">Obtém os dados solicitados sobre o assembly especificado.</span><span class="sxs-lookup"><span data-stu-id="c7636-114">Gets the requested data about the specified assembly.</span></span>|  
|[<span data-ttu-id="c7636-115">Método UninstallAssembly</span><span class="sxs-lookup"><span data-stu-id="c7636-115">UninstallAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-uninstallassembly-method.md)|<span data-ttu-id="c7636-116">Desinstala o assembly especificado do cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="c7636-116">Uninstalls the specified assembly from the global assembly cache.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c7636-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c7636-117">Requirements</span></span>  
 <span data-ttu-id="c7636-118">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7636-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7636-119">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="c7636-119">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="c7636-120">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7636-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7636-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c7636-121">See Also</span></span>  
 [<span data-ttu-id="c7636-122">Interfaces de fusão</span><span class="sxs-lookup"><span data-stu-id="c7636-122">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [<span data-ttu-id="c7636-123">Cache de assembly global</span><span class="sxs-lookup"><span data-stu-id="c7636-123">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
