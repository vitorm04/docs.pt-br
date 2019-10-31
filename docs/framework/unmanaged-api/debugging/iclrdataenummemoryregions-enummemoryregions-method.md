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
ms.openlocfilehash: 693ec07176f80711709cd9b85c6886bea8be74b2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122962"
---
# <a name="iclrdataenummemoryregionsenummemoryregions-method"></a><span data-ttu-id="d1c9c-102">Método ICLRDataEnumMemoryRegions::EnumMemoryRegions</span><span class="sxs-lookup"><span data-stu-id="d1c9c-102">ICLRDataEnumMemoryRegions::EnumMemoryRegions Method</span></span>
<span data-ttu-id="d1c9c-103">Enumera áreas especificadas de memória.</span><span class="sxs-lookup"><span data-stu-id="d1c9c-103">Enumerates specified areas of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1c9c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d1c9c-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMemoryRegions (  
    [in] ICLRDataEnumMemoryRegionsCallback  *callback,  
    [in] ULONG32                            miniDumpFlags,  
    [in] CLRDataEnumMemoryFlags             clrFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d1c9c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d1c9c-105">Parameters</span></span>  
 `callback`  
 <span data-ttu-id="d1c9c-106">no Um ponteiro para uma instância de [ICLRDataEnumMemoryRegionsCallback](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) que é chamada por esse método para cada região de memória que está sendo enumerada para notificar o depurador do resultado.</span><span class="sxs-lookup"><span data-stu-id="d1c9c-106">[in] A pointer to an [ICLRDataEnumMemoryRegionsCallback](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) instance that is called by this method for each memory region being enumerated to notify the debugger of the result.</span></span>  
  
 <span data-ttu-id="d1c9c-107">A enumeração de regiões de memória continua mesmo que o retorno de chamada indique uma falha.</span><span class="sxs-lookup"><span data-stu-id="d1c9c-107">The enumeration of memory regions continues even if the callback indicates a failure.</span></span>  
  
 `miniDumpFlags`  
 <span data-ttu-id="d1c9c-108">no Não usado.</span><span class="sxs-lookup"><span data-stu-id="d1c9c-108">[in] Not used.</span></span>  
  
 `clrFlags`  
 <span data-ttu-id="d1c9c-109">no Um valor da enumeração [CLRDataEnumMemoryFlags](../../../../docs/framework/unmanaged-api/debugging/clrdataenummemoryflags-enumeration.md) que especifica as regiões de memória a serem enumeradas.</span><span class="sxs-lookup"><span data-stu-id="d1c9c-109">[in] A value of the [CLRDataEnumMemoryFlags](../../../../docs/framework/unmanaged-api/debugging/clrdataenummemoryflags-enumeration.md) enumeration that specifies the regions of memory to be enumerated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d1c9c-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="d1c9c-110">Remarks</span></span>  
 <span data-ttu-id="d1c9c-111">Esse método usa a instância [ICLRDataEnumMemoryRegionsCallback](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) especificada para notificar o chamador de resultados.</span><span class="sxs-lookup"><span data-stu-id="d1c9c-111">This method uses the specified [ICLRDataEnumMemoryRegionsCallback](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) instance to notify the caller of results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1c9c-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d1c9c-112">Requirements</span></span>  
 <span data-ttu-id="d1c9c-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1c9c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1c9c-114">**Cabeçalho:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="d1c9c-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="d1c9c-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d1c9c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d1c9c-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1c9c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1c9c-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d1c9c-117">See also</span></span>

- [<span data-ttu-id="d1c9c-118">Interface ICLRDataEnumMemoryRegions</span><span class="sxs-lookup"><span data-stu-id="d1c9c-118">ICLRDataEnumMemoryRegions Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-interface.md)
