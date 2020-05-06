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
ms.openlocfilehash: ddcb8064dfb9be30c66404a8762a9ca73cd6afe4
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860656"
---
# <a name="iclrdataenummemoryregionscallback-interface"></a><span data-ttu-id="5ac3f-102">Interface ICLRDataEnumMemoryRegionsCallback</span><span class="sxs-lookup"><span data-stu-id="5ac3f-102">ICLRDataEnumMemoryRegionsCallback Interface</span></span>
<span data-ttu-id="5ac3f-103">Fornece um método de retorno de chamada para [ICLRDataEnumMemoryRegions:: EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) para relatar ao depurador o resultado de uma tentativa de enumerar uma região especificada de memória.</span><span class="sxs-lookup"><span data-stu-id="5ac3f-103">Provides a callback method for [ICLRDataEnumMemoryRegions::EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5ac3f-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="5ac3f-104">Methods</span></span>  
  
|<span data-ttu-id="5ac3f-105">Método</span><span class="sxs-lookup"><span data-stu-id="5ac3f-105">Method</span></span>|<span data-ttu-id="5ac3f-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ac3f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5ac3f-107">Método EnumMemoryRegion</span><span class="sxs-lookup"><span data-stu-id="5ac3f-107">EnumMemoryRegion Method</span></span>](iclrdataenummemoryregionscallback-enummemoryregion-method.md)|<span data-ttu-id="5ac3f-108">Chamado por `ICLRDataEnumMemoryRegions::EnumMemoryRegions` para relatar ao depurador o resultado de uma tentativa de enumerar uma região especificada de memória.</span><span class="sxs-lookup"><span data-stu-id="5ac3f-108">Called by `ICLRDataEnumMemoryRegions::EnumMemoryRegions` to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5ac3f-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5ac3f-109">Requirements</span></span>  
 <span data-ttu-id="5ac3f-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ac3f-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ac3f-111">**Cabeçalho:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="5ac3f-111">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="5ac3f-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5ac3f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5ac3f-113">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ac3f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ac3f-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="5ac3f-114">See also</span></span>

- [<span data-ttu-id="5ac3f-115">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="5ac3f-115">Debugging Interfaces</span></span>](debugging-interfaces.md)
