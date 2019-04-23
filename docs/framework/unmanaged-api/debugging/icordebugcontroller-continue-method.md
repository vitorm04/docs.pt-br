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
ms.openlocfilehash: 7eacffe5769bc77ab626f6adbc99db1137da565f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59146803"
---
# <a name="icordebugcontrollercontinue-method"></a><span data-ttu-id="94b66-102">Método ICorDebugController::Continue</span><span class="sxs-lookup"><span data-stu-id="94b66-102">ICorDebugController::Continue Method</span></span>
<span data-ttu-id="94b66-103">Retoma a execução de threads gerenciados após uma chamada para [método Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).</span><span class="sxs-lookup"><span data-stu-id="94b66-103">Resumes execution of managed threads after a call to [Stop Method](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94b66-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="94b66-104">Syntax</span></span>  
  
```  
HRESULT Continue (  
    [in] BOOL fIsOutOfBand  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="94b66-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="94b66-105">Parameters</span></span>  
 `fIsOutOfBand`  
 <span data-ttu-id="94b66-106">[in] Definido como `true` se continuar a partir de um evento de out-of-band; caso contrário, defina como `false`.</span><span class="sxs-lookup"><span data-stu-id="94b66-106">[in] Set to `true` if continuing from an out-of-band event; otherwise, set to `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="94b66-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="94b66-107">Remarks</span></span>  
 <span data-ttu-id="94b66-108">`Continue` continua o processo após uma chamada para o `ICorDebugController::Stop` método.</span><span class="sxs-lookup"><span data-stu-id="94b66-108">`Continue` continues the process after a call to the `ICorDebugController::Stop` method.</span></span>  
  
 <span data-ttu-id="94b66-109">Ao fazer a depuração de modo misto, não chame `Continue` no Win32 eventos de thread, a menos que você está continuando a partir de um evento de fora da banda.</span><span class="sxs-lookup"><span data-stu-id="94b66-109">When doing mixed-mode debugging, do not call `Continue` on the Win32 event thread unless you are continuing from an out-of-band event.</span></span>  
  
 <span data-ttu-id="94b66-110">Uma *eventos em banda* é um evento gerenciado ou um evento não gerenciado normal durante o qual o depurador oferece suporte a interação com o estado do processo gerenciado.</span><span class="sxs-lookup"><span data-stu-id="94b66-110">An *in-band event* is either a managed event or a normal unmanaged event during which the debugger supports interaction with the managed state of the process.</span></span> <span data-ttu-id="94b66-111">Nesse caso, o depurador recebe o [icordebugunmanagedcallback:: Debugevent](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-debugevent-method.md) retorno de chamada com seus `fOutOfBand` parâmetro definido como `false`.</span><span class="sxs-lookup"><span data-stu-id="94b66-111">In this case, the debugger receives the [ICorDebugUnmanagedCallback::DebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-debugevent-method.md) callback with its `fOutOfBand` parameter set to `false`.</span></span>  
  
 <span data-ttu-id="94b66-112">Uma *evento out-of-band* é um evento não gerenciado durante o qual a interação com o estado do processo gerenciado é impossível enquanto o processo é interrompido devido a evento.</span><span class="sxs-lookup"><span data-stu-id="94b66-112">An *out-of-band event* is an unmanaged event during which interaction with the managed state of the process is impossible while the process is stopped due to the event.</span></span> <span data-ttu-id="94b66-113">Nesse caso, o depurador recebe o `ICorDebugUnmanagedCallback::DebugEvent` retorno de chamada com seus `fOutOfBand` parâmetro definido como `true`.</span><span class="sxs-lookup"><span data-stu-id="94b66-113">In this case, the debugger receives the `ICorDebugUnmanagedCallback::DebugEvent` callback with its `fOutOfBand` parameter set to `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94b66-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="94b66-114">Requirements</span></span>  
 <span data-ttu-id="94b66-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94b66-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94b66-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="94b66-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="94b66-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="94b66-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="94b66-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94b66-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94b66-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="94b66-119">See also</span></span>
