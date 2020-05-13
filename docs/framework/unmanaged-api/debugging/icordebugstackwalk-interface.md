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
ms.openlocfilehash: 5f71dfcdffaaa683ca4f2abebaa99115ef90e0ff
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378901"
---
# <a name="icordebugstackwalk-interface"></a><span data-ttu-id="65b3b-102">Interface ICorDebugStackWalk</span><span class="sxs-lookup"><span data-stu-id="65b3b-102">ICorDebugStackWalk Interface</span></span>
<span data-ttu-id="65b3b-103">Fornece métodos para colocar os métodos gerenciados, ou quadros, em uma pilha de thread.</span><span class="sxs-lookup"><span data-stu-id="65b3b-103">Provides methods for getting the managed methods, or frames, on a thread’s stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="65b3b-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="65b3b-104">Methods</span></span>  
  
|<span data-ttu-id="65b3b-105">Método</span><span class="sxs-lookup"><span data-stu-id="65b3b-105">Method</span></span>|<span data-ttu-id="65b3b-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="65b3b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="65b3b-107">Método GetContext</span><span class="sxs-lookup"><span data-stu-id="65b3b-107">GetContext Method</span></span>](icordebugstackwalk-getcontext-method.md)|<span data-ttu-id="65b3b-108">Retorna o contexto do quadro atual no `ICorDebugStackWalk` objeto.</span><span class="sxs-lookup"><span data-stu-id="65b3b-108">Returns the context for the current frame in the `ICorDebugStackWalk` object.</span></span>|  
|[<span data-ttu-id="65b3b-109">Método SetContext</span><span class="sxs-lookup"><span data-stu-id="65b3b-109">SetContext Method</span></span>](icordebugstackwalk-setcontext-method.md)|<span data-ttu-id="65b3b-110">Define o `ICorDebugStackWalk` contexto atual do objeto como um contexto válido para o thread.</span><span class="sxs-lookup"><span data-stu-id="65b3b-110">Sets the `ICorDebugStackWalk` object’s current context to a valid context for the thread.</span></span>|  
|[<span data-ttu-id="65b3b-111">Método Next</span><span class="sxs-lookup"><span data-stu-id="65b3b-111">Next Method</span></span>](icordebugstackwalk-next-method.md)|<span data-ttu-id="65b3b-112">Move o `ICorDebugStackWalk` objeto para o próximo quadro.</span><span class="sxs-lookup"><span data-stu-id="65b3b-112">Moves the `ICorDebugStackWalk` object to the next frame.</span></span>|  
|[<span data-ttu-id="65b3b-113">Método GetFrame</span><span class="sxs-lookup"><span data-stu-id="65b3b-113">GetFrame Method</span></span>](icordebugstackwalk-getframe-method.md)|<span data-ttu-id="65b3b-114">Obtém o quadro atual no `ICorDebugStackWalk` objeto.</span><span class="sxs-lookup"><span data-stu-id="65b3b-114">Gets the current frame in the `ICorDebugStackWalk` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="65b3b-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="65b3b-115">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="65b3b-116">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="65b3b-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65b3b-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="65b3b-117">Requirements</span></span>  
 <span data-ttu-id="65b3b-118">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65b3b-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65b3b-119">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="65b3b-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="65b3b-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="65b3b-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="65b3b-121">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65b3b-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65b3b-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="65b3b-122">See also</span></span>

- [<span data-ttu-id="65b3b-123">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="65b3b-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="65b3b-124">Depuração</span><span class="sxs-lookup"><span data-stu-id="65b3b-124">Debugging</span></span>](index.md)
