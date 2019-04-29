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
ms.openlocfilehash: ad96224daf79b17d3902217af061173580f1478a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61597187"
---
# <a name="icorprofilercallback4survivingreferences2-method"></a><span data-ttu-id="2259c-102">Método ICorProfilerCallback4::SurvivingReferences2</span><span class="sxs-lookup"><span data-stu-id="2259c-102">ICorProfilerCallback4::SurvivingReferences2 Method</span></span>
<span data-ttu-id="2259c-103">Relata o layout dos objetos no heap como resultado de uma coleta de lixo sem compactação.</span><span class="sxs-lookup"><span data-stu-id="2259c-103">Reports the layout of objects in the heap as a result of a non-compacting garbage collection.</span></span> <span data-ttu-id="2259c-104">Esse método é chamado se o criador de perfil tiver implementado a [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="2259c-104">This method is called if the profiler has implemented the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interface.</span></span> <span data-ttu-id="2259c-105">Esse retorno de chamada substitui o [ICorProfilerCallback2::SurvivingReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md) método, porque ele pode relatar intervalos maiores de objetos cujo comprimento excede o que pode ser expresso em um ULONG.</span><span class="sxs-lookup"><span data-stu-id="2259c-105">This callback replaces the [ICorProfilerCallback2::SurvivingReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md) method, because it can report larger ranges of objects whose lengths exceed what can be expressed in a ULONG.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2259c-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2259c-106">Syntax</span></span>  
  
```  
HRESULT SurvivingReferences2(  
    [in] ULONG  cSurvivingObjectIDRanges,  
    [in, size_is(cSurvivingObjectIDRanges)] ObjectID  
                objectIDRangeStart[] ,  
    [in, size_is(cSurvivingObjectIDRanges)] SIZE_T  
                cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="2259c-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2259c-107">Parameters</span></span>  
 `cSurvivingObjectIDRanges`  
 <span data-ttu-id="2259c-108">[in] O número de blocos contíguos objetos que sobreviveram como resultado da coleta de lixo sem compactação.</span><span class="sxs-lookup"><span data-stu-id="2259c-108">[in] The number of blocks of contiguous objects that survived as the result of the non-compacting garbage collection.</span></span> <span data-ttu-id="2259c-109">Ou seja, o valor de `cSurvivingObjectIDRanges` é o tamanho do `objectIDRangeStart` e `cObjectIDRangeLength` matrizes, qual repositório um `ObjectID` e um comprimento, respectivamente, para cada bloco de objetos.</span><span class="sxs-lookup"><span data-stu-id="2259c-109">That is, the value of `cSurvivingObjectIDRanges` is the size of the `objectIDRangeStart` and `cObjectIDRangeLength` arrays, which store an `ObjectID` and a length, respectively, for each block of objects.</span></span>  
  
 <span data-ttu-id="2259c-110">Os próximos dois argumentos de `SurvivingReferences2` são matrizes paralelas.</span><span class="sxs-lookup"><span data-stu-id="2259c-110">The next two arguments of `SurvivingReferences2` are parallel arrays.</span></span> <span data-ttu-id="2259c-111">Em outras palavras, `objectIDRangeStart` e `cObjectIDRangeLength` referem-se do mesmo bloco de objetos contíguos.</span><span class="sxs-lookup"><span data-stu-id="2259c-111">In other words, `objectIDRangeStart` and `cObjectIDRangeLength` concern the same block of contiguous objects.</span></span>  
  
 `objectIDRangeStart`  
 <span data-ttu-id="2259c-112">[in] Uma matriz de `ObjectID` valores, cada um deles é o endereço inicial de um bloco de contíguos, live objetos na memória.</span><span class="sxs-lookup"><span data-stu-id="2259c-112">[in] An array of `ObjectID` values, each of which is the starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `cObjectIDRangeLength`  
 <span data-ttu-id="2259c-113">[in] Uma matriz de inteiros, cada um deles é o tamanho de um bloco sobrevivente de objetos adjacentes na memória.</span><span class="sxs-lookup"><span data-stu-id="2259c-113">[in] An array of integers, each of which is the size of a surviving block of contiguous objects in memory.</span></span>  
  
 <span data-ttu-id="2259c-114">Um tamanho for especificado para cada bloco que é referenciado no `objectIDRangeStart` matriz.</span><span class="sxs-lookup"><span data-stu-id="2259c-114">A size is specified for each block that is referenced in the `objectIDRangeStart` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2259c-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="2259c-115">Remarks</span></span>  
 <span data-ttu-id="2259c-116">Os elementos do `objectIDRangeStart` e `cObjectIDRangeLength` matrizes devem ser interpretadas da seguinte maneira para determinar se um objeto sobreviveu a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="2259c-116">The elements of the `objectIDRangeStart` and `cObjectIDRangeLength` arrays should be interpreted as follows to determine whether an object survived the garbage collection.</span></span> <span data-ttu-id="2259c-117">Suponha que um `ObjectID` valor (`ObjectID`) se encontra dentro do seguinte intervalo:</span><span class="sxs-lookup"><span data-stu-id="2259c-117">Assume that an `ObjectID` value (`ObjectID`) lies within the following range:</span></span>  
  
 `ObjectIDRangeStart[i]` <= `ObjectID` < `ObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 <span data-ttu-id="2259c-118">Para qualquer valor de `i` que está no intervalo a seguir, o objeto sobrevive à coleta de lixo:</span><span class="sxs-lookup"><span data-stu-id="2259c-118">For any value of `i` that is in the following range, the object has survived the garbage collection:</span></span>  
  
 <span data-ttu-id="2259c-119">0 <= `i` < `cSurvivingObjectIDRanges`</span><span class="sxs-lookup"><span data-stu-id="2259c-119">0 <= `i` < `cSurvivingObjectIDRanges`</span></span>  
  
 <span data-ttu-id="2259c-120">Uma coleta de lixo sem compactação recupera a memória ocupada por objetos "inativos", mas não compacta que o espaço livre.</span><span class="sxs-lookup"><span data-stu-id="2259c-120">A non-compacting garbage collection reclaims the memory occupied by "dead" objects, but does not compact that freed space.</span></span> <span data-ttu-id="2259c-121">Como resultado, memória é retornada para o heap, mas não há objetos "ativos" são movidos.</span><span class="sxs-lookup"><span data-stu-id="2259c-121">As a result, memory is returned to the heap, but no "live" objects are moved.</span></span>  
  
 <span data-ttu-id="2259c-122">O common language runtime (CLR) chama `SurvivingReferences2` para coletas de lixo sem compactação.</span><span class="sxs-lookup"><span data-stu-id="2259c-122">The common language runtime (CLR) calls `SurvivingReferences2` for non-compacting garbage collections.</span></span> <span data-ttu-id="2259c-123">Para compactação coletas de lixo, [MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) é chamado em vez disso.</span><span class="sxs-lookup"><span data-stu-id="2259c-123">For compacting garbage collections, [MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) is called instead.</span></span> <span data-ttu-id="2259c-124">Uma coleta de lixo único pode ser compactação para uma geração e sem compactação para outro.</span><span class="sxs-lookup"><span data-stu-id="2259c-124">A single garbage collection can be compacting for one generation and non-compacting for another.</span></span> <span data-ttu-id="2259c-125">Para uma coleta de lixo de qualquer geração específica, o criador de perfil serão recebê-las uma `SurvivingReferences2` retorno de chamada ou um [MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) retorno de chamada, mas não ambos.</span><span class="sxs-lookup"><span data-stu-id="2259c-125">For a garbage collection on any particular generation, the profiler will receive either a `SurvivingReferences2` callback or a [MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) callback, but not both.</span></span>  
  
 <span data-ttu-id="2259c-126">Vários `SurvivingReferences2` retornos de chamada podem ser recebidos durante uma coleta de lixo específico, devido a buffer interno limitado, vários retornos de chamada durante a coleta de lixo do servidor e outros motivos.</span><span class="sxs-lookup"><span data-stu-id="2259c-126">Multiple `SurvivingReferences2` callbacks might be received during a particular garbage collection, because of limited internal buffering, multiple callbacks during server garbage collection, and other reasons.</span></span> <span data-ttu-id="2259c-127">No caso de vários retornos de chamada durante uma coleta de lixo, as informações são cumulativas; todas as referências que são relatadas em qualquer `SurvivingReferences2` retorno de chamada sobreviver a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="2259c-127">In the case of multiple callbacks during a garbage collection, the information is cumulative; all references that are reported in any `SurvivingReferences2` callback survive the garbage collection.</span></span>  
  
 <span data-ttu-id="2259c-128">Se o criador de perfis implementa ambos os [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) e o [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interfaces, o `SurvivingReferences2` método é chamado antes do [ICorProfilerCallback2:: SurvivingReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md) método, mas somente se `SurvivingReferences2` retorna com êxito.</span><span class="sxs-lookup"><span data-stu-id="2259c-128">If the profiler implements both the [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) and the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interfaces, the `SurvivingReferences2` method is called before the [ICorProfilerCallback2::SurvivingReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md) method, but only if `SurvivingReferences2` returns successfully.</span></span> <span data-ttu-id="2259c-129">Os criadores de perfis podem retornar um HRESULT que indica uma falha do `SurvivingReferences2` método para evitar o segundo método de chamada.</span><span class="sxs-lookup"><span data-stu-id="2259c-129">Profilers can return an HRESULT that indicates failure from the `SurvivingReferences2` method to avoid calling the second method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2259c-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2259c-130">Requirements</span></span>  
 <span data-ttu-id="2259c-131">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2259c-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2259c-132">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2259c-132">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2259c-133">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2259c-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2259c-134">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2259c-134">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2259c-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2259c-135">See also</span></span>

- [<span data-ttu-id="2259c-136">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="2259c-136">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="2259c-137">Interface ICorProfilerCallback2</span><span class="sxs-lookup"><span data-stu-id="2259c-137">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
- [<span data-ttu-id="2259c-138">Interface ICorProfilerCallback4</span><span class="sxs-lookup"><span data-stu-id="2259c-138">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
