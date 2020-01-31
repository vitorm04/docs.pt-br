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
ms.openlocfilehash: 26b0c78d5b34b920decc8c549d90ba8147e3f323
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791916"
---
# <a name="icordebugruntimeunwindableframe-interface"></a><span data-ttu-id="f2ffb-102">Interface ICorDebugRuntimeUnwindableFrame</span><span class="sxs-lookup"><span data-stu-id="f2ffb-102">ICorDebugRuntimeUnwindableFrame Interface</span></span>
<span data-ttu-id="f2ffb-103">Fornece suporte para os métodos não gerenciados que exigem que o CLR (Common Language Runtime) desenrole um quadro.</span><span class="sxs-lookup"><span data-stu-id="f2ffb-103">Provides support for unmanaged methods that require the common language runtime (CLR) to unwind a frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f2ffb-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="f2ffb-104">Remarks</span></span>  
 <span data-ttu-id="f2ffb-105">`ICorDebugRuntimeUnwindableFrame` é uma versão especializada da interface ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="f2ffb-105">`ICorDebugRuntimeUnwindableFrame` is a specialized version of the ICorDebugFrame interface.</span></span> <span data-ttu-id="f2ffb-106">Ele é usado por métodos não gerenciados que exigem o tempo de execução para desenrolar um quadro na pilha atual.</span><span class="sxs-lookup"><span data-stu-id="f2ffb-106">It is used by unmanaged methods that require the runtime to unwind a frame on the current stack.</span></span> <span data-ttu-id="f2ffb-107">As convenções de desenrolação existentes não funcionam, pois não usam código de compilação JIT.</span><span class="sxs-lookup"><span data-stu-id="f2ffb-107">Existing unwinding conventions do not work, because they do not use JIT-compiled code.</span></span> <span data-ttu-id="f2ffb-108">Quando o depurador vê um quadro não-envento, ele deve usar o método [ICorDebugStackWalk:: Next](icordebugstackwalk-next-method.md) para desenrolar, mas deve executar a inspeção em si.</span><span class="sxs-lookup"><span data-stu-id="f2ffb-108">When the debugger sees an unwindable frame, it should use the [ICorDebugStackWalk::Next](icordebugstackwalk-next-method.md) method to unwind it, but it should perform inspection itself.</span></span> <span data-ttu-id="f2ffb-109">Quando o depurador recebe uma `ICorDebugRuntimeUnwindableFrame`, ele pode chamar o método [ICorDebugStackWalk:: GetContext](icordebugstackwalk-getcontext-method.md) para recuperar o contexto do quadro.</span><span class="sxs-lookup"><span data-stu-id="f2ffb-109">When the debugger receives an `ICorDebugRuntimeUnwindableFrame`, it can call the [ICorDebugStackWalk::GetContext](icordebugstackwalk-getcontext-method.md) method to retrieve the context of the frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2ffb-110">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="f2ffb-110">Requirements</span></span>  
 <span data-ttu-id="f2ffb-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2ffb-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2ffb-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f2ffb-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f2ffb-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f2ffb-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f2ffb-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2ffb-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2ffb-115">Veja também</span><span class="sxs-lookup"><span data-stu-id="f2ffb-115">See also</span></span>

- [<span data-ttu-id="f2ffb-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="f2ffb-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="f2ffb-117">Depuração</span><span class="sxs-lookup"><span data-stu-id="f2ffb-117">Debugging</span></span>](index.md)
