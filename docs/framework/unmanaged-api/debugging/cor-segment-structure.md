---
title: Estrutura COR_SEGMENT
ms.date: 03/30/2017
api_name:
- COR_SEGMENT
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_SEGMENT
helpviewer_keywords:
- COR_SEGMENT structure [.NET Framework debugging]
ms.assetid: 93aeecb9-7fef-4545-8daf-f566dfc47084
topic_type:
- apiref
ms.openlocfilehash: 0370c74bde9ca5bdbd0fd03515f4b174ddd0a39a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132312"
---
# <a name="cor_segment-structure"></a><span data-ttu-id="80472-102">Estrutura COR_SEGMENT</span><span class="sxs-lookup"><span data-stu-id="80472-102">COR_SEGMENT Structure</span></span>
<span data-ttu-id="80472-103">Contém informações sobre uma região da memória no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="80472-103">Contains information about a region of memory in the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80472-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="80472-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_SEGMENT {  
    CORDB_ADDRESS start;            
    CORDB_ADDRESS end;              
    CorDebugGenerationTypes gen;    
    ULONG heap;                     
} COR_SEGMENT;  
```  
  
## <a name="members"></a><span data-ttu-id="80472-105">Membros</span><span class="sxs-lookup"><span data-stu-id="80472-105">Members</span></span>  
  
|<span data-ttu-id="80472-106">Membro</span><span class="sxs-lookup"><span data-stu-id="80472-106">Member</span></span>|<span data-ttu-id="80472-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="80472-107">Description</span></span>|  
|------------|-----------------|  
|`start`|<span data-ttu-id="80472-108">O endereço inicial da região de memória.</span><span class="sxs-lookup"><span data-stu-id="80472-108">The starting address of the memory region.</span></span>|  
|`end`|<span data-ttu-id="80472-109">O endereço final da região de memória.</span><span class="sxs-lookup"><span data-stu-id="80472-109">The ending address of the memory region.</span></span>|  
|`gen`|<span data-ttu-id="80472-110">Um membro de enumeração [CorDebugGenerationTypes](cordebuggenerationtypes-enumeration.md) que indica a geração da região de memória.</span><span class="sxs-lookup"><span data-stu-id="80472-110">A [CorDebugGenerationTypes](cordebuggenerationtypes-enumeration.md) enumeration member that indicates the generation of the memory region.</span></span>|  
|`heap`|<span data-ttu-id="80472-111">O número de heap no qual reside a região de memória.</span><span class="sxs-lookup"><span data-stu-id="80472-111">The heap number in which the memory region resides.</span></span> <span data-ttu-id="80472-112">Consulte a seção Comentários para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="80472-112">See the Remarks section for more information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="80472-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="80472-113">Remarks</span></span>  
 <span data-ttu-id="80472-114">A estrutura `COR_SEGMENTS` representa uma região da memória no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="80472-114">The `COR_SEGMENTS` structure represents a region of memory in the managed heap.</span></span>  <span data-ttu-id="80472-115">Objetos `COR_SEGMENTS` são membros do objeto da coleção [ICorDebugHeapRegionEnum](icordebugheapsegmentenum-interface.md), que é preenchido chamando o método [ICorDebugProcess5::EnumerateHeapRegions](icordebugprocess5-enumerateheapregions-method.md).</span><span class="sxs-lookup"><span data-stu-id="80472-115">`COR_SEGMENTS` objects are members of the [ICorDebugHeapRegionEnum](icordebugheapsegmentenum-interface.md) collection object, which is populated by calling the [ICorDebugProcess5::EnumerateHeapRegions](icordebugprocess5-enumerateheapregions-method.md) method.</span></span>  
  
 <span data-ttu-id="80472-116">O campo `heap` é o número de processadores, que corresponde ao heap que está sendo relatado.</span><span class="sxs-lookup"><span data-stu-id="80472-116">The `heap` field is the processor number, which corresponds to the heap being reported.</span></span> <span data-ttu-id="80472-117">Para os coletores de lixo de estação de trabalho, seu valor é sempre zero, uma vez que estações de trabalho têm apenas um heap de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="80472-117">For workstation garbage collectors, its value is always zero, because workstations have only one garbage collection heap.</span></span> <span data-ttu-id="80472-118">Para os coletores de lixo do servidor, seu valor corresponde ao processador ao qual o heap está anexado.</span><span class="sxs-lookup"><span data-stu-id="80472-118">For server garbage collectors, its value corresponds to the processor the heap is attached to.</span></span> <span data-ttu-id="80472-119">Observe que pode haver mais ou menos heaps de coleta de lixo que o número real de processadores devido a detalhes de implementação do coletor de lixo.</span><span class="sxs-lookup"><span data-stu-id="80472-119">Note that there may be more or fewer garbage collection heaps than there are actual processors due to the implementation details of the garbage collector.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80472-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="80472-120">Requirements</span></span>  
 <span data-ttu-id="80472-121">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80472-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80472-122">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="80472-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="80472-123">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="80472-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="80472-124">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80472-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80472-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="80472-125">See also</span></span>

- [<span data-ttu-id="80472-126">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="80472-126">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="80472-127">Depuração</span><span class="sxs-lookup"><span data-stu-id="80472-127">Debugging</span></span>](index.md)
