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
ms.openlocfilehash: e88fa543eca39c14962f0dbbe8053829713401c8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137576"
---
# <a name="icordebugsteppersetinterceptmask-method"></a><span data-ttu-id="76dfd-102">Método ICorDebugStepper::SetInterceptMask</span><span class="sxs-lookup"><span data-stu-id="76dfd-102">ICorDebugStepper::SetInterceptMask Method</span></span>
<span data-ttu-id="76dfd-103">Define um valor que especifica os tipos de código que são percorridos.</span><span class="sxs-lookup"><span data-stu-id="76dfd-103">Sets a value that specifies the types of code that are stepped into.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76dfd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="76dfd-104">Syntax</span></span>  
  
```cpp  
HRESULT SetInterceptMask (  
    [in] CorDebugIntercept    mask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="76dfd-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="76dfd-105">Parameters</span></span>  
 `mask`  
 <span data-ttu-id="76dfd-106">no Uma combinação de valores da enumeração CorDebugIntercept que especifica os tipos de código.</span><span class="sxs-lookup"><span data-stu-id="76dfd-106">[in] A combination of values of the CorDebugIntercept enumeration that specifies the types of code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="76dfd-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="76dfd-107">Remarks</span></span>  
 <span data-ttu-id="76dfd-108">Se o bit de um interceptor for definido, o stepper será concluído quando o tipo de código de interceptação for encontrado.</span><span class="sxs-lookup"><span data-stu-id="76dfd-108">If the bit for an interceptor is set, the stepper will complete when the given type of intercepting code is encountered.</span></span> <span data-ttu-id="76dfd-109">Se o bit for apagado, o código de interceptação será ignorado.</span><span class="sxs-lookup"><span data-stu-id="76dfd-109">If the bit is cleared, the intercepting code will be skipped.</span></span>  
  
 <span data-ttu-id="76dfd-110">O método `SetInterceptMask` pode ter interações imprevistas com [ICorDebugStepper:: SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) (do ponto de vista do usuário).</span><span class="sxs-lookup"><span data-stu-id="76dfd-110">The `SetInterceptMask` method may have unforeseen interactions with [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) (from the user's point of view).</span></span> <span data-ttu-id="76dfd-111">Por exemplo, se a única parte visível (ou seja, não interna) do código de inicialização da classe não tiver informações de mapeamento e STOP_NO_MAPPING_INFO não estiver definido (consulte o método [ICorDebugStepper:: SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) e o CorDebugUnmappedStop Enumeração), o stepper passará pela inicialização da classe.</span><span class="sxs-lookup"><span data-stu-id="76dfd-111">For example, if the only visible (that is, non-internal) portion of class initialization code lacks mapping information and STOP_NO_MAPPING_INFO isn't set (see the [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) method and the CorDebugUnmappedStop enumeration), the stepper will step over the class initialization.</span></span> <span data-ttu-id="76dfd-112">Por padrão, somente o valor INTERCEPT_NONE da enumeração `CorDebugIntercept` será usado.</span><span class="sxs-lookup"><span data-stu-id="76dfd-112">By default, only the INTERCEPT_NONE value of the `CorDebugIntercept` enumeration will be used.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76dfd-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="76dfd-113">Requirements</span></span>  
 <span data-ttu-id="76dfd-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="76dfd-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76dfd-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="76dfd-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="76dfd-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="76dfd-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="76dfd-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76dfd-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
