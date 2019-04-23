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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7306ee61d750ae256c93c049819a23d3d61f7297
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59116461"
---
# <a name="icordebugstackwalksetcontext-method"></a><span data-ttu-id="2e6e1-102">Método ICorDebugStackWalk::SetContext</span><span class="sxs-lookup"><span data-stu-id="2e6e1-102">ICorDebugStackWalk::SetContext Method</span></span>
<span data-ttu-id="2e6e1-103">Define o [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) o contexto atual de objeto para um contexto válido para o thread.</span><span class="sxs-lookup"><span data-stu-id="2e6e1-103">Sets the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object’s current context to a valid context for the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e6e1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2e6e1-104">Syntax</span></span>  
  
```  
HRESULT SetContext([in] CorDebugSetContextFlag flag,  
                   [in] ULONG32 contextSize,  
                   [in, size_is(contextSize)] BYTE context[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2e6e1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2e6e1-105">Parameters</span></span>  
 `flag`  
 <span data-ttu-id="2e6e1-106">[in] Um [CorDebugSetContextFlag](../../../../docs/framework/unmanaged-api/debugging/cordebugsetcontextflag-enumeration.md) sinalizador que indica se o contexto é do quadro ativo na pilha ou um contexto obtido pelo desenrolamento de pilha.</span><span class="sxs-lookup"><span data-stu-id="2e6e1-106">[in] A [CorDebugSetContextFlag](../../../../docs/framework/unmanaged-api/debugging/cordebugsetcontextflag-enumeration.md) flag that indicates whether the context is from the active frame on the stack, or a context obtained by unwinding the stack.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="2e6e1-107">[in] O tamanho alocado do `CONTEXT` buffer.</span><span class="sxs-lookup"><span data-stu-id="2e6e1-107">[in] The allocated size of the `CONTEXT` buffer.</span></span>  
  
 `context`  
 <span data-ttu-id="2e6e1-108">[in] O `CONTEXT` buffer.</span><span class="sxs-lookup"><span data-stu-id="2e6e1-108">[in] The `CONTEXT` buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2e6e1-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="2e6e1-109">Return Value</span></span>  
 <span data-ttu-id="2e6e1-110">Esse método retorna os HRESULTs específicos a seguir, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="2e6e1-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="2e6e1-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2e6e1-111">HRESULT</span></span>|<span data-ttu-id="2e6e1-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="2e6e1-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2e6e1-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="2e6e1-113">S_OK</span></span>|<span data-ttu-id="2e6e1-114">O `ICorDebugStackWalk` contexto de objeto foi definido com êxito.</span><span class="sxs-lookup"><span data-stu-id="2e6e1-114">The `ICorDebugStackWalk` object's context was successfully set.</span></span>|  
|<span data-ttu-id="2e6e1-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2e6e1-115">E_FAIL</span></span>|<span data-ttu-id="2e6e1-116">O `ICorDebugStackWalk` contexto de objeto não foi definido.</span><span class="sxs-lookup"><span data-stu-id="2e6e1-116">The `ICorDebugStackWalk` object's context was not set.</span></span>|  
|<span data-ttu-id="2e6e1-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="2e6e1-117">E_INVALIDARG</span></span>|<span data-ttu-id="2e6e1-118">O contexto é nulo.</span><span class="sxs-lookup"><span data-stu-id="2e6e1-118">The context is null.</span></span>|  
|<span data-ttu-id="2e6e1-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="2e6e1-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>|<span data-ttu-id="2e6e1-120">O buffer de contexto é muito pequeno.</span><span class="sxs-lookup"><span data-stu-id="2e6e1-120">The context buffer is too small.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="2e6e1-121">Exceções</span><span class="sxs-lookup"><span data-stu-id="2e6e1-121">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2e6e1-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="2e6e1-122">Remarks</span></span>  
 <span data-ttu-id="2e6e1-123">Esse método não altera o contexto atual do thread.</span><span class="sxs-lookup"><span data-stu-id="2e6e1-123">This method does not alter the current context of the thread.</span></span>  
  
 <span data-ttu-id="2e6e1-124">Definir o contexto atual para um contexto inválido pode causar resultados imprevisíveis de movimentador de pilhas.</span><span class="sxs-lookup"><span data-stu-id="2e6e1-124">Setting the current context to an invalid context may cause unpredictable results from the stack walker.</span></span>  
  
 <span data-ttu-id="2e6e1-125">Você pode recuperar uma cópia bit a bit exata deste contexto imediatamente chamando o [icordebugstackwalk:: GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="2e6e1-125">You can retrieve an exact bitwise copy of this context by immediately calling the [ICorDebugStackWalk::GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e6e1-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2e6e1-126">Requirements</span></span>  
 <span data-ttu-id="2e6e1-127">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e6e1-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e6e1-128">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2e6e1-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2e6e1-129">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2e6e1-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2e6e1-130">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e6e1-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e6e1-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2e6e1-131">See also</span></span>

- [<span data-ttu-id="2e6e1-132">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="2e6e1-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="2e6e1-133">Depuração</span><span class="sxs-lookup"><span data-stu-id="2e6e1-133">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
