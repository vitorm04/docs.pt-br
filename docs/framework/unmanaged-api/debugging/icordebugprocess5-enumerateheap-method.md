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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 412ade32daaed4802215c628ab94b535fc542b93
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423339"
---
# <a name="icordebugprocess5enumerateheap-method"></a><span data-ttu-id="98e37-102">Método ICorDebugProcess5::EnumerateHeap</span><span class="sxs-lookup"><span data-stu-id="98e37-102">ICorDebugProcess5::EnumerateHeap Method</span></span>
<span data-ttu-id="98e37-103">Obtém um enumerador para os objetos no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="98e37-103">Gets an enumerator for the objects on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98e37-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="98e37-104">Syntax</span></span>  
  
```  
HRESULT EnumerateHeap(  
    [out] ICorDebugHeapEnum **ppObjects  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="98e37-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="98e37-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="98e37-106">[out] Um ponteiro para o endereço de um [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) objeto de interface que é um enumerador para os objetos que residem no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="98e37-106">[out] A pointer to the address of an [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) interface object that is an enumerator for the objects that reside on the managed heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="98e37-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="98e37-107">Remarks</span></span>  
 <span data-ttu-id="98e37-108">Antes de chamar o `ICorDebugProcess5::EnumerateHeap` método, você deve chamar o [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) método e examinar o valor da `areGCStructuresValid` campo retornado [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) objeto para garantir que o heap de coleta de lixo em seu estado atual é enumerável.</span><span class="sxs-lookup"><span data-stu-id="98e37-108">Before calling the `ICorDebugProcess5::EnumerateHeap` method, you should call the [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) method and examine the value of the `areGCStructuresValid` field of the returned [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) object to ensure that the garbage collection heap in its current state is enumerable.</span></span> <span data-ttu-id="98e37-109">Além disso, o `ICorDebugProcess5::EnumerateHeap` retorna `E_FAIL` se você anexar muito cedo no tempo de vida do processo, antes de memória de heap gerenciado é alocado.</span><span class="sxs-lookup"><span data-stu-id="98e37-109">In addition, the `ICorDebugProcess5::EnumerateHeap` returns `E_FAIL` if you attach too early in the lifetime of the process, before memory for the managed heap is allocated.</span></span>  
  
 <span data-ttu-id="98e37-110">O [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) objeto de interface é um enumerador padrão derivado da interface ICorDebugEnum que permite que você enumere [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objetos.</span><span class="sxs-lookup"><span data-stu-id="98e37-110">The [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) interface object is a standard enumerator derived from the ICorDebugEnum interface that allows you to enumerate [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects.</span></span> <span data-ttu-id="98e37-111">Este método preenche o [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) objeto da coleção com [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instâncias que fornecem informações sobre todos os objetos.</span><span class="sxs-lookup"><span data-stu-id="98e37-111">This method populates the [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) collection object with [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that provide information about all objects.</span></span> <span data-ttu-id="98e37-112">A coleção também pode incluir [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instâncias que fornecem informações sobre objetos que não estão vinculados por qualquer objeto, mas ainda não foram coletadas pelo coletor de lixo.</span><span class="sxs-lookup"><span data-stu-id="98e37-112">The collection may also include [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that provide information about objects that are not rooted by any object but have not yet been collected by the garbage collector.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98e37-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="98e37-113">Requirements</span></span>  
 <span data-ttu-id="98e37-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98e37-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98e37-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="98e37-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="98e37-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="98e37-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="98e37-117">**Versões do .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98e37-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98e37-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="98e37-118">See Also</span></span>  
 [<span data-ttu-id="98e37-119">Interface ICorDebugProcess5</span><span class="sxs-lookup"><span data-stu-id="98e37-119">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [<span data-ttu-id="98e37-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="98e37-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
