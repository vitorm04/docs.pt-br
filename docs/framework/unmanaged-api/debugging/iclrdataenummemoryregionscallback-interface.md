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
ms.openlocfilehash: 0a0af0c86bc44a4968119e1afd2a84e17e941601
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405493"
---
# <a name="iclrdataenummemoryregionscallback-interface"></a><span data-ttu-id="47576-102">Interface ICLRDataEnumMemoryRegionsCallback</span><span class="sxs-lookup"><span data-stu-id="47576-102">ICLRDataEnumMemoryRegionsCallback Interface</span></span>
<span data-ttu-id="47576-103">Fornece um método de retorno de chamada para [Iclrdataenummemoryregions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) para informar o depurador o resultado de uma tentativa para enumerar uma região especificada de memória.</span><span class="sxs-lookup"><span data-stu-id="47576-103">Provides a callback method for [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="47576-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="47576-104">Methods</span></span>  
  
|<span data-ttu-id="47576-105">Método</span><span class="sxs-lookup"><span data-stu-id="47576-105">Method</span></span>|<span data-ttu-id="47576-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="47576-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="47576-107">Método EnumMemoryRegion</span><span class="sxs-lookup"><span data-stu-id="47576-107">EnumMemoryRegion Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-enummemoryregion-method.md)|<span data-ttu-id="47576-108">Chamado por `ICLRDataEnumMemoryRegions::EnumMemoryRegions` para informar o depurador o resultado de uma tentativa para enumerar uma região especificada de memória.</span><span class="sxs-lookup"><span data-stu-id="47576-108">Called by `ICLRDataEnumMemoryRegions::EnumMemoryRegions` to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="47576-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="47576-109">Requirements</span></span>  
 <span data-ttu-id="47576-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47576-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47576-111">**Cabeçalho:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="47576-111">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="47576-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="47576-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="47576-113">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47576-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47576-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="47576-114">See Also</span></span>  
 [<span data-ttu-id="47576-115">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="47576-115">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
