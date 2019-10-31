---
title: Método ICorDebugProcess5::EnumerateHeap
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.EnumerateHeap
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateHeap
helpviewer_keywords:
- EnumerateHeap method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHeap method [.NET Framework debugging]
ms.assetid: b0192104-6073-4089-a4df-dc29ee033074
topic_type:
- apiref
ms.openlocfilehash: c8cfc9cdf6580a002f6ac15080012a9e8c63be20
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129658"
---
# <a name="icordebugprocess5enumerateheap-method"></a><span data-ttu-id="aff7e-102">Método ICorDebugProcess5::EnumerateHeap</span><span class="sxs-lookup"><span data-stu-id="aff7e-102">ICorDebugProcess5::EnumerateHeap Method</span></span>
<span data-ttu-id="aff7e-103">Obtém um enumerador para os objetos no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="aff7e-103">Gets an enumerator for the objects on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aff7e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="aff7e-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateHeap(  
    [out] ICorDebugHeapEnum **ppObjects  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aff7e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="aff7e-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="aff7e-106">fora Um ponteiro para o endereço de um objeto de interface [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) que é um enumerador para os objetos que residem no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="aff7e-106">[out] A pointer to the address of an [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) interface object that is an enumerator for the objects that reside on the managed heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aff7e-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="aff7e-107">Remarks</span></span>  
 <span data-ttu-id="aff7e-108">Antes de chamar o método `ICorDebugProcess5::EnumerateHeap`, você deve chamar o método [ICorDebugProcess5:: GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) e examinar o valor do campo `areGCStructuresValid` do objeto [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) retornado para garantir que o heap de coleta de lixo em seu o estado atual é enumerable.</span><span class="sxs-lookup"><span data-stu-id="aff7e-108">Before calling the `ICorDebugProcess5::EnumerateHeap` method, you should call the [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) method and examine the value of the `areGCStructuresValid` field of the returned [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) object to ensure that the garbage collection heap in its current state is enumerable.</span></span> <span data-ttu-id="aff7e-109">Além disso, o `ICorDebugProcess5::EnumerateHeap` retornará `E_FAIL` se você anexar muito cedo no tempo de vida do processo, antes da memória para o heap gerenciado ser alocado.</span><span class="sxs-lookup"><span data-stu-id="aff7e-109">In addition, the `ICorDebugProcess5::EnumerateHeap` returns `E_FAIL` if you attach too early in the lifetime of the process, before memory for the managed heap is allocated.</span></span>  
  
 <span data-ttu-id="aff7e-110">O objeto de interface [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) é um enumerador padrão derivado da interface ICorDebugEnum que permite enumerar objetos [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="aff7e-110">The [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) interface object is a standard enumerator derived from the ICorDebugEnum interface that allows you to enumerate [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects.</span></span> <span data-ttu-id="aff7e-111">Esse método popula o objeto de coleção [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) com instâncias [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) que fornecem informações sobre todos os objetos.</span><span class="sxs-lookup"><span data-stu-id="aff7e-111">This method populates the [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) collection object with [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that provide information about all objects.</span></span> <span data-ttu-id="aff7e-112">A coleção também pode incluir instâncias [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) que fornecem informações sobre objetos que não são enraizada por nenhum objeto, mas que ainda não foram coletados pelo coletor de lixo.</span><span class="sxs-lookup"><span data-stu-id="aff7e-112">The collection may also include [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that provide information about objects that are not rooted by any object but have not yet been collected by the garbage collector.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aff7e-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="aff7e-113">Requirements</span></span>  
 <span data-ttu-id="aff7e-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aff7e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aff7e-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aff7e-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aff7e-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aff7e-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aff7e-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aff7e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aff7e-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aff7e-118">See also</span></span>

- [<span data-ttu-id="aff7e-119">Interface ICorDebugProcess5</span><span class="sxs-lookup"><span data-stu-id="aff7e-119">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="aff7e-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="aff7e-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
