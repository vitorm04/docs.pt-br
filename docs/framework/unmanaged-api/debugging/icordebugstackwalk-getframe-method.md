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
ms.openlocfilehash: 77210edfdc954f38ff06bc43a8b41a6abe8dc3d6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131833"
---
# <a name="icordebugstackwalkgetframe-method"></a><span data-ttu-id="16680-102">Método ICorDebugStackWalk::GetFrame</span><span class="sxs-lookup"><span data-stu-id="16680-102">ICorDebugStackWalk::GetFrame Method</span></span>
<span data-ttu-id="16680-103">Obtém o quadro atual no objeto [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="16680-103">Gets the current frame in the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16680-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="16680-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFrame([out] ICorDebugFrame ** pFrame);  
```  
  
## <a name="parameters"></a><span data-ttu-id="16680-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="16680-105">Parameters</span></span>  
 `pFrame`  
 <span data-ttu-id="16680-106">no Um ponteiro para o endereço do objeto frame criado que representa o quadro atual na pilha.</span><span class="sxs-lookup"><span data-stu-id="16680-106">[in] A pointer to the address of the created frame object that represents the current frame in the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="16680-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="16680-107">Return Value</span></span>  
 <span data-ttu-id="16680-108">Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.</span><span class="sxs-lookup"><span data-stu-id="16680-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="16680-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="16680-109">HRESULT</span></span>|<span data-ttu-id="16680-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="16680-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="16680-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="16680-111">S_OK</span></span>|<span data-ttu-id="16680-112">O tempo de execução retornou com êxito o quadro atual.</span><span class="sxs-lookup"><span data-stu-id="16680-112">The runtime successfully returned the current frame.</span></span>|  
|<span data-ttu-id="16680-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="16680-113">E_FAIL</span></span>|<span data-ttu-id="16680-114">O quadro atual não foi retornado.</span><span class="sxs-lookup"><span data-stu-id="16680-114">The current frame was not returned.</span></span>|  
|<span data-ttu-id="16680-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="16680-115">S_FALSE</span></span>|<span data-ttu-id="16680-116">O quadro atual é um quadro de ativação nativo.</span><span class="sxs-lookup"><span data-stu-id="16680-116">The current frame is a native stack frame.</span></span>|  
|<span data-ttu-id="16680-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="16680-117">E_INVALIDARG</span></span>|<span data-ttu-id="16680-118">`pFrame` é nulo.</span><span class="sxs-lookup"><span data-stu-id="16680-118">`pFrame` is null.</span></span>|  
|<span data-ttu-id="16680-119">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="16680-119">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="16680-120">O ponteiro de quadro já está no final da pilha; Portanto, nenhum quadro adicional pode ser acessado.</span><span class="sxs-lookup"><span data-stu-id="16680-120">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="16680-121">Exceções</span><span class="sxs-lookup"><span data-stu-id="16680-121">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="16680-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="16680-122">Remarks</span></span>  
 <span data-ttu-id="16680-123">`ICorDebugStackWalk` retorna apenas os quadros de pilhas reais.</span><span class="sxs-lookup"><span data-stu-id="16680-123">`ICorDebugStackWalk` returns only actual stack frames.</span></span> <span data-ttu-id="16680-124">Use o método [ICorDebugThread3:: GetActiveInternalFrames](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md) para retornar quadros internos.</span><span class="sxs-lookup"><span data-stu-id="16680-124">Use the [ICorDebugThread3::GetActiveInternalFrames](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md) method to return internal frames.</span></span> <span data-ttu-id="16680-125">(Os quadros internos são estruturas de dados enviadas por push para a pilha pelo tempo de execução para armazenar dados temporários.)</span><span class="sxs-lookup"><span data-stu-id="16680-125">(Internal frames are data structures pushed onto the stack by the runtime to store temporary data.)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16680-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="16680-126">Requirements</span></span>  
 <span data-ttu-id="16680-127">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16680-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16680-128">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="16680-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="16680-129">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="16680-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="16680-130">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16680-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16680-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="16680-131">See also</span></span>

- [<span data-ttu-id="16680-132">Interface ICorDebugStackWalk</span><span class="sxs-lookup"><span data-stu-id="16680-132">ICorDebugStackWalk Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)
- [<span data-ttu-id="16680-133">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="16680-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="16680-134">Depuração</span><span class="sxs-lookup"><span data-stu-id="16680-134">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
