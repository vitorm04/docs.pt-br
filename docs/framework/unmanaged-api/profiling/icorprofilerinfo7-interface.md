---
title: Interface ICorProfilerInfo7
ms.date: 03/30/2017
ms.assetid: cf37c462-73c5-412a-a7f8-bb26ca746313
ms.openlocfilehash: 0e9f76717aeff27e863245faac241927e7495076
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495483"
---
# <a name="icorprofilerinfo7-interface"></a><span data-ttu-id="63109-102">Interface ICorProfilerInfo7</span><span class="sxs-lookup"><span data-stu-id="63109-102">ICorProfilerInfo7 Interface</span></span>
<span data-ttu-id="63109-103">[Com suporte no .NET Framework 4.6.1 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="63109-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="63109-104">Uma subclasse de [ICorProfilerInfo6](icorprofilerinfo6-interface.md) que fornece um método para aplicar metadados definidos recentemente a um módulo e que fornece acesso a um fluxo de símbolo na memória.</span><span class="sxs-lookup"><span data-stu-id="63109-104">A subclass of [ICorProfilerInfo6](icorprofilerinfo6-interface.md) that provides a method to apply newly defined metadata to a module and that provides access to an in-memory symbol stream.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="63109-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="63109-105">Methods</span></span>  
  
|<span data-ttu-id="63109-106">Método</span><span class="sxs-lookup"><span data-stu-id="63109-106">Method</span></span>|<span data-ttu-id="63109-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="63109-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="63109-108">Método ApplyMetaData</span><span class="sxs-lookup"><span data-stu-id="63109-108">ApplyMetaData Method</span></span>](icorprofilerinfo7-applymetadata-method.md)|<span data-ttu-id="63109-109">Aplica os metadados recentemente definidos pelos `IMetadataEmit::Define*` métodos a um módulo especificado.</span><span class="sxs-lookup"><span data-stu-id="63109-109">Applies the metadata newly defined by the `IMetadataEmit::Define*` methods to a specified module.</span></span>|  
|[<span data-ttu-id="63109-110">Método GetInMemorySymbolsLength</span><span class="sxs-lookup"><span data-stu-id="63109-110">GetInMemorySymbolsLength Method</span></span>](icorprofilerinfo7-getinmemorysymbolslength-method.md)|<span data-ttu-id="63109-111">Retorna o comprimento de um fluxo de símbolo na memória.</span><span class="sxs-lookup"><span data-stu-id="63109-111">Returns the length of an in-memory symbol stream.</span></span>|  
|[<span data-ttu-id="63109-112">ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="63109-112">ReadInMemorySymbols</span></span>](icorprofilerinfo7-readinmemorysymbols.md)|<span data-ttu-id="63109-113">Lê bytes de um fluxo de símbolo na memória.</span><span class="sxs-lookup"><span data-stu-id="63109-113">Reads bytes from an in-memory symbol stream.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="63109-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="63109-114">Requirements</span></span>  
 <span data-ttu-id="63109-115">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63109-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63109-116">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="63109-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="63109-117">**.NET Framework versões:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63109-117">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63109-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="63109-118">See also</span></span>

- [<span data-ttu-id="63109-119">Criação de perfil de interfaces</span><span class="sxs-lookup"><span data-stu-id="63109-119">Profiling Interfaces</span></span>](profiling-interfaces.md)
