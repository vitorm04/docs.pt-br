---
title: Enumeração CorDebugIntercept
ms.date: 03/30/2017
api_name:
- CorDebugIntercept
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugIntercept
helpviewer_keywords:
- CorDebugIntercept enumeration [.NET Framework debugging]
ms.assetid: 3d5b642e-7ef2-428b-a5ae-509c35ed461a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0791a59e0325668960dcfc98816920db55bcfb87
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59199928"
---
# <a name="cordebugintercept-enumeration"></a><span data-ttu-id="58157-102">Enumeração CorDebugIntercept</span><span class="sxs-lookup"><span data-stu-id="58157-102">CorDebugIntercept Enumeration</span></span>
<span data-ttu-id="58157-103">Indica os tipos de código que podem ser interceptadas (isto é, entrados).</span><span class="sxs-lookup"><span data-stu-id="58157-103">Indicates the types of code that can be intercepted (that is, stepped into).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58157-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="58157-104">Syntax</span></span>  
  
```  
typedef enum CorDebugIntercept {  
    INTERCEPT_NONE                = 0x0,  
    INTERCEPT_CLASS_INIT          = 0x01,  
    INTERCEPT_EXCEPTION_FILTER    = 0x02,  
    INTERCEPT_SECURITY            = 0x04,  
    INTERCEPT_CONTEXT_POLICY      = 0x08,  
    INTERCEPT_INTERCEPTION        = 0x10,  
    INTERCEPT_ALL                 = 0xffff  
} CorDebugIntercept;  
```  
  
## <a name="members"></a><span data-ttu-id="58157-105">Membros</span><span class="sxs-lookup"><span data-stu-id="58157-105">Members</span></span>  
  
|<span data-ttu-id="58157-106">Membro</span><span class="sxs-lookup"><span data-stu-id="58157-106">Member</span></span>|<span data-ttu-id="58157-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="58157-107">Description</span></span>|  
|------------|-----------------|  
|`INTERCEPT_NONE`|<span data-ttu-id="58157-108">Nenhum código pode ser interceptado.</span><span class="sxs-lookup"><span data-stu-id="58157-108">No code can be intercepted.</span></span>|  
|`INTERCEPT_CLASS_INIT`|<span data-ttu-id="58157-109">Um construtor pode ser interceptado.</span><span class="sxs-lookup"><span data-stu-id="58157-109">A constructor can be intercepted.</span></span>|  
|`INTERCEPT_EXCEPTION_FILTER`|<span data-ttu-id="58157-110">Um filtro de exceção pode ser interceptado.</span><span class="sxs-lookup"><span data-stu-id="58157-110">An exception filter can be intercepted.</span></span>|  
|`INTERCEPT_SECURITY`|<span data-ttu-id="58157-111">Código que impõe a segurança pode ser interceptado.</span><span class="sxs-lookup"><span data-stu-id="58157-111">Code that enforces security can be intercepted.</span></span>|  
|`INTERCEPT_CONTEXT_POLICY`|<span data-ttu-id="58157-112">Uma política de contexto pode ser interceptada.</span><span class="sxs-lookup"><span data-stu-id="58157-112">A context policy can be intercepted.</span></span>|  
|`INTERCEPT_INTERCEPTION`|<span data-ttu-id="58157-113">Não usado.</span><span class="sxs-lookup"><span data-stu-id="58157-113">Not used.</span></span>|  
|`INTERCEPT_ALL`|<span data-ttu-id="58157-114">Todos os códigos podem ser interceptados.</span><span class="sxs-lookup"><span data-stu-id="58157-114">All code can be intercepted.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="58157-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="58157-115">Remarks</span></span>  
 <span data-ttu-id="58157-116">Use o [ICorDebugStepper:: Setinterceptmask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setinterceptmask-method.md) método para estabelecer os tipos de código que podem ser interceptadas.</span><span class="sxs-lookup"><span data-stu-id="58157-116">Use the [ICorDebugStepper::SetInterceptMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setinterceptmask-method.md) method to establish the types of code that can be intercepted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58157-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="58157-117">Requirements</span></span>  
 <span data-ttu-id="58157-118">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58157-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58157-119">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="58157-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="58157-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="58157-120">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="58157-121">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="58157-121">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="58157-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="58157-122">See also</span></span>

- [<span data-ttu-id="58157-123">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="58157-123">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
