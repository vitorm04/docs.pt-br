---
title: Enumeração CorDebugStepReason
ms.date: 03/30/2017
api_name:
- CorDebugStepReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugStepReason
helpviewer_keywords:
- CorDebugStepReason enumeration [.NET Framework debugging]
ms.assetid: fe248069-b33c-48e1-a777-06ac9b239c54
topic_type:
- apiref
ms.openlocfilehash: 6c73afb00cbd104cff3d310d1369097b459c131e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133683"
---
# <a name="cordebugstepreason-enumeration"></a><span data-ttu-id="c1ffe-102">Enumeração CorDebugStepReason</span><span class="sxs-lookup"><span data-stu-id="c1ffe-102">CorDebugStepReason Enumeration</span></span>
<span data-ttu-id="c1ffe-103">Indica o resultado de uma etapa individual.</span><span class="sxs-lookup"><span data-stu-id="c1ffe-103">Indicates the outcome of an individual step.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1ffe-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c1ffe-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugStepReason {  
    STEP_NORMAL,  
    STEP_RETURN,  
    STEP_CALL,  
    STEP_EXCEPTION_FILTER,  
    STEP_EXCEPTION_HANDLER,  
    STEP_INTERCEPT,  
    STEP_EXIT  
} CorDebugStepReason;  
```  
  
## <a name="members"></a><span data-ttu-id="c1ffe-105">Membros</span><span class="sxs-lookup"><span data-stu-id="c1ffe-105">Members</span></span>  
  
|<span data-ttu-id="c1ffe-106">Membro</span><span class="sxs-lookup"><span data-stu-id="c1ffe-106">Member</span></span>|<span data-ttu-id="c1ffe-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="c1ffe-107">Description</span></span>|  
|------------|-----------------|  
|`STEP_NORMAL`|<span data-ttu-id="c1ffe-108">A etapa foi concluída normalmente, dentro da mesma função.</span><span class="sxs-lookup"><span data-stu-id="c1ffe-108">Stepping completed normally, within the same function.</span></span>|  
|`STEP_RETURN`|<span data-ttu-id="c1ffe-109">A depuração continua normalmente, depois que a função é retornada.</span><span class="sxs-lookup"><span data-stu-id="c1ffe-109">Stepping continued normally, after the function returned.</span></span>|  
|`STEP_CALL`|<span data-ttu-id="c1ffe-110">A etapa continuou normalmente, no início de uma função chamada recentemente.</span><span class="sxs-lookup"><span data-stu-id="c1ffe-110">Stepping continued normally, at the beginning of a newly called function.</span></span>|  
|`STEP_EXCEPTION_FILTER`|<span data-ttu-id="c1ffe-111">Uma exceção foi gerada e o controle foi passado para um filtro de exceção.</span><span class="sxs-lookup"><span data-stu-id="c1ffe-111">An exception was generated and control was passed to an exception filter.</span></span>|  
|`STEP_EXCEPTION_HANDLER`|<span data-ttu-id="c1ffe-112">Uma exceção foi gerada e o controle foi passado para um manipulador de exceção.</span><span class="sxs-lookup"><span data-stu-id="c1ffe-112">An exception was generated and control was passed to an exception handler.</span></span>|  
|`STEP_INTERCEPT`|<span data-ttu-id="c1ffe-113">O controle foi passado para um interceptor.</span><span class="sxs-lookup"><span data-stu-id="c1ffe-113">Control was passed to an interceptor.</span></span>|  
|`STEP_EXIT`|<span data-ttu-id="c1ffe-114">O thread saiu antes da conclusão da etapa.</span><span class="sxs-lookup"><span data-stu-id="c1ffe-114">The thread exited before the step was completed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c1ffe-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c1ffe-115">Requirements</span></span>  
 <span data-ttu-id="c1ffe-116">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1ffe-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1ffe-117">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c1ffe-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c1ffe-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c1ffe-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c1ffe-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1ffe-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1ffe-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c1ffe-120">See also</span></span>

- [<span data-ttu-id="c1ffe-121">Método StepComplete</span><span class="sxs-lookup"><span data-stu-id="c1ffe-121">StepComplete Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md)
- [<span data-ttu-id="c1ffe-122">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="c1ffe-122">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
