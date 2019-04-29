---
title: Enumeração CorDebugHandleType
ms.date: 03/30/2017
api_name:
- CorDebugHandleType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugHandleType
helpviewer_keywords:
- CorDebugHandleType enumeration [.NET Framework debugging]
ms.assetid: 84296b55-c2c5-424c-ac9c-8e28e2895945
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 513fc93bdac71e2a3ba59ebb53fdde44f1659af5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61651709"
---
# <a name="cordebughandletype-enumeration"></a><span data-ttu-id="10c16-102">Enumeração CorDebugHandleType</span><span class="sxs-lookup"><span data-stu-id="10c16-102">CorDebugHandleType Enumeration</span></span>
<span data-ttu-id="10c16-103">Indica o tipo de manipulação.</span><span class="sxs-lookup"><span data-stu-id="10c16-103">Indicates the handle type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10c16-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="10c16-104">Syntax</span></span>  
  
```  
typedef enum CorDebugHandleType {  
    HANDLE_STRONG                  = 1,  
    HANDLE_WEAK_TRACK_RESURRECTION = 2  
} CorDebugHandleType;  
```  
  
## <a name="members"></a><span data-ttu-id="10c16-105">Membros</span><span class="sxs-lookup"><span data-stu-id="10c16-105">Members</span></span>  
  
|<span data-ttu-id="10c16-106">Membro</span><span class="sxs-lookup"><span data-stu-id="10c16-106">Member</span></span>|<span data-ttu-id="10c16-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="10c16-107">Description</span></span>|  
|------------|-----------------|  
|`HANDLE_STRONG`|<span data-ttu-id="10c16-108">O identificador será forte, o que impede que um objeto seja recuperada pela coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="10c16-108">The handle is strong, which prevents an object from being reclaimed by garbage collection.</span></span>|  
|`HANDLE_WEAK_TRACK_RESURRECTION`|<span data-ttu-id="10c16-109">O identificador é fraco, que não impede que um objeto seja recuperada pela coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="10c16-109">The handle is weak, which does not prevent an object from being reclaimed by garbage collection.</span></span><br /><br /> <span data-ttu-id="10c16-110">O identificador se torna inválido quando o objeto seja coletado.</span><span class="sxs-lookup"><span data-stu-id="10c16-110">The handle becomes invalid when the object is collected.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="10c16-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="10c16-111">Requirements</span></span>  
 <span data-ttu-id="10c16-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="10c16-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10c16-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="10c16-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="10c16-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="10c16-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="10c16-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10c16-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10c16-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="10c16-116">See also</span></span>

- [<span data-ttu-id="10c16-117">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="10c16-117">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
