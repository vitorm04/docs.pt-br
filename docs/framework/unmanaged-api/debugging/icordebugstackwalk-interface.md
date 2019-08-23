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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 06ce2da435df9458ca59d76fa426becbede2e619
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959669"
---
# <a name="icordebugstackwalk-interface"></a><span data-ttu-id="30410-102">Interface ICorDebugStackWalk</span><span class="sxs-lookup"><span data-stu-id="30410-102">ICorDebugStackWalk Interface</span></span>
<span data-ttu-id="30410-103">Fornece métodos para colocar os métodos gerenciados, ou quadros, em uma pilha de thread.</span><span class="sxs-lookup"><span data-stu-id="30410-103">Provides methods for getting the managed methods, or frames, on a thread’s stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="30410-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="30410-104">Methods</span></span>  
  
|<span data-ttu-id="30410-105">Método</span><span class="sxs-lookup"><span data-stu-id="30410-105">Method</span></span>|<span data-ttu-id="30410-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="30410-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="30410-107">Método GetContext</span><span class="sxs-lookup"><span data-stu-id="30410-107">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md)|<span data-ttu-id="30410-108">Retorna o contexto do quadro atual no `ICorDebugStackWalk` objeto.</span><span class="sxs-lookup"><span data-stu-id="30410-108">Returns the context for the current frame in the `ICorDebugStackWalk` object.</span></span>|  
|[<span data-ttu-id="30410-109">Método SetContext</span><span class="sxs-lookup"><span data-stu-id="30410-109">SetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-setcontext-method.md)|<span data-ttu-id="30410-110">Define o `ICorDebugStackWalk` contexto atual do objeto como um contexto válido para o thread.</span><span class="sxs-lookup"><span data-stu-id="30410-110">Sets the `ICorDebugStackWalk` object’s current context to a valid context for the thread.</span></span>|  
|[<span data-ttu-id="30410-111">Método Next</span><span class="sxs-lookup"><span data-stu-id="30410-111">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-next-method.md)|<span data-ttu-id="30410-112">Move o `ICorDebugStackWalk` objeto para o próximo quadro.</span><span class="sxs-lookup"><span data-stu-id="30410-112">Moves the `ICorDebugStackWalk` object to the next frame.</span></span>|  
|[<span data-ttu-id="30410-113">Método GetFrame</span><span class="sxs-lookup"><span data-stu-id="30410-113">GetFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getframe-method.md)|<span data-ttu-id="30410-114">Obtém o quadro atual no `ICorDebugStackWalk` objeto.</span><span class="sxs-lookup"><span data-stu-id="30410-114">Gets the current frame in the `ICorDebugStackWalk` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="30410-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="30410-115">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="30410-116">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="30410-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30410-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="30410-117">Requirements</span></span>  
 <span data-ttu-id="30410-118">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30410-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30410-119">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="30410-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="30410-120">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="30410-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="30410-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30410-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30410-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30410-122">See also</span></span>

- [<span data-ttu-id="30410-123">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="30410-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="30410-124">Depuração</span><span class="sxs-lookup"><span data-stu-id="30410-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
