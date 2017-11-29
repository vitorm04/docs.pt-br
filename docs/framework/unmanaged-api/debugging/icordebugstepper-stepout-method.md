---
title: "Método ICorDebugStepper::StepOut"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStepper.StepOut
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStepper::StepOut
helpviewer_keywords:
- ICorDebugStepper::StepOut method [.NET Framework debugging]
- StepOut method [.NET Framework debugging]
ms.assetid: aae0f48c-4ede-4256-9251-a7fc85a229dc
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8b3ceca69b6b4710a3f1b8e1e9bdb4baf574119c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugstepperstepout-method"></a><span data-ttu-id="7ade7-102">Método ICorDebugStepper::StepOut</span><span class="sxs-lookup"><span data-stu-id="7ade7-102">ICorDebugStepper::StepOut Method</span></span>
<span data-ttu-id="7ade7-103">Faz com que este ICorDebugStepper para percorrer por meio de seu recipiente thread e concluir quando o quadro atual retorna o controle para o quadro de chamada.</span><span class="sxs-lookup"><span data-stu-id="7ade7-103">Causes this ICorDebugStepper to single-step through its containing thread, and to complete when the current frame returns control to the calling frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ade7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7ade7-104">Syntax</span></span>  
  
```  
HRESULT StepOut ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="7ade7-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="7ade7-105">Remarks</span></span>  
 <span data-ttu-id="7ade7-106">Um `StepOut` operação será concluída após o retorno normalmente do quadro atual para o quadro de chamada.</span><span class="sxs-lookup"><span data-stu-id="7ade7-106">A `StepOut` operation will complete after returning normally from the current frame to the calling frame.</span></span>  
  
 <span data-ttu-id="7ade7-107">Se `StepOut` é chamado quando em código não gerenciado, a etapa será concluída quando o quadro atual retorna para o código gerenciado que o chamou.</span><span class="sxs-lookup"><span data-stu-id="7ade7-107">If `StepOut` is called when in unmanaged code, the step will complete when the current frame returns to the managed code that called it.</span></span>  
  
 <span data-ttu-id="7ade7-108">No .NET Framework versão 2.0, não use `StepOut` com o STOP_UNMANAGED o sinalizador será definido porque ele falhará.</span><span class="sxs-lookup"><span data-stu-id="7ade7-108">In the .NET Framework version 2.0, do not use `StepOut` with the STOP_UNMANAGED flag set because it will fail.</span></span> <span data-ttu-id="7ade7-109">(Use [: Setunmappedstopmask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) para definir os sinalizadores para depuração.) Interoperabilidade depuradores devem sair para código nativo próprios.</span><span class="sxs-lookup"><span data-stu-id="7ade7-109">(Use [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) to set flags for stepping.) Interop debuggers must step out to native code themselves.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ade7-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7ade7-110">Requirements</span></span>  
 <span data-ttu-id="7ade7-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ade7-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ade7-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7ade7-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7ade7-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7ade7-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7ade7-114">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ade7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
