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
ms.openlocfilehash: 4e3891996af5945ed95c8c37dddfee5c446db248
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789117"
---
# <a name="iclrdataenummemoryregionscallback-interface"></a><span data-ttu-id="5f211-102">Interface ICLRDataEnumMemoryRegionsCallback</span><span class="sxs-lookup"><span data-stu-id="5f211-102">ICLRDataEnumMemoryRegionsCallback Interface</span></span>
<span data-ttu-id="5f211-103">Fornece um método de retorno de chamada para [ICLRDataEnumMemoryRegions:: EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) para relatar ao depurador o resultado de uma tentativa de enumerar uma região especificada de memória.</span><span class="sxs-lookup"><span data-stu-id="5f211-103">Provides a callback method for [ICLRDataEnumMemoryRegions::EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5f211-104">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="5f211-104">Methods</span></span>  
  
|<span data-ttu-id="5f211-105">Método</span><span class="sxs-lookup"><span data-stu-id="5f211-105">Method</span></span>|<span data-ttu-id="5f211-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="5f211-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5f211-107">Método EnumMemoryRegion</span><span class="sxs-lookup"><span data-stu-id="5f211-107">EnumMemoryRegion Method</span></span>](iclrdataenummemoryregionscallback-enummemoryregion-method.md)|<span data-ttu-id="5f211-108">Chamado pelo `ICLRDataEnumMemoryRegions::EnumMemoryRegions` para relatar ao depurador o resultado de uma tentativa de enumerar uma região especificada de memória.</span><span class="sxs-lookup"><span data-stu-id="5f211-108">Called by `ICLRDataEnumMemoryRegions::EnumMemoryRegions` to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5f211-109">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="5f211-109">Requirements</span></span>  
 <span data-ttu-id="5f211-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5f211-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f211-111">**Cabeçalho:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="5f211-111">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="5f211-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5f211-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5f211-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f211-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f211-114">Veja também</span><span class="sxs-lookup"><span data-stu-id="5f211-114">See also</span></span>

- [<span data-ttu-id="5f211-115">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="5f211-115">Debugging Interfaces</span></span>](debugging-interfaces.md)
