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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3ce2b23306e7e38f3982f8d5a4b377aa2f9547c4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59186245"
---
# <a name="cordebugstepreason-enumeration"></a><span data-ttu-id="3845c-102">Enumeração CorDebugStepReason</span><span class="sxs-lookup"><span data-stu-id="3845c-102">CorDebugStepReason Enumeration</span></span>
<span data-ttu-id="3845c-103">Indica o resultado de uma etapa individual.</span><span class="sxs-lookup"><span data-stu-id="3845c-103">Indicates the outcome of an individual step.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3845c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3845c-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="3845c-105">Membros</span><span class="sxs-lookup"><span data-stu-id="3845c-105">Members</span></span>  
  
|<span data-ttu-id="3845c-106">Membro</span><span class="sxs-lookup"><span data-stu-id="3845c-106">Member</span></span>|<span data-ttu-id="3845c-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="3845c-107">Description</span></span>|  
|------------|-----------------|  
|`STEP_NORMAL`|<span data-ttu-id="3845c-108">Passo a passo concluída normalmente, dentro da mesma função.</span><span class="sxs-lookup"><span data-stu-id="3845c-108">Stepping completed normally, within the same function.</span></span>|  
|`STEP_RETURN`|<span data-ttu-id="3845c-109">Passo a passo continuação normalmente, depois que a função é retornado.</span><span class="sxs-lookup"><span data-stu-id="3845c-109">Stepping continued normally, after the function returned.</span></span>|  
|`STEP_CALL`|<span data-ttu-id="3845c-110">Passo a passo continuação normalmente, no início de uma função chamada recentemente.</span><span class="sxs-lookup"><span data-stu-id="3845c-110">Stepping continued normally, at the beginning of a newly called function.</span></span>|  
|`STEP_EXCEPTION_FILTER`|<span data-ttu-id="3845c-111">Uma exceção foi gerada e o controle foi passado para um filtro de exceção.</span><span class="sxs-lookup"><span data-stu-id="3845c-111">An exception was generated and control was passed to an exception filter.</span></span>|  
|`STEP_EXCEPTION_HANDLER`|<span data-ttu-id="3845c-112">Uma exceção foi gerada e o controle foi passado para um manipulador de exceção.</span><span class="sxs-lookup"><span data-stu-id="3845c-112">An exception was generated and control was passed to an exception handler.</span></span>|  
|`STEP_INTERCEPT`|<span data-ttu-id="3845c-113">Controle foi passado para um interceptador.</span><span class="sxs-lookup"><span data-stu-id="3845c-113">Control was passed to an interceptor.</span></span>|  
|`STEP_EXIT`|<span data-ttu-id="3845c-114">O thread foi encerrado antes que a etapa foi concluída.</span><span class="sxs-lookup"><span data-stu-id="3845c-114">The thread exited before the step was completed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3845c-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3845c-115">Requirements</span></span>  
 <span data-ttu-id="3845c-116">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3845c-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3845c-117">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3845c-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3845c-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3845c-118">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="3845c-119">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="3845c-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3845c-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3845c-120">See also</span></span>

- [<span data-ttu-id="3845c-121">Método StepComplete</span><span class="sxs-lookup"><span data-stu-id="3845c-121">StepComplete Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md)
- [<span data-ttu-id="3845c-122">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="3845c-122">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
