---
title: Enumeração CorDebugExceptionUnwindCallbackType
ms.date: 03/30/2017
api_name:
- CorDebugExceptionUnwindCallbackType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugExceptionUnwindCallbackType
helpviewer_keywords:
- CorDebugExceptionUnwindCallbackType enumeration [.NET Framework debugging]
ms.assetid: 783dce92-8a98-43db-8f78-888d943dd5b2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ef3f1d5e78efe37070bb2bdd6d2834178947af7b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740078"
---
# <a name="cordebugexceptionunwindcallbacktype-enumeration"></a><span data-ttu-id="e0d7e-102">Enumeração CorDebugExceptionUnwindCallbackType</span><span class="sxs-lookup"><span data-stu-id="e0d7e-102">CorDebugExceptionUnwindCallbackType Enumeration</span></span>
<span data-ttu-id="e0d7e-103">Indica o evento que está sendo sinalizado pelo retorno de chamada durante a fase de desenrolamento.</span><span class="sxs-lookup"><span data-stu-id="e0d7e-103">Indicates the event that is being signaled by the callback during the unwind phase.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0d7e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e0d7e-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugExceptionUnwindCallbackType {  
    DEBUG_EXCEPTION_UNWIND_BEGIN = 1,  
    DEBUG_EXCEPTION_INTERCEPTED  = 2  
} CorDebugExceptionUnwindCallbackType;  
```  
  
## <a name="members"></a><span data-ttu-id="e0d7e-105">Membros</span><span class="sxs-lookup"><span data-stu-id="e0d7e-105">Members</span></span>  
  
|<span data-ttu-id="e0d7e-106">Membro</span><span class="sxs-lookup"><span data-stu-id="e0d7e-106">Member</span></span>|<span data-ttu-id="e0d7e-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="e0d7e-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_UNWIND_BEGIN`|<span data-ttu-id="e0d7e-108">O início do processo de desenrolamento.</span><span class="sxs-lookup"><span data-stu-id="e0d7e-108">The beginning of the unwind process.</span></span>|  
|`DEBUG_EXCEPTION_INTERCEPTED`|<span data-ttu-id="e0d7e-109">A exceção foi interceptada.</span><span class="sxs-lookup"><span data-stu-id="e0d7e-109">The exception was intercepted.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e0d7e-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e0d7e-110">Requirements</span></span>  
 <span data-ttu-id="e0d7e-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0d7e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0d7e-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e0d7e-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e0d7e-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e0d7e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e0d7e-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0d7e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0d7e-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e0d7e-115">See also</span></span>

- [<span data-ttu-id="e0d7e-116">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="e0d7e-116">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
