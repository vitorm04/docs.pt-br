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
ms.openlocfilehash: cb52150a17c9ec8f4bbc25c13b85bce56b221eeb
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791186"
---
# <a name="icordebugunmanagedcallbackdebugevent-method"></a><span data-ttu-id="79349-102">Método ICorDebugUnmanagedCallback::DebugEvent</span><span class="sxs-lookup"><span data-stu-id="79349-102">ICorDebugUnmanagedCallback::DebugEvent Method</span></span>
<span data-ttu-id="79349-103">Notifica o depurador de que um evento nativo foi acionado.</span><span class="sxs-lookup"><span data-stu-id="79349-103">Notifies the debugger that a native event has been fired.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79349-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="79349-104">Syntax</span></span>  
  
```cpp  
HRESULT DebugEvent (  
    [in] LPDEBUG_EVENT  pDebugEvent,  
    [in] BOOL           fOutOfBand  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="79349-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="79349-105">Parameters</span></span>  
 `pDebugEvent`  
 <span data-ttu-id="79349-106">no Um ponteiro para o evento nativo.</span><span class="sxs-lookup"><span data-stu-id="79349-106">[in] A pointer to the native event.</span></span>  
  
 `fOutOfBand`  
 <span data-ttu-id="79349-107">[in] `true`, se a interação com o estado do processo gerenciado for impossível depois que um evento não gerenciado ocorrer, até que o depurador chame [ICorDebugController:: Continue](icordebugcontroller-continue-method.md); caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="79349-107">[in] `true`, if interaction with the managed process state is impossible after an unmanaged event occurs, until the debugger calls [ICorDebugController::Continue](icordebugcontroller-continue-method.md); otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="79349-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="79349-108">Remarks</span></span>  
 <span data-ttu-id="79349-109">Se o thread que está sendo depurado for um Thread Win32, não use nenhum membro da interface de depuração do Win32.</span><span class="sxs-lookup"><span data-stu-id="79349-109">If the thread being debugged is a Win32 thread, do not use any members of the Win32 debugging interface.</span></span> <span data-ttu-id="79349-110">Você pode chamar `ICorDebugController::Continue` apenas em um Thread Win32 e apenas quando estiver continuando um evento fora de banda.</span><span class="sxs-lookup"><span data-stu-id="79349-110">You can call `ICorDebugController::Continue` only on a Win32 thread and only when continuing past an out-of-band event.</span></span>  
  
 <span data-ttu-id="79349-111">O retorno de chamada `DebugEvent` não segue as regras padrão para retornos de chamada.</span><span class="sxs-lookup"><span data-stu-id="79349-111">The `DebugEvent` callback does not follow the standard rules for callbacks.</span></span> <span data-ttu-id="79349-112">Quando você chama `DebugEvent`, o processo estará no estado RAW, de depuração do sistema operacional interrompido.</span><span class="sxs-lookup"><span data-stu-id="79349-112">When you call `DebugEvent`, the process will be in the raw, OS-debug stopped state.</span></span> <span data-ttu-id="79349-113">O processo não será sincronizado.</span><span class="sxs-lookup"><span data-stu-id="79349-113">The process will not be synchronized.</span></span> <span data-ttu-id="79349-114">Ele inserirá automaticamente o estado SYNCHRONIZED quando necessário para atender a solicitações de informações sobre código gerenciado, o que pode resultar em outros retornos de chamada de `DebugEvent` aninhados.</span><span class="sxs-lookup"><span data-stu-id="79349-114">It will automatically enter the synchronized state when necessary to satisfy requests for information about managed code, which may result in other nested `DebugEvent` callbacks.</span></span>  
  
 <span data-ttu-id="79349-115">Chame [ICorDebugProcess:: ClearCurrentException](icordebugprocess-clearcurrentexception-method.md) no processo para ignorar um evento de exceção antes de continuar o processo.</span><span class="sxs-lookup"><span data-stu-id="79349-115">Call [ICorDebugProcess::ClearCurrentException](icordebugprocess-clearcurrentexception-method.md) on the process to ignore an exception event before continuing the process.</span></span> <span data-ttu-id="79349-116">Chamar esse método envia DBG_CONTINUE em vez de DBG_EXCEPTION_NOT_HANDLED na solicitação continue e limpa automaticamente os pontos de interrupção fora de banda e as exceções de etapa única.</span><span class="sxs-lookup"><span data-stu-id="79349-116">Calling this method sends DBG_CONTINUE instead of DBG_EXCEPTION_NOT_HANDLED on the continue request, and automatically clears out-of-band breakpoints and single-step exceptions.</span></span> <span data-ttu-id="79349-117">Eventos fora de banda podem vir a qualquer momento, mesmo quando o aplicativo que está sendo depurado aparece parado e quando um evento em banda pendente já existe.</span><span class="sxs-lookup"><span data-stu-id="79349-117">Out-of-band events can come at any time, even when the application being debugged appears stopped and when an outstanding in-band event already exists.</span></span>  
  
 <span data-ttu-id="79349-118">No .NET Framework versão 2,0, o depurador deve continuar imediatamente após um evento de ponto de interrupção fora de banda.</span><span class="sxs-lookup"><span data-stu-id="79349-118">In the .NET Framework version 2.0, the debugger should immediately continue past an out-of-band breakpoint event.</span></span> <span data-ttu-id="79349-119">O depurador deve usar os métodos [ICorDebugProcess2:: SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md) e [ICorDebugProcess2:: ClearUnmanagedBreakpoint](icordebugprocess2-clearunmanagedbreakpoint-method.md) para adicionar e remover pontos de interrupção.</span><span class="sxs-lookup"><span data-stu-id="79349-119">The debugger should be using the [ICorDebugProcess2::SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md) and [ICorDebugProcess2::ClearUnmanagedBreakpoint](icordebugprocess2-clearunmanagedbreakpoint-method.md) methods to add and remove breakpoints.</span></span> <span data-ttu-id="79349-120">Esses métodos ignorarão todos os pontos de interrupção fora de banda automaticamente.</span><span class="sxs-lookup"><span data-stu-id="79349-120">These methods will skip over any out-of-band breakpoints automatically.</span></span> <span data-ttu-id="79349-121">Portanto, os únicos pontos de interrupção fora de banda que são expedidos devem ser pontos de interrupção brutos que já estão no fluxo de instrução, como uma chamada para a função de `DebugBreak` do Win32.</span><span class="sxs-lookup"><span data-stu-id="79349-121">Thus, the only out-of-band breakpoints that get dispatched should be raw breakpoints that are already in the instruction stream, such as a call to the Win32 `DebugBreak` function.</span></span> <span data-ttu-id="79349-122">Não tente usar `ICorDebugProcess::ClearCurrentException`, [ICorDebugProcess:: GetThreadContext](icordebugprocess-getthreadcontext-method.md), [ICorDebugProcess:: SetThreadContext](icordebugprocess-setthreadcontext-method.md)ou qualquer outro membro da [API de depuração](index.md).</span><span class="sxs-lookup"><span data-stu-id="79349-122">Do not try to use `ICorDebugProcess::ClearCurrentException`, [ICorDebugProcess::GetThreadContext](icordebugprocess-getthreadcontext-method.md), [ICorDebugProcess::SetThreadContext](icordebugprocess-setthreadcontext-method.md), or any other member of the [debugging API](index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79349-123">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="79349-123">Requirements</span></span>  
 <span data-ttu-id="79349-124">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79349-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79349-125">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="79349-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="79349-126">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="79349-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="79349-127">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79349-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79349-128">Veja também</span><span class="sxs-lookup"><span data-stu-id="79349-128">See also</span></span>

- [<span data-ttu-id="79349-129">Interface ICorDebugUnmanagedCallback</span><span class="sxs-lookup"><span data-stu-id="79349-129">ICorDebugUnmanagedCallback Interface</span></span>](icordebugunmanagedcallback-interface.md)
