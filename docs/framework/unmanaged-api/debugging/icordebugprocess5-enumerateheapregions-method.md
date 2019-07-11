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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cf9340977c55c54b9a4683115000293d1c98dfcf
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767462"
---
# <a name="icordebugprocess5enumerateheapregions-method"></a><span data-ttu-id="54c72-102">Método ICorDebugProcess5::EnumerateHeapRegions</span><span class="sxs-lookup"><span data-stu-id="54c72-102">ICorDebugProcess5::EnumerateHeapRegions Method</span></span>
<span data-ttu-id="54c72-103">Obtém um enumerador para os intervalos de memória do heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="54c72-103">Gets an enumerator for the memory ranges of the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54c72-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="54c72-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateHeapRegions(  
   [out] ICorDebugHeapSegmentEnum **ppRegions  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="54c72-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="54c72-105">Parameters</span></span>  
 `ppRegions`  
 <span data-ttu-id="54c72-106">[out] Um ponteiro para o endereço de um [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) objeto de interface que é um enumerador para os intervalos de memória no qual os objetos residem no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="54c72-106">[out] A pointer to the address of an [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) interface object that is an enumerator for the ranges of memory in which objects reside in the managed heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="54c72-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="54c72-107">Remarks</span></span>  
 <span data-ttu-id="54c72-108">Antes de chamar o `ICorDebugProcess5::EnumerateHeapRegions` método, você deve chamar o [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) método e examinar o valor da `areGCStructuresValid` campo retornado [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) objeto para garantir que o heap de coleta de lixo em seu estado atual é enumerável.</span><span class="sxs-lookup"><span data-stu-id="54c72-108">Before calling the `ICorDebugProcess5::EnumerateHeapRegions` method, you should call the [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) method and examine the value of the `areGCStructuresValid` field of the returned [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) object to ensure that the garbage collection heap in its current state is enumerable.</span></span> <span data-ttu-id="54c72-109">Além disso, o `ICorDebugProcess5::EnumerateHeapRegions` método retorna `E_FAIL` se você anexar muito cedo no tempo de vida do processo, antes de memória regiões são criadas.</span><span class="sxs-lookup"><span data-stu-id="54c72-109">In addition, the `ICorDebugProcess5::EnumerateHeapRegions` method returns `E_FAIL` if you attach too early in the lifetime of the process, before memory regions are created.</span></span>  
  
 <span data-ttu-id="54c72-110">Esse método é garantido para enumerar todas as regiões de memória que podem conter objetos gerenciados, mas ele não garante que os objetos gerenciados, na verdade, residam nessas regiões.</span><span class="sxs-lookup"><span data-stu-id="54c72-110">This method is guaranteed to enumerate all memory regions that may contain managed objects, but it does not guarantee that managed objects actually reside in those regions.</span></span> <span data-ttu-id="54c72-111">O [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) objeto da coleção pode incluir regiões de memória reservada ou vazio.</span><span class="sxs-lookup"><span data-stu-id="54c72-111">The [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) collection object may include empty or reserved memory regions.</span></span>  
  
 <span data-ttu-id="54c72-112">O [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) objeto de interface é um enumerador padrão derivado da interface ICorDebugEnum que permite que você enumere [COR_SEGMENT](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) objetos.</span><span class="sxs-lookup"><span data-stu-id="54c72-112">The [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) interface object is a standard enumerator derived from the ICorDebugEnum interface that allows you to enumerate [COR_SEGMENT](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) objects.</span></span> <span data-ttu-id="54c72-113">Cada [COR_SEGMENT](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) objeto fornece informações sobre o intervalo de memória de um segmento específico, juntamente com a geração dos objetos no segmento.</span><span class="sxs-lookup"><span data-stu-id="54c72-113">Each [COR_SEGMENT](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) object provides information about the memory range of a particular segment, along with the generation of the objects in that segment.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54c72-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="54c72-114">Requirements</span></span>  
 <span data-ttu-id="54c72-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54c72-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54c72-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="54c72-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="54c72-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="54c72-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="54c72-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54c72-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54c72-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="54c72-119">See also</span></span>

- [<span data-ttu-id="54c72-120">Interface ICorDebugProcess5</span><span class="sxs-lookup"><span data-stu-id="54c72-120">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="54c72-121">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="54c72-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
