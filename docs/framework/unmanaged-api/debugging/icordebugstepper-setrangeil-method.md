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
ms.openlocfilehash: cb3c24b3a96a03359dc6983bcaac4a800613ff5d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugsteppersetrangeil-method"></a><span data-ttu-id="b2ce8-102">Método ICorDebugStepper::SetRangeIL</span><span class="sxs-lookup"><span data-stu-id="b2ce8-102">ICorDebugStepper::SetRangeIL Method</span></span>
<span data-ttu-id="b2ce8-103">Define um valor que especifica se chamadas para [: Steprange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) passar valores que são relativos ao código nativo ou em relação ao Microsoft intermediário código language (MSIL) do método que está sendo passado de argumento a.</span><span class="sxs-lookup"><span data-stu-id="b2ce8-103">Sets a value that specifies whether calls to [ICorDebugStepper::StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) pass argument values that are relative to the native code or relative to Microsoft intermediate language (MSIL) code of the method that is being stepped through.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2ce8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b2ce8-104">Syntax</span></span>  
  
```  
HRESULT SetRangeIL (  
    [in] BOOL    bIL  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b2ce8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b2ce8-105">Parameters</span></span>  
 `bIL`  
 <span data-ttu-id="b2ce8-106">[in] Definido como `true` para especificar que os intervalos são relativas ao código MSIL.</span><span class="sxs-lookup"><span data-stu-id="b2ce8-106">[in] Set to `true` to specify that the ranges are relative to the MSIL code.</span></span> <span data-ttu-id="b2ce8-107">Definido como `false` para especificar que os intervalos são relativas ao código nativo.</span><span class="sxs-lookup"><span data-stu-id="b2ce8-107">Set to `false` to specify that the ranges are relative to the native code.</span></span> <span data-ttu-id="b2ce8-108">O valor padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="b2ce8-108">The default value is `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2ce8-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b2ce8-109">Requirements</span></span>  
 <span data-ttu-id="b2ce8-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2ce8-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2ce8-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b2ce8-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b2ce8-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b2ce8-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b2ce8-113">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2ce8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
