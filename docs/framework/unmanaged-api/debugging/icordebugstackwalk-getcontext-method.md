---
title: "Método ICorDebugStackWalk::GetContext"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStackWalk.GetContext Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStackWalk::GetContext
helpviewer_keywords:
- GetContext method, ICorDebugStackWalk interface [.NET Framework debugging]
- ICorDebugStackWalk::GetContext method [.NET Framework debugging]
ms.assetid: 081d1c95-152b-4797-8552-18453eb7b14b
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2bdd910862e7198d616e79ec732708f708959d26
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugstackwalkgetcontext-method"></a><span data-ttu-id="09678-102">Método ICorDebugStackWalk::GetContext</span><span class="sxs-lookup"><span data-stu-id="09678-102">ICorDebugStackWalk::GetContext Method</span></span>
<span data-ttu-id="09678-103">Retorna o contexto para o quadro atual de [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) objeto.</span><span class="sxs-lookup"><span data-stu-id="09678-103">Returns the context for the current frame in the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09678-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="09678-104">Syntax</span></span>  
  
```  
HRESULT GetContext([in]  ULONG32 contextFlags,  
                   [in]  ULONG32 contextBufSize,  
                   [out] ULONG32* contextSize,  
                   [out, size_is(contextBufSize)] BYTE contextBuf[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="09678-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="09678-105">Parameters</span></span>  
 `contextFlags`  
 <span data-ttu-id="09678-106">[in] Sinalizadores que indicam o conteúdo solicitado do buffer de contexto (definido em Winnt. H).</span><span class="sxs-lookup"><span data-stu-id="09678-106">[in] Flags that indicate the requested contents of the context buffer (defined in WinNT.h).</span></span>  
  
 `contextBufSize`  
 <span data-ttu-id="09678-107">[in] O tamanho alocado do buffer de contexto.</span><span class="sxs-lookup"><span data-stu-id="09678-107">[in] The allocated size of the context buffer.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="09678-108">[out] O tamanho real do contexto.</span><span class="sxs-lookup"><span data-stu-id="09678-108">[out] The actual size of the context.</span></span> <span data-ttu-id="09678-109">Esse valor deve ser menor ou igual ao tamanho do buffer de contexto.</span><span class="sxs-lookup"><span data-stu-id="09678-109">This value must be less than or equal to the size of the context buffer.</span></span>  
  
 `contextBuf`  
 <span data-ttu-id="09678-110">[out] O buffer de contexto.</span><span class="sxs-lookup"><span data-stu-id="09678-110">[out] The context buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="09678-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="09678-111">Return Value</span></span>  
 <span data-ttu-id="09678-112">Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="09678-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="09678-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="09678-113">HRESULT</span></span>|<span data-ttu-id="09678-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="09678-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="09678-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="09678-115">S_OK</span></span>|<span data-ttu-id="09678-116">O contexto para o quadro atual foi retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="09678-116">The context for the current frame was successfully returned.</span></span>|  
|<span data-ttu-id="09678-117">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="09678-117">E_FAIL</span></span>|<span data-ttu-id="09678-118">O contexto não pôde ser retornado.</span><span class="sxs-lookup"><span data-stu-id="09678-118">The context could not be returned.</span></span>|  
|<span data-ttu-id="09678-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT BUFFER)</span><span class="sxs-lookup"><span data-stu-id="09678-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT BUFFER)</span></span>|<span data-ttu-id="09678-120">O buffer de contexto é muito pequeno.</span><span class="sxs-lookup"><span data-stu-id="09678-120">The context buffer is too small.</span></span>|  
|<span data-ttu-id="09678-121">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="09678-121">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="09678-122">O ponteiro de quadro já está no final da pilha; Portanto, não há quadros adicionais podem ser acessados.</span><span class="sxs-lookup"><span data-stu-id="09678-122">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="09678-123">Exceções</span><span class="sxs-lookup"><span data-stu-id="09678-123">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="09678-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="09678-124">Remarks</span></span>  
 <span data-ttu-id="09678-125">Porque desenrolamento restaura apenas um subconjunto de registros, como registros não volátil, o contexto pode não coincidir com o estado do registro no momento da chamada.</span><span class="sxs-lookup"><span data-stu-id="09678-125">Because unwinding restores only a subset of the registers, such as non-volatile registers, the context may not exactly match the register state at the time of the call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09678-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="09678-126">Requirements</span></span>  
 <span data-ttu-id="09678-127">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="09678-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09678-128">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="09678-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="09678-129">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="09678-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="09678-130">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09678-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09678-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="09678-131">See Also</span></span>  
 [<span data-ttu-id="09678-132">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="09678-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="09678-133">Depuração</span><span class="sxs-lookup"><span data-stu-id="09678-133">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
