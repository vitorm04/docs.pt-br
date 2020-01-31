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
ms.openlocfilehash: b3153a88867d249aad8365bb774348fb8c9d57d5
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791745"
---
# <a name="icordebugsteppersetrangeil-method"></a><span data-ttu-id="20fa8-102">Método ICorDebugStepper::SetRangeIL</span><span class="sxs-lookup"><span data-stu-id="20fa8-102">ICorDebugStepper::SetRangeIL Method</span></span>
<span data-ttu-id="20fa8-103">Define um valor que especifica se as chamadas para [ICorDebugStepper:: StepRange](icordebugstepper-steprange-method.md) passam valores de argumentos que são relativos ao código nativo ou em relação ao código MSIL (Microsoft Intermediate Language) do método que está sendo percorrido.</span><span class="sxs-lookup"><span data-stu-id="20fa8-103">Sets a value that specifies whether calls to [ICorDebugStepper::StepRange](icordebugstepper-steprange-method.md) pass argument values that are relative to the native code or relative to Microsoft intermediate language (MSIL) code of the method that is being stepped through.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20fa8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="20fa8-104">Syntax</span></span>  
  
```cpp  
HRESULT SetRangeIL (  
    [in] BOOL    bIL  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="20fa8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="20fa8-105">Parameters</span></span>  
 `bIL`  
 <span data-ttu-id="20fa8-106">no Defina como `true` para especificar que os intervalos são relativos ao código MSIL.</span><span class="sxs-lookup"><span data-stu-id="20fa8-106">[in] Set to `true` to specify that the ranges are relative to the MSIL code.</span></span> <span data-ttu-id="20fa8-107">Defina como `false` para especificar que os intervalos são relativos ao código nativo.</span><span class="sxs-lookup"><span data-stu-id="20fa8-107">Set to `false` to specify that the ranges are relative to the native code.</span></span> <span data-ttu-id="20fa8-108">O valor padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="20fa8-108">The default value is `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20fa8-109">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="20fa8-109">Requirements</span></span>  
 <span data-ttu-id="20fa8-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20fa8-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20fa8-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="20fa8-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="20fa8-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="20fa8-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="20fa8-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20fa8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
