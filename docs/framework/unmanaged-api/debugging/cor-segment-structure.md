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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: deea4e6128eace0ffa539d77bb63f7629eb72354
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36207398"
---
# <a name="corsegment-structure"></a><span data-ttu-id="aa87a-102">Estrutura COR_SEGMENT</span><span class="sxs-lookup"><span data-stu-id="aa87a-102">COR_SEGMENT Structure</span></span>
<span data-ttu-id="aa87a-103">Contém informações sobre uma região da memória no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="aa87a-103">Contains information about a region of memory in the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa87a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="aa87a-104">Syntax</span></span>  
  
```  
typedef struct _COR_SEGMENT {  
    CORDB_ADDRESS start;            
    CORDB_ADDRESS end;              
    CorDebugGenerationTypes gen;    
    ULONG heap;                     
} COR_SEGMENT;  
```  
  
## <a name="members"></a><span data-ttu-id="aa87a-105">Membros</span><span class="sxs-lookup"><span data-stu-id="aa87a-105">Members</span></span>  
  
|<span data-ttu-id="aa87a-106">Membro</span><span class="sxs-lookup"><span data-stu-id="aa87a-106">Member</span></span>|<span data-ttu-id="aa87a-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="aa87a-107">Description</span></span>|  
|------------|-----------------|  
|`start`|<span data-ttu-id="aa87a-108">O endereço inicial da região de memória.</span><span class="sxs-lookup"><span data-stu-id="aa87a-108">The starting address of the memory region.</span></span>|  
|`end`|<span data-ttu-id="aa87a-109">O endereço final da região de memória.</span><span class="sxs-lookup"><span data-stu-id="aa87a-109">The ending address of the memory region.</span></span>|  
|`gen`|<span data-ttu-id="aa87a-110">Um membro de enumeração [CorDebugGenerationTypes](../../../../docs/framework/unmanaged-api/debugging/cordebuggenerationtypes-enumeration.md) que indica a geração da região de memória.</span><span class="sxs-lookup"><span data-stu-id="aa87a-110">A [CorDebugGenerationTypes](../../../../docs/framework/unmanaged-api/debugging/cordebuggenerationtypes-enumeration.md) enumeration member that indicates the generation of the memory region.</span></span>|  
|`heap`|<span data-ttu-id="aa87a-111">O número de heap no qual reside a região de memória.</span><span class="sxs-lookup"><span data-stu-id="aa87a-111">The heap number in which the memory region resides.</span></span> <span data-ttu-id="aa87a-112">Consulte a seção Comentários para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="aa87a-112">See the Remarks section for more information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aa87a-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="aa87a-113">Remarks</span></span>  
 <span data-ttu-id="aa87a-114">A estrutura `COR_SEGMENTS` representa uma região da memória no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="aa87a-114">The `COR_SEGMENTS` structure represents a region of memory in the managed heap.</span></span>  <span data-ttu-id="aa87a-115">Objetos `COR_SEGMENTS` são membros do objeto da coleção [ICorDebugHeapRegionEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md), que é preenchido chamando o método [ICorDebugProcess5::EnumerateHeapRegions](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md).</span><span class="sxs-lookup"><span data-stu-id="aa87a-115">`COR_SEGMENTS` objects are members of the [ICorDebugHeapRegionEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) collection object, which is populated by calling the [ICorDebugProcess5::EnumerateHeapRegions](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md) method.</span></span>  
  
 <span data-ttu-id="aa87a-116">O campo `heap` é o número de processadores, que corresponde ao heap que está sendo relatado.</span><span class="sxs-lookup"><span data-stu-id="aa87a-116">The `heap` field is the processor number, which corresponds to the heap being reported.</span></span> <span data-ttu-id="aa87a-117">Para os coletores de lixo de estação de trabalho, seu valor é sempre zero, uma vez que estações de trabalho têm apenas um heap de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="aa87a-117">For workstation garbage collectors, its value is always zero, because workstations have only one garbage collection heap.</span></span> <span data-ttu-id="aa87a-118">Para os coletores de lixo do servidor, seu valor corresponde ao processador ao qual o heap está anexado.</span><span class="sxs-lookup"><span data-stu-id="aa87a-118">For server garbage collectors, its value corresponds to the processor the heap is attached to.</span></span> <span data-ttu-id="aa87a-119">Observe que pode haver mais ou menos heaps de coleta de lixo que o número real de processadores devido a detalhes de implementação do coletor de lixo.</span><span class="sxs-lookup"><span data-stu-id="aa87a-119">Note that there may be more or fewer garbage collection heaps than there are actual processors due to the implementation details of the garbage collector.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa87a-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="aa87a-120">Requirements</span></span>  
 <span data-ttu-id="aa87a-121">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aa87a-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa87a-122">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aa87a-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aa87a-123">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aa87a-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aa87a-124">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa87a-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa87a-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aa87a-125">See Also</span></span>  
 [<span data-ttu-id="aa87a-126">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="aa87a-126">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="aa87a-127">Depuração</span><span class="sxs-lookup"><span data-stu-id="aa87a-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
