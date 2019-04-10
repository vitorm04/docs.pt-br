---
title: Estrutura COR_PRF_GC_GENERATION_RANGE
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_GENERATION_RANGE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_GENERATION_RANGE
helpviewer_keywords:
- COR_PRF_GC_GENERATION_RANGE structure [.NET Framework profiling]
ms.assetid: e7e07273-8d10-4a68-807e-59634e3f8c5e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 646c4e37a7fab503a26557f9fdfc926b1186b17b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59216698"
---
# <a name="corprfgcgenerationrange-structure"></a><span data-ttu-id="5d6c3-102">Estrutura COR_PRF_GC_GENERATION_RANGE</span><span class="sxs-lookup"><span data-stu-id="5d6c3-102">COR_PRF_GC_GENERATION_RANGE Structure</span></span>
<span data-ttu-id="5d6c3-103">Descreve um intervalo (ou seja, um bloco) de memória que está passando por coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="5d6c3-103">Describes a range (that is, block) of memory that is undergoing garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d6c3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5d6c3-104">Syntax</span></span>  
  
```  
typedef struct COR_PRF_GC_GENERATION_RANGE {  
    COR_PRF_GC_GENERATION generation;  
    ObjectID rangeStart;  
    UINT_PTR rangeLength;  
    UINT_PTR rangeLengthReserved;  
} COR_PRF_GC_GENERATION_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="5d6c3-105">Membros</span><span class="sxs-lookup"><span data-stu-id="5d6c3-105">Members</span></span>  
  
|<span data-ttu-id="5d6c3-106">Membro</span><span class="sxs-lookup"><span data-stu-id="5d6c3-106">Member</span></span>|<span data-ttu-id="5d6c3-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="5d6c3-107">Description</span></span>|  
|------------|-----------------|  
|`generation`|<span data-ttu-id="5d6c3-108">Um valor igual a [COR_PRF_GC_GENERATION](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md) enumeração que especifica a geração para o qual o bloco de memória pertence.</span><span class="sxs-lookup"><span data-stu-id="5d6c3-108">A value of the [COR_PRF_GC_GENERATION](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md) enumeration that specifies the generation to which the block of memory belongs.</span></span>|  
|`rangeStart`|<span data-ttu-id="5d6c3-109">A ID de um objeto que especifica o local de início do bloco de memória.</span><span class="sxs-lookup"><span data-stu-id="5d6c3-109">The ID of an object that specifies the starting location of the block of memory.</span></span>|  
|`rangeLength`|<span data-ttu-id="5d6c3-110">Um ponteiro para um inteiro que especifica o tamanho da parte usada do bloco de memória (ou seja, a quantidade de memória usada dentro do bloco).</span><span class="sxs-lookup"><span data-stu-id="5d6c3-110">A pointer to an integer that specifies the size of the used portion of the memory block (that is, the amount of memory used within the block).</span></span>|  
|`rangeLengthReserved`|<span data-ttu-id="5d6c3-111">Um ponteiro para um inteiro que especifica o tamanho do bloco de memória (ou seja, a quantidade de memória reservada para o bloco).</span><span class="sxs-lookup"><span data-stu-id="5d6c3-111">A pointer to an integer that specifies the size of the memory block (that is, the amount of memory reserved for the block).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5d6c3-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="5d6c3-112">Remarks</span></span>  
 <span data-ttu-id="5d6c3-113">O `rangeLength` valor é garantido que seja preciso apenas se [ICorProfilerInfo2::GetGenerationBounds](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getgenerationbounds-method.md) ou [ICorProfilerInfo2::GetObjectGeneration](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getobjectgeneration-method.md), ambas que usam o `COR_PRF_GC_GENERATION_RANGE` estrutura, é chamado a partir de [ICorProfilerCallback2::GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) ou o [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="5d6c3-113">The `rangeLength` value is guaranteed to be accurate only if [ICorProfilerInfo2::GetGenerationBounds](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getgenerationbounds-method.md) or [ICorProfilerInfo2::GetObjectGeneration](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getobjectgeneration-method.md), both of which use the `COR_PRF_GC_GENERATION_RANGE` structure, is called from the [ICorProfilerCallback2::GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) or the [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d6c3-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5d6c3-114">Requirements</span></span>  
 <span data-ttu-id="5d6c3-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d6c3-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d6c3-116">**Cabeçalho:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="5d6c3-116">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="5d6c3-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5d6c3-117">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="5d6c3-118">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="5d6c3-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5d6c3-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5d6c3-119">See also</span></span>

- [<span data-ttu-id="5d6c3-120">Estruturas de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="5d6c3-120">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
