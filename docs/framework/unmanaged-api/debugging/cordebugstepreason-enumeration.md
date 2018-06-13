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
ms.openlocfilehash: 71dcc34fd3489fc71cec4050b168548927833082
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404525"
---
# <a name="cordebugstepreason-enumeration"></a><span data-ttu-id="fc518-102">Enumeração CorDebugStepReason</span><span class="sxs-lookup"><span data-stu-id="fc518-102">CorDebugStepReason Enumeration</span></span>
<span data-ttu-id="fc518-103">Indica o resultado de uma etapa individual.</span><span class="sxs-lookup"><span data-stu-id="fc518-103">Indicates the outcome of an individual step.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc518-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fc518-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="fc518-105">Membros</span><span class="sxs-lookup"><span data-stu-id="fc518-105">Members</span></span>  
  
|<span data-ttu-id="fc518-106">Membro</span><span class="sxs-lookup"><span data-stu-id="fc518-106">Member</span></span>|<span data-ttu-id="fc518-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="fc518-107">Description</span></span>|  
|------------|-----------------|  
|`STEP_NORMAL`|<span data-ttu-id="fc518-108">Passo a passo concluída normalmente, dentro da mesma função.</span><span class="sxs-lookup"><span data-stu-id="fc518-108">Stepping completed normally, within the same function.</span></span>|  
|`STEP_RETURN`|<span data-ttu-id="fc518-109">Passo a passo continuação normalmente, depois que a função retornou.</span><span class="sxs-lookup"><span data-stu-id="fc518-109">Stepping continued normally, after the function returned.</span></span>|  
|`STEP_CALL`|<span data-ttu-id="fc518-110">Passo a passo continuação normalmente, no início de uma função chamada recentemente.</span><span class="sxs-lookup"><span data-stu-id="fc518-110">Stepping continued normally, at the beginning of a newly called function.</span></span>|  
|`STEP_EXCEPTION_FILTER`|<span data-ttu-id="fc518-111">Uma exceção foi gerada e o controle foi passado para um filtro de exceção.</span><span class="sxs-lookup"><span data-stu-id="fc518-111">An exception was generated and control was passed to an exception filter.</span></span>|  
|`STEP_EXCEPTION_HANDLER`|<span data-ttu-id="fc518-112">Uma exceção foi gerada e o controle foi passado para um manipulador de exceção.</span><span class="sxs-lookup"><span data-stu-id="fc518-112">An exception was generated and control was passed to an exception handler.</span></span>|  
|`STEP_INTERCEPT`|<span data-ttu-id="fc518-113">Controle foi passado para um interceptador.</span><span class="sxs-lookup"><span data-stu-id="fc518-113">Control was passed to an interceptor.</span></span>|  
|`STEP_EXIT`|<span data-ttu-id="fc518-114">O thread foi encerrado antes que a etapa foi concluída.</span><span class="sxs-lookup"><span data-stu-id="fc518-114">The thread exited before the step was completed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fc518-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fc518-115">Requirements</span></span>  
 <span data-ttu-id="fc518-116">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc518-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc518-117">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fc518-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fc518-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fc518-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fc518-119">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc518-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc518-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fc518-120">See Also</span></span>  
 [<span data-ttu-id="fc518-121">Método StepComplete</span><span class="sxs-lookup"><span data-stu-id="fc518-121">StepComplete Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md)  
 [<span data-ttu-id="fc518-122">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="fc518-122">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
