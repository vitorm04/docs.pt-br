---
title: "Método ICorDebugStepper::IsActive"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStepper.IsActive
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStepper::IsActive
helpviewer_keywords:
- IsActive method, ICorDebugStepper interface [.NET Framework debugging]
- ICorDebugStepper::IsActive method [.NET Framework debugging]
ms.assetid: 8b35e7a9-b40e-40a9-8d8e-b82e823fc575
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dd919852d3e7c187dff7fc4304d0a1b42f5294e0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugstepperisactive-method"></a><span data-ttu-id="2fe44-102">Método ICorDebugStepper::IsActive</span><span class="sxs-lookup"><span data-stu-id="2fe44-102">ICorDebugStepper::IsActive Method</span></span>
<span data-ttu-id="2fe44-103">Obtém um valor que indica se este ICorDebugStepper está atualmente executando uma etapa.</span><span class="sxs-lookup"><span data-stu-id="2fe44-103">Gets a value that indicates whether this ICorDebugStepper is currently executing a step.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fe44-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2fe44-104">Syntax</span></span>  
  
```  
HRESULT IsActive (  
    [out] BOOL   *pbActive  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2fe44-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2fe44-105">Parameters</span></span>  
 `pbActive`  
 <span data-ttu-id="2fe44-106">[out] Retorna `true` se o seletor está executando uma etapa; caso contrário, retornará `false`.</span><span class="sxs-lookup"><span data-stu-id="2fe44-106">[out] Returns `true` if the stepper is currently executing a step; otherwise, returns `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2fe44-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="2fe44-107">Remarks</span></span>  
 <span data-ttu-id="2fe44-108">Qualquer ação de etapa permanece ativa até que o depurador recebe um [: Stepcomplete](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md) chamar, que automaticamente desativa o seletor.</span><span class="sxs-lookup"><span data-stu-id="2fe44-108">Any step action remains active until the debugger receives a [ICorDebugManagedCallback::StepComplete](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md) call, which automatically deactivates the stepper.</span></span> <span data-ttu-id="2fe44-109">Um seletor também pode ser desativado prematuramente chamando [ICorDebugStepper](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-deactivate-method.md) antes do retorno de chamada condição for atingida.</span><span class="sxs-lookup"><span data-stu-id="2fe44-109">A stepper may also be deactivated prematurely by calling [ICorDebugStepper::Deactivate](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-deactivate-method.md) before the callback condition is reached.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2fe44-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2fe44-110">Requirements</span></span>  
 <span data-ttu-id="2fe44-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2fe44-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2fe44-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2fe44-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2fe44-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2fe44-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2fe44-114">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2fe44-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
