---
title: "Método ICorDebugController::Continue"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugController.Continue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugController::Continue
helpviewer_keywords:
- Continue method [.NET Framework debugging]
- ICorDebugController::Continue method [.NET Framework debugging]
ms.assetid: 8684cd06-ad3e-48ef-832e-15320e1f43a2
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e6a96145801aa8ef6482e30e9c00b763d2501f36
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcontrollercontinue-method"></a><span data-ttu-id="f1d60-102">Método ICorDebugController::Continue</span><span class="sxs-lookup"><span data-stu-id="f1d60-102">ICorDebugController::Continue Method</span></span>
<span data-ttu-id="f1d60-103">Retoma a execução de threads gerenciados após uma chamada para [método Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).</span><span class="sxs-lookup"><span data-stu-id="f1d60-103">Resumes execution of managed threads after a call to [Stop Method](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1d60-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f1d60-104">Syntax</span></span>  
  
```  
HRESULT Continue (  
    [in] BOOL fIsOutOfBand  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f1d60-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f1d60-105">Parameters</span></span>  
 `fIsOutOfBand`  
 <span data-ttu-id="f1d60-106">[in] Definido como `true` se continuar a partir de um evento fora de banda; caso contrário, defina como `false`.</span><span class="sxs-lookup"><span data-stu-id="f1d60-106">[in] Set to `true` if continuing from an out-of-band event; otherwise, set to `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f1d60-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="f1d60-107">Remarks</span></span>  
 <span data-ttu-id="f1d60-108">`Continue`continua o processo após uma chamada para o `ICorDebugController::Stop` método.</span><span class="sxs-lookup"><span data-stu-id="f1d60-108">`Continue` continues the process after a call to the `ICorDebugController::Stop` method.</span></span>  
  
 <span data-ttu-id="f1d60-109">Ao fazer a depuração de modo misto, não chame `Continue` em Win32 do thread eventos, a menos que você está continuando a partir de um evento fora de banda.</span><span class="sxs-lookup"><span data-stu-id="f1d60-109">When doing mixed-mode debugging, do not call `Continue` on the Win32 event thread unless you are continuing from an out-of-band event.</span></span>  
  
 <span data-ttu-id="f1d60-110">Um *em banda evento* é um evento gerenciado ou um evento normal de não gerenciado durante o qual o depurador oferece suporte à interação com o estado do processo gerenciado.</span><span class="sxs-lookup"><span data-stu-id="f1d60-110">An *in-band event* is either a managed event or a normal unmanaged event during which the debugger supports interaction with the managed state of the process.</span></span> <span data-ttu-id="f1d60-111">Nesse caso, o depurador recebe o [Icordebugunmanagedcallback](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-debugevent-method.md) retorno de chamada com seu `fOutOfBand` parâmetro definido como `false`.</span><span class="sxs-lookup"><span data-stu-id="f1d60-111">In this case, the debugger receives the [ICorDebugUnmanagedCallback::DebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-debugevent-method.md) callback with its `fOutOfBand` parameter set to `false`.</span></span>  
  
 <span data-ttu-id="f1d60-112">Um *eventos fora de banda* é um evento não gerenciado durante o qual a interação com o estado do processo gerenciado é impossível enquanto o processo foi interrompido devido ao evento.</span><span class="sxs-lookup"><span data-stu-id="f1d60-112">An *out-of-band event* is an unmanaged event during which interaction with the managed state of the process is impossible while the process is stopped due to the event.</span></span> <span data-ttu-id="f1d60-113">Nesse caso, o depurador recebe o `ICorDebugUnmanagedCallback::DebugEvent` retorno de chamada com seu `fOutOfBand` parâmetro definido como `true`.</span><span class="sxs-lookup"><span data-stu-id="f1d60-113">In this case, the debugger receives the `ICorDebugUnmanagedCallback::DebugEvent` callback with its `fOutOfBand` parameter set to `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1d60-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f1d60-114">Requirements</span></span>  
 <span data-ttu-id="f1d60-115">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1d60-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1d60-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f1d60-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f1d60-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f1d60-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f1d60-118">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1d60-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1d60-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f1d60-119">See Also</span></span>  
 
