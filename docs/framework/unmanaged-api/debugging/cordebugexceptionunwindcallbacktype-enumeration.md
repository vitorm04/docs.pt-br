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
ms.openlocfilehash: 4d2be9960f8935b754791a8badd4ea98b5d54912
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795905"
---
# <a name="cordebugexceptionunwindcallbacktype-enumeration"></a><span data-ttu-id="0d704-102">Enumeração CorDebugExceptionUnwindCallbackType</span><span class="sxs-lookup"><span data-stu-id="0d704-102">CorDebugExceptionUnwindCallbackType Enumeration</span></span>
<span data-ttu-id="0d704-103">Indica o evento que está sendo sinalizado pelo retorno de chamada durante a fase de desenrolamento.</span><span class="sxs-lookup"><span data-stu-id="0d704-103">Indicates the event that is being signaled by the callback during the unwind phase.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d704-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0d704-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugExceptionUnwindCallbackType {  
    DEBUG_EXCEPTION_UNWIND_BEGIN = 1,  
    DEBUG_EXCEPTION_INTERCEPTED  = 2  
} CorDebugExceptionUnwindCallbackType;  
```  
  
## <a name="members"></a><span data-ttu-id="0d704-105">Membros</span><span class="sxs-lookup"><span data-stu-id="0d704-105">Members</span></span>  
  
|<span data-ttu-id="0d704-106">Membro</span><span class="sxs-lookup"><span data-stu-id="0d704-106">Member</span></span>|<span data-ttu-id="0d704-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="0d704-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_UNWIND_BEGIN`|<span data-ttu-id="0d704-108">O início do processo de desenrolar.</span><span class="sxs-lookup"><span data-stu-id="0d704-108">The beginning of the unwind process.</span></span>|  
|`DEBUG_EXCEPTION_INTERCEPTED`|<span data-ttu-id="0d704-109">A exceção foi interceptada.</span><span class="sxs-lookup"><span data-stu-id="0d704-109">The exception was intercepted.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0d704-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0d704-110">Requirements</span></span>  
 <span data-ttu-id="0d704-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d704-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d704-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0d704-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0d704-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0d704-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0d704-114">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d704-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d704-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0d704-115">See also</span></span>

- [<span data-ttu-id="0d704-116">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="0d704-116">Debugging Enumerations</span></span>](debugging-enumerations.md)
