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
ms.openlocfilehash: a7b0608e85411844828cebea34c0ce5ef5b1bd11
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379381"
---
# <a name="icordebugruntimeunwindableframe-interface"></a><span data-ttu-id="969d1-102">Interface ICorDebugRuntimeUnwindableFrame</span><span class="sxs-lookup"><span data-stu-id="969d1-102">ICorDebugRuntimeUnwindableFrame Interface</span></span>
<span data-ttu-id="969d1-103">Fornece suporte para os métodos não gerenciados que exigem que o CLR (Common Language Runtime) desenrole um quadro.</span><span class="sxs-lookup"><span data-stu-id="969d1-103">Provides support for unmanaged methods that require the common language runtime (CLR) to unwind a frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="969d1-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="969d1-104">Remarks</span></span>  
 <span data-ttu-id="969d1-105">`ICorDebugRuntimeUnwindableFrame`é uma versão especializada da interface ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="969d1-105">`ICorDebugRuntimeUnwindableFrame` is a specialized version of the ICorDebugFrame interface.</span></span> <span data-ttu-id="969d1-106">Ele é usado por métodos não gerenciados que exigem o tempo de execução para desenrolar um quadro na pilha atual.</span><span class="sxs-lookup"><span data-stu-id="969d1-106">It is used by unmanaged methods that require the runtime to unwind a frame on the current stack.</span></span> <span data-ttu-id="969d1-107">As convenções de desenrolação existentes não funcionam, pois não usam código de compilação JIT.</span><span class="sxs-lookup"><span data-stu-id="969d1-107">Existing unwinding conventions do not work, because they do not use JIT-compiled code.</span></span> <span data-ttu-id="969d1-108">Quando o depurador vê um quadro não-envento, ele deve usar o método [ICorDebugStackWalk:: Next](icordebugstackwalk-next-method.md) para desenrolar, mas deve executar a inspeção em si.</span><span class="sxs-lookup"><span data-stu-id="969d1-108">When the debugger sees an unwindable frame, it should use the [ICorDebugStackWalk::Next](icordebugstackwalk-next-method.md) method to unwind it, but it should perform inspection itself.</span></span> <span data-ttu-id="969d1-109">Quando o depurador recebe um `ICorDebugRuntimeUnwindableFrame` , ele pode chamar o método [ICorDebugStackWalk:: GetContext](icordebugstackwalk-getcontext-method.md) para recuperar o contexto do quadro.</span><span class="sxs-lookup"><span data-stu-id="969d1-109">When the debugger receives an `ICorDebugRuntimeUnwindableFrame`, it can call the [ICorDebugStackWalk::GetContext](icordebugstackwalk-getcontext-method.md) method to retrieve the context of the frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="969d1-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="969d1-110">Requirements</span></span>  
 <span data-ttu-id="969d1-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="969d1-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="969d1-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="969d1-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="969d1-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="969d1-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="969d1-114">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="969d1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="969d1-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="969d1-115">See also</span></span>

- [<span data-ttu-id="969d1-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="969d1-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="969d1-117">Depuração</span><span class="sxs-lookup"><span data-stu-id="969d1-117">Debugging</span></span>](index.md)
