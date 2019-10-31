---
title: Método ICorDebugController::Continue
ms.date: 03/30/2017
api_name:
- ICorDebugController.Continue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Continue
helpviewer_keywords:
- Continue method [.NET Framework debugging]
- ICorDebugController::Continue method [.NET Framework debugging]
ms.assetid: 8684cd06-ad3e-48ef-832e-15320e1f43a2
topic_type:
- apiref
ms.openlocfilehash: 14356a12c944ef93dba5e7b818d3ee5cf5adc607
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125416"
---
# <a name="icordebugcontrollercontinue-method"></a><span data-ttu-id="90242-102">Método ICorDebugController::Continue</span><span class="sxs-lookup"><span data-stu-id="90242-102">ICorDebugController::Continue Method</span></span>

<span data-ttu-id="90242-103">Retoma a execução de threads gerenciados após uma chamada para o [método Stop](icordebugcontroller-stop-method.md).</span><span class="sxs-lookup"><span data-stu-id="90242-103">Resumes execution of managed threads after a call to [Stop Method](icordebugcontroller-stop-method.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="90242-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="90242-104">Syntax</span></span>

```cpp
HRESULT Continue (
    [in] BOOL fIsOutOfBand
);
```

## <a name="parameters"></a><span data-ttu-id="90242-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="90242-105">Parameters</span></span>

`fIsOutOfBand`  
<span data-ttu-id="90242-106">no Defina como `true` se continuar com um evento fora de banda; caso contrário, defina como `false`.</span><span class="sxs-lookup"><span data-stu-id="90242-106">[in] Set to `true` if continuing from an out-of-band event; otherwise, set to `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="90242-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="90242-107">Remarks</span></span>

<span data-ttu-id="90242-108">`Continue` continua o processo após uma chamada para o método `ICorDebugController::Stop`.</span><span class="sxs-lookup"><span data-stu-id="90242-108">`Continue` continues the process after a call to the `ICorDebugController::Stop` method.</span></span>

<span data-ttu-id="90242-109">Ao fazer a depuração de modo misto, não chame `Continue` no thread de eventos do Win32, a menos que você esteja continuando de um evento fora de banda.</span><span class="sxs-lookup"><span data-stu-id="90242-109">When doing mixed-mode debugging, do not call `Continue` on the Win32 event thread unless you are continuing from an out-of-band event.</span></span>

<span data-ttu-id="90242-110">Um *evento em banda* é um evento gerenciado ou um evento não gerenciado normal durante o qual o depurador dá suporte à interação com o estado gerenciado do processo.</span><span class="sxs-lookup"><span data-stu-id="90242-110">An *in-band event* is either a managed event or a normal unmanaged event during which the debugger supports interaction with the managed state of the process.</span></span> <span data-ttu-id="90242-111">Nesse caso, o depurador recebe o retorno de chamada [ICorDebugUnmanagedCallback::D ebugevent](icordebugunmanagedcallback-debugevent-method.md) com seu parâmetro `fOutOfBand` definido como `false`.</span><span class="sxs-lookup"><span data-stu-id="90242-111">In this case, the debugger receives the [ICorDebugUnmanagedCallback::DebugEvent](icordebugunmanagedcallback-debugevent-method.md) callback with its `fOutOfBand` parameter set to `false`.</span></span>

<span data-ttu-id="90242-112">Um *evento fora de banda* é um evento não gerenciado durante o qual a interação com o estado gerenciado do processo é impossível enquanto o processo é interrompido devido ao evento.</span><span class="sxs-lookup"><span data-stu-id="90242-112">An *out-of-band event* is an unmanaged event during which interaction with the managed state of the process is impossible while the process is stopped due to the event.</span></span> <span data-ttu-id="90242-113">Nesse caso, o depurador recebe o retorno de chamada `ICorDebugUnmanagedCallback::DebugEvent` com seu parâmetro `fOutOfBand` definido como `true`.</span><span class="sxs-lookup"><span data-stu-id="90242-113">In this case, the debugger receives the `ICorDebugUnmanagedCallback::DebugEvent` callback with its `fOutOfBand` parameter set to `true`.</span></span>

## <a name="requirements"></a><span data-ttu-id="90242-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="90242-114">Requirements</span></span>

<span data-ttu-id="90242-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90242-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="90242-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="90242-116">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="90242-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="90242-117">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="90242-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90242-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
