---
title: Interface ICorDebugStackWalk
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk
helpviewer_keywords:
- ICorDebugStackWalk interface [.NET Framework debugging]
ms.assetid: 16d695e8-975d-431b-8421-e9e6c3e3f476
topic_type:
- apiref
ms.openlocfilehash: a6283d699263dc9b79e457010f31923f77443129
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791886"
---
# <a name="icordebugstackwalk-interface"></a><span data-ttu-id="9faf0-102">Interface ICorDebugStackWalk</span><span class="sxs-lookup"><span data-stu-id="9faf0-102">ICorDebugStackWalk Interface</span></span>
<span data-ttu-id="9faf0-103">Fornece métodos para colocar os métodos gerenciados, ou quadros, em uma pilha de thread.</span><span class="sxs-lookup"><span data-stu-id="9faf0-103">Provides methods for getting the managed methods, or frames, on a thread’s stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9faf0-104">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="9faf0-104">Methods</span></span>  
  
|<span data-ttu-id="9faf0-105">Método</span><span class="sxs-lookup"><span data-stu-id="9faf0-105">Method</span></span>|<span data-ttu-id="9faf0-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="9faf0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9faf0-107">Método GetContext</span><span class="sxs-lookup"><span data-stu-id="9faf0-107">GetContext Method</span></span>](icordebugstackwalk-getcontext-method.md)|<span data-ttu-id="9faf0-108">Retorna o contexto para o quadro atual no objeto `ICorDebugStackWalk`.</span><span class="sxs-lookup"><span data-stu-id="9faf0-108">Returns the context for the current frame in the `ICorDebugStackWalk` object.</span></span>|  
|[<span data-ttu-id="9faf0-109">Método SetContext</span><span class="sxs-lookup"><span data-stu-id="9faf0-109">SetContext Method</span></span>](icordebugstackwalk-setcontext-method.md)|<span data-ttu-id="9faf0-110">Define o contexto atual do objeto de `ICorDebugStackWalk` como um contexto válido para o thread.</span><span class="sxs-lookup"><span data-stu-id="9faf0-110">Sets the `ICorDebugStackWalk` object’s current context to a valid context for the thread.</span></span>|  
|[<span data-ttu-id="9faf0-111">Método Next</span><span class="sxs-lookup"><span data-stu-id="9faf0-111">Next Method</span></span>](icordebugstackwalk-next-method.md)|<span data-ttu-id="9faf0-112">Move o objeto `ICorDebugStackWalk` para o próximo quadro.</span><span class="sxs-lookup"><span data-stu-id="9faf0-112">Moves the `ICorDebugStackWalk` object to the next frame.</span></span>|  
|[<span data-ttu-id="9faf0-113">Método GetFrame</span><span class="sxs-lookup"><span data-stu-id="9faf0-113">GetFrame Method</span></span>](icordebugstackwalk-getframe-method.md)|<span data-ttu-id="9faf0-114">Obtém o quadro atual no objeto `ICorDebugStackWalk`.</span><span class="sxs-lookup"><span data-stu-id="9faf0-114">Gets the current frame in the `ICorDebugStackWalk` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9faf0-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="9faf0-115">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9faf0-116">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="9faf0-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9faf0-117">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="9faf0-117">Requirements</span></span>  
 <span data-ttu-id="9faf0-118">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9faf0-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9faf0-119">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9faf0-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9faf0-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9faf0-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9faf0-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9faf0-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9faf0-122">Veja também</span><span class="sxs-lookup"><span data-stu-id="9faf0-122">See also</span></span>

- [<span data-ttu-id="9faf0-123">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="9faf0-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="9faf0-124">Depuração</span><span class="sxs-lookup"><span data-stu-id="9faf0-124">Debugging</span></span>](index.md)
