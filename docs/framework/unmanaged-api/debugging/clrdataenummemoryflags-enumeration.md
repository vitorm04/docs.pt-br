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
ms.openlocfilehash: 67b85917be590bdba7ed3f10972ad39b731dbcdd
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274238"
---
# <a name="clrdataenummemoryflags-enumeration"></a><span data-ttu-id="29027-102">Enumeração CLRDataEnumMemoryFlags</span><span class="sxs-lookup"><span data-stu-id="29027-102">CLRDataEnumMemoryFlags Enumeration</span></span>
<span data-ttu-id="29027-103">Indica quais regiões de memória uma chamada para o método [ICLRDataEnumMemoryRegions:: EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) deve incluir.</span><span class="sxs-lookup"><span data-stu-id="29027-103">Indicates which memory regions a call to the [ICLRDataEnumMemoryRegions::EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) method should include.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29027-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="29027-104">Syntax</span></span>  
  
```cpp  
typedef enum CLRDataEnumMemoryFlags {  
    CLRDATA_ENUM_MEM_DEFAULT  = 0x0,  
    CLRDATA_ENUM_MEM_MINI     = CLRDATA_ENUM_MEM_DEFAULT,  
    CLRDATA_ENUM_MEM_HEAP     = 0x1  
} CLRDataEnumMemoryFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="29027-105">Membros</span><span class="sxs-lookup"><span data-stu-id="29027-105">Members</span></span>  
  
|<span data-ttu-id="29027-106">Membro</span><span class="sxs-lookup"><span data-stu-id="29027-106">Member</span></span>|<span data-ttu-id="29027-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="29027-107">Description</span></span>|  
|------------|-----------------|  
|`CLRDATA_ENUM_MEM_DEFAULT`|<span data-ttu-id="29027-108">Um minidespejo, ou seja, um despejo de memória esparso.</span><span class="sxs-lookup"><span data-stu-id="29027-108">A minidump, that is, a sparse memory dump.</span></span>|  
|`CLRDATA_ENUM_MEM_HEAP`|<span data-ttu-id="29027-109">Um despejo de pilha completo.</span><span class="sxs-lookup"><span data-stu-id="29027-109">A full heap dump.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="29027-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="29027-110">Requirements</span></span>  
 <span data-ttu-id="29027-111">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29027-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29027-112">**Cabeçalho:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="29027-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="29027-113">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="29027-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29027-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29027-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29027-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="29027-115">See also</span></span>

- [<span data-ttu-id="29027-116">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="29027-116">Debugging Enumerations</span></span>](debugging-enumerations.md)
