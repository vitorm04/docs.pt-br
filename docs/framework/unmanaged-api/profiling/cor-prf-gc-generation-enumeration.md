---
title: Enumeração COR_PRF_GC_GENERATION
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_GENERATION
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_GENERATION
helpviewer_keywords:
- COR_GC_GENERATION_FLAGS enumeration [.NET Framework profiling]
ms.assetid: d6ece160-26ad-4d39-abd7-05acd6f78c48
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0178e2a7877803644bb25e6700306d7ac2ef2d4f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59215882"
---
# <a name="corprfgcgeneration-enumeration"></a><span data-ttu-id="82cb1-102">Enumeração COR_PRF_GC_GENERATION</span><span class="sxs-lookup"><span data-stu-id="82cb1-102">COR_PRF_GC_GENERATION Enumeration</span></span>
<span data-ttu-id="82cb1-103">Identifica uma geração de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="82cb1-103">Identifies a garbage-collection generation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82cb1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="82cb1-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_GC_GEN_0 = 0,  
    COR_PRF_GC_GEN_1 = 1,  
    COR_PRF_GC_GEN_2 = 2,  
    COR_PRF_GC_LARGE_OBJECT_HEAP = 3  
} COR_PRF_GC_GENERATION;  
```  
  
## <a name="members"></a><span data-ttu-id="82cb1-105">Membros</span><span class="sxs-lookup"><span data-stu-id="82cb1-105">Members</span></span>  
  
|<span data-ttu-id="82cb1-106">Membro</span><span class="sxs-lookup"><span data-stu-id="82cb1-106">Member</span></span>|<span data-ttu-id="82cb1-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="82cb1-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_GEN_0`|<span data-ttu-id="82cb1-108">O objeto é armazenado como geração 0.</span><span class="sxs-lookup"><span data-stu-id="82cb1-108">The object is stored as generation 0.</span></span>|  
|`COR_PRF_GC_GEN_1`|<span data-ttu-id="82cb1-109">O objeto é armazenado como geração 1.</span><span class="sxs-lookup"><span data-stu-id="82cb1-109">The object is stored as generation 1.</span></span>|  
|`COR_PRF_GC_GEN_2`|<span data-ttu-id="82cb1-110">O objeto é armazenado como geração 2.</span><span class="sxs-lookup"><span data-stu-id="82cb1-110">The object is stored as generation 2.</span></span>|  
|`COR_PRF_GC_LARGE_OBJECT_HEAP`|<span data-ttu-id="82cb1-111">O objeto é armazenado na heap de objeto grande.</span><span class="sxs-lookup"><span data-stu-id="82cb1-111">The object is stored in the large-object heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="82cb1-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="82cb1-112">Remarks</span></span>  
 <span data-ttu-id="82cb1-113">O coletor de lixo melhora o desempenho de gerenciamento de memória, divisão de objetos em gerações com base na idade.</span><span class="sxs-lookup"><span data-stu-id="82cb1-113">The garbage collector improves memory management performance by dividing objects into generations based on age.</span></span> <span data-ttu-id="82cb1-114">Atualmente, o coletor de lixo usa três gerações, numeradas de 0, 1 e 2, além de um segmento de heap especial que é usado para objetos grandes.</span><span class="sxs-lookup"><span data-stu-id="82cb1-114">The garbage collector currently uses three generations, numbered 0, 1, and 2, plus a special heap segment that is used for large objects.</span></span> <span data-ttu-id="82cb1-115">Objetos cujo tamanho é maior do que um determinado valor são armazenados no heap de objeto grande.</span><span class="sxs-lookup"><span data-stu-id="82cb1-115">Objects whose size is larger than a particular value are stored in the large-object heap.</span></span> <span data-ttu-id="82cb1-116">Outros objetos alocados começam que pertencem a geração 0.</span><span class="sxs-lookup"><span data-stu-id="82cb1-116">Other allocated objects start out belonging to generation 0.</span></span> <span data-ttu-id="82cb1-117">Todos os objetos que existem após a coleta de lixo na geração 0 são promovidos à geração 1.</span><span class="sxs-lookup"><span data-stu-id="82cb1-117">All objects that exist after garbage collection occurs in generation 0 are promoted to generation 1.</span></span> <span data-ttu-id="82cb1-118">Movem objetos existentes após a coleta de lixo na geração 1 para a geração 2.</span><span class="sxs-lookup"><span data-stu-id="82cb1-118">Objects that exist after garbage collection occurs in generation 1 move into generation 2.</span></span>  
  
 <span data-ttu-id="82cb1-119">O uso de gerações significa que o coletor de lixo tem que trabalhar com apenas um subconjunto dos objetos alocados a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="82cb1-119">The use of generations means that the garbage collector has to work with only a subset of the allocated objects at any one time.</span></span>  
  
 <span data-ttu-id="82cb1-120">O `COR_PRF_GC_GENERATION` enumeração é usada pelo [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) estrutura.</span><span class="sxs-lookup"><span data-stu-id="82cb1-120">The `COR_PRF_GC_GENERATION` enumeration is used by the [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82cb1-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="82cb1-121">Requirements</span></span>  
 <span data-ttu-id="82cb1-122">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82cb1-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82cb1-123">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="82cb1-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="82cb1-124">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="82cb1-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="82cb1-125">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82cb1-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82cb1-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="82cb1-126">See also</span></span>

- [<span data-ttu-id="82cb1-127">Criando perfil de enumerações</span><span class="sxs-lookup"><span data-stu-id="82cb1-127">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
