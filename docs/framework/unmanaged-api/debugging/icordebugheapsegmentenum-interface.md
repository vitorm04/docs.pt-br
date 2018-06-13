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
ms.openlocfilehash: cac4ddc33bcaf07d615fd186a63d96b1f4f6464c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417726"
---
# <a name="icordebugheapsegmentenum-interface"></a><span data-ttu-id="d874a-102">Interface ICorDebugHeapSegmentEnum</span><span class="sxs-lookup"><span data-stu-id="d874a-102">ICorDebugHeapSegmentEnum Interface</span></span>
<span data-ttu-id="d874a-103">Fornece um enumerador para regiões de memória do heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="d874a-103">Provides an enumerator for the memory regions of the managed heap.</span></span> <span data-ttu-id="d874a-104">Esta interface é uma subclasse da interface ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="d874a-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d874a-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="d874a-105">Methods</span></span>  
  
|<span data-ttu-id="d874a-106">Método</span><span class="sxs-lookup"><span data-stu-id="d874a-106">Method</span></span>|<span data-ttu-id="d874a-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="d874a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d874a-108">Método Next</span><span class="sxs-lookup"><span data-stu-id="d874a-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-next-method.md)|<span data-ttu-id="d874a-109">Obtém o número especificado de [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instâncias que contêm informações sobre as regiões do heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="d874a-109">Gets the specified number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that contain information about regions of the managed heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d874a-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="d874a-110">Remarks</span></span>  
 <span data-ttu-id="d874a-111">O `ICorDebugHeapSegmentEnum` interface implementa a interface ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="d874a-111">The `ICorDebugHeapSegmentEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="d874a-112">Um `ICorDebugHeapSegmentEnum` instância é populada com [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instâncias chamando o [ICorDebugProcess5::EnumerateHeapRegions](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="d874a-112">An `ICorDebugHeapSegmentEnum` instance is populated with [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances by calling the [ICorDebugProcess5::EnumerateHeapRegions](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md) method.</span></span> <span data-ttu-id="d874a-113">O [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objetos na coleção podem ser enumerados chamando o [Icordebugheapsegmentenum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-next-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="d874a-113">The [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects in the collection can be enumerated by calling the [ICorDebugHeapSegmentEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-next-method.md) method.</span></span>  
  
 <span data-ttu-id="d874a-114">Um `ICorDebugHeapSegmentEnum` objeto da coleção enumera todas as regiões de memória que podem conter objetos gerenciados, mas não garante que os objetos gerenciados, na verdade, residam nessas regiões.</span><span class="sxs-lookup"><span data-stu-id="d874a-114">An `ICorDebugHeapSegmentEnum` collection object enumerates all memory regions that may contain managed objects, but it does not guarantee that managed objects actually reside in those regions.</span></span> <span data-ttu-id="d874a-115">Ele pode incluir informações sobre regiões de memória reservada ou vazio.</span><span class="sxs-lookup"><span data-stu-id="d874a-115">It may include information about empty or reserved memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d874a-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d874a-116">Requirements</span></span>  
 <span data-ttu-id="d874a-117">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d874a-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d874a-118">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d874a-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d874a-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d874a-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d874a-120">**Versões do .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d874a-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d874a-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d874a-121">See Also</span></span>  
 [<span data-ttu-id="d874a-122">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="d874a-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
