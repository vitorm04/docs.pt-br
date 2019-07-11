---
title: Método ICorProfilerCallback4::MovedReferences2
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.MovedReferences2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::MovedReferences2
helpviewer_keywords:
- MovedReferences2 method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::MovedReferences2 method [.NET Framework profiling]
ms.assetid: d17a065b-5bc6-4817-b3e1-1e413fcb33a8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e676d03efc950ce911bce43e15322d1f9882d0fd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67758221"
---
# <a name="icorprofilercallback4movedreferences2-method"></a><span data-ttu-id="949a4-102">Método ICorProfilerCallback4::MovedReferences2</span><span class="sxs-lookup"><span data-stu-id="949a4-102">ICorProfilerCallback4::MovedReferences2 Method</span></span>
<span data-ttu-id="949a4-103">Chamado para relatar o novo layout dos objetos no heap como resultado de uma coleta de lixo de compactação.</span><span class="sxs-lookup"><span data-stu-id="949a4-103">Called to report the new layout of objects in the heap as a result of a compacting garbage collection.</span></span> <span data-ttu-id="949a4-104">Esse método é chamado se o criador de perfil tiver implementado a [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="949a4-104">This method is called if the profiler has implemented the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interface.</span></span> <span data-ttu-id="949a4-105">Esse retorno de chamada substitui o [ICorProfilerCallback:: Movedreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) método, porque ele pode relatar intervalos maiores de objetos cujo comprimento excede o que pode ser expresso em um ULONG.</span><span class="sxs-lookup"><span data-stu-id="949a4-105">This callback replaces the [ICorProfilerCallback::MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) method, because it can report larger ranges of objects whose lengths exceed what can be expressed in a ULONG.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="949a4-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="949a4-106">Syntax</span></span>  
  
```cpp  
HRESULT MovedReferences2(  
    [in]  ULONG  cMovedObjectIDRanges,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID oldObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID newObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] SIZE_T    cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="949a4-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="949a4-107">Parameters</span></span>  
 `cMovedObjectIDRanges`  
 <span data-ttu-id="949a4-108">[in] O número de blocos de objetos contíguos que movidas como resultado da compactação coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="949a4-108">[in] The number of blocks of contiguous objects that moved as the result of the compacting garbage collection.</span></span> <span data-ttu-id="949a4-109">Ou seja, o valor de `cMovedObjectIDRanges` é o tamanho total do `oldObjectIDRangeStart`, `newObjectIDRangeStart`, e `cObjectIDRangeLength` matrizes.</span><span class="sxs-lookup"><span data-stu-id="949a4-109">That is, the value of `cMovedObjectIDRanges` is the total size of the `oldObjectIDRangeStart`, `newObjectIDRangeStart`, and `cObjectIDRangeLength` arrays.</span></span>  
  
 <span data-ttu-id="949a4-110">Os próximos três argumentos de `MovedReferences2` são matrizes paralelas.</span><span class="sxs-lookup"><span data-stu-id="949a4-110">The next three arguments of `MovedReferences2` are parallel arrays.</span></span> <span data-ttu-id="949a4-111">Em outras palavras, `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]`, e `cObjectIDRangeLength[i]` todos dizem respeito a um único bloco de objetos contíguos.</span><span class="sxs-lookup"><span data-stu-id="949a4-111">In other words, `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]`, and `cObjectIDRangeLength[i]` all concern a single block of contiguous objects.</span></span>  
  
 `oldObjectIDRangeStart`  
 <span data-ttu-id="949a4-112">[in] Uma matriz de `ObjectID` valores, cada um deles é o antigo (coleta de lixo de pré-lançamento) endereço de um bloco de contíguos inicial, os objetos dinâmicos na memória.</span><span class="sxs-lookup"><span data-stu-id="949a4-112">[in] An array of `ObjectID` values, each of which is the old (pre-garbage collection) starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `newObjectIDRangeStart`  
 <span data-ttu-id="949a4-113">[in] Uma matriz de `ObjectID` valores, cada um deles é o novo endereço inicial (coleta de pós-lixo) de um bloco de contíguos, live objetos na memória.</span><span class="sxs-lookup"><span data-stu-id="949a4-113">[in] An array of `ObjectID` values, each of which is the new (post-garbage collection) starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `cObjectIDRangeLength`  
 <span data-ttu-id="949a4-114">[in] Uma matriz de inteiros, cada um deles é o tamanho de um bloco de objetos adjacentes na memória.</span><span class="sxs-lookup"><span data-stu-id="949a4-114">[in] An array of integers, each of which is the size of a block of contiguous objects in memory.</span></span>  
  
 <span data-ttu-id="949a4-115">Um tamanho for especificado para cada bloco que é referenciado na `oldObjectIDRangeStart` e `newObjectIDRangeStart` matrizes.</span><span class="sxs-lookup"><span data-stu-id="949a4-115">A size is specified for each block that is referenced in the `oldObjectIDRangeStart` and `newObjectIDRangeStart` arrays.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="949a4-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="949a4-116">Remarks</span></span>  
 <span data-ttu-id="949a4-117">Um compactação coletor de lixo recupera a memória ocupada por objetos inativos e compacta que liberado espaço.</span><span class="sxs-lookup"><span data-stu-id="949a4-117">A compacting garbage collector reclaims the memory occupied by dead objects and compacts that freed space.</span></span> <span data-ttu-id="949a4-118">Como resultado, os objetos em tempo real podem ser movidos no heap, e `ObjectID` valores distribuídos por meio de notificações anteriores pode ser alterado.</span><span class="sxs-lookup"><span data-stu-id="949a4-118">As a result, live objects might be moved within the heap, and `ObjectID` values distributed by previous notifications might change.</span></span>  
  
 <span data-ttu-id="949a4-119">Suponha que uma já existente `ObjectID` valor (`oldObjectID`) se encontra dentro do seguinte intervalo:</span><span class="sxs-lookup"><span data-stu-id="949a4-119">Assume that an existing `ObjectID` value (`oldObjectID`) lies within the following range:</span></span>  
  
 `oldObjectIDRangeStart[i]` <= `oldObjectID` < `oldObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 <span data-ttu-id="949a4-120">Nesse caso, o deslocamento do início do intervalo para o início do objeto é da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="949a4-120">In this case, the offset from the start of the range to the start of the object is as follows:</span></span>  
  
 `oldObjectID` - `oldObjectRangeStart[i]`  
  
 <span data-ttu-id="949a4-121">Para qualquer valor de `i` que está no seguinte intervalo:</span><span class="sxs-lookup"><span data-stu-id="949a4-121">For any value of `i` that is in the following range:</span></span>  
  
 <span data-ttu-id="949a4-122">0 <= `i` < `cMovedObjectIDRanges`</span><span class="sxs-lookup"><span data-stu-id="949a4-122">0 <= `i` < `cMovedObjectIDRanges`</span></span>  
  
 <span data-ttu-id="949a4-123">Você pode calcular o novo `ObjectID` da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="949a4-123">you can calculate the new `ObjectID` as follows:</span></span>  
  
 <span data-ttu-id="949a4-124">`newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)</span><span class="sxs-lookup"><span data-stu-id="949a4-124">`newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)</span></span>  
  
 <span data-ttu-id="949a4-125">Nenhum dos `ObjectID` valores passados pelo `MovedReferences2` são válidos durante o retorno de chamada em si, porque o coletor de lixo pode estar no meio de movimentação de objetos de locais antigos para novos locais.</span><span class="sxs-lookup"><span data-stu-id="949a4-125">None of the `ObjectID` values passed by `MovedReferences2` are valid during the callback itself, because the garbage collector might be in the middle of moving objects from old locations to new locations.</span></span> <span data-ttu-id="949a4-126">Portanto, os criadores de perfis não devem tentar inspecionar objetos durante uma chamada `MovedReferences2`.</span><span class="sxs-lookup"><span data-stu-id="949a4-126">Therefore, profilers should not attempt to inspect objects during a `MovedReferences2` call.</span></span> <span data-ttu-id="949a4-127">Um [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) retorno de chamada indica que todos os objetos foram movidos para os novos locais e inspeção pode ser executada.</span><span class="sxs-lookup"><span data-stu-id="949a4-127">A [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) callback indicates that all objects have been moved to their new locations and inspection can be performed.</span></span>  
  
 <span data-ttu-id="949a4-128">Se o criador de perfis implementa ambos os [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) e o [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interfaces, o `MovedReferences2` método é chamado antes do [ICorProfilerCallback:: MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) método, mas somente se o `MovedReferences2` método retorna com êxito.</span><span class="sxs-lookup"><span data-stu-id="949a4-128">If the profiler implements both the [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) and the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interfaces, the `MovedReferences2` method is called before the [ICorProfilerCallback::MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) method, but only if the `MovedReferences2` method returns successfully.</span></span> <span data-ttu-id="949a4-129">Os criadores de perfis podem retornar um HRESULT que indica uma falha do `MovedReferences2` método, para evitar que o segundo método de chamada.</span><span class="sxs-lookup"><span data-stu-id="949a4-129">Profilers can return an HRESULT that indicates failure from the `MovedReferences2` method, to avoid calling the second method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="949a4-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="949a4-130">Requirements</span></span>  
 <span data-ttu-id="949a4-131">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="949a4-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="949a4-132">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="949a4-132">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="949a4-133">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="949a4-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="949a4-134">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="949a4-134">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="949a4-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="949a4-135">See also</span></span>

- [<span data-ttu-id="949a4-136">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="949a4-136">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="949a4-137">Método MovedReferences</span><span class="sxs-lookup"><span data-stu-id="949a4-137">MovedReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md)
- [<span data-ttu-id="949a4-138">Interface ICorProfilerCallback4</span><span class="sxs-lookup"><span data-stu-id="949a4-138">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
- [<span data-ttu-id="949a4-139">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="949a4-139">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="949a4-140">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="949a4-140">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
