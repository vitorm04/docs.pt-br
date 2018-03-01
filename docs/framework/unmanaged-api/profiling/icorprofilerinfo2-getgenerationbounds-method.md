---
title: "Método ICorProfilerInfo2::GetGenerationBounds"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerInfo2.GetGenerationBounds
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetGenerationBounds
helpviewer_keywords:
- ICorProfilerInfo2::GetGenerationBounds method [.NET Framework profiling]
- GetGenerationBounds method [.NET Framework profiling]
ms.assetid: 9c37185f-d1e0-4a6e-8b99-707f7df61d88
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c84be5d7e78c348c0368e9639a470a8fc60e2ca7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2getgenerationbounds-method"></a><span data-ttu-id="90885-102">Método ICorProfilerInfo2::GetGenerationBounds</span><span class="sxs-lookup"><span data-stu-id="90885-102">ICorProfilerInfo2::GetGenerationBounds Method</span></span>
<span data-ttu-id="90885-103">Obtém as regiões de memória, que são segmentos de heap, que compõem as várias gerações de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="90885-103">Gets the memory regions, which are segments of the heap, that make up the various garbage collection generations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90885-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="90885-104">Syntax</span></span>  
  
```  
HRESULT GetGenerationBounds(  
    [in]  ULONG cObjectRanges,  
    [out] ULONG *pcObjectRanges,  
    [out, size_is(cObjectRanges), length_is(*pcObjectRanges)] COR_PRF_GC_GENERATION_RANGE ranges[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="90885-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="90885-105">Parameters</span></span>  
 `cObjectRanges`  
 <span data-ttu-id="90885-106">[in] O número de elementos alocada pelo chamador para o `ranges` matriz.</span><span class="sxs-lookup"><span data-stu-id="90885-106">[in] The number of elements allocated by the caller for the `ranges` array.</span></span>  
  
 `pcObjectRanges`  
 <span data-ttu-id="90885-107">[out] Um ponteiro para um número inteiro que especifica o número total de intervalos, alguns ou todos os quais serão retornados o `ranges` matriz.</span><span class="sxs-lookup"><span data-stu-id="90885-107">[out] A pointer to an integer that specifies the total number of ranges, some or all of which will be returned in the `ranges` array.</span></span>  
  
 `ranges`  
 <span data-ttu-id="90885-108">[out] Uma matriz de [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) estruturas, cada um deles descreve um intervalo (ou seja, o bloco) de memória dentro a geração que está passando por coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="90885-108">[out] An array of [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) structures, each of which describes a range (that is, block) of memory within the generation that is undergoing garbage collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="90885-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="90885-109">Remarks</span></span>  
 <span data-ttu-id="90885-110">O `GetGenerationBounds` método pode ser chamado de qualquer retorno de chamada do criador de perfil, desde que a coleta de lixo não está em andamento.</span><span class="sxs-lookup"><span data-stu-id="90885-110">The `GetGenerationBounds` method can be called from any profiler callback, provided that garbage collection is not in progress.</span></span> <span data-ttu-id="90885-111">Ou seja, ele pode ser chamado de qualquer retorno de chamada, exceto os que ocorrem entre [Icorprofilercallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) e [Icorprofilercallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md).</span><span class="sxs-lookup"><span data-stu-id="90885-111">That is, it can be called from any callback except those that occur between [ICorProfilerCallback2::GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) and [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md).</span></span>  
  
 <span data-ttu-id="90885-112">A maioria dos mudando de gerações ocorre durante a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="90885-112">Most shifting of generations takes place during garbage collections.</span></span> <span data-ttu-id="90885-113">Gerações podem crescer entre coleções, mas geralmente não mover.</span><span class="sxs-lookup"><span data-stu-id="90885-113">Generations might grow between collections but generally do not move around.</span></span> <span data-ttu-id="90885-114">Portanto, os locais mais interessantes para chamar `GetGenerationBounds` no `ICorProfilerCallback2::GarbageCollectionStarted` e `ICorProfilerCallback2::GarbageCollectionFinished`.</span><span class="sxs-lookup"><span data-stu-id="90885-114">Therefore, the most interesting places to call `GetGenerationBounds` are in `ICorProfilerCallback2::GarbageCollectionStarted` and `ICorProfilerCallback2::GarbageCollectionFinished`.</span></span>  
  
 <span data-ttu-id="90885-115">Durante a inicialização do programa, alguns objetos são alocados pelo common language runtime (CLR), geralmente em gerações 3 e 0.</span><span class="sxs-lookup"><span data-stu-id="90885-115">During program startup, some objects are allocated by the common language runtime (CLR) itself, generally in generations 3 and 0.</span></span> <span data-ttu-id="90885-116">Assim, quando o código gerenciado inicia a execução, essas gerações já contém objetos.</span><span class="sxs-lookup"><span data-stu-id="90885-116">Thus, by the time managed code starts executing, these generations will already contain objects.</span></span> <span data-ttu-id="90885-117">Gerações 1 e 2 normalmente estará vazias, exceto para objetos fictícios que são gerados pelo coletor de lixo.</span><span class="sxs-lookup"><span data-stu-id="90885-117">Generations 1 and 2 will normally be empty, except for dummy objects that are generated by the garbage collector.</span></span> <span data-ttu-id="90885-118">(O tamanho dos objetos fictícios será de 12 bytes em implementações de 32 bits do CLR; o tamanho é maior em implementações de 64 bits). Você também poderá ver os intervalos de geração 2 dentro de módulos produzidos pelo gerador de imagem nativa (NGen.exe).</span><span class="sxs-lookup"><span data-stu-id="90885-118">(The size of dummy objects is 12 bytes in 32-bit implementations of the CLR; the size is larger in 64-bit implementations.) You might also see generation 2 ranges that are inside modules produced by the Native Image Generator (NGen.exe).</span></span> <span data-ttu-id="90885-119">Nesse caso, os objetos na geração 2 são *congelado objetos*, que é alocado quando NGen.exe é executado em vez de pelo coletor de lixo.</span><span class="sxs-lookup"><span data-stu-id="90885-119">In this case, the objects in generation 2 are *frozen objects*, which are allocated when NGen.exe runs rather than by the garbage collector.</span></span>  
  
 <span data-ttu-id="90885-120">Essa função usa buffers alocada pelo chamador.</span><span class="sxs-lookup"><span data-stu-id="90885-120">This function uses caller-allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90885-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="90885-121">Requirements</span></span>  
 <span data-ttu-id="90885-122">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90885-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90885-123">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="90885-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="90885-124">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="90885-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="90885-125">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90885-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90885-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="90885-126">See Also</span></span>  
 [<span data-ttu-id="90885-127">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="90885-127">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="90885-128">Interface ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="90885-128">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 [<span data-ttu-id="90885-129">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="90885-129">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="90885-130">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="90885-130">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
