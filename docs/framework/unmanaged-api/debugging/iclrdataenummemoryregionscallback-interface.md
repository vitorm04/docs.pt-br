---
title: Interface ICLRDataEnumMemoryRegionsCallback
ms.date: 03/30/2017
api_name:
- ICLRDataEnumMemoryRegionsCallback
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataEnumMemoryRegionsCallback
helpviewer_keywords:
- ICLRDataEnumMemoryRegionsCallback interface [.NET Framework debugging]
ms.assetid: 3f1af8b0-8478-48e0-a7ec-3e90e0b97649
topic_type:
- apiref
ms.openlocfilehash: cf46133095d1345ffbe0356d3ab486c11ae6dbd6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122907"
---
# <a name="iclrdataenummemoryregionscallback-interface"></a><span data-ttu-id="4d7cf-102">Interface ICLRDataEnumMemoryRegionsCallback</span><span class="sxs-lookup"><span data-stu-id="4d7cf-102">ICLRDataEnumMemoryRegionsCallback Interface</span></span>
<span data-ttu-id="4d7cf-103">Fornece um método de retorno de chamada para [ICLRDataEnumMemoryRegions:: EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) para relatar ao depurador o resultado de uma tentativa de enumerar uma região especificada de memória.</span><span class="sxs-lookup"><span data-stu-id="4d7cf-103">Provides a callback method for [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4d7cf-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="4d7cf-104">Methods</span></span>  
  
|<span data-ttu-id="4d7cf-105">Método</span><span class="sxs-lookup"><span data-stu-id="4d7cf-105">Method</span></span>|<span data-ttu-id="4d7cf-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="4d7cf-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4d7cf-107">Método EnumMemoryRegion</span><span class="sxs-lookup"><span data-stu-id="4d7cf-107">EnumMemoryRegion Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-enummemoryregion-method.md)|<span data-ttu-id="4d7cf-108">Chamado pelo `ICLRDataEnumMemoryRegions::EnumMemoryRegions` para relatar ao depurador o resultado de uma tentativa de enumerar uma região especificada de memória.</span><span class="sxs-lookup"><span data-stu-id="4d7cf-108">Called by `ICLRDataEnumMemoryRegions::EnumMemoryRegions` to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4d7cf-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4d7cf-109">Requirements</span></span>  
 <span data-ttu-id="4d7cf-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d7cf-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d7cf-111">**Cabeçalho:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="4d7cf-111">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="4d7cf-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4d7cf-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4d7cf-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d7cf-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d7cf-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4d7cf-114">See also</span></span>

- [<span data-ttu-id="4d7cf-115">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="4d7cf-115">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
