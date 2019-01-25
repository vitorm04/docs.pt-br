---
title: Método ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion
ms.date: 03/30/2017
api_name:
- ICLRDataEnumMemoryRegionsCallback.EnumMemoryRegion
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion
helpviewer_keywords:
- EnumMemoryRegion method [.NET Framework debugging]
- ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion method [.NET Framework debugging]
ms.assetid: 9bb93fab-57e8-4f9a-9ef3-1794504fa896
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0f87107be14554d8d826c58108446ecd245549b6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54603674"
---
# <a name="iclrdataenummemoryregionscallbackenummemoryregion-method"></a><span data-ttu-id="50a37-102">Método ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion</span><span class="sxs-lookup"><span data-stu-id="50a37-102">ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion Method</span></span>
<span data-ttu-id="50a37-103">Chamado pelo [iclrdataenummemoryregions:: Enummemoryregions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) para relatar ao depurador o resultado de uma tentativa de enumerar uma região especificada de memória.</span><span class="sxs-lookup"><span data-stu-id="50a37-103">Called by [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50a37-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="50a37-104">Syntax</span></span>  
  
```  
HRESULT EnumMemoryRegion (  
    [in] CLRDATA_ADDRESS  address,  
    [in] ULONG32          size  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="50a37-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="50a37-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="50a37-106">[in] O endereço inicial da região de memória que foi a serem enumerados.</span><span class="sxs-lookup"><span data-stu-id="50a37-106">[in] The starting address of the memory region that was to be enumerated.</span></span>  
  
 `size`  
 <span data-ttu-id="50a37-107">[in] O tamanho, em bytes, da região de memória.</span><span class="sxs-lookup"><span data-stu-id="50a37-107">[in] The size, in bytes, of the memory region.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="50a37-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="50a37-108">Remarks</span></span>  
 <span data-ttu-id="50a37-109">O `ICLRDataEnumMemoryRegions::EnumMemoryRegions` método irá chamar esse método de retorno de chamada após cada tentativa de enumerar uma região de memória.</span><span class="sxs-lookup"><span data-stu-id="50a37-109">The `ICLRDataEnumMemoryRegions::EnumMemoryRegions` method will call this callback method after each attempt to enumerate a memory region.</span></span> <span data-ttu-id="50a37-110">A enumeração continuará mesmo se esse método retorna um HRESULT indicando uma falha.</span><span class="sxs-lookup"><span data-stu-id="50a37-110">The enumeration will continue even if this method returns an HRESULT indicating failure.</span></span>  
  
 <span data-ttu-id="50a37-111">Regiões relatados por esse retorno de chamada podem ser duplicatas ou regiões sobrepostas.</span><span class="sxs-lookup"><span data-stu-id="50a37-111">Regions reported by this callback may be duplicates or overlapping regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50a37-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="50a37-112">Requirements</span></span>  
 <span data-ttu-id="50a37-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50a37-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50a37-114">**Cabeçalho:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="50a37-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="50a37-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="50a37-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="50a37-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50a37-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50a37-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="50a37-117">See also</span></span>
- [<span data-ttu-id="50a37-118">Interface ICLRDataEnumMemoryRegionsCallback</span><span class="sxs-lookup"><span data-stu-id="50a37-118">ICLRDataEnumMemoryRegionsCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md)
