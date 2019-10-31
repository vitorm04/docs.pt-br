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
ms.openlocfilehash: 3ab4da3fcf43731587dae6f3a8e82ea48c5ee1ec
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129636"
---
# <a name="icordebugprocess5enumerateheapregions-method"></a><span data-ttu-id="518f6-102">Método ICorDebugProcess5::EnumerateHeapRegions</span><span class="sxs-lookup"><span data-stu-id="518f6-102">ICorDebugProcess5::EnumerateHeapRegions Method</span></span>
<span data-ttu-id="518f6-103">Obtém um enumerador para os intervalos de memória do heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="518f6-103">Gets an enumerator for the memory ranges of the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="518f6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="518f6-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateHeapRegions(  
   [out] ICorDebugHeapSegmentEnum **ppRegions  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="518f6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="518f6-105">Parameters</span></span>  
 `ppRegions`  
 <span data-ttu-id="518f6-106">fora Um ponteiro para o endereço de um objeto de interface [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) que é um enumerador para os intervalos de memória em que os objetos residem no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="518f6-106">[out] A pointer to the address of an [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) interface object that is an enumerator for the ranges of memory in which objects reside in the managed heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="518f6-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="518f6-107">Remarks</span></span>  
 <span data-ttu-id="518f6-108">Antes de chamar o método `ICorDebugProcess5::EnumerateHeapRegions`, você deve chamar o método [ICorDebugProcess5:: GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) e examinar o valor do campo `areGCStructuresValid` do objeto [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) retornado para garantir que o heap de coleta de lixo em seu o estado atual é enumerable.</span><span class="sxs-lookup"><span data-stu-id="518f6-108">Before calling the `ICorDebugProcess5::EnumerateHeapRegions` method, you should call the [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) method and examine the value of the `areGCStructuresValid` field of the returned [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) object to ensure that the garbage collection heap in its current state is enumerable.</span></span> <span data-ttu-id="518f6-109">Além disso, o método `ICorDebugProcess5::EnumerateHeapRegions` retorna `E_FAIL` se você anexar muito cedo no tempo de vida do processo, antes de as regiões de memória serem criadas.</span><span class="sxs-lookup"><span data-stu-id="518f6-109">In addition, the `ICorDebugProcess5::EnumerateHeapRegions` method returns `E_FAIL` if you attach too early in the lifetime of the process, before memory regions are created.</span></span>  
  
 <span data-ttu-id="518f6-110">Esse método é garantido para enumerar todas as regiões de memória que podem conter objetos gerenciados, mas não garante que os objetos gerenciados realmente residam nessas regiões.</span><span class="sxs-lookup"><span data-stu-id="518f6-110">This method is guaranteed to enumerate all memory regions that may contain managed objects, but it does not guarantee that managed objects actually reside in those regions.</span></span> <span data-ttu-id="518f6-111">O objeto da coleção [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) pode incluir regiões de memória vazias ou reservadas.</span><span class="sxs-lookup"><span data-stu-id="518f6-111">The [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) collection object may include empty or reserved memory regions.</span></span>  
  
 <span data-ttu-id="518f6-112">O objeto de interface [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) é um enumerador padrão derivado da interface ICorDebugEnum que permite enumerar objetos [COR_SEGMENT](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="518f6-112">The [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) interface object is a standard enumerator derived from the ICorDebugEnum interface that allows you to enumerate [COR_SEGMENT](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) objects.</span></span> <span data-ttu-id="518f6-113">Cada objeto [COR_SEGMENT](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) fornece informações sobre o intervalo de memória de um segmento específico, juntamente com a geração dos objetos nesse segmento.</span><span class="sxs-lookup"><span data-stu-id="518f6-113">Each [COR_SEGMENT](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) object provides information about the memory range of a particular segment, along with the generation of the objects in that segment.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="518f6-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="518f6-114">Requirements</span></span>  
 <span data-ttu-id="518f6-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="518f6-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="518f6-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="518f6-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="518f6-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="518f6-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="518f6-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="518f6-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="518f6-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="518f6-119">See also</span></span>

- [<span data-ttu-id="518f6-120">Interface ICorDebugProcess5</span><span class="sxs-lookup"><span data-stu-id="518f6-120">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="518f6-121">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="518f6-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
