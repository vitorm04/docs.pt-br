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
ms.openlocfilehash: 0eb1f57e3505f9ce5bb8b831d30c3891e51097c3
ms.sourcegitcommit: c2c1269a81ffdcfc8675bcd9a8505b1a11ffb271
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/25/2020
ms.locfileid: "82158561"
---
# <a name="cor_prf_gc_generation-enumeration"></a><span data-ttu-id="f7b3f-102">Enumeração COR_PRF_GC_GENERATION</span><span class="sxs-lookup"><span data-stu-id="f7b3f-102">COR_PRF_GC_GENERATION Enumeration</span></span>
<span data-ttu-id="f7b3f-103">Identifica uma geração de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="f7b3f-103">Identifies a garbage-collection generation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7b3f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f7b3f-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_GC_GEN_0 = 0,  
    COR_PRF_GC_GEN_1 = 1,  
    COR_PRF_GC_GEN_2 = 2,  
    COR_PRF_GC_LARGE_OBJECT_HEAP = 3,
    COR_PRF_GC_PINNED_OBJECT_HEAP= 4
} COR_PRF_GC_GENERATION;  
```  
  
## <a name="members"></a><span data-ttu-id="f7b3f-105">Membros</span><span class="sxs-lookup"><span data-stu-id="f7b3f-105">Members</span></span>  
  
|<span data-ttu-id="f7b3f-106">Membro</span><span class="sxs-lookup"><span data-stu-id="f7b3f-106">Member</span></span>|<span data-ttu-id="f7b3f-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="f7b3f-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_GEN_0`|<span data-ttu-id="f7b3f-108">O objeto é armazenado como geração 0.</span><span class="sxs-lookup"><span data-stu-id="f7b3f-108">The object is stored as generation 0.</span></span>|  
|`COR_PRF_GC_GEN_1`|<span data-ttu-id="f7b3f-109">O objeto é armazenado como geração 1.</span><span class="sxs-lookup"><span data-stu-id="f7b3f-109">The object is stored as generation 1.</span></span>|  
|`COR_PRF_GC_GEN_2`|<span data-ttu-id="f7b3f-110">O objeto é armazenado como geração 2.</span><span class="sxs-lookup"><span data-stu-id="f7b3f-110">The object is stored as generation 2.</span></span>|  
|`COR_PRF_GC_LARGE_OBJECT_HEAP`|<span data-ttu-id="f7b3f-111">O objeto é armazenado no heap de objeto grande.</span><span class="sxs-lookup"><span data-stu-id="f7b3f-111">The object is stored in the large-object heap.</span></span>|  
|`COR_PRF_GC_PINNED_OBJECT_HEAP`|<span data-ttu-id="f7b3f-112">O objeto é armazenado no heap fixado-Object.</span><span class="sxs-lookup"><span data-stu-id="f7b3f-112">The object is stored in the pinned-object heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f7b3f-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="f7b3f-113">Remarks</span></span>  
 <span data-ttu-id="f7b3f-114">O coletor de lixo melhora o desempenho de gerenciamento de memória dividindo objetos em gerações com base na idade.</span><span class="sxs-lookup"><span data-stu-id="f7b3f-114">The garbage collector improves memory management performance by dividing objects into generations based on age.</span></span> <span data-ttu-id="f7b3f-115">O coletor de lixo atualmente usa três gerações, numeradas de 0, 1 e 2 e dois segmentos de heap especiais, um para objetos grandes e outro para objetos fixados.</span><span class="sxs-lookup"><span data-stu-id="f7b3f-115">The garbage collector currently uses three generations, numbered 0, 1, and 2, and two special heap segments, one for large objects and one for pinned objects.</span></span>
  
 <span data-ttu-id="f7b3f-116">Objetos cujo tamanho é maior do que um valor de limite são armazenados no heap de objeto grande.</span><span class="sxs-lookup"><span data-stu-id="f7b3f-116">Objects whose size is larger than a threshold value are stored in the large-object heap.</span></span> <span data-ttu-id="f7b3f-117">Os objetos fixados podem ser alocados para o heap de objeto fixado para evitar o custo de desempenho de alocá-los nos heaps normais.</span><span class="sxs-lookup"><span data-stu-id="f7b3f-117">Pinned objects can be allocated to the pinned-object heap to avoid the performance cost of allocating them on the normal heaps.</span></span> <span data-ttu-id="f7b3f-118">Outros objetos alocados começam a pertencer à geração 0.</span><span class="sxs-lookup"><span data-stu-id="f7b3f-118">Other allocated objects start out belonging to generation 0.</span></span> <span data-ttu-id="f7b3f-119">Todos os objetos que existem após a coleta de lixo ocorre na geração 0 são promovidos para a geração 1.</span><span class="sxs-lookup"><span data-stu-id="f7b3f-119">All objects that exist after garbage collection occurs in generation 0 are promoted to generation 1.</span></span> <span data-ttu-id="f7b3f-120">Os objetos que existem após a coleta de lixo ocorrem na passagem de geração 1 para a geração 2.</span><span class="sxs-lookup"><span data-stu-id="f7b3f-120">Objects that exist after garbage collection occurs in generation 1 move into generation 2.</span></span>  
  
 <span data-ttu-id="f7b3f-121">O uso de gerações significa que o coletor de lixo tem que trabalhar apenas com um subconjunto dos objetos alocados a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="f7b3f-121">The use of generations means that the garbage collector has to work with only a subset of the allocated objects at any one time.</span></span>  
  
 <span data-ttu-id="f7b3f-122">A `COR_PRF_GC_GENERATION` enumeração é usada pela estrutura de [COR_PRF_GC_GENERATION_RANGE](cor-prf-gc-generation-range-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="f7b3f-122">The `COR_PRF_GC_GENERATION` enumeration is used by the [COR_PRF_GC_GENERATION_RANGE](cor-prf-gc-generation-range-structure.md) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7b3f-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f7b3f-123">Requirements</span></span>  
 <span data-ttu-id="f7b3f-124">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7b3f-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7b3f-125">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="f7b3f-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f7b3f-126">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f7b3f-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f7b3f-127">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7b3f-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7b3f-128">Veja também</span><span class="sxs-lookup"><span data-stu-id="f7b3f-128">See also</span></span>

- [<span data-ttu-id="f7b3f-129">Criando perfil de enumerações</span><span class="sxs-lookup"><span data-stu-id="f7b3f-129">Profiling Enumerations</span></span>](profiling-enumerations.md)
