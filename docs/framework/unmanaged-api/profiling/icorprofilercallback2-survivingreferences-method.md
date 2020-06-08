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
ms.openlocfilehash: 3681106bca94f1fefb2f24a1aa4254eb2b1b0531
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499734"
---
# <a name="icorprofilercallback2survivingreferences-method"></a><span data-ttu-id="48337-102">Método ICorProfilerCallback2::SurvivingReferences</span><span class="sxs-lookup"><span data-stu-id="48337-102">ICorProfilerCallback2::SurvivingReferences Method</span></span>
<span data-ttu-id="48337-103">Relata o layout dos objetos no heap como resultado de uma coleta de lixo sem compactação.</span><span class="sxs-lookup"><span data-stu-id="48337-103">Reports the layout of objects in the heap as a result of a non-compacting garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48337-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="48337-104">Syntax</span></span>  
  
```cpp  
HRESULT SurvivingReferences(  
    [in] ULONG  cSurvivingObjectIDRanges,  
    [in, size_is(cSurvivingObjectIDRanges)] ObjectID  
                objectIDRangeStart[] ,  
    [in, size_is(cSurvivingObjectIDRanges)] ULONG  
                cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="48337-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="48337-105">Parameters</span></span>  
 `cSurvivingObjectIDRanges`  
 <span data-ttu-id="48337-106">no O número de blocos de objetos contíguos que sobreviveram como resultado da coleta de lixo sem compactação.</span><span class="sxs-lookup"><span data-stu-id="48337-106">[in] The number of blocks of contiguous objects that survived as the result of the non-compacting garbage collection.</span></span> <span data-ttu-id="48337-107">Ou seja, o valor de `cSurvivingObjectIDRanges` é o tamanho das `objectIDRangeStart` `cObjectIDRangeLength` matrizes e, que armazena um `ObjectID` e um comprimento, respectivamente, para cada bloco de objetos.</span><span class="sxs-lookup"><span data-stu-id="48337-107">That is, the value of `cSurvivingObjectIDRanges` is the size of the `objectIDRangeStart` and `cObjectIDRangeLength` arrays, which store an `ObjectID` and a length, respectively, for each block of objects.</span></span>  
  
 <span data-ttu-id="48337-108">Os dois próximos argumentos de `SurvivingReferences` são matrizes paralelas.</span><span class="sxs-lookup"><span data-stu-id="48337-108">The next two arguments of `SurvivingReferences` are parallel arrays.</span></span> <span data-ttu-id="48337-109">Em outras palavras, `objectIDRangeStart` e `cObjectIDRangeLength` preocupação com o mesmo bloco de objetos contíguos.</span><span class="sxs-lookup"><span data-stu-id="48337-109">In other words, `objectIDRangeStart` and `cObjectIDRangeLength` concern the same block of contiguous objects.</span></span>  
  
 `objectIDRangeStart`  
 <span data-ttu-id="48337-110">no Uma matriz de `ObjectID` valores, cada um dos quais é o endereço inicial de um bloco de objetos dinâmicos contíguos na memória.</span><span class="sxs-lookup"><span data-stu-id="48337-110">[in] An array of `ObjectID` values, each of which is the starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `cObjectIDRangeLength`  
 <span data-ttu-id="48337-111">no Uma matriz de inteiros, cada qual é o tamanho de um bloco sobrevivente de objetos contíguos na memória.</span><span class="sxs-lookup"><span data-stu-id="48337-111">[in] An array of integers, each of which is the size of a surviving block of contiguous objects in memory.</span></span>  
  
 <span data-ttu-id="48337-112">Um tamanho é especificado para cada bloco que é referenciado na `objectIDRangeStart` matriz.</span><span class="sxs-lookup"><span data-stu-id="48337-112">A size is specified for each block that is referenced in the `objectIDRangeStart` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="48337-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="48337-113">Remarks</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="48337-114">Esse método relata tamanhos `MAX_ULONG` para objetos que são maiores que 4 GB em plataformas de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="48337-114">This method reports sizes as `MAX_ULONG` for objects that are greater than 4 GB on 64-bit platforms.</span></span> <span data-ttu-id="48337-115">Para objetos com mais de 4 GB, use o método [ICorProfilerCallback4:: SurvivingReferences2](icorprofilercallback4-survivingreferences2-method.md) em vez disso.</span><span class="sxs-lookup"><span data-stu-id="48337-115">For objects that are larger than 4 GB, use the [ICorProfilerCallback4::SurvivingReferences2](icorprofilercallback4-survivingreferences2-method.md) method instead.</span></span>  
  
 <span data-ttu-id="48337-116">Os elementos das `objectIDRangeStart` `cObjectIDRangeLength` matrizes e devem ser interpretados da seguinte maneira para determinar se um objeto sobreviveram a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="48337-116">The elements of the `objectIDRangeStart` and `cObjectIDRangeLength` arrays should be interpreted as follows to determine whether an object survived the garbage collection.</span></span> <span data-ttu-id="48337-117">Suponha que um `ObjectID` valor ( `ObjectID` ) esteja dentro do seguinte intervalo:</span><span class="sxs-lookup"><span data-stu-id="48337-117">Assume that an `ObjectID` value (`ObjectID`) lies within the following range:</span></span>  
  
 `ObjectIDRangeStart[i]` <= `ObjectID` < `ObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 <span data-ttu-id="48337-118">Para qualquer valor de `i` que esteja no seguinte intervalo, o objeto tem sobreviveram a coleta de lixo:</span><span class="sxs-lookup"><span data-stu-id="48337-118">For any value of `i` that is in the following range, the object has survived the garbage collection:</span></span>  
  
 <span data-ttu-id="48337-119">0 <=`i` < `cSurvivingObjectIDRanges`</span><span class="sxs-lookup"><span data-stu-id="48337-119">0 <= `i` < `cSurvivingObjectIDRanges`</span></span>  
  
 <span data-ttu-id="48337-120">Uma coleta de lixo não compactada recupera a memória ocupada por objetos "inativos", mas não compacta esse espaço livre.</span><span class="sxs-lookup"><span data-stu-id="48337-120">A non-compacting garbage collection reclaims the memory occupied by "dead" objects, but does not compact that freed space.</span></span> <span data-ttu-id="48337-121">Como resultado, a memória é retornada para o heap, mas nenhum objeto "ao vivo" é movido.</span><span class="sxs-lookup"><span data-stu-id="48337-121">As a result, memory is returned to the heap, but no "live" objects are moved.</span></span>  
  
 <span data-ttu-id="48337-122">As chamadas de Common Language Runtime (CLR) `SurvivingReferences` para coletas de lixo não compactadas.</span><span class="sxs-lookup"><span data-stu-id="48337-122">The common language runtime (CLR) calls `SurvivingReferences` for non-compacting garbage collections.</span></span> <span data-ttu-id="48337-123">Para compactar as coleções de lixo, [ICorProfilerCallback:: MovedReferences](icorprofilercallback-movedreferences-method.md) é chamado em vez disso.</span><span class="sxs-lookup"><span data-stu-id="48337-123">For compacting garbage collections, [ICorProfilerCallback::MovedReferences](icorprofilercallback-movedreferences-method.md) is called instead.</span></span> <span data-ttu-id="48337-124">Uma única coleta de lixo pode ser compactada para uma geração e não compactação para outra.</span><span class="sxs-lookup"><span data-stu-id="48337-124">A single garbage collection can be compacting for one generation and non-compacting for another.</span></span> <span data-ttu-id="48337-125">Para uma coleta de lixo em qualquer geração específica, o criador de perfil receberá um retorno de chamada `SurvivingReferences` ou um `MovedReferences` retorno de chamada, mas não ambos.</span><span class="sxs-lookup"><span data-stu-id="48337-125">For a garbage collection on any particular generation, the profiler will receive either a `SurvivingReferences` callback or a `MovedReferences` callback, but not both.</span></span>  
  
 <span data-ttu-id="48337-126">Vários `SurvivingReferences` retornos de chamada podem ser recebidos durante uma determinada coleta de lixo, devido ao buffer interno limitado, a vários threads relatando no caso da coleta de lixo do servidor e por outros motivos.</span><span class="sxs-lookup"><span data-stu-id="48337-126">Multiple `SurvivingReferences` callbacks might be received during a particular garbage collection, due to limited internal buffering, multiple threads reporting in the case of server garbage collection, and other reasons.</span></span> <span data-ttu-id="48337-127">No caso de vários retornos de chamada durante uma coleta de lixo, as informações são cumulativas – todas as referências que são relatadas em qualquer `SurvivingReferences` retorno de chamada sobrevivem à coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="48337-127">In the case of multiple callbacks during a garbage collection, the information is cumulative — all references that are reported in any `SurvivingReferences` callback survive the garbage collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48337-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="48337-128">Requirements</span></span>  
 <span data-ttu-id="48337-129">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48337-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48337-130">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="48337-130">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="48337-131">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="48337-131">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="48337-132">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48337-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48337-133">Confira também</span><span class="sxs-lookup"><span data-stu-id="48337-133">See also</span></span>

- [<span data-ttu-id="48337-134">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="48337-134">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="48337-135">Interface ICorProfilerCallback2</span><span class="sxs-lookup"><span data-stu-id="48337-135">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
- [<span data-ttu-id="48337-136">Método SurvivingReferences2</span><span class="sxs-lookup"><span data-stu-id="48337-136">SurvivingReferences2 Method</span></span>](icorprofilercallback4-survivingreferences2-method.md)
