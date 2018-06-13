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
ms.openlocfilehash: 7fe2fcf10b517f4eb7b1c7e87142afb386821246
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404088"
---
# <a name="cordebugexceptionunwindcallbacktype-enumeration"></a><span data-ttu-id="00f8d-102">Enumeração CorDebugExceptionUnwindCallbackType</span><span class="sxs-lookup"><span data-stu-id="00f8d-102">CorDebugExceptionUnwindCallbackType Enumeration</span></span>
<span data-ttu-id="00f8d-103">Indica o evento que está sendo sinalizado pelo retorno de chamada durante a fase de desenrolamento.</span><span class="sxs-lookup"><span data-stu-id="00f8d-103">Indicates the event that is being signaled by the callback during the unwind phase.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00f8d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="00f8d-104">Syntax</span></span>  
  
```  
typedef enum CorDebugExceptionUnwindCallbackType {  
    DEBUG_EXCEPTION_UNWIND_BEGIN = 1,  
    DEBUG_EXCEPTION_INTERCEPTED  = 2  
} CorDebugExceptionUnwindCallbackType;  
```  
  
## <a name="members"></a><span data-ttu-id="00f8d-105">Membros</span><span class="sxs-lookup"><span data-stu-id="00f8d-105">Members</span></span>  
  
|<span data-ttu-id="00f8d-106">Membro</span><span class="sxs-lookup"><span data-stu-id="00f8d-106">Member</span></span>|<span data-ttu-id="00f8d-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="00f8d-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_UNWIND_BEGIN`|<span data-ttu-id="00f8d-108">O início do processo de liberação.</span><span class="sxs-lookup"><span data-stu-id="00f8d-108">The beginning of the unwind process.</span></span>|  
|`DEBUG_EXCEPTION_INTERCEPTED`|<span data-ttu-id="00f8d-109">A exceção foi interceptada.</span><span class="sxs-lookup"><span data-stu-id="00f8d-109">The exception was intercepted.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="00f8d-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="00f8d-110">Requirements</span></span>  
 <span data-ttu-id="00f8d-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00f8d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00f8d-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="00f8d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="00f8d-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="00f8d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="00f8d-114">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00f8d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00f8d-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="00f8d-115">See Also</span></span>  
 [<span data-ttu-id="00f8d-116">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="00f8d-116">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
