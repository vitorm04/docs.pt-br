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
ms.openlocfilehash: bba1e6c113fb4caa0db8963e238d3eceba0cc8ce
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61782740"
---
# <a name="icordebugstackwalkgetcontext-method"></a><span data-ttu-id="7609f-102">Método ICorDebugStackWalk::GetContext</span><span class="sxs-lookup"><span data-stu-id="7609f-102">ICorDebugStackWalk::GetContext Method</span></span>
<span data-ttu-id="7609f-103">Retorna o contexto para o quadro atual na [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) objeto.</span><span class="sxs-lookup"><span data-stu-id="7609f-103">Returns the context for the current frame in the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7609f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7609f-104">Syntax</span></span>  
  
```  
HRESULT GetContext([in]  ULONG32 contextFlags,  
                   [in]  ULONG32 contextBufSize,  
                   [out] ULONG32* contextSize,  
                   [out, size_is(contextBufSize)] BYTE contextBuf[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7609f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7609f-105">Parameters</span></span>  
 `contextFlags`  
 <span data-ttu-id="7609f-106">[in] Sinalizadores que indicam o conteúdo solicitado do buffer de contexto (definidos em Winnt. H).</span><span class="sxs-lookup"><span data-stu-id="7609f-106">[in] Flags that indicate the requested contents of the context buffer (defined in WinNT.h).</span></span>  
  
 `contextBufSize`  
 <span data-ttu-id="7609f-107">[in] O tamanho alocado do buffer de contexto.</span><span class="sxs-lookup"><span data-stu-id="7609f-107">[in] The allocated size of the context buffer.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="7609f-108">[out] O tamanho real do contexto.</span><span class="sxs-lookup"><span data-stu-id="7609f-108">[out] The actual size of the context.</span></span> <span data-ttu-id="7609f-109">Esse valor deve ser menor ou igual ao tamanho do buffer de contexto.</span><span class="sxs-lookup"><span data-stu-id="7609f-109">This value must be less than or equal to the size of the context buffer.</span></span>  
  
 `contextBuf`  
 <span data-ttu-id="7609f-110">[out] O buffer de contexto.</span><span class="sxs-lookup"><span data-stu-id="7609f-110">[out] The context buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7609f-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="7609f-111">Return Value</span></span>  
 <span data-ttu-id="7609f-112">Esse método retorna os HRESULTs específicos a seguir, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="7609f-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="7609f-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7609f-113">HRESULT</span></span>|<span data-ttu-id="7609f-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="7609f-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7609f-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="7609f-115">S_OK</span></span>|<span data-ttu-id="7609f-116">O contexto para o quadro atual foi retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="7609f-116">The context for the current frame was successfully returned.</span></span>|  
|<span data-ttu-id="7609f-117">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7609f-117">E_FAIL</span></span>|<span data-ttu-id="7609f-118">O contexto não pôde ser retornado.</span><span class="sxs-lookup"><span data-stu-id="7609f-118">The context could not be returned.</span></span>|  
|<span data-ttu-id="7609f-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT BUFFER)</span><span class="sxs-lookup"><span data-stu-id="7609f-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT BUFFER)</span></span>|<span data-ttu-id="7609f-120">O buffer de contexto é muito pequeno.</span><span class="sxs-lookup"><span data-stu-id="7609f-120">The context buffer is too small.</span></span>|  
|<span data-ttu-id="7609f-121">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="7609f-121">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="7609f-122">O ponteiro de quadro já está no final da pilha; Portanto, não há quadros adicionais podem ser acessados.</span><span class="sxs-lookup"><span data-stu-id="7609f-122">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="7609f-123">Exceções</span><span class="sxs-lookup"><span data-stu-id="7609f-123">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7609f-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="7609f-124">Remarks</span></span>  
 <span data-ttu-id="7609f-125">Porque o desenrolamento restaura apenas um subconjunto de registros, como registros não voláteis, o contexto pode não coincidir com o estado de registro no momento da chamada.</span><span class="sxs-lookup"><span data-stu-id="7609f-125">Because unwinding restores only a subset of the registers, such as non-volatile registers, the context may not exactly match the register state at the time of the call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7609f-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7609f-126">Requirements</span></span>  
 <span data-ttu-id="7609f-127">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7609f-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7609f-128">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7609f-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7609f-129">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7609f-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7609f-130">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7609f-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7609f-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7609f-131">See also</span></span>

- [<span data-ttu-id="7609f-132">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="7609f-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="7609f-133">Depuração</span><span class="sxs-lookup"><span data-stu-id="7609f-133">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
