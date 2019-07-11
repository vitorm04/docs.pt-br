---
title: Método ICorDebugStepper::SetRangeIL
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.SetRangeIL
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::SetRangeIL
helpviewer_keywords:
- SetRangeIL method [.NET Framework debugging]
- ICorDebugStepper::SetRangeIL method [.NET Framework debugging]
ms.assetid: a20c95f0-6da7-4b41-b27f-584211cebb92
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 610225708bf990850fce73d6d7ff66c556e24e5d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760598"
---
# <a name="icordebugsteppersetrangeil-method"></a><span data-ttu-id="92513-102">Método ICorDebugStepper::SetRangeIL</span><span class="sxs-lookup"><span data-stu-id="92513-102">ICorDebugStepper::SetRangeIL Method</span></span>
<span data-ttu-id="92513-103">Define um valor que especifica se chamadas para [ICorDebugStepper:: Steprange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) passar argumento código language (MSIL) do método que está sendo de nível intermediário de valores que são relativos ao código nativo ou em relação à Microsoft por meio do.</span><span class="sxs-lookup"><span data-stu-id="92513-103">Sets a value that specifies whether calls to [ICorDebugStepper::StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) pass argument values that are relative to the native code or relative to Microsoft intermediate language (MSIL) code of the method that is being stepped through.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92513-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="92513-104">Syntax</span></span>  
  
```cpp  
HRESULT SetRangeIL (  
    [in] BOOL    bIL  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92513-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="92513-105">Parameters</span></span>  
 `bIL`  
 <span data-ttu-id="92513-106">[in] Definido como `true` para especificar que os intervalos são em relação ao código MSIL.</span><span class="sxs-lookup"><span data-stu-id="92513-106">[in] Set to `true` to specify that the ranges are relative to the MSIL code.</span></span> <span data-ttu-id="92513-107">Definido como `false` para especificar que os intervalos são em relação ao código nativo.</span><span class="sxs-lookup"><span data-stu-id="92513-107">Set to `false` to specify that the ranges are relative to the native code.</span></span> <span data-ttu-id="92513-108">O valor padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="92513-108">The default value is `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92513-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="92513-109">Requirements</span></span>  
 <span data-ttu-id="92513-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92513-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92513-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="92513-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="92513-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="92513-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="92513-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92513-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
