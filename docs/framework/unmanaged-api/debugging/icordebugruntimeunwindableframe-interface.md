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
ms.workload: dotnet
ms.openlocfilehash: 80b4212691784d88c92235a5c5c65acaee165201
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugruntimeunwindableframe-interface"></a><span data-ttu-id="be757-102">Interface ICorDebugRuntimeUnwindableFrame</span><span class="sxs-lookup"><span data-stu-id="be757-102">ICorDebugRuntimeUnwindableFrame Interface</span></span>
<span data-ttu-id="be757-103">Fornece suporte para os métodos não gerenciados que exigem que o CLR (Common Language Runtime) desenrole um quadro.</span><span class="sxs-lookup"><span data-stu-id="be757-103">Provides support for unmanaged methods that require the common language runtime (CLR) to unwind a frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="be757-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="be757-104">Remarks</span></span>  
 <span data-ttu-id="be757-105">`ICorDebugRuntimeUnwindableFrame`é uma versão especializada da interface ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="be757-105">`ICorDebugRuntimeUnwindableFrame` is a specialized version of the ICorDebugFrame interface.</span></span> <span data-ttu-id="be757-106">Ela é usada por métodos não gerenciados que exigem o tempo de execução desenrolar um quadro de pilha atual.</span><span class="sxs-lookup"><span data-stu-id="be757-106">It is used by unmanaged methods that require the runtime to unwind a frame on the current stack.</span></span> <span data-ttu-id="be757-107">Convenções de desenrolamento existentes não funcionará, porque eles não usam código com compilação JIT.</span><span class="sxs-lookup"><span data-stu-id="be757-107">Existing unwinding conventions do not work, because they do not use JIT-compiled code.</span></span> <span data-ttu-id="be757-108">Quando o depurador vê um quadro unwindable, ele deve usar o [Icordebugstackwalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-next-method.md) método de liberação, mas ele deve executar inspeção em si.</span><span class="sxs-lookup"><span data-stu-id="be757-108">When the debugger sees an unwindable frame, it should use the [ICorDebugStackWalk::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-next-method.md) method to unwind it, but it should perform inspection itself.</span></span> <span data-ttu-id="be757-109">Quando o depurador recebe um `ICorDebugRuntimeUnwindableFrame`, ele pode chamar o [Icordebugstackwalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) método para recuperar o contexto do quadro.</span><span class="sxs-lookup"><span data-stu-id="be757-109">When the debugger receives an `ICorDebugRuntimeUnwindableFrame`, it can call the [ICorDebugStackWalk::GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) method to retrieve the context of the frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be757-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="be757-110">Requirements</span></span>  
 <span data-ttu-id="be757-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be757-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be757-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="be757-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="be757-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="be757-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="be757-114">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be757-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be757-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="be757-115">See Also</span></span>  
 [<span data-ttu-id="be757-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="be757-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="be757-117">Depuração</span><span class="sxs-lookup"><span data-stu-id="be757-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
