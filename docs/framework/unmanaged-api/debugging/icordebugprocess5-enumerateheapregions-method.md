---
title: Método ICorDebugProcess5::EnumerateHeapRegions
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.EnumerateHeapRegions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateHeapRegions
helpviewer_keywords:
- EnumerateHeapRegions method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHeapRegions method [.NET Framework debugging]
ms.assetid: b1edba68-9c36-4f69-be9f-678ce0b33480
topic_type:
- apiref
ms.openlocfilehash: 50b0859d6727a25906f2c8b0f3fe96da228ab886
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213550"
---
# <a name="icordebugprocess5enumerateheapregions-method"></a><span data-ttu-id="dd9ca-102">Método ICorDebugProcess5::EnumerateHeapRegions</span><span class="sxs-lookup"><span data-stu-id="dd9ca-102">ICorDebugProcess5::EnumerateHeapRegions Method</span></span>
<span data-ttu-id="dd9ca-103">Obtém um enumerador para os intervalos de memória do heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="dd9ca-103">Gets an enumerator for the memory ranges of the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd9ca-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dd9ca-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateHeapRegions(  
   [out] ICorDebugHeapSegmentEnum **ppRegions  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dd9ca-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dd9ca-105">Parameters</span></span>  
 `ppRegions`  
 <span data-ttu-id="dd9ca-106">fora Um ponteiro para o endereço de um objeto de interface [ICorDebugHeapSegmentEnum](icordebugheapsegmentenum-interface.md) que é um enumerador para os intervalos de memória em que os objetos residem no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="dd9ca-106">[out] A pointer to the address of an [ICorDebugHeapSegmentEnum](icordebugheapsegmentenum-interface.md) interface object that is an enumerator for the ranges of memory in which objects reside in the managed heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dd9ca-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="dd9ca-107">Remarks</span></span>  
 <span data-ttu-id="dd9ca-108">Antes de chamar o `ICorDebugProcess5::EnumerateHeapRegions` método, você deve chamar o método [ICorDebugProcess5:: GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) e examinar o valor do `areGCStructuresValid` campo do objeto de [COR_HEAPINFO](cor-heapinfo-structure.md) retornado para garantir que o heap de coleta de lixo em seu estado atual seja enumerável.</span><span class="sxs-lookup"><span data-stu-id="dd9ca-108">Before calling the `ICorDebugProcess5::EnumerateHeapRegions` method, you should call the [ICorDebugProcess5::GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) method and examine the value of the `areGCStructuresValid` field of the returned [COR_HEAPINFO](cor-heapinfo-structure.md) object to ensure that the garbage collection heap in its current state is enumerable.</span></span> <span data-ttu-id="dd9ca-109">Além disso, o `ICorDebugProcess5::EnumerateHeapRegions` método retorna `E_FAIL` se você anexar muito cedo no tempo de vida do processo, antes que as regiões de memória sejam criadas.</span><span class="sxs-lookup"><span data-stu-id="dd9ca-109">In addition, the `ICorDebugProcess5::EnumerateHeapRegions` method returns `E_FAIL` if you attach too early in the lifetime of the process, before memory regions are created.</span></span>  
  
 <span data-ttu-id="dd9ca-110">Esse método é garantido para enumerar todas as regiões de memória que podem conter objetos gerenciados, mas não garante que os objetos gerenciados realmente residam nessas regiões.</span><span class="sxs-lookup"><span data-stu-id="dd9ca-110">This method is guaranteed to enumerate all memory regions that may contain managed objects, but it does not guarantee that managed objects actually reside in those regions.</span></span> <span data-ttu-id="dd9ca-111">O objeto da coleção [ICorDebugHeapSegmentEnum](icordebugheapsegmentenum-interface.md) pode incluir regiões de memória vazias ou reservadas.</span><span class="sxs-lookup"><span data-stu-id="dd9ca-111">The [ICorDebugHeapSegmentEnum](icordebugheapsegmentenum-interface.md) collection object may include empty or reserved memory regions.</span></span>  
  
 <span data-ttu-id="dd9ca-112">O objeto de interface [ICorDebugHeapSegmentEnum](icordebugheapsegmentenum-interface.md) é um enumerador padrão derivado da interface ICorDebugEnum que permite que você enumere [COR_SEGMENT](cor-segment-structure.md) objetos.</span><span class="sxs-lookup"><span data-stu-id="dd9ca-112">The [ICorDebugHeapSegmentEnum](icordebugheapsegmentenum-interface.md) interface object is a standard enumerator derived from the ICorDebugEnum interface that allows you to enumerate [COR_SEGMENT](cor-segment-structure.md) objects.</span></span> <span data-ttu-id="dd9ca-113">Cada objeto de [COR_SEGMENT](cor-segment-structure.md) fornece informações sobre o intervalo de memória de um segmento específico, juntamente com a geração dos objetos nesse segmento.</span><span class="sxs-lookup"><span data-stu-id="dd9ca-113">Each [COR_SEGMENT](cor-segment-structure.md) object provides information about the memory range of a particular segment, along with the generation of the objects in that segment.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd9ca-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="dd9ca-114">Requirements</span></span>  
 <span data-ttu-id="dd9ca-115">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd9ca-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd9ca-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dd9ca-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dd9ca-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dd9ca-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dd9ca-118">**.NET Framework versões:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd9ca-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd9ca-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="dd9ca-119">See also</span></span>

- [<span data-ttu-id="dd9ca-120">Interface ICorDebugProcess5</span><span class="sxs-lookup"><span data-stu-id="dd9ca-120">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="dd9ca-121">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="dd9ca-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
