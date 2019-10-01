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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bdf59ee3c7bf41a2bb0ff68db5e70dd5a519a0e9
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700775"
---
# <a name="icordebugcontrollercontinue-method"></a><span data-ttu-id="db822-102">Método ICorDebugController::Continue</span><span class="sxs-lookup"><span data-stu-id="db822-102">ICorDebugController::Continue Method</span></span>

<span data-ttu-id="db822-103">Retoma a execução de threads gerenciados após uma chamada para o [método Stop](icordebugcontroller-stop-method.md).</span><span class="sxs-lookup"><span data-stu-id="db822-103">Resumes execution of managed threads after a call to [Stop Method](icordebugcontroller-stop-method.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="db822-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="db822-104">Syntax</span></span>

```cpp
HRESULT Continue (
    [in] BOOL fIsOutOfBand
);
```

## <a name="parameters"></a><span data-ttu-id="db822-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="db822-105">Parameters</span></span>

 `fIsOutOfBand`  
 <span data-ttu-id="db822-106">no Defina como `true` se continuar a partir de um evento fora de banda; caso contrário, defina como `false`.</span><span class="sxs-lookup"><span data-stu-id="db822-106">[in] Set to `true` if continuing from an out-of-band event; otherwise, set to `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="db822-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="db822-107">Remarks</span></span>

<span data-ttu-id="db822-108">`Continue` continua o processo após uma chamada para o método `ICorDebugController::Stop`.</span><span class="sxs-lookup"><span data-stu-id="db822-108">`Continue` continues the process after a call to the `ICorDebugController::Stop` method.</span></span>

<span data-ttu-id="db822-109">Ao fazer a depuração de modo misto, não chame `Continue` no thread de eventos do Win32, a menos que você esteja continuando de um evento fora de banda.</span><span class="sxs-lookup"><span data-stu-id="db822-109">When doing mixed-mode debugging, do not call `Continue` on the Win32 event thread unless you are continuing from an out-of-band event.</span></span>

<span data-ttu-id="db822-110">Um *evento em banda* é um evento gerenciado ou um evento não gerenciado normal durante o qual o depurador dá suporte à interação com o estado gerenciado do processo.</span><span class="sxs-lookup"><span data-stu-id="db822-110">An *in-band event* is either a managed event or a normal unmanaged event during which the debugger supports interaction with the managed state of the process.</span></span> <span data-ttu-id="db822-111">Nesse caso, o depurador recebe o retorno de chamada [ICorDebugUnmanagedCallback::D ebugevent](icordebugunmanagedcallback-debugevent-method.md) com seu parâmetro `fOutOfBand` definido como `false`.</span><span class="sxs-lookup"><span data-stu-id="db822-111">In this case, the debugger receives the [ICorDebugUnmanagedCallback::DebugEvent](icordebugunmanagedcallback-debugevent-method.md) callback with its `fOutOfBand` parameter set to `false`.</span></span>
  
<span data-ttu-id="db822-112">Um *evento fora de banda* é um evento não gerenciado durante o qual a interação com o estado gerenciado do processo é impossível enquanto o processo é interrompido devido ao evento.</span><span class="sxs-lookup"><span data-stu-id="db822-112">An *out-of-band event* is an unmanaged event during which interaction with the managed state of the process is impossible while the process is stopped due to the event.</span></span> <span data-ttu-id="db822-113">Nesse caso, o depurador recebe o retorno de chamada `ICorDebugUnmanagedCallback::DebugEvent` com seu parâmetro `fOutOfBand` definido como `true`.</span><span class="sxs-lookup"><span data-stu-id="db822-113">In this case, the debugger receives the `ICorDebugUnmanagedCallback::DebugEvent` callback with its `fOutOfBand` parameter set to `true`.</span></span>

## <a name="requirements"></a><span data-ttu-id="db822-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="db822-114">Requirements</span></span>

 <span data-ttu-id="db822-115">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db822-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

 <span data-ttu-id="db822-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="db822-116">**Header:** CorDebug.idl, CorDebug.h</span></span>

 <span data-ttu-id="db822-117">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="db822-117">**Library:** CorGuids.lib</span></span>

 <span data-ttu-id="db822-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db822-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
 
