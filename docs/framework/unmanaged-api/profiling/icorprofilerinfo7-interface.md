---
title: Interface ICorProfilerInfo7
ms.date: 03/30/2017
ms.assetid: cf37c462-73c5-412a-a7f8-bb26ca746313
ms.openlocfilehash: 4c7e94ffa60bcfaead009e1a8baa9b54b2e8ab7e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125062"
---
# <a name="icorprofilerinfo7-interface"></a><span data-ttu-id="921c7-102">Interface ICorProfilerInfo7</span><span class="sxs-lookup"><span data-stu-id="921c7-102">ICorProfilerInfo7 Interface</span></span>
<span data-ttu-id="921c7-103">[Com suporte no .NET Framework 4.6.1 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="921c7-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="921c7-104">Uma subclasse de [ICorProfilerInfo6](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md) que fornece um método para aplicar metadados definidos recentemente a um módulo e que fornece acesso a um fluxo de símbolo na memória.</span><span class="sxs-lookup"><span data-stu-id="921c7-104">A subclass of [ICorProfilerInfo6](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md) that provides a method to apply newly defined metadata to a module and that provides access to an in-memory symbol stream.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="921c7-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="921c7-105">Methods</span></span>  
  
|<span data-ttu-id="921c7-106">Método</span><span class="sxs-lookup"><span data-stu-id="921c7-106">Method</span></span>|<span data-ttu-id="921c7-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="921c7-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="921c7-108">Método ApplyMetaData</span><span class="sxs-lookup"><span data-stu-id="921c7-108">ApplyMetaData Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-applymetadata-method.md)|<span data-ttu-id="921c7-109">Aplica os metadados recentemente definidos pelos métodos de `IMetadataEmit::Define*` a um módulo especificado.</span><span class="sxs-lookup"><span data-stu-id="921c7-109">Applies the metadata newly defined by the `IMetadataEmit::Define*` methods to a specified module.</span></span>|  
|[<span data-ttu-id="921c7-110">Método GetInMemorySymbolsLength</span><span class="sxs-lookup"><span data-stu-id="921c7-110">GetInMemorySymbolsLength Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-getinmemorysymbolslength-method.md)|<span data-ttu-id="921c7-111">Retorna o comprimento de um fluxo de símbolo na memória.</span><span class="sxs-lookup"><span data-stu-id="921c7-111">Returns the length of an in-memory symbol stream.</span></span>|  
|[<span data-ttu-id="921c7-112">ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="921c7-112">ReadInMemorySymbols</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-readinmemorysymbols.md)|<span data-ttu-id="921c7-113">Lê bytes de um fluxo de símbolo na memória.</span><span class="sxs-lookup"><span data-stu-id="921c7-113">Reads bytes from an in-memory symbol stream.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="921c7-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="921c7-114">Requirements</span></span>  
 <span data-ttu-id="921c7-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="921c7-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="921c7-116">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="921c7-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="921c7-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="921c7-117">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="921c7-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="921c7-118">See also</span></span>

- [<span data-ttu-id="921c7-119">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="921c7-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
