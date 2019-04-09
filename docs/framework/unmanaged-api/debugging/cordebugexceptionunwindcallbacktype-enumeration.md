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
ms.openlocfilehash: 408e72eeaa1dac83c45488d186425f30c6043280
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59155617"
---
# <a name="cordebugexceptionunwindcallbacktype-enumeration"></a><span data-ttu-id="fbb44-102">Enumeração CorDebugExceptionUnwindCallbackType</span><span class="sxs-lookup"><span data-stu-id="fbb44-102">CorDebugExceptionUnwindCallbackType Enumeration</span></span>
<span data-ttu-id="fbb44-103">Indica o evento que está sendo sinalizado pelo retorno de chamada durante a fase de desenrolamento.</span><span class="sxs-lookup"><span data-stu-id="fbb44-103">Indicates the event that is being signaled by the callback during the unwind phase.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbb44-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fbb44-104">Syntax</span></span>  
  
```  
typedef enum CorDebugExceptionUnwindCallbackType {  
    DEBUG_EXCEPTION_UNWIND_BEGIN = 1,  
    DEBUG_EXCEPTION_INTERCEPTED  = 2  
} CorDebugExceptionUnwindCallbackType;  
```  
  
## <a name="members"></a><span data-ttu-id="fbb44-105">Membros</span><span class="sxs-lookup"><span data-stu-id="fbb44-105">Members</span></span>  
  
|<span data-ttu-id="fbb44-106">Membro</span><span class="sxs-lookup"><span data-stu-id="fbb44-106">Member</span></span>|<span data-ttu-id="fbb44-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="fbb44-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_UNWIND_BEGIN`|<span data-ttu-id="fbb44-108">O início do processo de desenrolamento.</span><span class="sxs-lookup"><span data-stu-id="fbb44-108">The beginning of the unwind process.</span></span>|  
|`DEBUG_EXCEPTION_INTERCEPTED`|<span data-ttu-id="fbb44-109">A exceção foi interceptada.</span><span class="sxs-lookup"><span data-stu-id="fbb44-109">The exception was intercepted.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fbb44-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fbb44-110">Requirements</span></span>  
 <span data-ttu-id="fbb44-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fbb44-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fbb44-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fbb44-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fbb44-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fbb44-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="fbb44-114">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="fbb44-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="fbb44-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fbb44-115">See also</span></span>

- [<span data-ttu-id="fbb44-116">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="fbb44-116">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
