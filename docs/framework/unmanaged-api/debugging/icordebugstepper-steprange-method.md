---
title: "Método ICorDebugStepper::StepRange"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStepper.StepRange
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStepper::StepRange
helpviewer_keywords:
- StepRange method [.NET Framework debugging]
- ICorDebugStepper::StepRange method [.NET Framework debugging]
ms.assetid: b9776112-6e6d-4708-892a-8873db02e16f
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 72a68000691dd23a55b77265cae839bea8b4ae1e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugsteppersteprange-method"></a><span data-ttu-id="b8c85-102">Método ICorDebugStepper::StepRange</span><span class="sxs-lookup"><span data-stu-id="b8c85-102">ICorDebugStepper::StepRange Method</span></span>
<span data-ttu-id="b8c85-103">Faz com que este ICorDebugStepper para percorrer por meio de seu recipiente thread e para retornar quando atingir código além do último dos intervalos especificados.</span><span class="sxs-lookup"><span data-stu-id="b8c85-103">Causes this ICorDebugStepper to single-step through its containing thread, and to return when it reaches code beyond the last of the specified ranges.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8c85-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b8c85-104">Syntax</span></span>  
  
```  
HRESULT StepRange (  
    [in] BOOL     bStepIn,  
    [in, size_is(cRangeCount)] COR_DEBUG_STEP_RANGE ranges[],  
    [in] ULONG32  cRangeCount  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b8c85-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b8c85-105">Parameters</span></span>  
 `bStepIn`  
 <span data-ttu-id="b8c85-106">[in] Definido como `true` para entrar em uma função que é chamada no thread.</span><span class="sxs-lookup"><span data-stu-id="b8c85-106">[in] Set to `true` to step into a function that is called within the thread.</span></span> <span data-ttu-id="b8c85-107">Definido como `false` ao passar sobre a função.</span><span class="sxs-lookup"><span data-stu-id="b8c85-107">Set to `false` to step over the function.</span></span>  
  
 `ranges`  
 <span data-ttu-id="b8c85-108">[in] Uma matriz de estruturas COR_DEBUG_STEP_RANGE, cada uma delas Especifica um intervalo.</span><span class="sxs-lookup"><span data-stu-id="b8c85-108">[in] An array of COR_DEBUG_STEP_RANGE structures, each of which specifies a range.</span></span>  
  
 `cRangeCount`  
 <span data-ttu-id="b8c85-109">[in] O tamanho do `ranges` matriz.</span><span class="sxs-lookup"><span data-stu-id="b8c85-109">[in] The size of the `ranges` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b8c85-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="b8c85-110">Remarks</span></span>  
 <span data-ttu-id="b8c85-111">O `StepRange` método funciona como o [ICorDebugStepper](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md) método, exceto que ela não for concluída até que o código fora do intervalo especificado for atingido.</span><span class="sxs-lookup"><span data-stu-id="b8c85-111">The `StepRange` method works like the [ICorDebugStepper::Step](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md) method, except that it does not complete until code outside the given range is reached.</span></span>  
  
 <span data-ttu-id="b8c85-112">Isso pode ser mais eficiente do que o passo a passo de uma instrução de cada vez.</span><span class="sxs-lookup"><span data-stu-id="b8c85-112">This can be more efficient than stepping one instruction at a time.</span></span> <span data-ttu-id="b8c85-113">Os intervalos são especificados como uma lista de pares de deslocamento do início do quadro do seletor.</span><span class="sxs-lookup"><span data-stu-id="b8c85-113">Ranges are specified as a list of offset pairs from the start of the stepper's frame.</span></span>  
  
 <span data-ttu-id="b8c85-114">Os intervalos são relativas ao código do Microsoft intermediate language (MSIL) de um método.</span><span class="sxs-lookup"><span data-stu-id="b8c85-114">Ranges are relative to the Microsoft intermediate language (MSIL) code of a method.</span></span> <span data-ttu-id="b8c85-115">Chamar [: Setrangeil](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md) com `false` para tornar os intervalos em relação o código nativo de um método.</span><span class="sxs-lookup"><span data-stu-id="b8c85-115">Call [ICorDebugStepper::SetRangeIL](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md) with `false` to make the ranges relative to the native code of a method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8c85-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b8c85-116">Requirements</span></span>  
 <span data-ttu-id="b8c85-117">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8c85-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8c85-118">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b8c85-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b8c85-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b8c85-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b8c85-120">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8c85-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
