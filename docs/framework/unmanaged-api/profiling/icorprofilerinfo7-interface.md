---
title: Interface ICorProfilerInfo7
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cf37c462-73c5-412a-a7f8-bb26ca746313
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 13282bec74df5e6159148aa4fbe92a84d035e044
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo7-interface"></a><span data-ttu-id="08f5a-102">Interface ICorProfilerInfo7</span><span class="sxs-lookup"><span data-stu-id="08f5a-102">ICorProfilerInfo7 Interface</span></span>
<span data-ttu-id="08f5a-103">[Com suporte no [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)] e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="08f5a-103">[Supported in the [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)] and later versions]</span></span>  
  
 <span data-ttu-id="08f5a-104">Uma subclasse de [ICorProfilerInfo6](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md) que fornece um método para aplicar recentemente definiu os metadados para um módulo e que fornece acesso a um fluxo de símbolo na memória.</span><span class="sxs-lookup"><span data-stu-id="08f5a-104">A subclass of [ICorProfilerInfo6](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md) that provides a method to apply newly defined metadata to a module and that provides access to an in-memory symbol stream.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="08f5a-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="08f5a-105">Methods</span></span>  
  
|<span data-ttu-id="08f5a-106">Método</span><span class="sxs-lookup"><span data-stu-id="08f5a-106">Method</span></span>|<span data-ttu-id="08f5a-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="08f5a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="08f5a-108">Método ApplyMetaData</span><span class="sxs-lookup"><span data-stu-id="08f5a-108">ApplyMetaData Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-applymetadata-method.md)|<span data-ttu-id="08f5a-109">Aplica-se os metadados recentemente definido pelo `IMetadataEmit::Define*` métodos para um módulo especificado.</span><span class="sxs-lookup"><span data-stu-id="08f5a-109">Applies the metadata newly defined by the `IMetadataEmit::Define*` methods to a specified module.</span></span>|  
|[<span data-ttu-id="08f5a-110">Método GetInMemorySymbolsLength</span><span class="sxs-lookup"><span data-stu-id="08f5a-110">GetInMemorySymbolsLength Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-getinmemorysymbolslength-method.md)|<span data-ttu-id="08f5a-111">Retorna o comprimento de um fluxo de símbolo na memória.</span><span class="sxs-lookup"><span data-stu-id="08f5a-111">Returns the length of an in-memory symbol stream.</span></span>|  
|[<span data-ttu-id="08f5a-112">ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="08f5a-112">ReadInMemorySymbols</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-readinmemorysymbols.md)|<span data-ttu-id="08f5a-113">Leituras de bytes de um fluxo de símbolo na memória.</span><span class="sxs-lookup"><span data-stu-id="08f5a-113">Reads bytes from an in-memory symbol stream.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="08f5a-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="08f5a-114">Requirements</span></span>  
 <span data-ttu-id="08f5a-115">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08f5a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08f5a-116">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="08f5a-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="08f5a-117">**Versões do .NET framework:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08f5a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08f5a-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="08f5a-118">See Also</span></span>  
 [<span data-ttu-id="08f5a-119">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="08f5a-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
