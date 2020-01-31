---
title: Método ICorDebugStepper::IsActive
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.IsActive
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::IsActive
helpviewer_keywords:
- IsActive method, ICorDebugStepper interface [.NET Framework debugging]
- ICorDebugStepper::IsActive method [.NET Framework debugging]
ms.assetid: 8b35e7a9-b40e-40a9-8d8e-b82e823fc575
topic_type:
- apiref
ms.openlocfilehash: 703f454f7ed1d2a959b761726f433db22cb73b01
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791781"
---
# <a name="icordebugstepperisactive-method"></a><span data-ttu-id="e92e4-102">Método ICorDebugStepper::IsActive</span><span class="sxs-lookup"><span data-stu-id="e92e4-102">ICorDebugStepper::IsActive Method</span></span>
<span data-ttu-id="e92e4-103">Obtém um valor que indica se este ICorDebugStepper está executando uma etapa no momento.</span><span class="sxs-lookup"><span data-stu-id="e92e4-103">Gets a value that indicates whether this ICorDebugStepper is currently executing a step.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e92e4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e92e4-104">Syntax</span></span>  
  
```cpp  
HRESULT IsActive (  
    [out] BOOL   *pbActive  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e92e4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e92e4-105">Parameters</span></span>  
 `pbActive`  
 <span data-ttu-id="e92e4-106">fora Retorna `true` se o stepper estiver executando uma etapa no momento; caso contrário, retorna `false`.</span><span class="sxs-lookup"><span data-stu-id="e92e4-106">[out] Returns `true` if the stepper is currently executing a step; otherwise, returns `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e92e4-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="e92e4-107">Remarks</span></span>  
 <span data-ttu-id="e92e4-108">Qualquer ação de etapa permanece ativa até que o depurador receba uma chamada [ICorDebugManagedCallback:: StepComplete](icordebugmanagedcallback-stepcomplete-method.md) , que desativa automaticamente o stepper.</span><span class="sxs-lookup"><span data-stu-id="e92e4-108">Any step action remains active until the debugger receives a [ICorDebugManagedCallback::StepComplete](icordebugmanagedcallback-stepcomplete-method.md) call, which automatically deactivates the stepper.</span></span> <span data-ttu-id="e92e4-109">Um stepper também pode ser desativado prematuramente chamando [ICorDebugStepper::D eactivate](icordebugstepper-deactivate-method.md) antes que a condição de retorno de chamada seja atingida.</span><span class="sxs-lookup"><span data-stu-id="e92e4-109">A stepper may also be deactivated prematurely by calling [ICorDebugStepper::Deactivate](icordebugstepper-deactivate-method.md) before the callback condition is reached.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e92e4-110">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="e92e4-110">Requirements</span></span>  
 <span data-ttu-id="e92e4-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e92e4-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e92e4-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e92e4-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e92e4-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e92e4-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e92e4-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e92e4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
