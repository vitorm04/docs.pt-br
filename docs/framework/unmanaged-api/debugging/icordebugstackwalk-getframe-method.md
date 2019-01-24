---
title: Método ICorDebugStackWalk::GetFrame
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.GetFrame Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::GetFrame
helpviewer_keywords:
- GetFrame method [.NET Framework debugging]
- ICorDebugStackWalk::GetFrame method [.NET Framework debugging]
ms.assetid: 4083b505-5b59-44fb-8c5d-129db6a96c10
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 09a5d44e2f09c0a9ad87d590bb6d7330241143ce
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54666235"
---
# <a name="icordebugstackwalkgetframe-method"></a><span data-ttu-id="26f1c-102">Método ICorDebugStackWalk::GetFrame</span><span class="sxs-lookup"><span data-stu-id="26f1c-102">ICorDebugStackWalk::GetFrame Method</span></span>
<span data-ttu-id="26f1c-103">Obtém o quadro atual na [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) objeto.</span><span class="sxs-lookup"><span data-stu-id="26f1c-103">Gets the current frame in the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26f1c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="26f1c-104">Syntax</span></span>  
  
```  
HRESULT GetFrame([out] ICorDebugFrame ** pFrame);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="26f1c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="26f1c-105">Parameters</span></span>  
 `pFrame`  
 <span data-ttu-id="26f1c-106">[in] Um ponteiro para o endereço do objeto criado do quadro que representa o quadro atual na pilha.</span><span class="sxs-lookup"><span data-stu-id="26f1c-106">[in] A pointer to the address of the created frame object that represents the current frame in the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="26f1c-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="26f1c-107">Return Value</span></span>  
 <span data-ttu-id="26f1c-108">Esse método retorna os HRESULTs específicos a seguir, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="26f1c-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="26f1c-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="26f1c-109">HRESULT</span></span>|<span data-ttu-id="26f1c-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="26f1c-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="26f1c-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="26f1c-111">S_OK</span></span>|<span data-ttu-id="26f1c-112">O tempo de execução retornado com êxito o quadro atual.</span><span class="sxs-lookup"><span data-stu-id="26f1c-112">The runtime successfully returned the current frame.</span></span>|  
|<span data-ttu-id="26f1c-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="26f1c-113">E_FAIL</span></span>|<span data-ttu-id="26f1c-114">O quadro atual não foi retornado.</span><span class="sxs-lookup"><span data-stu-id="26f1c-114">The current frame was not returned.</span></span>|  
|<span data-ttu-id="26f1c-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="26f1c-115">S_FALSE</span></span>|<span data-ttu-id="26f1c-116">O quadro atual é um quadro de pilha nativo.</span><span class="sxs-lookup"><span data-stu-id="26f1c-116">The current frame is a native stack frame.</span></span>|  
|<span data-ttu-id="26f1c-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="26f1c-117">E_INVALIDARG</span></span>|<span data-ttu-id="26f1c-118">`pFrame` é nulo.</span><span class="sxs-lookup"><span data-stu-id="26f1c-118">`pFrame` is null.</span></span>|  
|<span data-ttu-id="26f1c-119">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="26f1c-119">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="26f1c-120">O ponteiro de quadro já está no final da pilha; Portanto, não há quadros adicionais podem ser acessados.</span><span class="sxs-lookup"><span data-stu-id="26f1c-120">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="26f1c-121">Exceções</span><span class="sxs-lookup"><span data-stu-id="26f1c-121">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="26f1c-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="26f1c-122">Remarks</span></span>  
 <span data-ttu-id="26f1c-123">`ICorDebugStackWalk` Retorna somente os quadros de pilha real.</span><span class="sxs-lookup"><span data-stu-id="26f1c-123">`ICorDebugStackWalk` returns only actual stack frames.</span></span> <span data-ttu-id="26f1c-124">Use o [ICorDebugThread3::GetActiveInternalFrames](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md) método para retornar os quadros internos.</span><span class="sxs-lookup"><span data-stu-id="26f1c-124">Use the [ICorDebugThread3::GetActiveInternalFrames](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md) method to return internal frames.</span></span> <span data-ttu-id="26f1c-125">(Quadros internos são colocadas na pilha em tempo de execução para armazenar dados temporários de estruturas de dados).</span><span class="sxs-lookup"><span data-stu-id="26f1c-125">(Internal frames are data structures pushed onto the stack by the runtime to store temporary data.)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26f1c-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="26f1c-126">Requirements</span></span>  
 <span data-ttu-id="26f1c-127">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26f1c-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26f1c-128">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="26f1c-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="26f1c-129">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="26f1c-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="26f1c-130">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26f1c-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26f1c-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="26f1c-131">See also</span></span>
- [<span data-ttu-id="26f1c-132">Interface ICorDebugStackWalk</span><span class="sxs-lookup"><span data-stu-id="26f1c-132">ICorDebugStackWalk Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)
- [<span data-ttu-id="26f1c-133">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="26f1c-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="26f1c-134">Depuração</span><span class="sxs-lookup"><span data-stu-id="26f1c-134">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
