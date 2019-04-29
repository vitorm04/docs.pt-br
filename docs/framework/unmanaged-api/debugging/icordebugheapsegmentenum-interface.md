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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 73036d1c12c46cbfda8031073a005bc9b376040e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61756202"
---
# <a name="icordebugheapsegmentenum-interface"></a><span data-ttu-id="74a9a-102">Interface ICorDebugHeapSegmentEnum</span><span class="sxs-lookup"><span data-stu-id="74a9a-102">ICorDebugHeapSegmentEnum Interface</span></span>
<span data-ttu-id="74a9a-103">Fornece um enumerador para regiões de memória do heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="74a9a-103">Provides an enumerator for the memory regions of the managed heap.</span></span> <span data-ttu-id="74a9a-104">Essa interface é uma subclasse da interface ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="74a9a-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="74a9a-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="74a9a-105">Methods</span></span>  
  
|<span data-ttu-id="74a9a-106">Método</span><span class="sxs-lookup"><span data-stu-id="74a9a-106">Method</span></span>|<span data-ttu-id="74a9a-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="74a9a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="74a9a-108">Método Next</span><span class="sxs-lookup"><span data-stu-id="74a9a-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-next-method.md)|<span data-ttu-id="74a9a-109">Obtém o número especificado de [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instâncias que contêm informações sobre as regiões do heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="74a9a-109">Gets the specified number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that contain information about regions of the managed heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="74a9a-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="74a9a-110">Remarks</span></span>  
 <span data-ttu-id="74a9a-111">O `ICorDebugHeapSegmentEnum` interface implementa a interface ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="74a9a-111">The `ICorDebugHeapSegmentEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="74a9a-112">Uma `ICorDebugHeapSegmentEnum` instância é preenchida com [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instâncias chamando o [ICorDebugProcess5::EnumerateHeapRegions](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="74a9a-112">An `ICorDebugHeapSegmentEnum` instance is populated with [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances by calling the [ICorDebugProcess5::EnumerateHeapRegions](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md) method.</span></span> <span data-ttu-id="74a9a-113">O [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objetos na coleção podem ser enumerados chamando o [icordebugheapsegmentenum:: Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-next-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="74a9a-113">The [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects in the collection can be enumerated by calling the [ICorDebugHeapSegmentEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-next-method.md) method.</span></span>  
  
 <span data-ttu-id="74a9a-114">Um `ICorDebugHeapSegmentEnum` objeto da coleção enumera todas as regiões de memória que podem conter objetos gerenciados, mas ele não garante que os objetos gerenciados, na verdade, residam nessas regiões.</span><span class="sxs-lookup"><span data-stu-id="74a9a-114">An `ICorDebugHeapSegmentEnum` collection object enumerates all memory regions that may contain managed objects, but it does not guarantee that managed objects actually reside in those regions.</span></span> <span data-ttu-id="74a9a-115">Ele pode incluir informações sobre regiões de memória reservada ou vazio.</span><span class="sxs-lookup"><span data-stu-id="74a9a-115">It may include information about empty or reserved memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74a9a-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="74a9a-116">Requirements</span></span>  
 <span data-ttu-id="74a9a-117">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74a9a-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74a9a-118">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="74a9a-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="74a9a-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="74a9a-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="74a9a-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74a9a-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74a9a-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="74a9a-121">See also</span></span>

- [<span data-ttu-id="74a9a-122">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="74a9a-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
