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
ms.openlocfilehash: 2902744b6af3c7b2bd4def73b04807ce3333a8a1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131882"
---
# <a name="icordebugruntimeunwindableframe-interface"></a><span data-ttu-id="17bf9-102">Interface ICorDebugRuntimeUnwindableFrame</span><span class="sxs-lookup"><span data-stu-id="17bf9-102">ICorDebugRuntimeUnwindableFrame Interface</span></span>
<span data-ttu-id="17bf9-103">Fornece suporte para os métodos não gerenciados que exigem que o CLR (Common Language Runtime) desenrole um quadro.</span><span class="sxs-lookup"><span data-stu-id="17bf9-103">Provides support for unmanaged methods that require the common language runtime (CLR) to unwind a frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="17bf9-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="17bf9-104">Remarks</span></span>  
 <span data-ttu-id="17bf9-105">`ICorDebugRuntimeUnwindableFrame` é uma versão especializada da interface ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="17bf9-105">`ICorDebugRuntimeUnwindableFrame` is a specialized version of the ICorDebugFrame interface.</span></span> <span data-ttu-id="17bf9-106">Ele é usado por métodos não gerenciados que exigem o tempo de execução para desenrolar um quadro na pilha atual.</span><span class="sxs-lookup"><span data-stu-id="17bf9-106">It is used by unmanaged methods that require the runtime to unwind a frame on the current stack.</span></span> <span data-ttu-id="17bf9-107">As convenções de desenrolação existentes não funcionam, pois não usam código de compilação JIT.</span><span class="sxs-lookup"><span data-stu-id="17bf9-107">Existing unwinding conventions do not work, because they do not use JIT-compiled code.</span></span> <span data-ttu-id="17bf9-108">Quando o depurador vê um quadro não-envento, ele deve usar o método [ICorDebugStackWalk:: Next](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-next-method.md) para desenrolar, mas deve executar a inspeção em si.</span><span class="sxs-lookup"><span data-stu-id="17bf9-108">When the debugger sees an unwindable frame, it should use the [ICorDebugStackWalk::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-next-method.md) method to unwind it, but it should perform inspection itself.</span></span> <span data-ttu-id="17bf9-109">Quando o depurador recebe uma `ICorDebugRuntimeUnwindableFrame`, ele pode chamar o método [ICorDebugStackWalk:: GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) para recuperar o contexto do quadro.</span><span class="sxs-lookup"><span data-stu-id="17bf9-109">When the debugger receives an `ICorDebugRuntimeUnwindableFrame`, it can call the [ICorDebugStackWalk::GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) method to retrieve the context of the frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17bf9-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="17bf9-110">Requirements</span></span>  
 <span data-ttu-id="17bf9-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17bf9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17bf9-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="17bf9-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="17bf9-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="17bf9-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="17bf9-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17bf9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17bf9-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="17bf9-115">See also</span></span>

- [<span data-ttu-id="17bf9-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="17bf9-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="17bf9-117">Depuração</span><span class="sxs-lookup"><span data-stu-id="17bf9-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
