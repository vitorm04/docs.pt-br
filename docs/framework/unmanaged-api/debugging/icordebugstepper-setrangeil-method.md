---
title: "Método ICorDebugStepper::SetRangeIL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStepper.SetRangeIL
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStepper::SetRangeIL
helpviewer_keywords:
- SetRangeIL method [.NET Framework debugging]
- ICorDebugStepper::SetRangeIL method [.NET Framework debugging]
ms.assetid: a20c95f0-6da7-4b41-b27f-584211cebb92
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 658f0164a73cfb5dbab0379eda2f61505865d2c4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsteppersetrangeil-method"></a><span data-ttu-id="0d83a-102">Método ICorDebugStepper::SetRangeIL</span><span class="sxs-lookup"><span data-stu-id="0d83a-102">ICorDebugStepper::SetRangeIL Method</span></span>
<span data-ttu-id="0d83a-103">Define um valor que especifica se chamadas para [: Steprange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) passar valores que são relativos ao código nativo ou em relação ao Microsoft intermediário código language (MSIL) do método que está sendo passado de argumento a.</span><span class="sxs-lookup"><span data-stu-id="0d83a-103">Sets a value that specifies whether calls to [ICorDebugStepper::StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) pass argument values that are relative to the native code or relative to Microsoft intermediate language (MSIL) code of the method that is being stepped through.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d83a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0d83a-104">Syntax</span></span>  
  
```  
HRESULT SetRangeIL (  
    [in] BOOL    bIL  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0d83a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0d83a-105">Parameters</span></span>  
 `bIL`  
 <span data-ttu-id="0d83a-106">[in] Definido como `true` para especificar que os intervalos são relativas ao código MSIL.</span><span class="sxs-lookup"><span data-stu-id="0d83a-106">[in] Set to `true` to specify that the ranges are relative to the MSIL code.</span></span> <span data-ttu-id="0d83a-107">Definido como `false` para especificar que os intervalos são relativas ao código nativo.</span><span class="sxs-lookup"><span data-stu-id="0d83a-107">Set to `false` to specify that the ranges are relative to the native code.</span></span> <span data-ttu-id="0d83a-108">O valor padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="0d83a-108">The default value is `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d83a-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0d83a-109">Requirements</span></span>  
 <span data-ttu-id="0d83a-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d83a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d83a-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0d83a-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0d83a-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0d83a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0d83a-113">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d83a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
