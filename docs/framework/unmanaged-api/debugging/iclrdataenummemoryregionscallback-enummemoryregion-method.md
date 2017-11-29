---
title: "Método ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataEnumMemoryRegionsCallback.EnumMemoryRegion
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion
helpviewer_keywords:
- EnumMemoryRegion method [.NET Framework debugging]
- ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion method [.NET Framework debugging]
ms.assetid: 9bb93fab-57e8-4f9a-9ef3-1794504fa896
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e1b1897b18a8dcbb261a5041ca8b530b7877b910
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="iclrdataenummemoryregionscallbackenummemoryregion-method"></a><span data-ttu-id="ec501-102">Método ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion</span><span class="sxs-lookup"><span data-stu-id="ec501-102">ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion Method</span></span>
<span data-ttu-id="ec501-103">Chamado pelo [Iclrdataenummemoryregions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) para informar o depurador o resultado de uma tentativa para enumerar uma região especificada de memória.</span><span class="sxs-lookup"><span data-stu-id="ec501-103">Called by [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec501-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ec501-104">Syntax</span></span>  
  
```  
HRESULT EnumMemoryRegion (  
    [in] CLRDATA_ADDRESS  address,  
    [in] ULONG32          size  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ec501-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ec501-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="ec501-106">[in] O endereço inicial da região de memória que foi a serem enumerados.</span><span class="sxs-lookup"><span data-stu-id="ec501-106">[in] The starting address of the memory region that was to be enumerated.</span></span>  
  
 `size`  
 <span data-ttu-id="ec501-107">[in] O tamanho, em bytes, da região de memória.</span><span class="sxs-lookup"><span data-stu-id="ec501-107">[in] The size, in bytes, of the memory region.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ec501-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="ec501-108">Remarks</span></span>  
 <span data-ttu-id="ec501-109">O `ICLRDataEnumMemoryRegions::EnumMemoryRegions` método chamará esse método de retorno de chamada após cada tentativa para enumerar uma região de memória.</span><span class="sxs-lookup"><span data-stu-id="ec501-109">The `ICLRDataEnumMemoryRegions::EnumMemoryRegions` method will call this callback method after each attempt to enumerate a memory region.</span></span> <span data-ttu-id="ec501-110">A enumeração continuará mesmo se esse método retorna um HRESULT indicando falha.</span><span class="sxs-lookup"><span data-stu-id="ec501-110">The enumeration will continue even if this method returns an HRESULT indicating failure.</span></span>  
  
 <span data-ttu-id="ec501-111">Regiões relatados por esse retorno de chamada podem ser duplicatas ou regiões sobrepostos.</span><span class="sxs-lookup"><span data-stu-id="ec501-111">Regions reported by this callback may be duplicates or overlapping regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec501-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ec501-112">Requirements</span></span>  
 <span data-ttu-id="ec501-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec501-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec501-114">**Cabeçalho:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="ec501-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="ec501-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ec501-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ec501-116">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec501-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec501-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ec501-117">See Also</span></span>  
 [<span data-ttu-id="ec501-118">Interface ICLRDataEnumMemoryRegionsCallback</span><span class="sxs-lookup"><span data-stu-id="ec501-118">ICLRDataEnumMemoryRegionsCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md)
