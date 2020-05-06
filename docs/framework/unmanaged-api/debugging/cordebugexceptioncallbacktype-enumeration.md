---
title: Enumeração CorDebugExceptionCallbackType
ms.date: 03/30/2017
api_name:
- CorDebugExceptionCallbackType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugExceptionCallbackType
helpviewer_keywords:
- CorDebugExceptionCallbackType enumeration [.NET Framework debugging]
ms.assetid: 4d946ad4-3c19-42cb-bec9-8633325ba769
topic_type:
- apiref
ms.openlocfilehash: d5cdb8c6740970f6a7469be8c763961bf76d6ecc
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795931"
---
# <a name="cordebugexceptioncallbacktype-enumeration"></a><span data-ttu-id="b2bac-102">Enumeração CorDebugExceptionCallbackType</span><span class="sxs-lookup"><span data-stu-id="b2bac-102">CorDebugExceptionCallbackType Enumeration</span></span>
<span data-ttu-id="b2bac-103">Indica o tipo de retorno de chamada que é feito de um evento [ICorDebugManagedCallback2:: Exception](icordebugmanagedcallback2-exception-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b2bac-103">Indicates the type of callback that is made from an [ICorDebugManagedCallback2::Exception](icordebugmanagedcallback2-exception-method.md) event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2bac-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b2bac-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugExceptionCallbackType {  
    DEBUG_EXCEPTION_FIRST_CHANCE         = 1,  
    DEBUG_EXCEPTION_USER_FIRST_CHANCE    = 2,  
    DEBUG_EXCEPTION_CATCH_HANDLER_FOUND  = 3,  
    DEBUG_EXCEPTION_UNHANDLED            = 4  
} CorDebugExceptionCallbackType;  
```  
  
## <a name="members"></a><span data-ttu-id="b2bac-105">Membros</span><span class="sxs-lookup"><span data-stu-id="b2bac-105">Members</span></span>  
  
|<span data-ttu-id="b2bac-106">Membro</span><span class="sxs-lookup"><span data-stu-id="b2bac-106">Member</span></span>|<span data-ttu-id="b2bac-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="b2bac-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_FIRST_CHANCE`|<span data-ttu-id="b2bac-108">Uma exceção foi lançada.</span><span class="sxs-lookup"><span data-stu-id="b2bac-108">An exception was thrown.</span></span>|  
|`DEBUG_EXCEPTION_USER_FIRST_CHANCE`|<span data-ttu-id="b2bac-109">O processo de windup de exceção inseriu o código do usuário.</span><span class="sxs-lookup"><span data-stu-id="b2bac-109">The exception windup process entered user code.</span></span>|  
|`DEBUG_EXCEPTION_CATCH_HANDLER_FOUND`|<span data-ttu-id="b2bac-110">O processo windup de exceção encontrou `catch` um bloco no código do usuário.</span><span class="sxs-lookup"><span data-stu-id="b2bac-110">The exception windup process found a `catch` block in user code.</span></span>|  
|`DEBUG_EXCEPTION_UNHANDLED`|<span data-ttu-id="b2bac-111">A exceção não foi tratada.</span><span class="sxs-lookup"><span data-stu-id="b2bac-111">The exception was not handled.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b2bac-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b2bac-112">Requirements</span></span>  
 <span data-ttu-id="b2bac-113">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2bac-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2bac-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b2bac-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b2bac-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b2bac-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b2bac-116">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2bac-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2bac-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b2bac-117">See also</span></span>

- [<span data-ttu-id="b2bac-118">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="b2bac-118">Debugging Enumerations</span></span>](debugging-enumerations.md)
