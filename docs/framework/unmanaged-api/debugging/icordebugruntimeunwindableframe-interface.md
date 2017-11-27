---
title: Interface ICorDebugRuntimeUnwindableFrame
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugUnwindableFrame
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugUnwindableFrame
helpviewer_keywords: ICorDebugUnwindableFrame interface [.NET Framework debugging]
ms.assetid: cd6a3982-6ed3-4909-808d-a66055e813e0
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 003bbab399a9ad0ffe2f1d761aea18ff71ba1834
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugruntimeunwindableframe-interface"></a><span data-ttu-id="d44ee-102">Interface ICorDebugRuntimeUnwindableFrame</span><span class="sxs-lookup"><span data-stu-id="d44ee-102">ICorDebugRuntimeUnwindableFrame Interface</span></span>
<span data-ttu-id="d44ee-103">Fornece suporte para os métodos não gerenciados que exigem que o CLR (Common Language Runtime) desenrole um quadro.</span><span class="sxs-lookup"><span data-stu-id="d44ee-103">Provides support for unmanaged methods that require the common language runtime (CLR) to unwind a frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d44ee-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="d44ee-104">Remarks</span></span>  
 <span data-ttu-id="d44ee-105">`ICorDebugRuntimeUnwindableFrame`é uma versão especializada da interface ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="d44ee-105">`ICorDebugRuntimeUnwindableFrame` is a specialized version of the ICorDebugFrame interface.</span></span> <span data-ttu-id="d44ee-106">Ela é usada por métodos não gerenciados que exigem o tempo de execução desenrolar um quadro de pilha atual.</span><span class="sxs-lookup"><span data-stu-id="d44ee-106">It is used by unmanaged methods that require the runtime to unwind a frame on the current stack.</span></span> <span data-ttu-id="d44ee-107">Convenções de desenrolamento existentes não funcionará, porque eles não usam código com compilação JIT.</span><span class="sxs-lookup"><span data-stu-id="d44ee-107">Existing unwinding conventions do not work, because they do not use JIT-compiled code.</span></span> <span data-ttu-id="d44ee-108">Quando o depurador vê um quadro unwindable, ele deve usar o [Icordebugstackwalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-next-method.md) método de liberação, mas ele deve executar inspeção em si.</span><span class="sxs-lookup"><span data-stu-id="d44ee-108">When the debugger sees an unwindable frame, it should use the [ICorDebugStackWalk::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-next-method.md) method to unwind it, but it should perform inspection itself.</span></span> <span data-ttu-id="d44ee-109">Quando o depurador recebe um `ICorDebugRuntimeUnwindableFrame`, ele pode chamar o [Icordebugstackwalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) método para recuperar o contexto do quadro.</span><span class="sxs-lookup"><span data-stu-id="d44ee-109">When the debugger receives an `ICorDebugRuntimeUnwindableFrame`, it can call the [ICorDebugStackWalk::GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) method to retrieve the context of the frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d44ee-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d44ee-110">Requirements</span></span>  
 <span data-ttu-id="d44ee-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d44ee-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d44ee-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d44ee-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d44ee-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d44ee-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d44ee-114">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d44ee-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d44ee-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d44ee-115">See Also</span></span>  
 [<span data-ttu-id="d44ee-116">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="d44ee-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="d44ee-117">Depuração</span><span class="sxs-lookup"><span data-stu-id="d44ee-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
