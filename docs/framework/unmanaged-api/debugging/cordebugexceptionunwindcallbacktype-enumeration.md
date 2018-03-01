---
title: "Enumeração CorDebugExceptionUnwindCallbackType"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0c5ee074e55d0d407f89c778c579aa5c4ce03a10
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugexceptionunwindcallbacktype-enumeration"></a><span data-ttu-id="73e4a-102">Enumeração CorDebugExceptionUnwindCallbackType</span><span class="sxs-lookup"><span data-stu-id="73e4a-102">CorDebugExceptionUnwindCallbackType Enumeration</span></span>
<span data-ttu-id="73e4a-103">Indica o evento que está sendo sinalizado pelo retorno de chamada durante a fase de desenrolamento.</span><span class="sxs-lookup"><span data-stu-id="73e4a-103">Indicates the event that is being signaled by the callback during the unwind phase.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73e4a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="73e4a-104">Syntax</span></span>  
  
```  
typedef enum CorDebugExceptionUnwindCallbackType {  
    DEBUG_EXCEPTION_UNWIND_BEGIN = 1,  
    DEBUG_EXCEPTION_INTERCEPTED  = 2  
} CorDebugExceptionUnwindCallbackType;  
```  
  
## <a name="members"></a><span data-ttu-id="73e4a-105">Membros</span><span class="sxs-lookup"><span data-stu-id="73e4a-105">Members</span></span>  
  
|<span data-ttu-id="73e4a-106">Membro</span><span class="sxs-lookup"><span data-stu-id="73e4a-106">Member</span></span>|<span data-ttu-id="73e4a-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="73e4a-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_UNWIND_BEGIN`|<span data-ttu-id="73e4a-108">O início do processo de liberação.</span><span class="sxs-lookup"><span data-stu-id="73e4a-108">The beginning of the unwind process.</span></span>|  
|`DEBUG_EXCEPTION_INTERCEPTED`|<span data-ttu-id="73e4a-109">A exceção foi interceptada.</span><span class="sxs-lookup"><span data-stu-id="73e4a-109">The exception was intercepted.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="73e4a-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="73e4a-110">Requirements</span></span>  
 <span data-ttu-id="73e4a-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73e4a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73e4a-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="73e4a-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="73e4a-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="73e4a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73e4a-114">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73e4a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73e4a-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="73e4a-115">See Also</span></span>  
 [<span data-ttu-id="73e4a-116">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="73e4a-116">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
