---
title: Interface ICorDebugHeapEnum
ms.date: 03/30/2017
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
ms.openlocfilehash: e8d1948a7d0ff23410ba8670628424a4067fb47d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138496"
---
# <a name="icordebugheapenum-interface"></a><span data-ttu-id="90901-102">Interface ICorDebugHeapEnum</span><span class="sxs-lookup"><span data-stu-id="90901-102">ICorDebugHeapEnum Interface</span></span>
<span data-ttu-id="90901-103">Fornece um enumerador para objetos no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="90901-103">Provides an enumerator for objects on the managed heap.</span></span> <span data-ttu-id="90901-104">Essa interface é uma subclasse da interface ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="90901-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="90901-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="90901-105">Methods</span></span>  
  
|<span data-ttu-id="90901-106">Método</span><span class="sxs-lookup"><span data-stu-id="90901-106">Method</span></span>|<span data-ttu-id="90901-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="90901-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="90901-108">Método Next</span><span class="sxs-lookup"><span data-stu-id="90901-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md)|<span data-ttu-id="90901-109">Obtém o número especificado de instâncias [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) que contêm informações sobre objetos no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="90901-109">Gets the specified number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that contain information about objects on the managed heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="90901-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="90901-110">Remarks</span></span>  
 <span data-ttu-id="90901-111">A interface `ICorDebugHeapEnum` implementa a interface ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="90901-111">The `ICorDebugHeapEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="90901-112">Uma instância de `ICorDebugHeapEnum` é populada com instâncias [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) chamando o método [ICorDebugProcess5:: EnumerateHeap](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md) .</span><span class="sxs-lookup"><span data-stu-id="90901-112">An `ICorDebugHeapEnum` instance is populated with [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances by calling the [ICorDebugProcess5::EnumerateHeap](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md) method.</span></span> <span data-ttu-id="90901-113">Cada instância de [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) na coleção representa um objeto dinâmico no heap ou um objeto que não tem raiz por nenhum objeto, mas ainda não foi coletado pelo coletor de lixo.</span><span class="sxs-lookup"><span data-stu-id="90901-113">Each [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instance in the collection represents either a live object on the heap or an object that is not rooted by any object but has not yet been collected by the garbage collector.</span></span> <span data-ttu-id="90901-114">Os objetos [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) na coleção podem ser enumerados chamando o método [ICorDebugHeapEnum:: Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md) .</span><span class="sxs-lookup"><span data-stu-id="90901-114">The [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects in the collection can be enumerated by calling the [ICorDebugHeapEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90901-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="90901-115">Requirements</span></span>  
 <span data-ttu-id="90901-116">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90901-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90901-117">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="90901-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="90901-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="90901-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="90901-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90901-119">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90901-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="90901-120">See also</span></span>

- [<span data-ttu-id="90901-121">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="90901-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
