---
title: Método ICorProfilerInfo2::GetGenerationBounds
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 19288b5631fea8865530f936ac6d77c0286ee169
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61791659"
---
# <a name="icorprofilerinfo2getgenerationbounds-method"></a><span data-ttu-id="55298-102">Método ICorProfilerInfo2::GetGenerationBounds</span><span class="sxs-lookup"><span data-stu-id="55298-102">ICorProfilerInfo2::GetGenerationBounds Method</span></span>
<span data-ttu-id="55298-103">Obtém as regiões de memória, que são segmentos de heap, que compõem as várias gerações de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="55298-103">Gets the memory regions, which are segments of the heap, that make up the various garbage collection generations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55298-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="55298-104">Syntax</span></span>  
  
```  
HRESULT GetGenerationBounds(  
    [in]  ULONG cObjectRanges,  
    [out] ULONG *pcObjectRanges,  
    [out, size_is(cObjectRanges), length_is(*pcObjectRanges)] COR_PRF_GC_GENERATION_RANGE ranges[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="55298-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="55298-105">Parameters</span></span>  
 `cObjectRanges`  
 <span data-ttu-id="55298-106">[in] O número de elementos alocada pelo chamador para o `ranges` matriz.</span><span class="sxs-lookup"><span data-stu-id="55298-106">[in] The number of elements allocated by the caller for the `ranges` array.</span></span>  
  
 `pcObjectRanges`  
 <span data-ttu-id="55298-107">[out] Um ponteiro para um inteiro que especifica o número total de intervalos de alguns ou todos os quais serão retornados o `ranges` matriz.</span><span class="sxs-lookup"><span data-stu-id="55298-107">[out] A pointer to an integer that specifies the total number of ranges, some or all of which will be returned in the `ranges` array.</span></span>  
  
 `ranges`  
 <span data-ttu-id="55298-108">[out] Uma matriz de [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) estruturas, cada um deles descreve um intervalo (ou seja, o bloco) de memória dentro a geração que está passando por coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="55298-108">[out] An array of [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) structures, each of which describes a range (that is, block) of memory within the generation that is undergoing garbage collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="55298-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="55298-109">Remarks</span></span>  
 <span data-ttu-id="55298-110">O `GetGenerationBounds` método pode ser chamado de qualquer retorno de chamada do criador de perfil, desde que a coleta de lixo não está em andamento.</span><span class="sxs-lookup"><span data-stu-id="55298-110">The `GetGenerationBounds` method can be called from any profiler callback, provided that garbage collection is not in progress.</span></span> <span data-ttu-id="55298-111">Ou seja, ele pode ser chamado de qualquer retorno de chamada, exceto aquelas que ocorrem entre [ICorProfilerCallback2::GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) e [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md).</span><span class="sxs-lookup"><span data-stu-id="55298-111">That is, it can be called from any callback except those that occur between [ICorProfilerCallback2::GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) and [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md).</span></span>  
  
 <span data-ttu-id="55298-112">A maioria das mudança de gerações ocorre durante as coletas de lixo.</span><span class="sxs-lookup"><span data-stu-id="55298-112">Most shifting of generations takes place during garbage collections.</span></span> <span data-ttu-id="55298-113">Gerações podem crescer entre coleções, mas geralmente não mover ao redor.</span><span class="sxs-lookup"><span data-stu-id="55298-113">Generations might grow between collections but generally do not move around.</span></span> <span data-ttu-id="55298-114">Portanto, os lugares mais interessantes para chamar `GetGenerationBounds` estão na `ICorProfilerCallback2::GarbageCollectionStarted` e `ICorProfilerCallback2::GarbageCollectionFinished`.</span><span class="sxs-lookup"><span data-stu-id="55298-114">Therefore, the most interesting places to call `GetGenerationBounds` are in `ICorProfilerCallback2::GarbageCollectionStarted` and `ICorProfilerCallback2::GarbageCollectionFinished`.</span></span>  
  
 <span data-ttu-id="55298-115">Durante a inicialização do programa, alguns objetos são alocados pelo common language runtime (CLR) em si, geralmente em gerações 3 e 0.</span><span class="sxs-lookup"><span data-stu-id="55298-115">During program startup, some objects are allocated by the common language runtime (CLR) itself, generally in generations 3 and 0.</span></span> <span data-ttu-id="55298-116">Assim, quando o código gerenciado inicia a execução, essas gerações já conterá objetos.</span><span class="sxs-lookup"><span data-stu-id="55298-116">Thus, by the time managed code starts executing, these generations will already contain objects.</span></span> <span data-ttu-id="55298-117">Gerações 1 e 2 normalmente estarão vazias, exceto para objetos fictícios que são gerados pelo coletor de lixo.</span><span class="sxs-lookup"><span data-stu-id="55298-117">Generations 1 and 2 will normally be empty, except for dummy objects that are generated by the garbage collector.</span></span> <span data-ttu-id="55298-118">(O tamanho dos objetos fictícios é 12 bytes em implementações de 32 bits do CLR; o tamanho é maior em implementações de 64 bits). Você também poderá ver os intervalos de geração 2 que estão dentro de módulos produzidos pelo gerador de imagem nativa (NGen.exe).</span><span class="sxs-lookup"><span data-stu-id="55298-118">(The size of dummy objects is 12 bytes in 32-bit implementations of the CLR; the size is larger in 64-bit implementations.) You might also see generation 2 ranges that are inside modules produced by the Native Image Generator (NGen.exe).</span></span> <span data-ttu-id="55298-119">Nesse caso, os objetos na geração 2 são *congelado objetos*, que é alocado quando NGen.exe é executado em vez de pelo coletor de lixo.</span><span class="sxs-lookup"><span data-stu-id="55298-119">In this case, the objects in generation 2 are *frozen objects*, which are allocated when NGen.exe runs rather than by the garbage collector.</span></span>  
  
 <span data-ttu-id="55298-120">Essa função usa buffers alocados pelo chamador.</span><span class="sxs-lookup"><span data-stu-id="55298-120">This function uses caller-allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55298-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="55298-121">Requirements</span></span>  
 <span data-ttu-id="55298-122">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="55298-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55298-123">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="55298-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="55298-124">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="55298-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="55298-125">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55298-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55298-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="55298-126">See also</span></span>

- [<span data-ttu-id="55298-127">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="55298-127">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="55298-128">Interface ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="55298-128">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [<span data-ttu-id="55298-129">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="55298-129">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="55298-130">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="55298-130">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
