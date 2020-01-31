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
ms.openlocfilehash: bed2871c46712490bc4b0520fa1ab8023dbab5cf
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794432"
---
# <a name="icordebugheapenum-interface"></a><span data-ttu-id="88273-102">Interface ICorDebugHeapEnum</span><span class="sxs-lookup"><span data-stu-id="88273-102">ICorDebugHeapEnum Interface</span></span>
<span data-ttu-id="88273-103">Fornece um enumerador para objetos no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="88273-103">Provides an enumerator for objects on the managed heap.</span></span> <span data-ttu-id="88273-104">Essa interface é uma subclasse da interface ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="88273-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="88273-105">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="88273-105">Methods</span></span>  
  
|<span data-ttu-id="88273-106">Método</span><span class="sxs-lookup"><span data-stu-id="88273-106">Method</span></span>|<span data-ttu-id="88273-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="88273-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="88273-108">Método Next</span><span class="sxs-lookup"><span data-stu-id="88273-108">Next Method</span></span>](icordebugheapenum-next-method.md)|<span data-ttu-id="88273-109">Obtém o número especificado de instâncias de [COR_HEAPOBJECT](cor-heapobject-structure.md) que contêm informações sobre objetos no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="88273-109">Gets the specified number of [COR_HEAPOBJECT](cor-heapobject-structure.md) instances that contain information about objects on the managed heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="88273-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="88273-110">Remarks</span></span>  
 <span data-ttu-id="88273-111">A interface `ICorDebugHeapEnum` implementa a interface ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="88273-111">The `ICorDebugHeapEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="88273-112">Uma instância de `ICorDebugHeapEnum` é populada com instâncias de [COR_HEAPOBJECT](cor-heapobject-structure.md) chamando o método [ICorDebugProcess5:: EnumerateHeap](icordebugprocess5-enumerateheap-method.md) .</span><span class="sxs-lookup"><span data-stu-id="88273-112">An `ICorDebugHeapEnum` instance is populated with [COR_HEAPOBJECT](cor-heapobject-structure.md) instances by calling the [ICorDebugProcess5::EnumerateHeap](icordebugprocess5-enumerateheap-method.md) method.</span></span> <span data-ttu-id="88273-113">Cada instância de [COR_HEAPOBJECT](cor-heapobject-structure.md) na coleção representa um objeto dinâmico no heap ou um objeto que não tem raiz por nenhum objeto, mas ainda não foi coletado pelo coletor de lixo.</span><span class="sxs-lookup"><span data-stu-id="88273-113">Each [COR_HEAPOBJECT](cor-heapobject-structure.md) instance in the collection represents either a live object on the heap or an object that is not rooted by any object but has not yet been collected by the garbage collector.</span></span> <span data-ttu-id="88273-114">Os objetos [COR_HEAPOBJECT](cor-heapobject-structure.md) na coleção podem ser enumerados chamando o método [ICorDebugHeapEnum:: Next](icordebugheapenum-next-method.md) .</span><span class="sxs-lookup"><span data-stu-id="88273-114">The [COR_HEAPOBJECT](cor-heapobject-structure.md) objects in the collection can be enumerated by calling the [ICorDebugHeapEnum::Next](icordebugheapenum-next-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88273-115">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="88273-115">Requirements</span></span>  
 <span data-ttu-id="88273-116">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88273-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88273-117">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="88273-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="88273-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="88273-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="88273-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88273-119">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88273-120">Veja também</span><span class="sxs-lookup"><span data-stu-id="88273-120">See also</span></span>

- [<span data-ttu-id="88273-121">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="88273-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
