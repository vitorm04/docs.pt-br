---
title: Método ICorDebugUnmanagedCallback::DebugEvent
ms.date: 03/30/2017
api_name:
- ICorDebugUnmanagedCallback.DebugEvent
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugUnmanagedCallback::DebugEvent
helpviewer_keywords:
- DebugEvent method [.NET Framework debugging]
- ICorDebugUnmanagedCallback::DebugEvent method [.NET Framework debugging]
ms.assetid: be9cab04-65ec-44d5-a39a-f90709fdd043
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6ec45004f5dd87983187690a0a4feefb35b05e85
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59183606"
---
# <a name="icordebugunmanagedcallbackdebugevent-method"></a><span data-ttu-id="8e4b7-102">Método ICorDebugUnmanagedCallback::DebugEvent</span><span class="sxs-lookup"><span data-stu-id="8e4b7-102">ICorDebugUnmanagedCallback::DebugEvent Method</span></span>
<span data-ttu-id="8e4b7-103">Notifica o depurador que um evento nativo foi disparado.</span><span class="sxs-lookup"><span data-stu-id="8e4b7-103">Notifies the debugger that a native event has been fired.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e4b7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8e4b7-104">Syntax</span></span>  
  
```  
HRESULT DebugEvent (  
    [in] LPDEBUG_EVENT  pDebugEvent,  
    [in] BOOL           fOutOfBand  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8e4b7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8e4b7-105">Parameters</span></span>  
 `pDebugEvent`  
 <span data-ttu-id="8e4b7-106">[in] Um ponteiro para o evento nativo.</span><span class="sxs-lookup"><span data-stu-id="8e4b7-106">[in] A pointer to the native event.</span></span>  
  
 `fOutOfBand`  
 <span data-ttu-id="8e4b7-107">[in] `true`, se a interação com o estado do processo gerenciado é impossível quando ocorre um evento de não gerenciado, até que as chamadas do depurador [icordebugcontroller:: continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md); caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="8e4b7-107">[in] `true`, if interaction with the managed process state is impossible after an unmanaged event occurs, until the debugger calls [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md); otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8e4b7-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="8e4b7-108">Remarks</span></span>  
 <span data-ttu-id="8e4b7-109">Se o thread que está sendo depurado é um thread do Win32, não use nenhum membro do Win32 na interface de depuração.</span><span class="sxs-lookup"><span data-stu-id="8e4b7-109">If the thread being debugged is a Win32 thread, do not use any members of the Win32 debugging interface.</span></span> <span data-ttu-id="8e4b7-110">Você pode chamar `ICorDebugController::Continue` somente em um thread do Win32 e somente quando continuar após um evento de fora da banda.</span><span class="sxs-lookup"><span data-stu-id="8e4b7-110">You can call `ICorDebugController::Continue` only on a Win32 thread and only when continuing past an out-of-band event.</span></span>  
  
 <span data-ttu-id="8e4b7-111">O `DebugEvent` retorno de chamada não segue as regras padrão para retornos de chamada.</span><span class="sxs-lookup"><span data-stu-id="8e4b7-111">The `DebugEvent` callback does not follow the standard rules for callbacks.</span></span> <span data-ttu-id="8e4b7-112">Quando você chama `DebugEvent`, o processo estará em bruto, o estado de parado de depuração do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="8e4b7-112">When you call `DebugEvent`, the process will be in the raw, OS-debug stopped state.</span></span> <span data-ttu-id="8e4b7-113">O processo não será sincronizado.</span><span class="sxs-lookup"><span data-stu-id="8e4b7-113">The process will not be synchronized.</span></span> <span data-ttu-id="8e4b7-114">Entrará automaticamente o estado sincronizado quando necessário para atender a solicitações para obter informações sobre o código gerenciado, que pode resultar em outros aninhados `DebugEvent` retornos de chamada.</span><span class="sxs-lookup"><span data-stu-id="8e4b7-114">It will automatically enter the synchronized state when necessary to satisfy requests for information about managed code, which may result in other nested `DebugEvent` callbacks.</span></span>  
  
 <span data-ttu-id="8e4b7-115">Chame [icordebugprocess:: Clearcurrentexception](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md) sobre o processo de ignorar um evento de exceção antes de continuar o processo.</span><span class="sxs-lookup"><span data-stu-id="8e4b7-115">Call [ICorDebugProcess::ClearCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md) on the process to ignore an exception event before continuing the process.</span></span> <span data-ttu-id="8e4b7-116">Chamar esse método envia a solicitação para continuar DBG_CONTINUE em vez de DBG_EXCEPTION_NOT_HANDLED e limpa automaticamente os pontos de interrupção de out-of-band e exceções do passo a passo.</span><span class="sxs-lookup"><span data-stu-id="8e4b7-116">Calling this method sends DBG_CONTINUE instead of DBG_EXCEPTION_NOT_HANDLED on the continue request, and automatically clears out-of-band breakpoints and single-step exceptions.</span></span> <span data-ttu-id="8e4b7-117">Eventos fora de banda podem vir a qualquer momento, mesmo quando o aplicativo que está sendo depurado aparece interrompido e quando um evento em banda pendente já existe.</span><span class="sxs-lookup"><span data-stu-id="8e4b7-117">Out-of-band events can come at any time, even when the application being debugged appears stopped and when an outstanding in-band event already exists.</span></span>  
  
 <span data-ttu-id="8e4b7-118">No .NET Framework versão 2.0, o depurador imediatamente deve continuar após um evento de ponto de interrupção de out-of-band.</span><span class="sxs-lookup"><span data-stu-id="8e4b7-118">In the .NET Framework version 2.0, the debugger should immediately continue past an out-of-band breakpoint event.</span></span> <span data-ttu-id="8e4b7-119">O depurador deve estar usando o [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md) e [ICorDebugProcess2::ClearUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md) métodos para adicionar e remover pontos de interrupção.</span><span class="sxs-lookup"><span data-stu-id="8e4b7-119">The debugger should be using the [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md) and [ICorDebugProcess2::ClearUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md) methods to add and remove breakpoints.</span></span> <span data-ttu-id="8e4b7-120">Esses métodos ignorará qualquer ponto de interrupção de out-of-band automaticamente.</span><span class="sxs-lookup"><span data-stu-id="8e4b7-120">These methods will skip over any out-of-band breakpoints automatically.</span></span> <span data-ttu-id="8e4b7-121">Assim, os pontos de interrupção somente out-of-band expedidos devem ser brutos pontos de interrupção que já estão no fluxo de instruções, como uma chamada para o Win32 `DebugBreak` função.</span><span class="sxs-lookup"><span data-stu-id="8e4b7-121">Thus, the only out-of-band breakpoints that get dispatched should be raw breakpoints that are already in the instruction stream, such as a call to the Win32 `DebugBreak` function.</span></span> <span data-ttu-id="8e4b7-122">Não tente usar `ICorDebugProcess::ClearCurrentException`, [icordebugprocess:: Getthreadcontext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md), [icordebugprocess:: Setthreadcontext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md), ou qualquer outro membro do [API de depuração](../../../../docs/framework/unmanaged-api/debugging/index.md).</span><span class="sxs-lookup"><span data-stu-id="8e4b7-122">Do not try to use `ICorDebugProcess::ClearCurrentException`, [ICorDebugProcess::GetThreadContext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md), [ICorDebugProcess::SetThreadContext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md), or any other member of the [debugging API](../../../../docs/framework/unmanaged-api/debugging/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e4b7-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8e4b7-123">Requirements</span></span>  
 <span data-ttu-id="8e4b7-124">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8e4b7-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e4b7-125">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8e4b7-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8e4b7-126">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8e4b7-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8e4b7-127">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e4b7-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e4b7-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8e4b7-128">See also</span></span>

- [<span data-ttu-id="8e4b7-129">Interface ICorDebugUnmanagedCallback</span><span class="sxs-lookup"><span data-stu-id="8e4b7-129">ICorDebugUnmanagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md)
