---
title: Interface ICorProfilerInfo7
ms.date: 03/30/2017
ms.assetid: cf37c462-73c5-412a-a7f8-bb26ca746313
ms.openlocfilehash: f80f310c10bae33583cb7cd2048ede4f5efbe14c
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861743"
---
# <a name="icorprofilerinfo7-interface"></a><span data-ttu-id="47dc0-102">Interface ICorProfilerInfo7</span><span class="sxs-lookup"><span data-stu-id="47dc0-102">ICorProfilerInfo7 Interface</span></span>
<span data-ttu-id="47dc0-103">[Com suporte no .NET Framework 4.6.1 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="47dc0-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="47dc0-104">Uma subclasse de [ICorProfilerInfo6](icorprofilerinfo6-interface.md) que fornece um método para aplicar metadados definidos recentemente a um módulo e que fornece acesso a um fluxo de símbolo na memória.</span><span class="sxs-lookup"><span data-stu-id="47dc0-104">A subclass of [ICorProfilerInfo6](icorprofilerinfo6-interface.md) that provides a method to apply newly defined metadata to a module and that provides access to an in-memory symbol stream.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="47dc0-105">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="47dc0-105">Methods</span></span>  
  
|<span data-ttu-id="47dc0-106">Método</span><span class="sxs-lookup"><span data-stu-id="47dc0-106">Method</span></span>|<span data-ttu-id="47dc0-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="47dc0-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="47dc0-108">Método ApplyMetaData</span><span class="sxs-lookup"><span data-stu-id="47dc0-108">ApplyMetaData Method</span></span>](icorprofilerinfo7-applymetadata-method.md)|<span data-ttu-id="47dc0-109">Aplica os metadados recentemente definidos pelos métodos de `IMetadataEmit::Define*` a um módulo especificado.</span><span class="sxs-lookup"><span data-stu-id="47dc0-109">Applies the metadata newly defined by the `IMetadataEmit::Define*` methods to a specified module.</span></span>|  
|[<span data-ttu-id="47dc0-110">Método GetInMemorySymbolsLength</span><span class="sxs-lookup"><span data-stu-id="47dc0-110">GetInMemorySymbolsLength Method</span></span>](icorprofilerinfo7-getinmemorysymbolslength-method.md)|<span data-ttu-id="47dc0-111">Retorna o comprimento de um fluxo de símbolo na memória.</span><span class="sxs-lookup"><span data-stu-id="47dc0-111">Returns the length of an in-memory symbol stream.</span></span>|  
|[<span data-ttu-id="47dc0-112">ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="47dc0-112">ReadInMemorySymbols</span></span>](icorprofilerinfo7-readinmemorysymbols.md)|<span data-ttu-id="47dc0-113">Lê bytes de um fluxo de símbolo na memória.</span><span class="sxs-lookup"><span data-stu-id="47dc0-113">Reads bytes from an in-memory symbol stream.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="47dc0-114">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="47dc0-114">Requirements</span></span>  
 <span data-ttu-id="47dc0-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47dc0-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47dc0-116">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="47dc0-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="47dc0-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47dc0-117">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47dc0-118">Veja também</span><span class="sxs-lookup"><span data-stu-id="47dc0-118">See also</span></span>

- [<span data-ttu-id="47dc0-119">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="47dc0-119">Profiling Interfaces</span></span>](profiling-interfaces.md)
