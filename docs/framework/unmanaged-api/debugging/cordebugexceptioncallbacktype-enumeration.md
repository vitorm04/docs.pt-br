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
ms.openlocfilehash: 91b09be04499396a2229962fd592f29cb8bc8d04
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59155552"
---
# <a name="cordebugexceptioncallbacktype-enumeration"></a><span data-ttu-id="36f69-102">Enumeração CorDebugExceptionCallbackType</span><span class="sxs-lookup"><span data-stu-id="36f69-102">CorDebugExceptionCallbackType Enumeration</span></span>
<span data-ttu-id="36f69-103">Indica o tipo de retorno de chamada é feito de um [ICorDebugManagedCallback2::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md) eventos.</span><span class="sxs-lookup"><span data-stu-id="36f69-103">Indicates the type of callback that is made from an [ICorDebugManagedCallback2::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md) event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36f69-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="36f69-104">Syntax</span></span>  
  
```  
typedef enum CorDebugExceptionCallbackType {  
    DEBUG_EXCEPTION_FIRST_CHANCE         = 1,  
    DEBUG_EXCEPTION_USER_FIRST_CHANCE    = 2,  
    DEBUG_EXCEPTION_CATCH_HANDLER_FOUND  = 3,  
    DEBUG_EXCEPTION_UNHANDLED            = 4  
} CorDebugExceptionCallbackType;  
```  
  
## <a name="members"></a><span data-ttu-id="36f69-105">Membros</span><span class="sxs-lookup"><span data-stu-id="36f69-105">Members</span></span>  
  
|<span data-ttu-id="36f69-106">Membro</span><span class="sxs-lookup"><span data-stu-id="36f69-106">Member</span></span>|<span data-ttu-id="36f69-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="36f69-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_FIRST_CHANCE`|<span data-ttu-id="36f69-108">Uma exceção foi lançada.</span><span class="sxs-lookup"><span data-stu-id="36f69-108">An exception was thrown.</span></span>|  
|`DEBUG_EXCEPTION_USER_FIRST_CHANCE`|<span data-ttu-id="36f69-109">O processo de exceção windup inseriu o código de usuário.</span><span class="sxs-lookup"><span data-stu-id="36f69-109">The exception windup process entered user code.</span></span>|  
|`DEBUG_EXCEPTION_CATCH_HANDLER_FOUND`|<span data-ttu-id="36f69-110">O processo de windup exceção encontrado uma `catch` bloquear no código do usuário.</span><span class="sxs-lookup"><span data-stu-id="36f69-110">The exception windup process found a `catch` block in user code.</span></span>|  
|`DEBUG_EXCEPTION_UNHANDLED`|<span data-ttu-id="36f69-111">A exceção não foi tratada.</span><span class="sxs-lookup"><span data-stu-id="36f69-111">The exception was not handled.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="36f69-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="36f69-112">Requirements</span></span>  
 <span data-ttu-id="36f69-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36f69-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36f69-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="36f69-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="36f69-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="36f69-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="36f69-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36f69-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36f69-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="36f69-117">See also</span></span>

- [<span data-ttu-id="36f69-118">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="36f69-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
