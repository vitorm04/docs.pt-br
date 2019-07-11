---
title: Método ICorProfilerCallback2::SurvivingReferences
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.SurvivingReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::SurvivingReferences
helpviewer_keywords:
- ICorProfilerCallback2::SurvivingReferences method [.NET Framework profiling]
- SurvivingReferences method [.NET Framework profiling]
ms.assetid: f165200e-3a91-47f7-88fc-13ff10c8babc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5070dba7e7e1218fedf24d350c0461a1cd3835e1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755514"
---
# <a name="icorprofilercallback2survivingreferences-method"></a><span data-ttu-id="b4600-102">Método ICorProfilerCallback2::SurvivingReferences</span><span class="sxs-lookup"><span data-stu-id="b4600-102">ICorProfilerCallback2::SurvivingReferences Method</span></span>
<span data-ttu-id="b4600-103">Relata o layout dos objetos no heap como resultado de uma coleta de lixo sem compactação.</span><span class="sxs-lookup"><span data-stu-id="b4600-103">Reports the layout of objects in the heap as a result of a non-compacting garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4600-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b4600-104">Syntax</span></span>  
  
```cpp  
HRESULT SurvivingReferences(  
    [in] ULONG  cSurvivingObjectIDRanges,  
    [in, size_is(cSurvivingObjectIDRanges)] ObjectID  
                objectIDRangeStart[] ,  
    [in, size_is(cSurvivingObjectIDRanges)] ULONG  
                cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="b4600-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b4600-105">Parameters</span></span>  
 `cSurvivingObjectIDRanges`  
 <span data-ttu-id="b4600-106">[in] O número de blocos contíguos objetos que sobreviveram como resultado da coleta de lixo sem compactação.</span><span class="sxs-lookup"><span data-stu-id="b4600-106">[in] The number of blocks of contiguous objects that survived as the result of the non-compacting garbage collection.</span></span> <span data-ttu-id="b4600-107">Ou seja, o valor de `cSurvivingObjectIDRanges` é o tamanho do `objectIDRangeStart` e `cObjectIDRangeLength` matrizes, qual repositório um `ObjectID` e um comprimento, respectivamente, para cada bloco de objetos.</span><span class="sxs-lookup"><span data-stu-id="b4600-107">That is, the value of `cSurvivingObjectIDRanges` is the size of the `objectIDRangeStart` and `cObjectIDRangeLength` arrays, which store an `ObjectID` and a length, respectively, for each block of objects.</span></span>  
  
 <span data-ttu-id="b4600-108">Os próximos dois argumentos de `SurvivingReferences` são matrizes paralelas.</span><span class="sxs-lookup"><span data-stu-id="b4600-108">The next two arguments of `SurvivingReferences` are parallel arrays.</span></span> <span data-ttu-id="b4600-109">Em outras palavras, `objectIDRangeStart` e `cObjectIDRangeLength` referem-se do mesmo bloco de objetos contíguos.</span><span class="sxs-lookup"><span data-stu-id="b4600-109">In other words, `objectIDRangeStart` and `cObjectIDRangeLength` concern the same block of contiguous objects.</span></span>  
  
 `objectIDRangeStart`  
 <span data-ttu-id="b4600-110">[in] Uma matriz de `ObjectID` valores, cada um deles é o endereço inicial de um bloco de contíguos, live objetos na memória.</span><span class="sxs-lookup"><span data-stu-id="b4600-110">[in] An array of `ObjectID` values, each of which is the starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `cObjectIDRangeLength`  
 <span data-ttu-id="b4600-111">[in] Uma matriz de inteiros, cada um deles é o tamanho de um bloco sobrevivente de objetos adjacentes na memória.</span><span class="sxs-lookup"><span data-stu-id="b4600-111">[in] An array of integers, each of which is the size of a surviving block of contiguous objects in memory.</span></span>  
  
 <span data-ttu-id="b4600-112">Um tamanho for especificado para cada bloco que é referenciado no `objectIDRangeStart` matriz.</span><span class="sxs-lookup"><span data-stu-id="b4600-112">A size is specified for each block that is referenced in the `objectIDRangeStart` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b4600-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="b4600-113">Remarks</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b4600-114">Esse método informa os tamanhos como `MAX_ULONG` para objetos que são maiores que 4 GB em plataformas de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="b4600-114">This method reports sizes as `MAX_ULONG` for objects that are greater than 4 GB on 64-bit platforms.</span></span> <span data-ttu-id="b4600-115">Para objetos que são maiores do que 4 GB, use o [ICorProfilerCallback4::SurvivingReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md) método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="b4600-115">For objects that are larger than 4 GB, use the [ICorProfilerCallback4::SurvivingReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md) method instead.</span></span>  
  
 <span data-ttu-id="b4600-116">Os elementos do `objectIDRangeStart` e `cObjectIDRangeLength` matrizes devem ser interpretadas da seguinte maneira para determinar se um objeto sobreviveu a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="b4600-116">The elements of the `objectIDRangeStart` and `cObjectIDRangeLength` arrays should be interpreted as follows to determine whether an object survived the garbage collection.</span></span> <span data-ttu-id="b4600-117">Suponha que um `ObjectID` valor (`ObjectID`) se encontra dentro do seguinte intervalo:</span><span class="sxs-lookup"><span data-stu-id="b4600-117">Assume that an `ObjectID` value (`ObjectID`) lies within the following range:</span></span>  
  
 `ObjectIDRangeStart[i]` <= `ObjectID` < `ObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 <span data-ttu-id="b4600-118">Para qualquer valor de `i` que está no intervalo a seguir, o objeto sobrevive à coleta de lixo:</span><span class="sxs-lookup"><span data-stu-id="b4600-118">For any value of `i` that is in the following range, the object has survived the garbage collection:</span></span>  
  
 <span data-ttu-id="b4600-119">0 <= `i` < `cSurvivingObjectIDRanges`</span><span class="sxs-lookup"><span data-stu-id="b4600-119">0 <= `i` < `cSurvivingObjectIDRanges`</span></span>  
  
 <span data-ttu-id="b4600-120">Uma coleta de lixo sem compactação recupera a memória ocupada por objetos "inativos", mas não compacta que o espaço livre.</span><span class="sxs-lookup"><span data-stu-id="b4600-120">A non-compacting garbage collection reclaims the memory occupied by "dead" objects, but does not compact that freed space.</span></span> <span data-ttu-id="b4600-121">Como resultado, memória é retornada para o heap, mas não há objetos "ativos" são movidos.</span><span class="sxs-lookup"><span data-stu-id="b4600-121">As a result, memory is returned to the heap, but no "live" objects are moved.</span></span>  
  
 <span data-ttu-id="b4600-122">O common language runtime (CLR) chama `SurvivingReferences` para coletas de lixo sem compactação.</span><span class="sxs-lookup"><span data-stu-id="b4600-122">The common language runtime (CLR) calls `SurvivingReferences` for non-compacting garbage collections.</span></span> <span data-ttu-id="b4600-123">Para compactação coletas de lixo, [ICorProfilerCallback:: Movedreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) é chamado em vez disso.</span><span class="sxs-lookup"><span data-stu-id="b4600-123">For compacting garbage collections, [ICorProfilerCallback::MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) is called instead.</span></span> <span data-ttu-id="b4600-124">Uma coleta de lixo único pode ser compactação para uma geração e sem compactação para outro.</span><span class="sxs-lookup"><span data-stu-id="b4600-124">A single garbage collection can be compacting for one generation and non-compacting for another.</span></span> <span data-ttu-id="b4600-125">Para uma coleta de lixo de qualquer geração específica, o criador de perfil serão recebê-las uma `SurvivingReferences` retorno de chamada ou um `MovedReferences` retorno de chamada, mas não ambos.</span><span class="sxs-lookup"><span data-stu-id="b4600-125">For a garbage collection on any particular generation, the profiler will receive either a `SurvivingReferences` callback or a `MovedReferences` callback, but not both.</span></span>  
  
 <span data-ttu-id="b4600-126">Vários `SurvivingReferences` retornos de chamada podem ser recebidos durante uma coleta de lixo específico, devido a buffer interno limitado, vários threads reporting no caso de coleta de lixo do servidor e outros motivos.</span><span class="sxs-lookup"><span data-stu-id="b4600-126">Multiple `SurvivingReferences` callbacks might be received during a particular garbage collection, due to limited internal buffering, multiple threads reporting in the case of server garbage collection, and other reasons.</span></span> <span data-ttu-id="b4600-127">No caso de vários retornos de chamada durante uma coleta de lixo, as informações são cumulativas — todas as referências que são relatadas em qualquer `SurvivingReferences` retorno de chamada sobreviver a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="b4600-127">In the case of multiple callbacks during a garbage collection, the information is cumulative — all references that are reported in any `SurvivingReferences` callback survive the garbage collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4600-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b4600-128">Requirements</span></span>  
 <span data-ttu-id="b4600-129">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4600-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4600-130">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b4600-130">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b4600-131">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b4600-131">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b4600-132">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4600-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4600-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b4600-133">See also</span></span>

- [<span data-ttu-id="b4600-134">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="b4600-134">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="b4600-135">Interface ICorProfilerCallback2</span><span class="sxs-lookup"><span data-stu-id="b4600-135">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
- [<span data-ttu-id="b4600-136">Método SurvivingReferences2</span><span class="sxs-lookup"><span data-stu-id="b4600-136">SurvivingReferences2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md)
