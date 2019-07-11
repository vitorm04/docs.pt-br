---
title: Método ICorDebugStepperEnum::Next
ms.date: 03/30/2017
api_name:
- ICorDebugStepperEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepperEnum::Next
helpviewer_keywords:
- Next method, ICorDebugStepperEnum interface [.NET Framework debugging]
- ICorDebugStepperEnum::Next method [.NET Framework debugging]
ms.assetid: d0ea0f30-e8d2-48b0-8477-e1a029ceb4dd
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 58f148eb4c3206ba12eed41df670846d7beab77a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771628"
---
# <a name="icordebugstepperenumnext-method"></a><span data-ttu-id="6a428-102">Método ICorDebugStepperEnum::Next</span><span class="sxs-lookup"><span data-stu-id="6a428-102">ICorDebugStepperEnum::Next Method</span></span>
<span data-ttu-id="6a428-103">Obtém o número especificado de instâncias de ICorDebugStepper de enumeração, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="6a428-103">Gets the specified number of ICorDebugStepper instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a428-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6a428-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugStepper *steppers[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6a428-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6a428-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="6a428-106">[in] O número de `ICorDebugStepper` instâncias a serem recuperados.</span><span class="sxs-lookup"><span data-stu-id="6a428-106">[in] The number of `ICorDebugStepper` instances to be retrieved.</span></span>  
  
 `steppers`  
 <span data-ttu-id="6a428-107">[out] Uma matriz de ponteiros, cada qual apontando para um `ICorDebugStepper` objeto.</span><span class="sxs-lookup"><span data-stu-id="6a428-107">[out] An array of pointers, each of which points to an `ICorDebugStepper` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="6a428-108">[out] Ponteiro para o número de `ICorDebugStepper` instâncias, na verdade, retornadas.</span><span class="sxs-lookup"><span data-stu-id="6a428-108">[out] Pointer to the number of `ICorDebugStepper` instances actually returned.</span></span> <span data-ttu-id="6a428-109">Esse valor pode ser nulo se `celt` é um.</span><span class="sxs-lookup"><span data-stu-id="6a428-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a428-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6a428-110">Requirements</span></span>  
 <span data-ttu-id="6a428-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a428-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a428-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6a428-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6a428-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6a428-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6a428-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a428-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
