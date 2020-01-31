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
ms.openlocfilehash: 682aac9729519e0861ae6e6f60df78a30063c278
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867198"
---
# <a name="cor_prf_gc_generation_range-structure"></a><span data-ttu-id="42865-102">Estrutura COR_PRF_GC_GENERATION_RANGE</span><span class="sxs-lookup"><span data-stu-id="42865-102">COR_PRF_GC_GENERATION_RANGE Structure</span></span>
<span data-ttu-id="42865-103">Descreve um intervalo (ou seja, um bloco) de memória que está passando por coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="42865-103">Describes a range (that is, block) of memory that is undergoing garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42865-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="42865-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_PRF_GC_GENERATION_RANGE {  
    COR_PRF_GC_GENERATION generation;  
    ObjectID rangeStart;  
    UINT_PTR rangeLength;  
    UINT_PTR rangeLengthReserved;  
} COR_PRF_GC_GENERATION_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="42865-105">Membros</span><span class="sxs-lookup"><span data-stu-id="42865-105">Members</span></span>  
  
|<span data-ttu-id="42865-106">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="42865-106">Member</span></span>|<span data-ttu-id="42865-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="42865-107">Description</span></span>|  
|------------|-----------------|  
|`generation`|<span data-ttu-id="42865-108">Um valor da enumeração [COR_PRF_GC_GENERATION](cor-prf-gc-generation-enumeration.md) que especifica a geração à qual o bloco de memória pertence.</span><span class="sxs-lookup"><span data-stu-id="42865-108">A value of the [COR_PRF_GC_GENERATION](cor-prf-gc-generation-enumeration.md) enumeration that specifies the generation to which the block of memory belongs.</span></span>|  
|`rangeStart`|<span data-ttu-id="42865-109">A ID de um objeto que especifica o local inicial do bloco de memória.</span><span class="sxs-lookup"><span data-stu-id="42865-109">The ID of an object that specifies the starting location of the block of memory.</span></span>|  
|`rangeLength`|<span data-ttu-id="42865-110">Um ponteiro para um inteiro que especifica o tamanho da parte usada do bloco de memória (ou seja, a quantidade de memória usada dentro do bloco).</span><span class="sxs-lookup"><span data-stu-id="42865-110">A pointer to an integer that specifies the size of the used portion of the memory block (that is, the amount of memory used within the block).</span></span>|  
|`rangeLengthReserved`|<span data-ttu-id="42865-111">Um ponteiro para um inteiro que especifica o tamanho do bloco de memória (ou seja, a quantidade de memória reservada para o bloco).</span><span class="sxs-lookup"><span data-stu-id="42865-111">A pointer to an integer that specifies the size of the memory block (that is, the amount of memory reserved for the block).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="42865-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="42865-112">Remarks</span></span>  
 <span data-ttu-id="42865-113">É garantido que o valor `rangeLength` seja preciso apenas se [ICorProfilerInfo2:: GetGenerationBounds](icorprofilerinfo2-getgenerationbounds-method.md) ou [ICorProfilerInfo2:: GetObjectGeneration](icorprofilerinfo2-getobjectgeneration-method.md), ambos usam a estrutura `COR_PRF_GC_GENERATION_RANGE`, é chamado do método [ICorProfilerCallback2:: GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md) ou [ICorProfilerCallback2:: GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) .</span><span class="sxs-lookup"><span data-stu-id="42865-113">The `rangeLength` value is guaranteed to be accurate only if [ICorProfilerInfo2::GetGenerationBounds](icorprofilerinfo2-getgenerationbounds-method.md) or [ICorProfilerInfo2::GetObjectGeneration](icorprofilerinfo2-getobjectgeneration-method.md), both of which use the `COR_PRF_GC_GENERATION_RANGE` structure, is called from the [ICorProfilerCallback2::GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md) or the [ICorProfilerCallback2::GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42865-114">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="42865-114">Requirements</span></span>  
 <span data-ttu-id="42865-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42865-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42865-116">**Cabeçalho:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="42865-116">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="42865-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="42865-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="42865-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42865-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42865-119">Veja também</span><span class="sxs-lookup"><span data-stu-id="42865-119">See also</span></span>

- [<span data-ttu-id="42865-120">Estruturas de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="42865-120">Profiling Structures</span></span>](profiling-structures.md)
