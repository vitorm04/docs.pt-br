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
ms.openlocfilehash: 2f305852ae218417aa1f4d4fe9d2076c0163fd60
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865266"
---
# <a name="icorprofilercallback4movedreferences2-method"></a><span data-ttu-id="52596-102">Método ICorProfilerCallback4::MovedReferences2</span><span class="sxs-lookup"><span data-stu-id="52596-102">ICorProfilerCallback4::MovedReferences2 Method</span></span>
<span data-ttu-id="52596-103">Chamado para relatar o novo layout de objetos no heap como resultado de uma coleta de lixo de compactação.</span><span class="sxs-lookup"><span data-stu-id="52596-103">Called to report the new layout of objects in the heap as a result of a compacting garbage collection.</span></span> <span data-ttu-id="52596-104">Esse método será chamado se o criador de perfil tiver implementado a interface [ICorProfilerCallback4](icorprofilercallback4-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="52596-104">This method is called if the profiler has implemented the [ICorProfilerCallback4](icorprofilercallback4-interface.md) interface.</span></span> <span data-ttu-id="52596-105">Esse retorno de chamada substitui o método [ICorProfilerCallback:: MovedReferences](icorprofilercallback-movedreferences-method.md) , pois ele pode relatar intervalos maiores de objetos cujos comprimentos excedem o que pode ser expresso em ULONG.</span><span class="sxs-lookup"><span data-stu-id="52596-105">This callback replaces the [ICorProfilerCallback::MovedReferences](icorprofilercallback-movedreferences-method.md) method, because it can report larger ranges of objects whose lengths exceed what can be expressed in a ULONG.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52596-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="52596-106">Syntax</span></span>  
  
```cpp  
HRESULT MovedReferences2(  
    [in]  ULONG  cMovedObjectIDRanges,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID oldObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID newObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] SIZE_T    cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="52596-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="52596-107">Parameters</span></span>  
 `cMovedObjectIDRanges`  
 <span data-ttu-id="52596-108">no O número de blocos de objetos contíguos que foram movidos como resultado da coleta de lixo de compactação.</span><span class="sxs-lookup"><span data-stu-id="52596-108">[in] The number of blocks of contiguous objects that moved as the result of the compacting garbage collection.</span></span> <span data-ttu-id="52596-109">Ou seja, o valor de `cMovedObjectIDRanges` é o tamanho total das matrizes `oldObjectIDRangeStart`, `newObjectIDRangeStart`e `cObjectIDRangeLength`.</span><span class="sxs-lookup"><span data-stu-id="52596-109">That is, the value of `cMovedObjectIDRanges` is the total size of the `oldObjectIDRangeStart`, `newObjectIDRangeStart`, and `cObjectIDRangeLength` arrays.</span></span>  
  
 <span data-ttu-id="52596-110">Os próximos três argumentos de `MovedReferences2` são matrizes paralelas.</span><span class="sxs-lookup"><span data-stu-id="52596-110">The next three arguments of `MovedReferences2` are parallel arrays.</span></span> <span data-ttu-id="52596-111">Em outras palavras, `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]`e `cObjectIDRangeLength[i]` se preocupam com um único bloco de objetos contíguos.</span><span class="sxs-lookup"><span data-stu-id="52596-111">In other words, `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]`, and `cObjectIDRangeLength[i]` all concern a single block of contiguous objects.</span></span>  
  
 `oldObjectIDRangeStart`  
 <span data-ttu-id="52596-112">no Uma matriz de valores de `ObjectID`, cada um dos quais é o endereço inicial (coleta antes de lixo) de um bloco de objetos dinâmicos contíguos na memória.</span><span class="sxs-lookup"><span data-stu-id="52596-112">[in] An array of `ObjectID` values, each of which is the old (pre-garbage collection) starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `newObjectIDRangeStart`  
 <span data-ttu-id="52596-113">no Uma matriz de valores de `ObjectID`, cada um dos quais é o novo endereço inicial (coleta de lixo) de um bloco de objetos dinâmicos contíguos na memória.</span><span class="sxs-lookup"><span data-stu-id="52596-113">[in] An array of `ObjectID` values, each of which is the new (post-garbage collection) starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `cObjectIDRangeLength`  
 <span data-ttu-id="52596-114">no Uma matriz de inteiros, cada qual é o tamanho de um bloco de objetos contíguos na memória.</span><span class="sxs-lookup"><span data-stu-id="52596-114">[in] An array of integers, each of which is the size of a block of contiguous objects in memory.</span></span>  
  
 <span data-ttu-id="52596-115">Um tamanho é especificado para cada bloco que é referenciado nas matrizes `oldObjectIDRangeStart` e `newObjectIDRangeStart`.</span><span class="sxs-lookup"><span data-stu-id="52596-115">A size is specified for each block that is referenced in the `oldObjectIDRangeStart` and `newObjectIDRangeStart` arrays.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="52596-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="52596-116">Remarks</span></span>  
 <span data-ttu-id="52596-117">Um coletor de lixo de compactação recupera a memória ocupada por objetos inativos e compacta o espaço livre.</span><span class="sxs-lookup"><span data-stu-id="52596-117">A compacting garbage collector reclaims the memory occupied by dead objects and compacts that freed space.</span></span> <span data-ttu-id="52596-118">Como resultado, os objetos dinâmicos podem ser movidos dentro do heap e `ObjectID` valores distribuídos por notificações anteriores podem ser alterados.</span><span class="sxs-lookup"><span data-stu-id="52596-118">As a result, live objects might be moved within the heap, and `ObjectID` values distributed by previous notifications might change.</span></span>  
  
 <span data-ttu-id="52596-119">Suponha que um valor de `ObjectID` existente (`oldObjectID`) está dentro do seguinte intervalo:</span><span class="sxs-lookup"><span data-stu-id="52596-119">Assume that an existing `ObjectID` value (`oldObjectID`) lies within the following range:</span></span>  
  
 `oldObjectIDRangeStart[i]` <= `oldObjectID` < `oldObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 <span data-ttu-id="52596-120">Nesse caso, o deslocamento do início do intervalo até o início do objeto é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="52596-120">In this case, the offset from the start of the range to the start of the object is as follows:</span></span>  
  
 `oldObjectID` - `oldObjectRangeStart[i]`  
  
 <span data-ttu-id="52596-121">Para qualquer valor de `i` que esteja no seguinte intervalo:</span><span class="sxs-lookup"><span data-stu-id="52596-121">For any value of `i` that is in the following range:</span></span>  
  
 <span data-ttu-id="52596-122">0 <= `i` < `cMovedObjectIDRanges`</span><span class="sxs-lookup"><span data-stu-id="52596-122">0 <= `i` < `cMovedObjectIDRanges`</span></span>  
  
 <span data-ttu-id="52596-123">Você pode calcular o novo `ObjectID` da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="52596-123">you can calculate the new `ObjectID` as follows:</span></span>  
  
 <span data-ttu-id="52596-124">`newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)</span><span class="sxs-lookup"><span data-stu-id="52596-124">`newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)</span></span>  
  
 <span data-ttu-id="52596-125">Nenhum dos valores de `ObjectID` passados por `MovedReferences2` são válidos durante o próprio retorno de chamada, pois o coletor de lixo pode estar no meio da movimentação de objetos de locais antigos para novos locais.</span><span class="sxs-lookup"><span data-stu-id="52596-125">None of the `ObjectID` values passed by `MovedReferences2` are valid during the callback itself, because the garbage collector might be in the middle of moving objects from old locations to new locations.</span></span> <span data-ttu-id="52596-126">Portanto, os criadores de perfis não devem tentar inspecionar objetos durante uma chamada `MovedReferences2`.</span><span class="sxs-lookup"><span data-stu-id="52596-126">Therefore, profilers should not attempt to inspect objects during a `MovedReferences2` call.</span></span> <span data-ttu-id="52596-127">Um retorno de chamada [ICorProfilerCallback2:: GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) indica que todos os objetos foram movidos para seus novos locais e a inspeção pode ser executada.</span><span class="sxs-lookup"><span data-stu-id="52596-127">A [ICorProfilerCallback2::GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) callback indicates that all objects have been moved to their new locations and inspection can be performed.</span></span>  
  
 <span data-ttu-id="52596-128">Se o criador de perfil implementar as interfaces [ICorProfilerCallback](icorprofilercallback-interface.md) e [ICorProfilerCallback4](icorprofilercallback4-interface.md) , o método `MovedReferences2` será chamado antes do método [ICorProfilerCallback:: MovedReferences](icorprofilercallback-movedreferences-method.md) , mas somente se o método `MovedReferences2` retornar com êxito.</span><span class="sxs-lookup"><span data-stu-id="52596-128">If the profiler implements both the [ICorProfilerCallback](icorprofilercallback-interface.md) and the [ICorProfilerCallback4](icorprofilercallback4-interface.md) interfaces, the `MovedReferences2` method is called before the [ICorProfilerCallback::MovedReferences](icorprofilercallback-movedreferences-method.md) method, but only if the `MovedReferences2` method returns successfully.</span></span> <span data-ttu-id="52596-129">Os profileres podem retornar um HRESULT que indica falha do método `MovedReferences2`, para evitar chamar o segundo método.</span><span class="sxs-lookup"><span data-stu-id="52596-129">Profilers can return an HRESULT that indicates failure from the `MovedReferences2` method, to avoid calling the second method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52596-130">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="52596-130">Requirements</span></span>  
 <span data-ttu-id="52596-131">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52596-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52596-132">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="52596-132">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="52596-133">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="52596-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="52596-134">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52596-134">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52596-135">Veja também</span><span class="sxs-lookup"><span data-stu-id="52596-135">See also</span></span>

- [<span data-ttu-id="52596-136">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="52596-136">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="52596-137">Método MovedReferences</span><span class="sxs-lookup"><span data-stu-id="52596-137">MovedReferences Method</span></span>](icorprofilercallback-movedreferences-method.md)
- [<span data-ttu-id="52596-138">Interface ICorProfilerCallback4</span><span class="sxs-lookup"><span data-stu-id="52596-138">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)
- [<span data-ttu-id="52596-139">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="52596-139">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="52596-140">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="52596-140">Profiling</span></span>](index.md)
