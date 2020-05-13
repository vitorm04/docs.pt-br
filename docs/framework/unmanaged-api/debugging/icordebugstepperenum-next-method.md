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
ms.openlocfilehash: 293d1a9cd93b5ce45105427e7df864ad8bfbe77a
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379189"
---
# <a name="icordebugstepperenumnext-method"></a><span data-ttu-id="11f62-102">Método ICorDebugStepperEnum::Next</span><span class="sxs-lookup"><span data-stu-id="11f62-102">ICorDebugStepperEnum::Next Method</span></span>
<span data-ttu-id="11f62-103">Obtém o número especificado de instâncias de ICorDebugStepper da enumeração, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="11f62-103">Gets the specified number of ICorDebugStepper instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11f62-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="11f62-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugStepper *steppers[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="11f62-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="11f62-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="11f62-106">no O número de `ICorDebugStepper` instâncias a serem recuperadas.</span><span class="sxs-lookup"><span data-stu-id="11f62-106">[in] The number of `ICorDebugStepper` instances to be retrieved.</span></span>  
  
 `steppers`  
 <span data-ttu-id="11f62-107">fora Uma matriz de ponteiros, cada um dos quais aponta para um `ICorDebugStepper` objeto.</span><span class="sxs-lookup"><span data-stu-id="11f62-107">[out] An array of pointers, each of which points to an `ICorDebugStepper` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="11f62-108">fora Aponta para o número de `ICorDebugStepper` instâncias realmente retornadas.</span><span class="sxs-lookup"><span data-stu-id="11f62-108">[out] Pointer to the number of `ICorDebugStepper` instances actually returned.</span></span> <span data-ttu-id="11f62-109">Esse valor pode ser nulo se `celt` for um.</span><span class="sxs-lookup"><span data-stu-id="11f62-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11f62-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="11f62-110">Requirements</span></span>  
 <span data-ttu-id="11f62-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11f62-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11f62-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="11f62-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="11f62-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="11f62-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="11f62-114">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11f62-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
