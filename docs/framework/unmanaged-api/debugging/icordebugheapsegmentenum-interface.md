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
ms.openlocfilehash: e9679029cd54ac44832add9bc4f47f8c8e9a26a2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138456"
---
# <a name="icordebugheapsegmentenum-interface"></a><span data-ttu-id="c7876-102">Interface ICorDebugHeapSegmentEnum</span><span class="sxs-lookup"><span data-stu-id="c7876-102">ICorDebugHeapSegmentEnum Interface</span></span>
<span data-ttu-id="c7876-103">Fornece um enumerador para regiões de memória do heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="c7876-103">Provides an enumerator for the memory regions of the managed heap.</span></span> <span data-ttu-id="c7876-104">Essa interface é uma subclasse da interface ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="c7876-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c7876-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="c7876-105">Methods</span></span>  
  
|<span data-ttu-id="c7876-106">Método</span><span class="sxs-lookup"><span data-stu-id="c7876-106">Method</span></span>|<span data-ttu-id="c7876-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="c7876-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c7876-108">Método Next</span><span class="sxs-lookup"><span data-stu-id="c7876-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-next-method.md)|<span data-ttu-id="c7876-109">Obtém o número especificado de instâncias [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) que contêm informações sobre regiões do heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="c7876-109">Gets the specified number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that contain information about regions of the managed heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c7876-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="c7876-110">Remarks</span></span>  
 <span data-ttu-id="c7876-111">A interface `ICorDebugHeapSegmentEnum` implementa a interface ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="c7876-111">The `ICorDebugHeapSegmentEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="c7876-112">Uma instância de `ICorDebugHeapSegmentEnum` é populada com instâncias [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) chamando o método [ICorDebugProcess5:: EnumerateHeapRegions](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c7876-112">An `ICorDebugHeapSegmentEnum` instance is populated with [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances by calling the [ICorDebugProcess5::EnumerateHeapRegions](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md) method.</span></span> <span data-ttu-id="c7876-113">Os objetos [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) na coleção podem ser enumerados chamando o método [ICorDebugHeapSegmentEnum:: Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-next-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c7876-113">The [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects in the collection can be enumerated by calling the [ICorDebugHeapSegmentEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-next-method.md) method.</span></span>  
  
 <span data-ttu-id="c7876-114">Um objeto de coleção de `ICorDebugHeapSegmentEnum` enumera todas as regiões de memória que podem conter objetos gerenciados, mas não garante que os objetos gerenciados realmente residam nessas regiões.</span><span class="sxs-lookup"><span data-stu-id="c7876-114">An `ICorDebugHeapSegmentEnum` collection object enumerates all memory regions that may contain managed objects, but it does not guarantee that managed objects actually reside in those regions.</span></span> <span data-ttu-id="c7876-115">Ele pode incluir informações sobre regiões de memória vazias ou reservadas.</span><span class="sxs-lookup"><span data-stu-id="c7876-115">It may include information about empty or reserved memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7876-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c7876-116">Requirements</span></span>  
 <span data-ttu-id="c7876-117">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7876-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7876-118">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c7876-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c7876-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c7876-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c7876-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7876-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7876-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c7876-121">See also</span></span>

- [<span data-ttu-id="c7876-122">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="c7876-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
