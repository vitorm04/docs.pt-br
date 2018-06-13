---
title: Método ICorProfilerCallback4::SurvivingReferences2
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.SurvivingReferences2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::SurvivingReferences2
helpviewer_keywords:
- ICorProfilerCallback4::SurvivingReferences2 method [.NET Framework profiling]
- SurvivingReferences2 method, ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 02b51888-5d89-4e50-a915-45b7e329aad9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: de081286096a9001ff48b565baeb47a1d1a4f28a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33460334"
---
# <a name="icorprofilercallback4survivingreferences2-method"></a><span data-ttu-id="4b8ff-102">Método ICorProfilerCallback4::SurvivingReferences2</span><span class="sxs-lookup"><span data-stu-id="4b8ff-102">ICorProfilerCallback4::SurvivingReferences2 Method</span></span>
<span data-ttu-id="4b8ff-103">Relata o layout dos objetos no heap como resultado de uma coleta de lixo não compactar.</span><span class="sxs-lookup"><span data-stu-id="4b8ff-103">Reports the layout of objects in the heap as a result of a non-compacting garbage collection.</span></span> <span data-ttu-id="4b8ff-104">Este método é chamado se o criador de perfil tiver implementado o [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="4b8ff-104">This method is called if the profiler has implemented the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interface.</span></span> <span data-ttu-id="4b8ff-105">Esse retorno de chamada substitui o [Icorprofilercallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md) método, porque ela pode relatar intervalos maiores de objetos cujos comprimentos excedem o que pode ser expressa em um ULONG.</span><span class="sxs-lookup"><span data-stu-id="4b8ff-105">This callback replaces the [ICorProfilerCallback2::SurvivingReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md) method, because it can report larger ranges of objects whose lengths exceed what can be expressed in a ULONG.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b8ff-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4b8ff-106">Syntax</span></span>  
  
```  
HRESULT SurvivingReferences2(  
    [in] ULONG  cSurvivingObjectIDRanges,  
    [in, size_is(cSurvivingObjectIDRanges)] ObjectID  
                objectIDRangeStart[] ,  
    [in, size_is(cSurvivingObjectIDRanges)] SIZE_T  
                cObjectIDRangeLength[] );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4b8ff-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4b8ff-107">Parameters</span></span>  
 `cSurvivingObjectIDRanges`  
 <span data-ttu-id="4b8ff-108">[in] O número de blocos de contíguos objetos que sobreviveram como resultado da coleta de lixo não compactar.</span><span class="sxs-lookup"><span data-stu-id="4b8ff-108">[in] The number of blocks of contiguous objects that survived as the result of the non-compacting garbage collection.</span></span> <span data-ttu-id="4b8ff-109">Ou seja, o valor de `cSurvivingObjectIDRanges` é o tamanho do `objectIDRangeStart` e `cObjectIDRangeLength` matrizes, qual repositório um `ObjectID` e um comprimento, respectivamente, para cada bloco de objetos.</span><span class="sxs-lookup"><span data-stu-id="4b8ff-109">That is, the value of `cSurvivingObjectIDRanges` is the size of the `objectIDRangeStart` and `cObjectIDRangeLength` arrays, which store an `ObjectID` and a length, respectively, for each block of objects.</span></span>  
  
 <span data-ttu-id="4b8ff-110">Os dois argumentos de `SurvivingReferences2` matrizes paralelos.</span><span class="sxs-lookup"><span data-stu-id="4b8ff-110">The next two arguments of `SurvivingReferences2` are parallel arrays.</span></span> <span data-ttu-id="4b8ff-111">Em outras palavras, `objectIDRangeStart` e `cObjectIDRangeLength` do mesmo bloco de contíguos objetos estão relacionados.</span><span class="sxs-lookup"><span data-stu-id="4b8ff-111">In other words, `objectIDRangeStart` and `cObjectIDRangeLength` concern the same block of contiguous objects.</span></span>  
  
 `objectIDRangeStart`  
 <span data-ttu-id="4b8ff-112">[in] Uma matriz de `ObjectID` valores, cada um deles é o endereço inicial de um bloco de contígua, live objetos na memória.</span><span class="sxs-lookup"><span data-stu-id="4b8ff-112">[in] An array of `ObjectID` values, each of which is the starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `cObjectIDRangeLength`  
 <span data-ttu-id="4b8ff-113">[in] Uma matriz de inteiros, cada um deles é o tamanho de um bloco sobrevivente de contíguos objetos na memória.</span><span class="sxs-lookup"><span data-stu-id="4b8ff-113">[in] An array of integers, each of which is the size of a surviving block of contiguous objects in memory.</span></span>  
  
 <span data-ttu-id="4b8ff-114">Um tamanho é especificado para cada bloco que é referenciado no `objectIDRangeStart` matriz.</span><span class="sxs-lookup"><span data-stu-id="4b8ff-114">A size is specified for each block that is referenced in the `objectIDRangeStart` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4b8ff-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="4b8ff-115">Remarks</span></span>  
 <span data-ttu-id="4b8ff-116">Os elementos do `objectIDRangeStart` e `cObjectIDRangeLength` matrizes devem ser interpretadas da seguinte maneira para determinar se um objeto sobreviveu a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="4b8ff-116">The elements of the `objectIDRangeStart` and `cObjectIDRangeLength` arrays should be interpreted as follows to determine whether an object survived the garbage collection.</span></span> <span data-ttu-id="4b8ff-117">Suponha que um `ObjectID` valor (`ObjectID`) está dentro do seguinte intervalo:</span><span class="sxs-lookup"><span data-stu-id="4b8ff-117">Assume that an `ObjectID` value (`ObjectID`) lies within the following range:</span></span>  
  
 `ObjectIDRangeStart[i]` <= `ObjectID` < `ObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 <span data-ttu-id="4b8ff-118">Para qualquer valor de `i` que está no intervalo a seguir, o objeto sobreviveu a coleta de lixo:</span><span class="sxs-lookup"><span data-stu-id="4b8ff-118">For any value of `i` that is in the following range, the object has survived the garbage collection:</span></span>  
  
 <span data-ttu-id="4b8ff-119">0 <= `i` < `cSurvivingObjectIDRanges`</span><span class="sxs-lookup"><span data-stu-id="4b8ff-119">0 <= `i` < `cSurvivingObjectIDRanges`</span></span>  
  
 <span data-ttu-id="4b8ff-120">Uma coleta de lixo não compactar recupera a memória ocupada por objetos "inativos", mas não compactar o que o espaço livre.</span><span class="sxs-lookup"><span data-stu-id="4b8ff-120">A non-compacting garbage collection reclaims the memory occupied by "dead" objects, but does not compact that freed space.</span></span> <span data-ttu-id="4b8ff-121">Como resultado, memória é retornada para o heap, mas não há objetos "ativos" são movidos.</span><span class="sxs-lookup"><span data-stu-id="4b8ff-121">As a result, memory is returned to the heap, but no "live" objects are moved.</span></span>  
  
 <span data-ttu-id="4b8ff-122">O common language runtime (CLR) chama `SurvivingReferences2` para não compactar coletas de lixo.</span><span class="sxs-lookup"><span data-stu-id="4b8ff-122">The common language runtime (CLR) calls `SurvivingReferences2` for non-compacting garbage collections.</span></span> <span data-ttu-id="4b8ff-123">Para compactar coletas de lixo, [MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) é chamado em vez disso.</span><span class="sxs-lookup"><span data-stu-id="4b8ff-123">For compacting garbage collections, [MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) is called instead.</span></span> <span data-ttu-id="4b8ff-124">Uma coleta de lixo único pode ser compactação para uma geração e não compactar para outro.</span><span class="sxs-lookup"><span data-stu-id="4b8ff-124">A single garbage collection can be compacting for one generation and non-compacting for another.</span></span> <span data-ttu-id="4b8ff-125">Para uma coleta de lixo na geração qualquer específica, o criador de perfil será exibido um `SurvivingReferences2` retorno de chamada ou uma [MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) retorno de chamada, mas não ambos.</span><span class="sxs-lookup"><span data-stu-id="4b8ff-125">For a garbage collection on any particular generation, the profiler will receive either a `SurvivingReferences2` callback or a [MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) callback, but not both.</span></span>  
  
 <span data-ttu-id="4b8ff-126">Vários `SurvivingReferences2` retornos de chamada podem ser recebidos durante uma coleta de lixo específico, devido a buffer interno limitado, vários retornos de chamada durante a coleta de lixo do servidor e outros motivos.</span><span class="sxs-lookup"><span data-stu-id="4b8ff-126">Multiple `SurvivingReferences2` callbacks might be received during a particular garbage collection, because of limited internal buffering, multiple callbacks during server garbage collection, and other reasons.</span></span> <span data-ttu-id="4b8ff-127">No caso de vários retornos de chamadas durante uma coleta de lixo, as informações são cumulativas; todas as referências são relatadas em qualquer `SurvivingReferences2` retorno de chamada sobreviver a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="4b8ff-127">In the case of multiple callbacks during a garbage collection, the information is cumulative; all references that are reported in any `SurvivingReferences2` callback survive the garbage collection.</span></span>  
  
 <span data-ttu-id="4b8ff-128">Se o criador de perfil implementa ambos o [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) e [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interfaces, o `SurvivingReferences2` método é chamado antes do [ICorProfilerCallback2:: SurvivingReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md) método, mas somente se `SurvivingReferences2` retorna com êxito.</span><span class="sxs-lookup"><span data-stu-id="4b8ff-128">If the profiler implements both the [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) and the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interfaces, the `SurvivingReferences2` method is called before the [ICorProfilerCallback2::SurvivingReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md) method, but only if `SurvivingReferences2` returns successfully.</span></span> <span data-ttu-id="4b8ff-129">Criadores de perfil podem retornar um HRESULT que indica falha a partir de `SurvivingReferences2` método para evitar o segundo método de chamada.</span><span class="sxs-lookup"><span data-stu-id="4b8ff-129">Profilers can return an HRESULT that indicates failure from the `SurvivingReferences2` method to avoid calling the second method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b8ff-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4b8ff-130">Requirements</span></span>  
 <span data-ttu-id="4b8ff-131">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b8ff-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b8ff-132">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4b8ff-132">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4b8ff-133">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4b8ff-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4b8ff-134">**Versões do .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b8ff-134">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b8ff-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4b8ff-135">See Also</span></span>  
 [<span data-ttu-id="4b8ff-136">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="4b8ff-136">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="4b8ff-137">Interface ICorProfilerCallback2</span><span class="sxs-lookup"><span data-stu-id="4b8ff-137">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 [<span data-ttu-id="4b8ff-138">Interface ICorProfilerCallback4</span><span class="sxs-lookup"><span data-stu-id="4b8ff-138">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
