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
ms.openlocfilehash: e714c41812c8aaccd713115712df05744cc015e3
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789379"
---
# <a name="cordebugexceptionunwindcallbacktype-enumeration"></a><span data-ttu-id="2b4e6-102">Enumeração CorDebugExceptionUnwindCallbackType</span><span class="sxs-lookup"><span data-stu-id="2b4e6-102">CorDebugExceptionUnwindCallbackType Enumeration</span></span>
<span data-ttu-id="2b4e6-103">Indica o evento que está sendo sinalizado pelo retorno de chamada durante a fase de desenrolamento.</span><span class="sxs-lookup"><span data-stu-id="2b4e6-103">Indicates the event that is being signaled by the callback during the unwind phase.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b4e6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2b4e6-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugExceptionUnwindCallbackType {  
    DEBUG_EXCEPTION_UNWIND_BEGIN = 1,  
    DEBUG_EXCEPTION_INTERCEPTED  = 2  
} CorDebugExceptionUnwindCallbackType;  
```  
  
## <a name="members"></a><span data-ttu-id="2b4e6-105">Membros</span><span class="sxs-lookup"><span data-stu-id="2b4e6-105">Members</span></span>  
  
|<span data-ttu-id="2b4e6-106">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="2b4e6-106">Member</span></span>|<span data-ttu-id="2b4e6-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b4e6-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_UNWIND_BEGIN`|<span data-ttu-id="2b4e6-108">O início do processo de desenrolar.</span><span class="sxs-lookup"><span data-stu-id="2b4e6-108">The beginning of the unwind process.</span></span>|  
|`DEBUG_EXCEPTION_INTERCEPTED`|<span data-ttu-id="2b4e6-109">A exceção foi interceptada.</span><span class="sxs-lookup"><span data-stu-id="2b4e6-109">The exception was intercepted.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2b4e6-110">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="2b4e6-110">Requirements</span></span>  
 <span data-ttu-id="2b4e6-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b4e6-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b4e6-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2b4e6-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2b4e6-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2b4e6-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2b4e6-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b4e6-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b4e6-115">Veja também</span><span class="sxs-lookup"><span data-stu-id="2b4e6-115">See also</span></span>

- [<span data-ttu-id="2b4e6-116">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="2b4e6-116">Debugging Enumerations</span></span>](debugging-enumerations.md)
