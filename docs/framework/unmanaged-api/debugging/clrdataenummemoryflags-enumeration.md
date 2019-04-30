---
title: Enumeração CLRDataEnumMemoryFlags
ms.date: 03/30/2017
api_name:
- CLRDataEnumMemoryFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CLRDataEnumMemoryFlags
helpviewer_keywords:
- CLRDataEnumMemoryFlags enumeration [.NET Framework debugging]
ms.assetid: e249f9fc-e24a-4506-903c-92781f6eab7c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 80ea3afef4aee51760e3a2ce6a2b895bca4a6ec5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61961350"
---
# <a name="clrdataenummemoryflags-enumeration"></a><span data-ttu-id="5ad77-102">Enumeração CLRDataEnumMemoryFlags</span><span class="sxs-lookup"><span data-stu-id="5ad77-102">CLRDataEnumMemoryFlags Enumeration</span></span>
<span data-ttu-id="5ad77-103">Indica quais regiões de memória uma chamada para o [iclrdataenummemoryregions:: Enummemoryregions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) método deve incluir.</span><span class="sxs-lookup"><span data-stu-id="5ad77-103">Indicates which memory regions a call to the [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) method should include.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ad77-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5ad77-104">Syntax</span></span>  
  
```  
typedef enum CLRDataEnumMemoryFlags {  
    CLRDATA_ENUM_MEM_DEFAULT  = 0x0,  
    CLRDATA_ENUM_MEM_MINI     = CLRDATA_ENUM_MEM_DEFAULT,  
    CLRDATA_ENUM_MEM_HEAP     = 0x1  
} CLRDataEnumMemoryFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="5ad77-105">Membros</span><span class="sxs-lookup"><span data-stu-id="5ad77-105">Members</span></span>  
  
|<span data-ttu-id="5ad77-106">Membro</span><span class="sxs-lookup"><span data-stu-id="5ad77-106">Member</span></span>|<span data-ttu-id="5ad77-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ad77-107">Description</span></span>|  
|------------|-----------------|  
|`CLRDATA_ENUM_MEM_DEFAULT`|<span data-ttu-id="5ad77-108">Um minidespejo, ou seja, um despejo de memória esparsos.</span><span class="sxs-lookup"><span data-stu-id="5ad77-108">A minidump, that is, a sparse memory dump.</span></span>|  
|`CLRDATA_ENUM_MEM_HEAP`|<span data-ttu-id="5ad77-109">Um despejo de pilha completa.</span><span class="sxs-lookup"><span data-stu-id="5ad77-109">A full heap dump.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5ad77-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5ad77-110">Requirements</span></span>  
 <span data-ttu-id="5ad77-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ad77-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ad77-112">**Cabeçalho:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="5ad77-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="5ad77-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5ad77-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5ad77-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ad77-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ad77-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5ad77-115">See also</span></span>

- [<span data-ttu-id="5ad77-116">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="5ad77-116">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
