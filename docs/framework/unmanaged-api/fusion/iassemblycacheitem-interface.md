---
title: Interface IAssemblyCacheItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAssemblyCacheItem
api_location: fusion.dll
api_type: COM
f1_keywords: IAssemblyCacheItem
helpviewer_keywords: IAssemblyCacheItem interface [.NET Framework fusion]
ms.assetid: ccc9387a-9f44-4f4f-bf8f-0ea6d2afa21b
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 323b501efbdf309d5e0d595137407dd8289de17a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iassemblycacheitem-interface"></a><span data-ttu-id="2459b-102">Interface IAssemblyCacheItem</span><span class="sxs-lookup"><span data-stu-id="2459b-102">IAssemblyCacheItem Interface</span></span>
<span data-ttu-id="2459b-103">Representa um único assembly no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="2459b-103">Represents a single assembly in the global assembly cache.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2459b-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="2459b-104">Methods</span></span>  
  
|<span data-ttu-id="2459b-105">Método</span><span class="sxs-lookup"><span data-stu-id="2459b-105">Method</span></span>|<span data-ttu-id="2459b-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="2459b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2459b-107">Método AbortItem</span><span class="sxs-lookup"><span data-stu-id="2459b-107">AbortItem Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-abortitem-method.md)|<span data-ttu-id="2459b-108">Permite que o assembly no cache de assembly global executar operações de limpeza antes que ele seja liberado.</span><span class="sxs-lookup"><span data-stu-id="2459b-108">Allows the assembly in the global assembly cache to perform cleanup operations before it is released.</span></span>|  
|[<span data-ttu-id="2459b-109">Método Commit</span><span class="sxs-lookup"><span data-stu-id="2459b-109">Commit Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-commit-method.md)|<span data-ttu-id="2459b-110">Confirma a referência de assembly em cache na memória.</span><span class="sxs-lookup"><span data-stu-id="2459b-110">Commits the cached assembly reference to memory.</span></span>|  
|[<span data-ttu-id="2459b-111">Método CreateStream</span><span class="sxs-lookup"><span data-stu-id="2459b-111">CreateStream Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-createstream-method.md)|<span data-ttu-id="2459b-112">Cria um fluxo com o nome especificado e o formato.</span><span class="sxs-lookup"><span data-stu-id="2459b-112">Creates a stream with the specified name and format.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2459b-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2459b-113">Requirements</span></span>  
 <span data-ttu-id="2459b-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2459b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2459b-115">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="2459b-115">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="2459b-116">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2459b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2459b-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2459b-117">See Also</span></span>  
 [<span data-ttu-id="2459b-118">Interfaces de fusão</span><span class="sxs-lookup"><span data-stu-id="2459b-118">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [<span data-ttu-id="2459b-119">Cache de assembly global</span><span class="sxs-lookup"><span data-stu-id="2459b-119">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)  
 [<span data-ttu-id="2459b-120">Interface IAssemblyCache</span><span class="sxs-lookup"><span data-stu-id="2459b-120">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)
