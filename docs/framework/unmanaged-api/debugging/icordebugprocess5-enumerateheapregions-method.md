---
title: "Método ICorDebugProcess5::EnumerateHeapRegions"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 478a8490e57946a08670d9f86e1f6ebcc67703a6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess5enumerateheapregions-method"></a><span data-ttu-id="07006-102">Método ICorDebugProcess5::EnumerateHeapRegions</span><span class="sxs-lookup"><span data-stu-id="07006-102">ICorDebugProcess5::EnumerateHeapRegions Method</span></span>
<span data-ttu-id="07006-103">Obtém um enumerador para os intervalos de memória de heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="07006-103">Gets an enumerator for the memory ranges of the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07006-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="07006-104">Syntax</span></span>  
  
```  
HRESULT EnumerateHeapRegions(  
   [out] ICorDebugHeapSegmentEnum **ppRegions  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="07006-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="07006-105">Parameters</span></span>  
 `ppRegions`  
 <span data-ttu-id="07006-106">[out] Um ponteiro para o endereço de um [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) objeto de interface que é um enumerador para os intervalos de memória na qual os objetos residem no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="07006-106">[out] A pointer to the address of an [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) interface object that is an enumerator for the ranges of memory in which objects reside in the managed heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="07006-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="07006-107">Remarks</span></span>  
 <span data-ttu-id="07006-108">Antes de chamar o `ICorDebugProcess5::EnumerateHeapRegions` método, você deve chamar o [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) método e examinar o valor da `areGCStructuresValid` campo retornado [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) objeto para garantir que o heap de coleta de lixo em seu estado atual é enumerável.</span><span class="sxs-lookup"><span data-stu-id="07006-108">Before calling the `ICorDebugProcess5::EnumerateHeapRegions` method, you should call the [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) method and examine the value of the `areGCStructuresValid` field of the returned [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) object to ensure that the garbage collection heap in its current state is enumerable.</span></span> <span data-ttu-id="07006-109">Além disso, o `ICorDebugProcess5::EnumerateHeapRegions` método retorna `E_FAIL` se anexar muito cedo no tempo de vida do processo, antes de memória regiões são criadas.</span><span class="sxs-lookup"><span data-stu-id="07006-109">In addition, the `ICorDebugProcess5::EnumerateHeapRegions` method returns `E_FAIL` if you attach too early in the lifetime of the process, before memory regions are created.</span></span>  
  
 <span data-ttu-id="07006-110">Esse método é garantido para enumerar todas as regiões de memória que podem conter objetos gerenciados, mas não garante que os objetos gerenciados, na verdade, residam nessas regiões.</span><span class="sxs-lookup"><span data-stu-id="07006-110">This method is guaranteed to enumerate all memory regions that may contain managed objects, but it does not guarantee that managed objects actually reside in those regions.</span></span> <span data-ttu-id="07006-111">O [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) objeto da coleção pode incluir regiões de memória reservada ou vazio.</span><span class="sxs-lookup"><span data-stu-id="07006-111">The [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) collection object may include empty or reserved memory regions.</span></span>  
  
 <span data-ttu-id="07006-112">O [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) objeto de interface é um enumerador padrão derivado da interface ICorDebugEnum que permite que você enumere [COR_SEGMENT](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) objetos.</span><span class="sxs-lookup"><span data-stu-id="07006-112">The [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) interface object is a standard enumerator derived from the ICorDebugEnum interface that allows you to enumerate [COR_SEGMENT](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) objects.</span></span> <span data-ttu-id="07006-113">Cada [COR_SEGMENT](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) objeto fornece informações sobre o intervalo de memória de um segmento específico, juntamente com a geração dos objetos nesse segmento.</span><span class="sxs-lookup"><span data-stu-id="07006-113">Each [COR_SEGMENT](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) object provides information about the memory range of a particular segment, along with the generation of the objects in that segment.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07006-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="07006-114">Requirements</span></span>  
 <span data-ttu-id="07006-115">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07006-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07006-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="07006-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="07006-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="07006-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="07006-118">**Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07006-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07006-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="07006-119">See Also</span></span>  
 [<span data-ttu-id="07006-120">Interface ICorDebugProcess5</span><span class="sxs-lookup"><span data-stu-id="07006-120">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [<span data-ttu-id="07006-121">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="07006-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
