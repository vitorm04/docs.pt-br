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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b712ee0bb8e67f448b7ea2bee3c092367181abad
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740218"
---
# <a name="cordebugexceptioncallbacktype-enumeration"></a><span data-ttu-id="03857-102">Enumeração CorDebugExceptionCallbackType</span><span class="sxs-lookup"><span data-stu-id="03857-102">CorDebugExceptionCallbackType Enumeration</span></span>
<span data-ttu-id="03857-103">Indica o tipo de retorno de chamada é feito de um [ICorDebugManagedCallback2::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md) eventos.</span><span class="sxs-lookup"><span data-stu-id="03857-103">Indicates the type of callback that is made from an [ICorDebugManagedCallback2::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md) event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03857-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="03857-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugExceptionCallbackType {  
    DEBUG_EXCEPTION_FIRST_CHANCE         = 1,  
    DEBUG_EXCEPTION_USER_FIRST_CHANCE    = 2,  
    DEBUG_EXCEPTION_CATCH_HANDLER_FOUND  = 3,  
    DEBUG_EXCEPTION_UNHANDLED            = 4  
} CorDebugExceptionCallbackType;  
```  
  
## <a name="members"></a><span data-ttu-id="03857-105">Membros</span><span class="sxs-lookup"><span data-stu-id="03857-105">Members</span></span>  
  
|<span data-ttu-id="03857-106">Membro</span><span class="sxs-lookup"><span data-stu-id="03857-106">Member</span></span>|<span data-ttu-id="03857-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="03857-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_FIRST_CHANCE`|<span data-ttu-id="03857-108">Uma exceção foi lançada.</span><span class="sxs-lookup"><span data-stu-id="03857-108">An exception was thrown.</span></span>|  
|`DEBUG_EXCEPTION_USER_FIRST_CHANCE`|<span data-ttu-id="03857-109">O processo de exceção windup inseriu o código de usuário.</span><span class="sxs-lookup"><span data-stu-id="03857-109">The exception windup process entered user code.</span></span>|  
|`DEBUG_EXCEPTION_CATCH_HANDLER_FOUND`|<span data-ttu-id="03857-110">O processo de windup exceção encontrado uma `catch` bloquear no código do usuário.</span><span class="sxs-lookup"><span data-stu-id="03857-110">The exception windup process found a `catch` block in user code.</span></span>|  
|`DEBUG_EXCEPTION_UNHANDLED`|<span data-ttu-id="03857-111">A exceção não foi tratada.</span><span class="sxs-lookup"><span data-stu-id="03857-111">The exception was not handled.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="03857-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="03857-112">Requirements</span></span>  
 <span data-ttu-id="03857-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03857-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03857-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="03857-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="03857-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="03857-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="03857-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03857-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03857-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="03857-117">See also</span></span>

- [<span data-ttu-id="03857-118">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="03857-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
