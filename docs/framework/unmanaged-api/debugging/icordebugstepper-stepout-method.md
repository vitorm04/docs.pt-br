---
title: Método ICorDebugStepper::StepOut
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.StepOut
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::StepOut
helpviewer_keywords:
- ICorDebugStepper::StepOut method [.NET Framework debugging]
- StepOut method [.NET Framework debugging]
ms.assetid: aae0f48c-4ede-4256-9251-a7fc85a229dc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f663f5134cf34bf9beb66da20bbb5886baff5415
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugstepperstepout-method"></a><span data-ttu-id="9eabb-102">Método ICorDebugStepper::StepOut</span><span class="sxs-lookup"><span data-stu-id="9eabb-102">ICorDebugStepper::StepOut Method</span></span>
<span data-ttu-id="9eabb-103">Faz com que este ICorDebugStepper para percorrer por meio de seu recipiente thread e concluir quando o quadro atual retorna o controle para o quadro de chamada.</span><span class="sxs-lookup"><span data-stu-id="9eabb-103">Causes this ICorDebugStepper to single-step through its containing thread, and to complete when the current frame returns control to the calling frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9eabb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9eabb-104">Syntax</span></span>  
  
```  
HRESULT StepOut ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="9eabb-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="9eabb-105">Remarks</span></span>  
 <span data-ttu-id="9eabb-106">Um `StepOut` operação será concluída após o retorno normalmente do quadro atual para o quadro de chamada.</span><span class="sxs-lookup"><span data-stu-id="9eabb-106">A `StepOut` operation will complete after returning normally from the current frame to the calling frame.</span></span>  
  
 <span data-ttu-id="9eabb-107">Se `StepOut` é chamado quando em código não gerenciado, a etapa será concluída quando o quadro atual retorna para o código gerenciado que o chamou.</span><span class="sxs-lookup"><span data-stu-id="9eabb-107">If `StepOut` is called when in unmanaged code, the step will complete when the current frame returns to the managed code that called it.</span></span>  
  
 <span data-ttu-id="9eabb-108">No .NET Framework versão 2.0, não use `StepOut` com o STOP_UNMANAGED o sinalizador será definido porque ele falhará.</span><span class="sxs-lookup"><span data-stu-id="9eabb-108">In the .NET Framework version 2.0, do not use `StepOut` with the STOP_UNMANAGED flag set because it will fail.</span></span> <span data-ttu-id="9eabb-109">(Use [: Setunmappedstopmask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) para definir os sinalizadores para depuração.) Interoperabilidade depuradores devem sair para código nativo próprios.</span><span class="sxs-lookup"><span data-stu-id="9eabb-109">(Use [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) to set flags for stepping.) Interop debuggers must step out to native code themselves.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9eabb-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9eabb-110">Requirements</span></span>  
 <span data-ttu-id="9eabb-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9eabb-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9eabb-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9eabb-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9eabb-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9eabb-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9eabb-114">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9eabb-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
