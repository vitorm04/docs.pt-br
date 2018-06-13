---
title: Método ICorDebugStackWalk::Next
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.Next Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::Next
helpviewer_keywords:
- ICorDebugStackWalk::Next method [.NET Framework debugging]
- Next method, ICorDebugStackWalk interface [.NET Framework debugging]
ms.assetid: 189c36be-028c-4fba-a002-5edfb8fcd07f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 367c43dc08722288dc3b32b5133f7770ffc3a27c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423098"
---
# <a name="icordebugstackwalknext-method"></a><span data-ttu-id="fa905-102">Método ICorDebugStackWalk::Next</span><span class="sxs-lookup"><span data-stu-id="fa905-102">ICorDebugStackWalk::Next Method</span></span>
<span data-ttu-id="fa905-103">Move o [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) objeto para o próximo quadro.</span><span class="sxs-lookup"><span data-stu-id="fa905-103">Moves the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object to the next frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa905-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fa905-104">Syntax</span></span>  
  
```  
HRESULT Next();  
```  
  
## <a name="return-value"></a><span data-ttu-id="fa905-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="fa905-105">Return Value</span></span>  
 <span data-ttu-id="fa905-106">Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="fa905-106">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="fa905-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fa905-107">HRESULT</span></span>|<span data-ttu-id="fa905-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="fa905-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fa905-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="fa905-109">S_OK</span></span>|<span data-ttu-id="fa905-110">O tempo de execução retornou com êxito para o próximo quadro (consulte comentários).</span><span class="sxs-lookup"><span data-stu-id="fa905-110">The runtime successfully unwound to the next frame (see Remarks).</span></span>|  
|<span data-ttu-id="fa905-111">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fa905-111">E_FAIL</span></span>|<span data-ttu-id="fa905-112">O `ICorDebugStackWalk` objeto não pôde ser avançado.</span><span class="sxs-lookup"><span data-stu-id="fa905-112">The `ICorDebugStackWalk` object could not be advanced.</span></span>|  
|<span data-ttu-id="fa905-113">CORDBG_S_AT_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="fa905-113">CORDBG_S_AT_END_OF_STACK</span></span>|<span data-ttu-id="fa905-114">Foi atingido o fim da pilha como resultado dessa liberação.</span><span class="sxs-lookup"><span data-stu-id="fa905-114">The end of the stack was reached as a result of this unwind.</span></span>|  
|<span data-ttu-id="fa905-115">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="fa905-115">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="fa905-116">O ponteiro de quadro já está no final da pilha; Portanto, não há quadros adicionais podem ser acessados.</span><span class="sxs-lookup"><span data-stu-id="fa905-116">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="fa905-117">Exceções</span><span class="sxs-lookup"><span data-stu-id="fa905-117">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fa905-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="fa905-118">Remarks</span></span>  
 <span data-ttu-id="fa905-119">O `Next` método avanços o `ICorDebugStackWalk` do objeto para o quadro chamado somente se o tempo de execução pode desenrolar o quadro atual.</span><span class="sxs-lookup"><span data-stu-id="fa905-119">The `Next` method advances the `ICorDebugStackWalk` object to the calling frame only if the runtime can unwind the current frame.</span></span> <span data-ttu-id="fa905-120">Caso contrário, o objeto avança para o próximo quadro que o tempo de execução é capaz de desenrolamento.</span><span class="sxs-lookup"><span data-stu-id="fa905-120">Otherwise, the object advances to the next frame that the runtime is able to unwind.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa905-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fa905-121">Requirements</span></span>  
 <span data-ttu-id="fa905-122">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa905-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa905-123">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fa905-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fa905-124">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fa905-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fa905-125">**Versões do .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa905-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa905-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fa905-126">See Also</span></span>  
 [<span data-ttu-id="fa905-127">Interface ICorDebugStackWalk</span><span class="sxs-lookup"><span data-stu-id="fa905-127">ICorDebugStackWalk Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)  
 [<span data-ttu-id="fa905-128">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="fa905-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="fa905-129">Depuração</span><span class="sxs-lookup"><span data-stu-id="fa905-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
