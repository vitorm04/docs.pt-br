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
ms.openlocfilehash: 743b0c8016ca5c0401046166a770d857215429a3
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379214"
---
# <a name="icordebugstackwalkgetcontext-method"></a><span data-ttu-id="f2b29-102">Método ICorDebugStackWalk::GetContext</span><span class="sxs-lookup"><span data-stu-id="f2b29-102">ICorDebugStackWalk::GetContext Method</span></span>
<span data-ttu-id="f2b29-103">Retorna o contexto para o quadro atual no objeto [ICorDebugStackWalk](icordebugstackwalk-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="f2b29-103">Returns the context for the current frame in the [ICorDebugStackWalk](icordebugstackwalk-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2b29-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f2b29-104">Syntax</span></span>  
  
```cpp  
HRESULT GetContext([in]  ULONG32 contextFlags,  
                   [in]  ULONG32 contextBufSize,  
                   [out] ULONG32* contextSize,  
                   [out, size_is(contextBufSize)] BYTE contextBuf[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f2b29-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f2b29-105">Parameters</span></span>  
 `contextFlags`  
 <span data-ttu-id="f2b29-106">no Sinalizadores que indicam o conteúdo solicitado do buffer de contexto (definido em WinNT. h).</span><span class="sxs-lookup"><span data-stu-id="f2b29-106">[in] Flags that indicate the requested contents of the context buffer (defined in WinNT.h).</span></span>  
  
 `contextBufSize`  
 <span data-ttu-id="f2b29-107">no O tamanho alocado do buffer de contexto.</span><span class="sxs-lookup"><span data-stu-id="f2b29-107">[in] The allocated size of the context buffer.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="f2b29-108">fora O tamanho real do contexto.</span><span class="sxs-lookup"><span data-stu-id="f2b29-108">[out] The actual size of the context.</span></span> <span data-ttu-id="f2b29-109">Esse valor deve ser menor ou igual ao tamanho do buffer de contexto.</span><span class="sxs-lookup"><span data-stu-id="f2b29-109">This value must be less than or equal to the size of the context buffer.</span></span>  
  
 `contextBuf`  
 <span data-ttu-id="f2b29-110">fora O buffer de contexto.</span><span class="sxs-lookup"><span data-stu-id="f2b29-110">[out] The context buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f2b29-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="f2b29-111">Return Value</span></span>  
 <span data-ttu-id="f2b29-112">Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.</span><span class="sxs-lookup"><span data-stu-id="f2b29-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="f2b29-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f2b29-113">HRESULT</span></span>|<span data-ttu-id="f2b29-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="f2b29-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f2b29-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="f2b29-115">S_OK</span></span>|<span data-ttu-id="f2b29-116">O contexto do quadro atual foi retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="f2b29-116">The context for the current frame was successfully returned.</span></span>|  
|<span data-ttu-id="f2b29-117">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f2b29-117">E_FAIL</span></span>|<span data-ttu-id="f2b29-118">Não foi possível retornar o contexto.</span><span class="sxs-lookup"><span data-stu-id="f2b29-118">The context could not be returned.</span></span>|  
|<span data-ttu-id="f2b29-119">HRESULT_FROM_WIN32 (ERROR_INSUFFICIENT BUFFER)</span><span class="sxs-lookup"><span data-stu-id="f2b29-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT BUFFER)</span></span>|<span data-ttu-id="f2b29-120">O buffer de contexto é muito pequeno.</span><span class="sxs-lookup"><span data-stu-id="f2b29-120">The context buffer is too small.</span></span>|  
|<span data-ttu-id="f2b29-121">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="f2b29-121">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="f2b29-122">O ponteiro de quadro já está no final da pilha; Portanto, nenhum quadro adicional pode ser acessado.</span><span class="sxs-lookup"><span data-stu-id="f2b29-122">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="f2b29-123">Exceções</span><span class="sxs-lookup"><span data-stu-id="f2b29-123">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f2b29-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="f2b29-124">Remarks</span></span>  
 <span data-ttu-id="f2b29-125">Como o desenrolamento restaura apenas um subconjunto dos registros, como registros não-voláteis, o contexto pode não corresponder exatamente ao estado de registro no momento da chamada.</span><span class="sxs-lookup"><span data-stu-id="f2b29-125">Because unwinding restores only a subset of the registers, such as non-volatile registers, the context may not exactly match the register state at the time of the call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2b29-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f2b29-126">Requirements</span></span>  
 <span data-ttu-id="f2b29-127">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2b29-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2b29-128">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f2b29-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f2b29-129">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f2b29-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f2b29-130">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2b29-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2b29-131">Confira também</span><span class="sxs-lookup"><span data-stu-id="f2b29-131">See also</span></span>

- [<span data-ttu-id="f2b29-132">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="f2b29-132">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="f2b29-133">Depuração</span><span class="sxs-lookup"><span data-stu-id="f2b29-133">Debugging</span></span>](index.md)
