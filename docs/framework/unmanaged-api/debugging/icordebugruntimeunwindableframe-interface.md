---
title: Interface ICorDebugRuntimeUnwindableFrame
ms.date: 03/30/2017
api_name:
- ICorDebugUnwindableFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugUnwindableFrame
helpviewer_keywords:
- ICorDebugUnwindableFrame interface [.NET Framework debugging]
ms.assetid: cd6a3982-6ed3-4909-808d-a66055e813e0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bf6bc73683a6c37ceaaffc635a58803b71c3b6cd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59134193"
---
# <a name="icordebugruntimeunwindableframe-interface"></a><span data-ttu-id="88819-102">Interface ICorDebugRuntimeUnwindableFrame</span><span class="sxs-lookup"><span data-stu-id="88819-102">ICorDebugRuntimeUnwindableFrame Interface</span></span>
<span data-ttu-id="88819-103">Fornece suporte para os métodos não gerenciados que exigem que o CLR (Common Language Runtime) desenrole um quadro.</span><span class="sxs-lookup"><span data-stu-id="88819-103">Provides support for unmanaged methods that require the common language runtime (CLR) to unwind a frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="88819-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="88819-104">Remarks</span></span>  
 <span data-ttu-id="88819-105">`ICorDebugRuntimeUnwindableFrame` é uma versão especializada da interface ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="88819-105">`ICorDebugRuntimeUnwindableFrame` is a specialized version of the ICorDebugFrame interface.</span></span> <span data-ttu-id="88819-106">Ele é usado por métodos não gerenciados que exigem o tempo de execução desenrole um quadro na pilha atual.</span><span class="sxs-lookup"><span data-stu-id="88819-106">It is used by unmanaged methods that require the runtime to unwind a frame on the current stack.</span></span> <span data-ttu-id="88819-107">Convenções de desenrolamento existentes não funcionam, porque eles não usam código compilado por JIT.</span><span class="sxs-lookup"><span data-stu-id="88819-107">Existing unwinding conventions do not work, because they do not use JIT-compiled code.</span></span> <span data-ttu-id="88819-108">Quando o depurador considera um quadro liberáveis, ele deve usar o [icordebugstackwalk:: Next](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-next-method.md) método desenrolar ele, mas ele deve executar a inspeção em si.</span><span class="sxs-lookup"><span data-stu-id="88819-108">When the debugger sees an unwindable frame, it should use the [ICorDebugStackWalk::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-next-method.md) method to unwind it, but it should perform inspection itself.</span></span> <span data-ttu-id="88819-109">Quando o depurador recebe uma `ICorDebugRuntimeUnwindableFrame`, ele chamará o [icordebugstackwalk:: GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) método para recuperar o contexto do quadro.</span><span class="sxs-lookup"><span data-stu-id="88819-109">When the debugger receives an `ICorDebugRuntimeUnwindableFrame`, it can call the [ICorDebugStackWalk::GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) method to retrieve the context of the frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88819-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="88819-110">Requirements</span></span>  
 <span data-ttu-id="88819-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88819-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88819-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="88819-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="88819-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="88819-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="88819-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88819-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88819-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="88819-115">See also</span></span>

- [<span data-ttu-id="88819-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="88819-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="88819-117">Depuração</span><span class="sxs-lookup"><span data-stu-id="88819-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
