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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b0e7ce243658a8c8a8404ff9079ed1395e56486f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54604139"
---
# <a name="iclrdataenummemoryregionscallback-interface"></a><span data-ttu-id="cef11-102">Interface ICLRDataEnumMemoryRegionsCallback</span><span class="sxs-lookup"><span data-stu-id="cef11-102">ICLRDataEnumMemoryRegionsCallback Interface</span></span>
<span data-ttu-id="cef11-103">Fornece um método de retorno de chamada para [iclrdataenummemoryregions:: Enummemoryregions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) para relatar ao depurador o resultado de uma tentativa de enumerar uma região especificada de memória.</span><span class="sxs-lookup"><span data-stu-id="cef11-103">Provides a callback method for [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cef11-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="cef11-104">Methods</span></span>  
  
|<span data-ttu-id="cef11-105">Método</span><span class="sxs-lookup"><span data-stu-id="cef11-105">Method</span></span>|<span data-ttu-id="cef11-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="cef11-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cef11-107">Método EnumMemoryRegion</span><span class="sxs-lookup"><span data-stu-id="cef11-107">EnumMemoryRegion Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-enummemoryregion-method.md)|<span data-ttu-id="cef11-108">Chamado pelo `ICLRDataEnumMemoryRegions::EnumMemoryRegions` para relatar ao depurador o resultado de uma tentativa de enumerar uma região especificada de memória.</span><span class="sxs-lookup"><span data-stu-id="cef11-108">Called by `ICLRDataEnumMemoryRegions::EnumMemoryRegions` to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cef11-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cef11-109">Requirements</span></span>  
 <span data-ttu-id="cef11-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cef11-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cef11-111">**Cabeçalho:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="cef11-111">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="cef11-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cef11-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cef11-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cef11-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cef11-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cef11-114">See also</span></span>
- [<span data-ttu-id="cef11-115">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="cef11-115">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
