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
ms.openlocfilehash: 21b8bf618e197372e301d5f56e7592c20710014d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791717"
---
# <a name="icordebugsteppersteprange-method"></a><span data-ttu-id="aa135-102">Método ICorDebugStepper::StepRange</span><span class="sxs-lookup"><span data-stu-id="aa135-102">ICorDebugStepper::StepRange Method</span></span>
<span data-ttu-id="aa135-103">Faz com que esse ICorDebugStepper faça uma única etapa por meio de seu thread que o contém e retorne quando ele atinge o código além do último intervalo especificado.</span><span class="sxs-lookup"><span data-stu-id="aa135-103">Causes this ICorDebugStepper to single-step through its containing thread, and to return when it reaches code beyond the last of the specified ranges.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa135-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="aa135-104">Syntax</span></span>  
  
```cpp  
HRESULT StepRange (  
    [in] BOOL     bStepIn,  
    [in, size_is(cRangeCount)] COR_DEBUG_STEP_RANGE ranges[],  
    [in] ULONG32  cRangeCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aa135-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="aa135-105">Parameters</span></span>  
 `bStepIn`  
 <span data-ttu-id="aa135-106">no Defina como `true` para entrar em uma função que é chamada dentro do thread.</span><span class="sxs-lookup"><span data-stu-id="aa135-106">[in] Set to `true` to step into a function that is called within the thread.</span></span> <span data-ttu-id="aa135-107">Defina como `false` para percorrer a função.</span><span class="sxs-lookup"><span data-stu-id="aa135-107">Set to `false` to step over the function.</span></span>  
  
 `ranges`  
 <span data-ttu-id="aa135-108">no Uma matriz de estruturas COR_DEBUG_STEP_RANGE, cada uma delas especifica um intervalo.</span><span class="sxs-lookup"><span data-stu-id="aa135-108">[in] An array of COR_DEBUG_STEP_RANGE structures, each of which specifies a range.</span></span>  
  
 `cRangeCount`  
 <span data-ttu-id="aa135-109">no O tamanho da matriz de `ranges`.</span><span class="sxs-lookup"><span data-stu-id="aa135-109">[in] The size of the `ranges` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aa135-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="aa135-110">Remarks</span></span>  
 <span data-ttu-id="aa135-111">O método `StepRange` funciona como o método [ICorDebugStepper:: Step](icordebugstepper-step-method.md) , exceto que ele não é concluído até que o código fora do intervalo especificado seja atingido.</span><span class="sxs-lookup"><span data-stu-id="aa135-111">The `StepRange` method works like the [ICorDebugStepper::Step](icordebugstepper-step-method.md) method, except that it does not complete until code outside the given range is reached.</span></span>  
  
 <span data-ttu-id="aa135-112">Isso pode ser mais eficiente do que a depuração de uma instrução por vez.</span><span class="sxs-lookup"><span data-stu-id="aa135-112">This can be more efficient than stepping one instruction at a time.</span></span> <span data-ttu-id="aa135-113">Os intervalos são especificados como uma lista de pares de deslocamento do início do quadro do stepper.</span><span class="sxs-lookup"><span data-stu-id="aa135-113">Ranges are specified as a list of offset pairs from the start of the stepper's frame.</span></span>  
  
 <span data-ttu-id="aa135-114">Os intervalos são relativos ao código da MSIL (Microsoft Intermediate Language) de um método.</span><span class="sxs-lookup"><span data-stu-id="aa135-114">Ranges are relative to the Microsoft intermediate language (MSIL) code of a method.</span></span> <span data-ttu-id="aa135-115">Chame [ICorDebugStepper:: SetRangeIL](icordebugstepper-setrangeil-method.md) com `false` para tornar os intervalos relativos ao código nativo de um método.</span><span class="sxs-lookup"><span data-stu-id="aa135-115">Call [ICorDebugStepper::SetRangeIL](icordebugstepper-setrangeil-method.md) with `false` to make the ranges relative to the native code of a method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa135-116">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="aa135-116">Requirements</span></span>  
 <span data-ttu-id="aa135-117">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aa135-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa135-118">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aa135-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aa135-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aa135-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aa135-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa135-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
