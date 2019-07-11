---
title: Método ICorDebugStackWalk::GetContext
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.GetContext Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::GetContext
helpviewer_keywords:
- GetContext method, ICorDebugStackWalk interface [.NET Framework debugging]
- ICorDebugStackWalk::GetContext method [.NET Framework debugging]
ms.assetid: 081d1c95-152b-4797-8552-18453eb7b14b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f453e950a79b0f929ec8f813cc13eb2e01ab8c87
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760936"
---
# <a name="icordebugstackwalkgetcontext-method"></a><span data-ttu-id="560a0-102">Método ICorDebugStackWalk::GetContext</span><span class="sxs-lookup"><span data-stu-id="560a0-102">ICorDebugStackWalk::GetContext Method</span></span>
<span data-ttu-id="560a0-103">Retorna o contexto para o quadro atual na [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) objeto.</span><span class="sxs-lookup"><span data-stu-id="560a0-103">Returns the context for the current frame in the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="560a0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="560a0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetContext([in]  ULONG32 contextFlags,  
                   [in]  ULONG32 contextBufSize,  
                   [out] ULONG32* contextSize,  
                   [out, size_is(contextBufSize)] BYTE contextBuf[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="560a0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="560a0-105">Parameters</span></span>  
 `contextFlags`  
 <span data-ttu-id="560a0-106">[in] Sinalizadores que indicam o conteúdo solicitado do buffer de contexto (definidos em Winnt. H).</span><span class="sxs-lookup"><span data-stu-id="560a0-106">[in] Flags that indicate the requested contents of the context buffer (defined in WinNT.h).</span></span>  
  
 `contextBufSize`  
 <span data-ttu-id="560a0-107">[in] O tamanho alocado do buffer de contexto.</span><span class="sxs-lookup"><span data-stu-id="560a0-107">[in] The allocated size of the context buffer.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="560a0-108">[out] O tamanho real do contexto.</span><span class="sxs-lookup"><span data-stu-id="560a0-108">[out] The actual size of the context.</span></span> <span data-ttu-id="560a0-109">Esse valor deve ser menor ou igual ao tamanho do buffer de contexto.</span><span class="sxs-lookup"><span data-stu-id="560a0-109">This value must be less than or equal to the size of the context buffer.</span></span>  
  
 `contextBuf`  
 <span data-ttu-id="560a0-110">[out] O buffer de contexto.</span><span class="sxs-lookup"><span data-stu-id="560a0-110">[out] The context buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="560a0-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="560a0-111">Return Value</span></span>  
 <span data-ttu-id="560a0-112">Esse método retorna os HRESULTs específicos a seguir, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="560a0-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="560a0-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="560a0-113">HRESULT</span></span>|<span data-ttu-id="560a0-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="560a0-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="560a0-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="560a0-115">S_OK</span></span>|<span data-ttu-id="560a0-116">O contexto para o quadro atual foi retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="560a0-116">The context for the current frame was successfully returned.</span></span>|  
|<span data-ttu-id="560a0-117">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="560a0-117">E_FAIL</span></span>|<span data-ttu-id="560a0-118">O contexto não pôde ser retornado.</span><span class="sxs-lookup"><span data-stu-id="560a0-118">The context could not be returned.</span></span>|  
|<span data-ttu-id="560a0-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT BUFFER)</span><span class="sxs-lookup"><span data-stu-id="560a0-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT BUFFER)</span></span>|<span data-ttu-id="560a0-120">O buffer de contexto é muito pequeno.</span><span class="sxs-lookup"><span data-stu-id="560a0-120">The context buffer is too small.</span></span>|  
|<span data-ttu-id="560a0-121">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="560a0-121">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="560a0-122">O ponteiro de quadro já está no final da pilha; Portanto, não há quadros adicionais podem ser acessados.</span><span class="sxs-lookup"><span data-stu-id="560a0-122">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="560a0-123">Exceções</span><span class="sxs-lookup"><span data-stu-id="560a0-123">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="560a0-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="560a0-124">Remarks</span></span>  
 <span data-ttu-id="560a0-125">Porque o desenrolamento restaura apenas um subconjunto de registros, como registros não voláteis, o contexto pode não coincidir com o estado de registro no momento da chamada.</span><span class="sxs-lookup"><span data-stu-id="560a0-125">Because unwinding restores only a subset of the registers, such as non-volatile registers, the context may not exactly match the register state at the time of the call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="560a0-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="560a0-126">Requirements</span></span>  
 <span data-ttu-id="560a0-127">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="560a0-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="560a0-128">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="560a0-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="560a0-129">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="560a0-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="560a0-130">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="560a0-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="560a0-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="560a0-131">See also</span></span>

- [<span data-ttu-id="560a0-132">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="560a0-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="560a0-133">Depuração</span><span class="sxs-lookup"><span data-stu-id="560a0-133">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
