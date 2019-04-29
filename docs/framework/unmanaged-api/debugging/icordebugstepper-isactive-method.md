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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d4166b63e0bb0ae276c48abb961e381809cc9792
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763744"
---
# <a name="icordebugstepperisactive-method"></a><span data-ttu-id="355c2-102">Método ICorDebugStepper::IsActive</span><span class="sxs-lookup"><span data-stu-id="355c2-102">ICorDebugStepper::IsActive Method</span></span>
<span data-ttu-id="355c2-103">Obtém um valor que indica se este ICorDebugStepper está atualmente executando uma etapa.</span><span class="sxs-lookup"><span data-stu-id="355c2-103">Gets a value that indicates whether this ICorDebugStepper is currently executing a step.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="355c2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="355c2-104">Syntax</span></span>  
  
```  
HRESULT IsActive (  
    [out] BOOL   *pbActive  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="355c2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="355c2-105">Parameters</span></span>  
 `pbActive`  
 <span data-ttu-id="355c2-106">[out] Retorna `true` se o escalonador está em execução no momento uma etapa; caso contrário, retornará `false`.</span><span class="sxs-lookup"><span data-stu-id="355c2-106">[out] Returns `true` if the stepper is currently executing a step; otherwise, returns `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="355c2-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="355c2-107">Remarks</span></span>  
 <span data-ttu-id="355c2-108">Qualquer ação da etapa permanece ativa até que o depurador recebe uma [icordebugmanagedcallback:: Stepcomplete](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md) chamar, que será desativada automaticamente passador.</span><span class="sxs-lookup"><span data-stu-id="355c2-108">Any step action remains active until the debugger receives a [ICorDebugManagedCallback::StepComplete](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md) call, which automatically deactivates the stepper.</span></span> <span data-ttu-id="355c2-109">Um seletor também pode ser desativado prematuramente chamando [ICorDebugStepper:: Deactivate](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-deactivate-method.md) antes do retorno de chamada a condição for atingida.</span><span class="sxs-lookup"><span data-stu-id="355c2-109">A stepper may also be deactivated prematurely by calling [ICorDebugStepper::Deactivate](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-deactivate-method.md) before the callback condition is reached.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="355c2-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="355c2-110">Requirements</span></span>  
 <span data-ttu-id="355c2-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="355c2-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="355c2-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="355c2-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="355c2-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="355c2-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="355c2-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="355c2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
