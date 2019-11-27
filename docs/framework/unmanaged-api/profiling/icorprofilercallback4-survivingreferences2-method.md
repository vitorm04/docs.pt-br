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
ms.openlocfilehash: 3178d099db96d52f0238cfcf7e055e761687ce30
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430089"
---
# <a name="icorprofilercallback4survivingreferences2-method"></a><span data-ttu-id="701b3-102">Método ICorProfilerCallback4::SurvivingReferences2</span><span class="sxs-lookup"><span data-stu-id="701b3-102">ICorProfilerCallback4::SurvivingReferences2 Method</span></span>
<span data-ttu-id="701b3-103">Relata o layout dos objetos no heap como resultado de uma coleta de lixo sem compactação.</span><span class="sxs-lookup"><span data-stu-id="701b3-103">Reports the layout of objects in the heap as a result of a non-compacting garbage collection.</span></span> <span data-ttu-id="701b3-104">Esse método será chamado se o criador de perfil tiver implementado a interface [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="701b3-104">This method is called if the profiler has implemented the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interface.</span></span> <span data-ttu-id="701b3-105">Esse retorno de chamada substitui o método [ICorProfilerCallback2:: SurvivingReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md) , pois ele pode relatar intervalos maiores de objetos cujos comprimentos excedem o que pode ser expresso em ULONG.</span><span class="sxs-lookup"><span data-stu-id="701b3-105">This callback replaces the [ICorProfilerCallback2::SurvivingReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md) method, because it can report larger ranges of objects whose lengths exceed what can be expressed in a ULONG.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="701b3-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="701b3-106">Syntax</span></span>  
  
```cpp  
HRESULT SurvivingReferences2(  
    [in] ULONG  cSurvivingObjectIDRanges,  
    [in, size_is(cSurvivingObjectIDRanges)] ObjectID  
                objectIDRangeStart[] ,  
    [in, size_is(cSurvivingObjectIDRanges)] SIZE_T  
                cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="701b3-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="701b3-107">Parameters</span></span>  
 `cSurvivingObjectIDRanges`  
 <span data-ttu-id="701b3-108">no O número de blocos de objetos contíguos que sobreviveram como resultado da coleta de lixo sem compactação.</span><span class="sxs-lookup"><span data-stu-id="701b3-108">[in] The number of blocks of contiguous objects that survived as the result of the non-compacting garbage collection.</span></span> <span data-ttu-id="701b3-109">Ou seja, o valor de `cSurvivingObjectIDRanges` é o tamanho das matrizes `objectIDRangeStart` e `cObjectIDRangeLength`, que armazenam um `ObjectID` e um comprimento, respectivamente, para cada bloco de objetos.</span><span class="sxs-lookup"><span data-stu-id="701b3-109">That is, the value of `cSurvivingObjectIDRanges` is the size of the `objectIDRangeStart` and `cObjectIDRangeLength` arrays, which store an `ObjectID` and a length, respectively, for each block of objects.</span></span>  
  
 <span data-ttu-id="701b3-110">Os dois próximos argumentos de `SurvivingReferences2` são matrizes paralelas.</span><span class="sxs-lookup"><span data-stu-id="701b3-110">The next two arguments of `SurvivingReferences2` are parallel arrays.</span></span> <span data-ttu-id="701b3-111">Em outras palavras, `objectIDRangeStart` e `cObjectIDRangeLength` se preocupam com o mesmo bloco de objetos contíguos.</span><span class="sxs-lookup"><span data-stu-id="701b3-111">In other words, `objectIDRangeStart` and `cObjectIDRangeLength` concern the same block of contiguous objects.</span></span>  
  
 `objectIDRangeStart`  
 <span data-ttu-id="701b3-112">no Uma matriz de valores de `ObjectID`, cada um dos quais é o endereço inicial de um bloco de objetos dinâmicos contíguos na memória.</span><span class="sxs-lookup"><span data-stu-id="701b3-112">[in] An array of `ObjectID` values, each of which is the starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `cObjectIDRangeLength`  
 <span data-ttu-id="701b3-113">no Uma matriz de inteiros, cada qual é o tamanho de um bloco sobrevivente de objetos contíguos na memória.</span><span class="sxs-lookup"><span data-stu-id="701b3-113">[in] An array of integers, each of which is the size of a surviving block of contiguous objects in memory.</span></span>  
  
 <span data-ttu-id="701b3-114">Um tamanho é especificado para cada bloco que é referenciado na matriz de `objectIDRangeStart`.</span><span class="sxs-lookup"><span data-stu-id="701b3-114">A size is specified for each block that is referenced in the `objectIDRangeStart` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="701b3-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="701b3-115">Remarks</span></span>  
 <span data-ttu-id="701b3-116">Os elementos das matrizes `objectIDRangeStart` e `cObjectIDRangeLength` devem ser interpretados da seguinte maneira para determinar se um objeto sobreviveram a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="701b3-116">The elements of the `objectIDRangeStart` and `cObjectIDRangeLength` arrays should be interpreted as follows to determine whether an object survived the garbage collection.</span></span> <span data-ttu-id="701b3-117">Suponha que um valor de `ObjectID` (`ObjectID`) está dentro do seguinte intervalo:</span><span class="sxs-lookup"><span data-stu-id="701b3-117">Assume that an `ObjectID` value (`ObjectID`) lies within the following range:</span></span>  
  
 `ObjectIDRangeStart[i]` <= `ObjectID` < `ObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 <span data-ttu-id="701b3-118">Para qualquer valor de `i` que esteja no seguinte intervalo, o objeto tem sobreviveram a coleta de lixo:</span><span class="sxs-lookup"><span data-stu-id="701b3-118">For any value of `i` that is in the following range, the object has survived the garbage collection:</span></span>  
  
 <span data-ttu-id="701b3-119">0 < = `i` < `cSurvivingObjectIDRanges`</span><span class="sxs-lookup"><span data-stu-id="701b3-119">0 <= `i` < `cSurvivingObjectIDRanges`</span></span>  
  
 <span data-ttu-id="701b3-120">Uma coleta de lixo não compactada recupera a memória ocupada por objetos "inativos", mas não compacta esse espaço livre.</span><span class="sxs-lookup"><span data-stu-id="701b3-120">A non-compacting garbage collection reclaims the memory occupied by "dead" objects, but does not compact that freed space.</span></span> <span data-ttu-id="701b3-121">Como resultado, a memória é retornada para o heap, mas nenhum objeto "ao vivo" é movido.</span><span class="sxs-lookup"><span data-stu-id="701b3-121">As a result, memory is returned to the heap, but no "live" objects are moved.</span></span>  
  
 <span data-ttu-id="701b3-122">O Common Language Runtime (CLR) chama `SurvivingReferences2` para coletas de lixo sem compactação.</span><span class="sxs-lookup"><span data-stu-id="701b3-122">The common language runtime (CLR) calls `SurvivingReferences2` for non-compacting garbage collections.</span></span> <span data-ttu-id="701b3-123">Para compactar as coleções de lixo, [MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) é chamado em vez disso.</span><span class="sxs-lookup"><span data-stu-id="701b3-123">For compacting garbage collections, [MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) is called instead.</span></span> <span data-ttu-id="701b3-124">Uma única coleta de lixo pode ser compactada para uma geração e não compactação para outra.</span><span class="sxs-lookup"><span data-stu-id="701b3-124">A single garbage collection can be compacting for one generation and non-compacting for another.</span></span> <span data-ttu-id="701b3-125">Para uma coleta de lixo em qualquer geração específica, o criador de perfil receberá um `SurvivingReferences2` retorno de chamada ou um retorno de chamada [MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) , mas não ambos.</span><span class="sxs-lookup"><span data-stu-id="701b3-125">For a garbage collection on any particular generation, the profiler will receive either a `SurvivingReferences2` callback or a [MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) callback, but not both.</span></span>  
  
 <span data-ttu-id="701b3-126">Vários retornos de chamada de `SurvivingReferences2` podem ser recebidos durante uma coleta de lixo específica, devido ao buffer interno limitado, a vários retornos de chamada durante a coleta de lixo do servidor e por outros motivos.</span><span class="sxs-lookup"><span data-stu-id="701b3-126">Multiple `SurvivingReferences2` callbacks might be received during a particular garbage collection, because of limited internal buffering, multiple callbacks during server garbage collection, and other reasons.</span></span> <span data-ttu-id="701b3-127">No caso de vários retornos de chamada durante uma coleta de lixo, as informações são cumulativas; todas as referências que são relatadas em qualquer `SurvivingReferences2` retorno de chamada sobrevivem à coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="701b3-127">In the case of multiple callbacks during a garbage collection, the information is cumulative; all references that are reported in any `SurvivingReferences2` callback survive the garbage collection.</span></span>  
  
 <span data-ttu-id="701b3-128">Se o criador de perfil implementar as interfaces [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) e [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) , o método `SurvivingReferences2` será chamado antes do método [ICorProfilerCallback2:: SurvivingReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md) , mas somente se `SurvivingReferences2` retornar com êxito.</span><span class="sxs-lookup"><span data-stu-id="701b3-128">If the profiler implements both the [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) and the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interfaces, the `SurvivingReferences2` method is called before the [ICorProfilerCallback2::SurvivingReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md) method, but only if `SurvivingReferences2` returns successfully.</span></span> <span data-ttu-id="701b3-129">Os profileres podem retornar um HRESULT que indica falha do método `SurvivingReferences2` para evitar chamar o segundo método.</span><span class="sxs-lookup"><span data-stu-id="701b3-129">Profilers can return an HRESULT that indicates failure from the `SurvivingReferences2` method to avoid calling the second method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="701b3-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="701b3-130">Requirements</span></span>  
 <span data-ttu-id="701b3-131">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="701b3-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="701b3-132">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="701b3-132">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="701b3-133">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="701b3-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="701b3-134">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="701b3-134">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="701b3-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="701b3-135">See also</span></span>

- [<span data-ttu-id="701b3-136">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="701b3-136">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="701b3-137">Interface ICorProfilerCallback2</span><span class="sxs-lookup"><span data-stu-id="701b3-137">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
- [<span data-ttu-id="701b3-138">Interface ICorProfilerCallback4</span><span class="sxs-lookup"><span data-stu-id="701b3-138">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
