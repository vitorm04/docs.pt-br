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
ms.openlocfilehash: f2b2bbe8bcecf71f6d3016fb35dfbf5ba1353aea
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76785634"
---
# <a name="iclrdataenummemoryregionsenummemoryregions-method"></a><span data-ttu-id="ac981-102">Método ICLRDataEnumMemoryRegions::EnumMemoryRegions</span><span class="sxs-lookup"><span data-stu-id="ac981-102">ICLRDataEnumMemoryRegions::EnumMemoryRegions Method</span></span>
<span data-ttu-id="ac981-103">Enumera áreas especificadas de memória.</span><span class="sxs-lookup"><span data-stu-id="ac981-103">Enumerates specified areas of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac981-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ac981-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMemoryRegions (  
    [in] ICLRDataEnumMemoryRegionsCallback  *callback,  
    [in] ULONG32                            miniDumpFlags,  
    [in] CLRDataEnumMemoryFlags             clrFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac981-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ac981-105">Parameters</span></span>  
 `callback`  
 <span data-ttu-id="ac981-106">no Um ponteiro para uma instância de [ICLRDataEnumMemoryRegionsCallback](iclrdataenummemoryregionscallback-interface.md) que é chamada por esse método para cada região de memória que está sendo enumerada para notificar o depurador do resultado.</span><span class="sxs-lookup"><span data-stu-id="ac981-106">[in] A pointer to an [ICLRDataEnumMemoryRegionsCallback](iclrdataenummemoryregionscallback-interface.md) instance that is called by this method for each memory region being enumerated to notify the debugger of the result.</span></span>  
  
 <span data-ttu-id="ac981-107">A enumeração de regiões de memória continua mesmo que o retorno de chamada indique uma falha.</span><span class="sxs-lookup"><span data-stu-id="ac981-107">The enumeration of memory regions continues even if the callback indicates a failure.</span></span>  
  
 `miniDumpFlags`  
 <span data-ttu-id="ac981-108">no Não usado.</span><span class="sxs-lookup"><span data-stu-id="ac981-108">[in] Not used.</span></span>  
  
 `clrFlags`  
 <span data-ttu-id="ac981-109">no Um valor da enumeração [CLRDataEnumMemoryFlags](clrdataenummemoryflags-enumeration.md) que especifica as regiões de memória a serem enumeradas.</span><span class="sxs-lookup"><span data-stu-id="ac981-109">[in] A value of the [CLRDataEnumMemoryFlags](clrdataenummemoryflags-enumeration.md) enumeration that specifies the regions of memory to be enumerated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ac981-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="ac981-110">Remarks</span></span>  
 <span data-ttu-id="ac981-111">Esse método usa a instância [ICLRDataEnumMemoryRegionsCallback](iclrdataenummemoryregionscallback-interface.md) especificada para notificar o chamador de resultados.</span><span class="sxs-lookup"><span data-stu-id="ac981-111">This method uses the specified [ICLRDataEnumMemoryRegionsCallback](iclrdataenummemoryregionscallback-interface.md) instance to notify the caller of results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac981-112">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="ac981-112">Requirements</span></span>  
 <span data-ttu-id="ac981-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac981-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac981-114">**Cabeçalho:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="ac981-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="ac981-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ac981-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ac981-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac981-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac981-117">Veja também</span><span class="sxs-lookup"><span data-stu-id="ac981-117">See also</span></span>

- [<span data-ttu-id="ac981-118">Interface ICLRDataEnumMemoryRegions</span><span class="sxs-lookup"><span data-stu-id="ac981-118">ICLRDataEnumMemoryRegions Interface</span></span>](iclrdataenummemoryregions-interface.md)
