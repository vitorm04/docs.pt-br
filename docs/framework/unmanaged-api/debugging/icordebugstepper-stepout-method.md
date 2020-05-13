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
ms.openlocfilehash: 9f6962f987079da1ccb04ea368307d7c119910a6
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379500"
---
# <a name="icordebugstepperstepout-method"></a><span data-ttu-id="59b87-102">Método ICorDebugStepper::StepOut</span><span class="sxs-lookup"><span data-stu-id="59b87-102">ICorDebugStepper::StepOut Method</span></span>
<span data-ttu-id="59b87-103">Faz com que esse ICorDebugStepper faça uma única etapa por meio de seu thread que o contém e seja concluído quando o quadro atual retorna o controle para o quadro de chamada.</span><span class="sxs-lookup"><span data-stu-id="59b87-103">Causes this ICorDebugStepper to single-step through its containing thread, and to complete when the current frame returns control to the calling frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59b87-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="59b87-104">Syntax</span></span>  
  
```cpp  
HRESULT StepOut ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="59b87-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="59b87-105">Remarks</span></span>  
 <span data-ttu-id="59b87-106">Uma `StepOut` operação será concluída depois de retornar normalmente do quadro atual para o quadro de chamada.</span><span class="sxs-lookup"><span data-stu-id="59b87-106">A `StepOut` operation will complete after returning normally from the current frame to the calling frame.</span></span>  
  
 <span data-ttu-id="59b87-107">Se `StepOut` for chamado quando estiver no código não gerenciado, a etapa será concluída quando o quadro atual retornar ao código gerenciado que o chamou.</span><span class="sxs-lookup"><span data-stu-id="59b87-107">If `StepOut` is called when in unmanaged code, the step will complete when the current frame returns to the managed code that called it.</span></span>  
  
 <span data-ttu-id="59b87-108">No .NET Framework versão 2,0, não use `StepOut` com o sinalizador STOP_UNMANAGED definido porque ele falhará.</span><span class="sxs-lookup"><span data-stu-id="59b87-108">In the .NET Framework version 2.0, do not use `StepOut` with the STOP_UNMANAGED flag set because it will fail.</span></span> <span data-ttu-id="59b87-109">(Use [ICorDebugStepper:: SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) para definir sinalizadores para depuração.) Os depuradores de interoperabilidade devem sair para o próprio código nativo.</span><span class="sxs-lookup"><span data-stu-id="59b87-109">(Use [ICorDebugStepper::SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) to set flags for stepping.) Interop debuggers must step out to native code themselves.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59b87-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="59b87-110">Requirements</span></span>  
 <span data-ttu-id="59b87-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59b87-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59b87-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="59b87-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="59b87-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="59b87-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="59b87-114">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59b87-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
