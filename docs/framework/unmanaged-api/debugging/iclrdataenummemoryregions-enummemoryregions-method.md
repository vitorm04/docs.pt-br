---
title: Método ICLRDataEnumMemoryRegions::EnumMemoryRegions
ms.date: 03/30/2017
api_name:
- ICLRDataEnumMemoryRegions.EnumMemoryRegions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataEnumMemoryRegions::EnumMemoryRegions
helpviewer_keywords:
- ICLRDataEnumMemoryRegions::EnumMemoryRegions method [.NET Framework debugging]
- EnumMemoryRegions method [.NET Framework debugging]
ms.assetid: 22d2e339-f174-40b5-a478-0b744501566f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bd29f6a0b0dfc0b7ab5b57bb61a3540d5caf66d0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54639627"
---
# <a name="iclrdataenummemoryregionsenummemoryregions-method"></a><span data-ttu-id="38032-102">Método ICLRDataEnumMemoryRegions::EnumMemoryRegions</span><span class="sxs-lookup"><span data-stu-id="38032-102">ICLRDataEnumMemoryRegions::EnumMemoryRegions Method</span></span>
<span data-ttu-id="38032-103">Enumera as áreas especificadas da memória.</span><span class="sxs-lookup"><span data-stu-id="38032-103">Enumerates specified areas of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38032-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="38032-104">Syntax</span></span>  
  
```  
HRESULT EnumMemoryRegions (  
    [in] ICLRDataEnumMemoryRegionsCallback  *callback,  
    [in] ULONG32                            miniDumpFlags,  
    [in] CLRDataEnumMemoryFlags             clrFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="38032-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="38032-105">Parameters</span></span>  
 `callback`  
 <span data-ttu-id="38032-106">[in] Um ponteiro para um [ICLRDataEnumMemoryRegionsCallback](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) instância que é chamada por esse método para cada região de memória que está sendo enumerado para notificar o depurador do resultado.</span><span class="sxs-lookup"><span data-stu-id="38032-106">[in] A pointer to an [ICLRDataEnumMemoryRegionsCallback](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) instance that is called by this method for each memory region being enumerated to notify the debugger of the result.</span></span>  
  
 <span data-ttu-id="38032-107">A enumeração de regiões de memória continuará mesmo que o retorno de chamada indica uma falha.</span><span class="sxs-lookup"><span data-stu-id="38032-107">The enumeration of memory regions continues even if the callback indicates a failure.</span></span>  
  
 `miniDumpFlags`  
 <span data-ttu-id="38032-108">[in] Não usado.</span><span class="sxs-lookup"><span data-stu-id="38032-108">[in] Not used.</span></span>  
  
 `clrFlags`  
 <span data-ttu-id="38032-109">[in] Um valor igual a [CLRDataEnumMemoryFlags](../../../../docs/framework/unmanaged-api/debugging/clrdataenummemoryflags-enumeration.md) enumeração que especifica as regiões de memória a serem enumerados.</span><span class="sxs-lookup"><span data-stu-id="38032-109">[in] A value of the [CLRDataEnumMemoryFlags](../../../../docs/framework/unmanaged-api/debugging/clrdataenummemoryflags-enumeration.md) enumeration that specifies the regions of memory to be enumerated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="38032-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="38032-110">Remarks</span></span>  
 <span data-ttu-id="38032-111">Esse método usa especificado [ICLRDataEnumMemoryRegionsCallback](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) instância para notificar o chamador de resultados.</span><span class="sxs-lookup"><span data-stu-id="38032-111">This method uses the specified [ICLRDataEnumMemoryRegionsCallback](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) instance to notify the caller of results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38032-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="38032-112">Requirements</span></span>  
 <span data-ttu-id="38032-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38032-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38032-114">**Cabeçalho:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="38032-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="38032-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="38032-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="38032-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38032-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38032-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="38032-117">See also</span></span>
- [<span data-ttu-id="38032-118">Interface ICLRDataEnumMemoryRegions</span><span class="sxs-lookup"><span data-stu-id="38032-118">ICLRDataEnumMemoryRegions Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-interface.md)
