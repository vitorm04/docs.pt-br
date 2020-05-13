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
ms.openlocfilehash: ff290cd8ad331ff109c3bbbf87638d22b9b183bc
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83208532"
---
# <a name="icordebugheapenum-interface"></a><span data-ttu-id="b4cdb-102">Interface ICorDebugHeapEnum</span><span class="sxs-lookup"><span data-stu-id="b4cdb-102">ICorDebugHeapEnum Interface</span></span>
<span data-ttu-id="b4cdb-103">Fornece um enumerador para objetos no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="b4cdb-103">Provides an enumerator for objects on the managed heap.</span></span> <span data-ttu-id="b4cdb-104">Essa interface é uma subclasse da interface ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="b4cdb-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b4cdb-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="b4cdb-105">Methods</span></span>  
  
|<span data-ttu-id="b4cdb-106">Método</span><span class="sxs-lookup"><span data-stu-id="b4cdb-106">Method</span></span>|<span data-ttu-id="b4cdb-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="b4cdb-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b4cdb-108">Método Next</span><span class="sxs-lookup"><span data-stu-id="b4cdb-108">Next Method</span></span>](icordebugheapenum-next-method.md)|<span data-ttu-id="b4cdb-109">Obtém o número especificado de instâncias de [COR_HEAPOBJECT](cor-heapobject-structure.md) que contêm informações sobre objetos no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="b4cdb-109">Gets the specified number of [COR_HEAPOBJECT](cor-heapobject-structure.md) instances that contain information about objects on the managed heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b4cdb-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="b4cdb-110">Remarks</span></span>  
 <span data-ttu-id="b4cdb-111">A `ICorDebugHeapEnum` interface implementa a interface ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="b4cdb-111">The `ICorDebugHeapEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="b4cdb-112">Uma `ICorDebugHeapEnum` instância é populada com instâncias de [COR_HEAPOBJECT](cor-heapobject-structure.md) chamando o método [ICorDebugProcess5:: EnumerateHeap](icordebugprocess5-enumerateheap-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b4cdb-112">An `ICorDebugHeapEnum` instance is populated with [COR_HEAPOBJECT](cor-heapobject-structure.md) instances by calling the [ICorDebugProcess5::EnumerateHeap](icordebugprocess5-enumerateheap-method.md) method.</span></span> <span data-ttu-id="b4cdb-113">Cada instância de [COR_HEAPOBJECT](cor-heapobject-structure.md) na coleção representa um objeto dinâmico no heap ou um objeto que não tem raiz por nenhum objeto, mas ainda não foi coletado pelo coletor de lixo.</span><span class="sxs-lookup"><span data-stu-id="b4cdb-113">Each [COR_HEAPOBJECT](cor-heapobject-structure.md) instance in the collection represents either a live object on the heap or an object that is not rooted by any object but has not yet been collected by the garbage collector.</span></span> <span data-ttu-id="b4cdb-114">Os objetos [COR_HEAPOBJECT](cor-heapobject-structure.md) na coleção podem ser enumerados chamando o método [ICorDebugHeapEnum:: Next](icordebugheapenum-next-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b4cdb-114">The [COR_HEAPOBJECT](cor-heapobject-structure.md) objects in the collection can be enumerated by calling the [ICorDebugHeapEnum::Next](icordebugheapenum-next-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4cdb-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b4cdb-115">Requirements</span></span>  
 <span data-ttu-id="b4cdb-116">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4cdb-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4cdb-117">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b4cdb-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b4cdb-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b4cdb-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b4cdb-119">**.NET Framework versões:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4cdb-119">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4cdb-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="b4cdb-120">See also</span></span>

- [<span data-ttu-id="b4cdb-121">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="b4cdb-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
