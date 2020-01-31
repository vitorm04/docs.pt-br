---
title: Método ICorDebugStackWalk::SetContext
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.SetContext Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::SetContext
helpviewer_keywords:
- SetContext method [.NET Framework debugging]
- ICorDebugStackWalk::SetContext method [.NET Framework debugging]
ms.assetid: bac0b156-31a3-4e7f-be4d-ab21789c81f1
topic_type:
- apiref
ms.openlocfilehash: 23ad8882ad97e5ceaeb690dfae08a6be55b85f64
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791852"
---
# <a name="icordebugstackwalksetcontext-method"></a><span data-ttu-id="9b95b-102">Método ICorDebugStackWalk::SetContext</span><span class="sxs-lookup"><span data-stu-id="9b95b-102">ICorDebugStackWalk::SetContext Method</span></span>
<span data-ttu-id="9b95b-103">Define o contexto atual do objeto [ICorDebugStackWalk](icordebugstackwalk-interface.md) como um contexto válido para o thread.</span><span class="sxs-lookup"><span data-stu-id="9b95b-103">Sets the [ICorDebugStackWalk](icordebugstackwalk-interface.md) object’s current context to a valid context for the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b95b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9b95b-104">Syntax</span></span>  
  
```cpp  
HRESULT SetContext([in] CorDebugSetContextFlag flag,  
                   [in] ULONG32 contextSize,  
                   [in, size_is(contextSize)] BYTE context[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9b95b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9b95b-105">Parameters</span></span>  
 `flag`  
 <span data-ttu-id="9b95b-106">no Um sinalizador [CorDebugSetContextFlag](cordebugsetcontextflag-enumeration.md) que indica se o contexto é do quadro ativo na pilha ou um contexto obtido com o desenrolamento da pilha.</span><span class="sxs-lookup"><span data-stu-id="9b95b-106">[in] A [CorDebugSetContextFlag](cordebugsetcontextflag-enumeration.md) flag that indicates whether the context is from the active frame on the stack, or a context obtained by unwinding the stack.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="9b95b-107">no O tamanho alocado do buffer de `CONTEXT`.</span><span class="sxs-lookup"><span data-stu-id="9b95b-107">[in] The allocated size of the `CONTEXT` buffer.</span></span>  
  
 `context`  
 <span data-ttu-id="9b95b-108">no O buffer de `CONTEXT`.</span><span class="sxs-lookup"><span data-stu-id="9b95b-108">[in] The `CONTEXT` buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9b95b-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="9b95b-109">Return Value</span></span>  
 <span data-ttu-id="9b95b-110">Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.</span><span class="sxs-lookup"><span data-stu-id="9b95b-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="9b95b-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9b95b-111">HRESULT</span></span>|<span data-ttu-id="9b95b-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="9b95b-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9b95b-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="9b95b-113">S_OK</span></span>|<span data-ttu-id="9b95b-114">O contexto do objeto de `ICorDebugStackWalk` foi definido com êxito.</span><span class="sxs-lookup"><span data-stu-id="9b95b-114">The `ICorDebugStackWalk` object's context was successfully set.</span></span>|  
|<span data-ttu-id="9b95b-115">{1&gt;E_FAIL&lt;1}</span><span class="sxs-lookup"><span data-stu-id="9b95b-115">E_FAIL</span></span>|<span data-ttu-id="9b95b-116">O contexto do objeto de `ICorDebugStackWalk` não foi definido.</span><span class="sxs-lookup"><span data-stu-id="9b95b-116">The `ICorDebugStackWalk` object's context was not set.</span></span>|  
|<span data-ttu-id="9b95b-117">{1&gt;E_INVALIDARG&lt;1}</span><span class="sxs-lookup"><span data-stu-id="9b95b-117">E_INVALIDARG</span></span>|<span data-ttu-id="9b95b-118">O contexto é nulo.</span><span class="sxs-lookup"><span data-stu-id="9b95b-118">The context is null.</span></span>|  
|<span data-ttu-id="9b95b-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="9b95b-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>|<span data-ttu-id="9b95b-120">O buffer de contexto é muito pequeno.</span><span class="sxs-lookup"><span data-stu-id="9b95b-120">The context buffer is too small.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="9b95b-121">Exceções</span><span class="sxs-lookup"><span data-stu-id="9b95b-121">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9b95b-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="9b95b-122">Remarks</span></span>  
 <span data-ttu-id="9b95b-123">Esse método não altera o contexto atual do thread.</span><span class="sxs-lookup"><span data-stu-id="9b95b-123">This method does not alter the current context of the thread.</span></span>  
  
 <span data-ttu-id="9b95b-124">A definição do contexto atual como um contexto inválido pode causar resultados imprevisíveis do Stack Walker.</span><span class="sxs-lookup"><span data-stu-id="9b95b-124">Setting the current context to an invalid context may cause unpredictable results from the stack walker.</span></span>  
  
 <span data-ttu-id="9b95b-125">Você pode recuperar uma cópia de bit exata desse contexto chamando imediatamente o método [ICorDebugStackWalk:: GetContext](icordebugstackwalk-getcontext-method.md) .</span><span class="sxs-lookup"><span data-stu-id="9b95b-125">You can retrieve an exact bitwise copy of this context by immediately calling the [ICorDebugStackWalk::GetContext](icordebugstackwalk-getcontext-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b95b-126">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="9b95b-126">Requirements</span></span>  
 <span data-ttu-id="9b95b-127">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b95b-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b95b-128">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9b95b-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9b95b-129">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9b95b-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9b95b-130">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b95b-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b95b-131">Veja também</span><span class="sxs-lookup"><span data-stu-id="9b95b-131">See also</span></span>

- [<span data-ttu-id="9b95b-132">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="9b95b-132">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="9b95b-133">Depuração</span><span class="sxs-lookup"><span data-stu-id="9b95b-133">Debugging</span></span>](index.md)
