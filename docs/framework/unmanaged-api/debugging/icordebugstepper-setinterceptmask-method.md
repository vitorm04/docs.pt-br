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
ms.openlocfilehash: aaba751a58e5b23b98b1d0629ea3cc9e1e7a83a9
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379015"
---
# <a name="icordebugsteppersetinterceptmask-method"></a><span data-ttu-id="aaf3e-102">Método ICorDebugStepper::SetInterceptMask</span><span class="sxs-lookup"><span data-stu-id="aaf3e-102">ICorDebugStepper::SetInterceptMask Method</span></span>
<span data-ttu-id="aaf3e-103">Define um valor que especifica os tipos de código que são percorridos.</span><span class="sxs-lookup"><span data-stu-id="aaf3e-103">Sets a value that specifies the types of code that are stepped into.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aaf3e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="aaf3e-104">Syntax</span></span>  
  
```cpp  
HRESULT SetInterceptMask (  
    [in] CorDebugIntercept    mask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aaf3e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="aaf3e-105">Parameters</span></span>  
 `mask`  
 <span data-ttu-id="aaf3e-106">no Uma combinação de valores da enumeração CorDebugIntercept que especifica os tipos de código.</span><span class="sxs-lookup"><span data-stu-id="aaf3e-106">[in] A combination of values of the CorDebugIntercept enumeration that specifies the types of code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aaf3e-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="aaf3e-107">Remarks</span></span>  
 <span data-ttu-id="aaf3e-108">Se o bit de um interceptor for definido, o stepper será concluído quando o tipo de código de interceptação for encontrado.</span><span class="sxs-lookup"><span data-stu-id="aaf3e-108">If the bit for an interceptor is set, the stepper will complete when the given type of intercepting code is encountered.</span></span> <span data-ttu-id="aaf3e-109">Se o bit for apagado, o código de interceptação será ignorado.</span><span class="sxs-lookup"><span data-stu-id="aaf3e-109">If the bit is cleared, the intercepting code will be skipped.</span></span>  
  
 <span data-ttu-id="aaf3e-110">O `SetInterceptMask` método pode ter interações imprevistas com [ICorDebugStepper:: SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) (do ponto de vista do usuário).</span><span class="sxs-lookup"><span data-stu-id="aaf3e-110">The `SetInterceptMask` method may have unforeseen interactions with [ICorDebugStepper::SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) (from the user's point of view).</span></span> <span data-ttu-id="aaf3e-111">Por exemplo, se a única parte visível (ou seja, não interna) do código de inicialização da classe não tiver informações de mapeamento e STOP_NO_MAPPING_INFO não estiver definida (consulte o método [ICorDebugStepper:: SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) e a Enumeração CorDebugUnmappedStop), o stepper passará pela inicialização da classe.</span><span class="sxs-lookup"><span data-stu-id="aaf3e-111">For example, if the only visible (that is, non-internal) portion of class initialization code lacks mapping information and STOP_NO_MAPPING_INFO isn't set (see the [ICorDebugStepper::SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) method and the CorDebugUnmappedStop enumeration), the stepper will step over the class initialization.</span></span> <span data-ttu-id="aaf3e-112">Por padrão, somente o valor INTERCEPT_NONE da `CorDebugIntercept` Enumeração será usado.</span><span class="sxs-lookup"><span data-stu-id="aaf3e-112">By default, only the INTERCEPT_NONE value of the `CorDebugIntercept` enumeration will be used.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aaf3e-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="aaf3e-113">Requirements</span></span>  
 <span data-ttu-id="aaf3e-114">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aaf3e-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aaf3e-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aaf3e-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aaf3e-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aaf3e-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aaf3e-117">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aaf3e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
