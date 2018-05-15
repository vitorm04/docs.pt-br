---
title: Método ICorDebugStepper::SetInterceptMask
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.SetInterceptMask
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::SetInterceptMask
helpviewer_keywords:
- SetInterceptMask method [.NET Framework debugging]
- ICorDebugStepper::SetInterceptMask method [.NET Framework debugging]
ms.assetid: 6245e2ae-5cc2-43ff-8cc1-71953d12113a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7654a91180dd0b4148cfb85b35bf1ce730764f28
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugsteppersetinterceptmask-method"></a><span data-ttu-id="a5e08-102">Método ICorDebugStepper::SetInterceptMask</span><span class="sxs-lookup"><span data-stu-id="a5e08-102">ICorDebugStepper::SetInterceptMask Method</span></span>
<span data-ttu-id="a5e08-103">Define um valor que especifica os tipos de código que são entrado em.</span><span class="sxs-lookup"><span data-stu-id="a5e08-103">Sets a value that specifies the types of code that are stepped into.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5e08-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a5e08-104">Syntax</span></span>  
  
```  
HRESULT SetInterceptMask (  
    [in] CorDebugIntercept    mask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a5e08-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a5e08-105">Parameters</span></span>  
 `mask`  
 <span data-ttu-id="a5e08-106">[in] Uma combinação de valores da enumeração CorDebugIntercept que especifica os tipos de código.</span><span class="sxs-lookup"><span data-stu-id="a5e08-106">[in] A combination of values of the CorDebugIntercept enumeration that specifies the types of code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a5e08-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="a5e08-107">Remarks</span></span>  
 <span data-ttu-id="a5e08-108">Se o bit de um interceptor for definido, o seletor será concluída quando o tipo determinado de interceptação de código é encontrado.</span><span class="sxs-lookup"><span data-stu-id="a5e08-108">If the bit for an interceptor is set, the stepper will complete when the given type of intercepting code is encountered.</span></span> <span data-ttu-id="a5e08-109">Se o bit estiver desmarcado, o código interceptando será ignorado.</span><span class="sxs-lookup"><span data-stu-id="a5e08-109">If the bit is cleared, the intercepting code will be skipped.</span></span>  
  
 <span data-ttu-id="a5e08-110">O `SetInterceptMask` método pode ter imprevistas interações com [: Setunmappedstopmask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) (a partir do ponto de vista do usuário).</span><span class="sxs-lookup"><span data-stu-id="a5e08-110">The `SetInterceptMask` method may have unforeseen interactions with [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) (from the user's point of view).</span></span> <span data-ttu-id="a5e08-111">Por exemplo, se visível somente (ou seja, não interno) parte do código de inicialização de classe não tem informações de mapeamento e STOP_NO_MAPPING_INFO não está definido (consulte o [: Setunmappedstopmask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) método e o Enumeração CorDebugUnmappedStop), o seletor orientará sobre a inicialização de classe.</span><span class="sxs-lookup"><span data-stu-id="a5e08-111">For example, if the only visible (that is, non-internal) portion of class initialization code lacks mapping information and STOP_NO_MAPPING_INFO isn't set (see the [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) method and the CorDebugUnmappedStop enumeration), the stepper will step over the class initialization.</span></span> <span data-ttu-id="a5e08-112">Por padrão, somente o valor INTERCEPT_NONE do `CorDebugIntercept` enumeração será usada.</span><span class="sxs-lookup"><span data-stu-id="a5e08-112">By default, only the INTERCEPT_NONE value of the `CorDebugIntercept` enumeration will be used.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5e08-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a5e08-113">Requirements</span></span>  
 <span data-ttu-id="a5e08-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5e08-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5e08-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a5e08-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a5e08-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a5e08-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a5e08-117">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5e08-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
