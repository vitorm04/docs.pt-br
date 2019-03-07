---
title: Método ICorDebugStepper::StepRange
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.StepRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::StepRange
helpviewer_keywords:
- StepRange method [.NET Framework debugging]
- ICorDebugStepper::StepRange method [.NET Framework debugging]
ms.assetid: b9776112-6e6d-4708-892a-8873db02e16f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7b18474aeaa79224de5371df3ff0cac5ed9bf4ff
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57475730"
---
# <a name="icordebugsteppersteprange-method"></a><span data-ttu-id="ea45a-102">Método ICorDebugStepper::StepRange</span><span class="sxs-lookup"><span data-stu-id="ea45a-102">ICorDebugStepper::StepRange Method</span></span>
<span data-ttu-id="ea45a-103">Faz com que esse ICorDebugStepper a etapa única por meio de seu recipiente thread e para retornar quando ele atinge o código além do último dos intervalos especificados.</span><span class="sxs-lookup"><span data-stu-id="ea45a-103">Causes this ICorDebugStepper to single-step through its containing thread, and to return when it reaches code beyond the last of the specified ranges.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea45a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ea45a-104">Syntax</span></span>  
  
```  
HRESULT StepRange (  
    [in] BOOL     bStepIn,  
    [in, size_is(cRangeCount)] COR_DEBUG_STEP_RANGE ranges[],  
    [in] ULONG32  cRangeCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea45a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ea45a-105">Parameters</span></span>  
 `bStepIn`  
 <span data-ttu-id="ea45a-106">[in] Definido como `true` para entrar em uma função que é chamada dentro do thread.</span><span class="sxs-lookup"><span data-stu-id="ea45a-106">[in] Set to `true` to step into a function that is called within the thread.</span></span> <span data-ttu-id="ea45a-107">Definido como `false` para ignorar a função.</span><span class="sxs-lookup"><span data-stu-id="ea45a-107">Set to `false` to step over the function.</span></span>  
  
 `ranges`  
 <span data-ttu-id="ea45a-108">[in] Uma matriz de estruturas COR_DEBUG_STEP_RANGE, cada um deles especifica um intervalo.</span><span class="sxs-lookup"><span data-stu-id="ea45a-108">[in] An array of COR_DEBUG_STEP_RANGE structures, each of which specifies a range.</span></span>  
  
 `cRangeCount`  
 <span data-ttu-id="ea45a-109">[in] O tamanho do `ranges` matriz.</span><span class="sxs-lookup"><span data-stu-id="ea45a-109">[in] The size of the `ranges` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ea45a-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="ea45a-110">Remarks</span></span>  
 <span data-ttu-id="ea45a-111">O `StepRange` método funciona como o [ICorDebugStepper:: Step](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md) método, exceto que ela não for concluída até que o código fora do intervalo especificado for atingido.</span><span class="sxs-lookup"><span data-stu-id="ea45a-111">The `StepRange` method works like the [ICorDebugStepper::Step](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md) method, except that it does not complete until code outside the given range is reached.</span></span>  
  
 <span data-ttu-id="ea45a-112">Isso pode ser mais eficiente do que o passo a passo de uma instrução por vez.</span><span class="sxs-lookup"><span data-stu-id="ea45a-112">This can be more efficient than stepping one instruction at a time.</span></span> <span data-ttu-id="ea45a-113">Intervalos são especificados como uma lista de pares de deslocamento do início do quadro do seletor.</span><span class="sxs-lookup"><span data-stu-id="ea45a-113">Ranges are specified as a list of offset pairs from the start of the stepper's frame.</span></span>  
  
 <span data-ttu-id="ea45a-114">Os intervalos são em relação ao código do Microsoft intermediate language (MSIL) de um método.</span><span class="sxs-lookup"><span data-stu-id="ea45a-114">Ranges are relative to the Microsoft intermediate language (MSIL) code of a method.</span></span> <span data-ttu-id="ea45a-115">Chame [ICorDebugStepper:: Setrangeil](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md) com `false` para tornar os intervalos em relação ao código nativo de um método.</span><span class="sxs-lookup"><span data-stu-id="ea45a-115">Call [ICorDebugStepper::SetRangeIL](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md) with `false` to make the ranges relative to the native code of a method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea45a-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ea45a-116">Requirements</span></span>  
 <span data-ttu-id="ea45a-117">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea45a-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea45a-118">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ea45a-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ea45a-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ea45a-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ea45a-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea45a-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
