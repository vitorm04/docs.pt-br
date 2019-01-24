---
title: Interface ICorProfilerInfo7
ms.date: 03/30/2017
ms.assetid: cf37c462-73c5-412a-a7f8-bb26ca746313
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c33e620b861f1065f95ba9f1f732911723c16f88
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54526266"
---
# <a name="icorprofilerinfo7-interface"></a><span data-ttu-id="eb9fc-102">Interface ICorProfilerInfo7</span><span class="sxs-lookup"><span data-stu-id="eb9fc-102">ICorProfilerInfo7 Interface</span></span>
<span data-ttu-id="eb9fc-103">[Com suporte no [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)] e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="eb9fc-103">[Supported in the [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)] and later versions]</span></span>  
  
 <span data-ttu-id="eb9fc-104">Uma subclasse de [ICorProfilerInfo6](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md) que fornece um método para aplicar recentemente definido metadados para um módulo e que fornece acesso a um fluxo de símbolo na memória.</span><span class="sxs-lookup"><span data-stu-id="eb9fc-104">A subclass of [ICorProfilerInfo6](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md) that provides a method to apply newly defined metadata to a module and that provides access to an in-memory symbol stream.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="eb9fc-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="eb9fc-105">Methods</span></span>  
  
|<span data-ttu-id="eb9fc-106">Método</span><span class="sxs-lookup"><span data-stu-id="eb9fc-106">Method</span></span>|<span data-ttu-id="eb9fc-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="eb9fc-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="eb9fc-108">Método ApplyMetaData</span><span class="sxs-lookup"><span data-stu-id="eb9fc-108">ApplyMetaData Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-applymetadata-method.md)|<span data-ttu-id="eb9fc-109">Aplica-se os metadados recentemente definido pelo `IMetadataEmit::Define*` métodos para um módulo especificado.</span><span class="sxs-lookup"><span data-stu-id="eb9fc-109">Applies the metadata newly defined by the `IMetadataEmit::Define*` methods to a specified module.</span></span>|  
|[<span data-ttu-id="eb9fc-110">Método GetInMemorySymbolsLength</span><span class="sxs-lookup"><span data-stu-id="eb9fc-110">GetInMemorySymbolsLength Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-getinmemorysymbolslength-method.md)|<span data-ttu-id="eb9fc-111">Retorna o comprimento de um fluxo de símbolo na memória.</span><span class="sxs-lookup"><span data-stu-id="eb9fc-111">Returns the length of an in-memory symbol stream.</span></span>|  
|[<span data-ttu-id="eb9fc-112">ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="eb9fc-112">ReadInMemorySymbols</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-readinmemorysymbols.md)|<span data-ttu-id="eb9fc-113">Lê os bytes do fluxo símbolo na memória.</span><span class="sxs-lookup"><span data-stu-id="eb9fc-113">Reads bytes from an in-memory symbol stream.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="eb9fc-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="eb9fc-114">Requirements</span></span>  
 <span data-ttu-id="eb9fc-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb9fc-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb9fc-116">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="eb9fc-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="eb9fc-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb9fc-117">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb9fc-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eb9fc-118">See also</span></span>
- [<span data-ttu-id="eb9fc-119">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="eb9fc-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
