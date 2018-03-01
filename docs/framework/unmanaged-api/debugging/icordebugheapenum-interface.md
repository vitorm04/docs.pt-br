---
title: Interface ICorDebugHeapEnum
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugHeapEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapEnum
helpviewer_keywords:
- ICorDebugHeapEnum interface [.NET Framework debugging]
ms.assetid: 99cbc1eb-d539-4f76-a0d8-b93348112f14
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e317cb24e0eeaeaa38833433791eb546ee3c0478
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugheapenum-interface"></a><span data-ttu-id="6466e-102">Interface ICorDebugHeapEnum</span><span class="sxs-lookup"><span data-stu-id="6466e-102">ICorDebugHeapEnum Interface</span></span>
<span data-ttu-id="6466e-103">Fornece um enumerador para objetos no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="6466e-103">Provides an enumerator for objects on the managed heap.</span></span> <span data-ttu-id="6466e-104">Esta interface é uma subclasse da interface ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="6466e-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6466e-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="6466e-105">Methods</span></span>  
  
|<span data-ttu-id="6466e-106">Método</span><span class="sxs-lookup"><span data-stu-id="6466e-106">Method</span></span>|<span data-ttu-id="6466e-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="6466e-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6466e-108">Método Next</span><span class="sxs-lookup"><span data-stu-id="6466e-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md)|<span data-ttu-id="6466e-109">Obtém o número especificado de [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instâncias que contêm informações sobre objetos no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="6466e-109">Gets the specified number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that contain information about objects on the managed heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6466e-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="6466e-110">Remarks</span></span>  
 <span data-ttu-id="6466e-111">O `ICorDebugHeapEnum` interface implementa a interface ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="6466e-111">The `ICorDebugHeapEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="6466e-112">Um `ICorDebugHeapEnum` instância é populada com [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instâncias chamando o [ICorDebugProcess5::EnumerateHeap](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="6466e-112">An `ICorDebugHeapEnum` instance is populated with [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances by calling the [ICorDebugProcess5::EnumerateHeap](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md) method.</span></span> <span data-ttu-id="6466e-113">Cada [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instância na coleção representa a um objeto vivo no heap ou um objeto que não tem raiz de qualquer objeto, mas que ainda não foram coletado pelo coletor de lixo.</span><span class="sxs-lookup"><span data-stu-id="6466e-113">Each [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instance in the collection represents either a live object on the heap or an object that is not rooted by any object but has not yet been collected by the garbage collector.</span></span> <span data-ttu-id="6466e-114">O [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objetos na coleção podem ser enumerados chamando o [Icordebugheapenum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="6466e-114">The [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects in the collection can be enumerated by calling the [ICorDebugHeapEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6466e-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6466e-115">Requirements</span></span>  
 <span data-ttu-id="6466e-116">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6466e-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6466e-117">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6466e-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6466e-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6466e-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6466e-119">**Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6466e-119">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6466e-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6466e-120">See Also</span></span>  
 [<span data-ttu-id="6466e-121">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="6466e-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
