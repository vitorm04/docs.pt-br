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
ms.openlocfilehash: 9386c77cc98df17d797d5886e1603ffc4824b6dc
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205230"
---
# <a name="icordebugprocess5enumerateheap-method"></a><span data-ttu-id="474ea-102">Método ICorDebugProcess5::EnumerateHeap</span><span class="sxs-lookup"><span data-stu-id="474ea-102">ICorDebugProcess5::EnumerateHeap Method</span></span>
<span data-ttu-id="474ea-103">Obtém um enumerador para os objetos no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="474ea-103">Gets an enumerator for the objects on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="474ea-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="474ea-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateHeap(  
    [out] ICorDebugHeapEnum **ppObjects  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="474ea-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="474ea-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="474ea-106">fora Um ponteiro para o endereço de um objeto de interface [ICorDebugHeapEnum](icordebugheapenum-interface.md) que é um enumerador para os objetos que residem no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="474ea-106">[out] A pointer to the address of an [ICorDebugHeapEnum](icordebugheapenum-interface.md) interface object that is an enumerator for the objects that reside on the managed heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="474ea-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="474ea-107">Remarks</span></span>  
 <span data-ttu-id="474ea-108">Antes de chamar o `ICorDebugProcess5::EnumerateHeap` método, você deve chamar o método [ICorDebugProcess5:: GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) e examinar o valor do `areGCStructuresValid` campo do objeto de [COR_HEAPINFO](cor-heapinfo-structure.md) retornado para garantir que o heap de coleta de lixo em seu estado atual seja enumerável.</span><span class="sxs-lookup"><span data-stu-id="474ea-108">Before calling the `ICorDebugProcess5::EnumerateHeap` method, you should call the [ICorDebugProcess5::GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) method and examine the value of the `areGCStructuresValid` field of the returned [COR_HEAPINFO](cor-heapinfo-structure.md) object to ensure that the garbage collection heap in its current state is enumerable.</span></span> <span data-ttu-id="474ea-109">Além disso, o `ICorDebugProcess5::EnumerateHeap` retorna `E_FAIL` se você anexar muito cedo no tempo de vida do processo, antes que a memória para o heap gerenciado seja alocada.</span><span class="sxs-lookup"><span data-stu-id="474ea-109">In addition, the `ICorDebugProcess5::EnumerateHeap` returns `E_FAIL` if you attach too early in the lifetime of the process, before memory for the managed heap is allocated.</span></span>  
  
 <span data-ttu-id="474ea-110">O objeto de interface [ICorDebugHeapEnum](icordebugheapenum-interface.md) é um enumerador padrão derivado da interface ICorDebugEnum que permite que você enumere [COR_HEAPOBJECT](cor-heapobject-structure.md) objetos.</span><span class="sxs-lookup"><span data-stu-id="474ea-110">The [ICorDebugHeapEnum](icordebugheapenum-interface.md) interface object is a standard enumerator derived from the ICorDebugEnum interface that allows you to enumerate [COR_HEAPOBJECT](cor-heapobject-structure.md) objects.</span></span> <span data-ttu-id="474ea-111">Esse método popula o objeto da coleção [ICorDebugHeapEnum](icordebugheapenum-interface.md) com [COR_HEAPOBJECT](cor-heapobject-structure.md) instâncias que fornecem informações sobre todos os objetos.</span><span class="sxs-lookup"><span data-stu-id="474ea-111">This method populates the [ICorDebugHeapEnum](icordebugheapenum-interface.md) collection object with [COR_HEAPOBJECT](cor-heapobject-structure.md) instances that provide information about all objects.</span></span> <span data-ttu-id="474ea-112">A coleção também pode incluir [COR_HEAPOBJECT](cor-heapobject-structure.md) instâncias que fornecem informações sobre objetos que não são enraizada por nenhum objeto, mas que ainda não foram coletados pelo coletor de lixo.</span><span class="sxs-lookup"><span data-stu-id="474ea-112">The collection may also include [COR_HEAPOBJECT](cor-heapobject-structure.md) instances that provide information about objects that are not rooted by any object but have not yet been collected by the garbage collector.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="474ea-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="474ea-113">Requirements</span></span>  
 <span data-ttu-id="474ea-114">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="474ea-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="474ea-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="474ea-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="474ea-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="474ea-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="474ea-117">**.NET Framework versões:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="474ea-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="474ea-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="474ea-118">See also</span></span>

- [<span data-ttu-id="474ea-119">Interface ICorDebugProcess5</span><span class="sxs-lookup"><span data-stu-id="474ea-119">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="474ea-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="474ea-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
