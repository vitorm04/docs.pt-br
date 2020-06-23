---
title: Interface ICorDebugHeapSegmentEnum
ms.date: 03/30/2017
api_name:
- ICorDebugHealRegionEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapSegmentEnum
helpviewer_keywords:
- ICorDebugHeapSegmentEnum interface [.NET Framework debugging]
ms.assetid: 20fc1b9d-e228-4107-bd76-53934c1724b9
topic_type:
- apiref
ms.openlocfilehash: acf490895db35af1c5d0d1e7fe7e3de5ae2a16b6
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904280"
---
# <a name="icordebugheapsegmentenum-interface"></a><span data-ttu-id="abde4-102">Interface ICorDebugHeapSegmentEnum</span><span class="sxs-lookup"><span data-stu-id="abde4-102">ICorDebugHeapSegmentEnum Interface</span></span>
<span data-ttu-id="abde4-103">Fornece um enumerador para regiões de memória do heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="abde4-103">Provides an enumerator for the memory regions of the managed heap.</span></span> <span data-ttu-id="abde4-104">Essa interface é uma subclasse da interface ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="abde4-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="abde4-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="abde4-105">Methods</span></span>  
  
|<span data-ttu-id="abde4-106">Método</span><span class="sxs-lookup"><span data-stu-id="abde4-106">Method</span></span>|<span data-ttu-id="abde4-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="abde4-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="abde4-108">Método Next</span><span class="sxs-lookup"><span data-stu-id="abde4-108">Next Method</span></span>](icordebugheapsegmentenum-next-method.md)|<span data-ttu-id="abde4-109">Obtém o número especificado de instâncias de [COR_SEGMENT](cor-segment-structure.md) que contêm informações sobre regiões do heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="abde4-109">Gets the specified number of [COR_SEGMENT](cor-segment-structure.md) instances that contain information about regions of the managed heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="abde4-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="abde4-110">Remarks</span></span>  
 <span data-ttu-id="abde4-111">A `ICorDebugHeapSegmentEnum` interface implementa a interface ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="abde4-111">The `ICorDebugHeapSegmentEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="abde4-112">Uma `ICorDebugHeapSegmentEnum` instância é populada com instâncias de [COR_SEGMENT](cor-segment-structure.md) chamando o método [ICorDebugProcess5:: EnumerateHeapRegions](icordebugprocess5-enumerateheapregions-method.md) .</span><span class="sxs-lookup"><span data-stu-id="abde4-112">An `ICorDebugHeapSegmentEnum` instance is populated with [COR_SEGMENT](cor-segment-structure.md) instances by calling the [ICorDebugProcess5::EnumerateHeapRegions](icordebugprocess5-enumerateheapregions-method.md) method.</span></span> <span data-ttu-id="abde4-113">Os objetos [COR_SEGMENT](cor-segment-structure.md) na coleção podem ser enumerados chamando o método [ICorDebugHeapSegmentEnum:: Next](icordebugheapsegmentenum-next-method.md) .</span><span class="sxs-lookup"><span data-stu-id="abde4-113">The [COR_SEGMENT](cor-segment-structure.md) objects in the collection can be enumerated by calling the [ICorDebugHeapSegmentEnum::Next](icordebugheapsegmentenum-next-method.md) method.</span></span>  
  
 <span data-ttu-id="abde4-114">Um `ICorDebugHeapSegmentEnum` objeto de coleção enumera todas as regiões de memória que podem conter objetos gerenciados, mas não garante que os objetos gerenciados realmente residam nessas regiões.</span><span class="sxs-lookup"><span data-stu-id="abde4-114">An `ICorDebugHeapSegmentEnum` collection object enumerates all memory regions that may contain managed objects, but it does not guarantee that managed objects actually reside in those regions.</span></span> <span data-ttu-id="abde4-115">Ele pode incluir informações sobre regiões de memória vazias ou reservadas.</span><span class="sxs-lookup"><span data-stu-id="abde4-115">It may include information about empty or reserved memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="abde4-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="abde4-116">Requirements</span></span>  
 <span data-ttu-id="abde4-117">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="abde4-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="abde4-118">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="abde4-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="abde4-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="abde4-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="abde4-120">**.NET Framework versões:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="abde4-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abde4-121">Veja também</span><span class="sxs-lookup"><span data-stu-id="abde4-121">See also</span></span>

- [<span data-ttu-id="abde4-122">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="abde4-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
