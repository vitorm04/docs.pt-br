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
ms.openlocfilehash: 2ebe7ef37fb072e3688cc4dcfa5ed89832e886e9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122941"
---
# <a name="iclrdataenummemoryregionscallbackenummemoryregion-method"></a><span data-ttu-id="34534-102">Método ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion</span><span class="sxs-lookup"><span data-stu-id="34534-102">ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion Method</span></span>
<span data-ttu-id="34534-103">Chamado por [ICLRDataEnumMemoryRegions:: EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) para relatar ao depurador o resultado de uma tentativa de enumerar uma região especificada de memória.</span><span class="sxs-lookup"><span data-stu-id="34534-103">Called by [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34534-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="34534-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMemoryRegion (  
    [in] CLRDATA_ADDRESS  address,  
    [in] ULONG32          size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="34534-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="34534-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="34534-106">no O endereço inicial da região de memória que deve ser enumerada.</span><span class="sxs-lookup"><span data-stu-id="34534-106">[in] The starting address of the memory region that was to be enumerated.</span></span>  
  
 `size`  
 <span data-ttu-id="34534-107">no O tamanho, em bytes, da região de memória.</span><span class="sxs-lookup"><span data-stu-id="34534-107">[in] The size, in bytes, of the memory region.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="34534-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="34534-108">Remarks</span></span>  
 <span data-ttu-id="34534-109">O método `ICLRDataEnumMemoryRegions::EnumMemoryRegions` chamará esse método de retorno de chamada após cada tentativa de enumerar uma região de memória.</span><span class="sxs-lookup"><span data-stu-id="34534-109">The `ICLRDataEnumMemoryRegions::EnumMemoryRegions` method will call this callback method after each attempt to enumerate a memory region.</span></span> <span data-ttu-id="34534-110">A enumeração continuará mesmo se esse método retornar um HRESULT indicando falha.</span><span class="sxs-lookup"><span data-stu-id="34534-110">The enumeration will continue even if this method returns an HRESULT indicating failure.</span></span>  
  
 <span data-ttu-id="34534-111">As regiões relatadas por esse retorno de chamada podem ser duplicatas ou sobrepostas regiões.</span><span class="sxs-lookup"><span data-stu-id="34534-111">Regions reported by this callback may be duplicates or overlapping regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34534-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="34534-112">Requirements</span></span>  
 <span data-ttu-id="34534-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34534-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34534-114">**Cabeçalho:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="34534-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="34534-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="34534-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="34534-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34534-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34534-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34534-117">See also</span></span>

- [<span data-ttu-id="34534-118">Interface ICLRDataEnumMemoryRegionsCallback</span><span class="sxs-lookup"><span data-stu-id="34534-118">ICLRDataEnumMemoryRegionsCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md)
