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
ms.openlocfilehash: 36a33b74a692761d772a888ce918aa28a2d92678
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760560"
---
# <a name="icordebugstepperstepout-method"></a><span data-ttu-id="cc887-102">Método ICorDebugStepper::StepOut</span><span class="sxs-lookup"><span data-stu-id="cc887-102">ICorDebugStepper::StepOut Method</span></span>
<span data-ttu-id="cc887-103">Faz com que esse ICorDebugStepper a etapa única por meio de seu recipiente thread e para ser concluído quando o quadro atual retorna o controle para o quadro de chamada.</span><span class="sxs-lookup"><span data-stu-id="cc887-103">Causes this ICorDebugStepper to single-step through its containing thread, and to complete when the current frame returns control to the calling frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc887-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cc887-104">Syntax</span></span>  
  
```cpp  
HRESULT StepOut ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="cc887-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="cc887-105">Remarks</span></span>  
 <span data-ttu-id="cc887-106">Um `StepOut` operação será concluída após retornar normalmente de quadro atual para o quadro de chamada.</span><span class="sxs-lookup"><span data-stu-id="cc887-106">A `StepOut` operation will complete after returning normally from the current frame to the calling frame.</span></span>  
  
 <span data-ttu-id="cc887-107">Se `StepOut` é chamado quando em código não gerenciado, a etapa será concluída quando o quadro atual retorna para o código gerenciado que o chamou.</span><span class="sxs-lookup"><span data-stu-id="cc887-107">If `StepOut` is called when in unmanaged code, the step will complete when the current frame returns to the managed code that called it.</span></span>  
  
 <span data-ttu-id="cc887-108">No .NET Framework versão 2.0, não use `StepOut` com o STOP_UNMANAGED sinalizador definido porque ele falhará.</span><span class="sxs-lookup"><span data-stu-id="cc887-108">In the .NET Framework version 2.0, do not use `StepOut` with the STOP_UNMANAGED flag set because it will fail.</span></span> <span data-ttu-id="cc887-109">(Use [ICorDebugStepper:: Setunmappedstopmask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) definir sinalizadores de passo a passo.) Depuradores de interoperabilidade devem sair para código nativo em si.</span><span class="sxs-lookup"><span data-stu-id="cc887-109">(Use [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) to set flags for stepping.) Interop debuggers must step out to native code themselves.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc887-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cc887-110">Requirements</span></span>  
 <span data-ttu-id="cc887-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc887-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc887-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cc887-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cc887-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cc887-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cc887-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc887-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
