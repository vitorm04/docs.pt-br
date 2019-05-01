---
title: Método ICorDebugStepper::Step
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.Step
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::Step
helpviewer_keywords:
- Step method, ICorDebugStepper interface [.NET Framework debugging]
- ICorDebugStepper::Step method [.NET Framework debugging]
ms.assetid: 38c1940b-ada1-40ba-8295-4c0833744e1e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 444390622ca68244661b91dc85814b05556b12a2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61994312"
---
# <a name="icordebugstepperstep-method"></a><span data-ttu-id="2643a-102">Método ICorDebugStepper::Step</span><span class="sxs-lookup"><span data-stu-id="2643a-102">ICorDebugStepper::Step Method</span></span>
<span data-ttu-id="2643a-103">Faz com que esse ICorDebugStepper a etapa única por meio de seu recipiente thread e, opcionalmente, para continuar a depuração de único por meio de funções que são chamadas de dentro do thread.</span><span class="sxs-lookup"><span data-stu-id="2643a-103">Causes this ICorDebugStepper to single-step through its containing thread, and optionally, to continue single-stepping through functions that are called within the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2643a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2643a-104">Syntax</span></span>  
  
```  
HRESULT Step (  
    [in] BOOL   bStepIn  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2643a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2643a-105">Parameters</span></span>  
 `bStepIn`  
 <span data-ttu-id="2643a-106">[in] Definido como `true` para entrar em uma função que é chamada dentro do thread.</span><span class="sxs-lookup"><span data-stu-id="2643a-106">[in] Set to `true` to step into a function that is called within the thread.</span></span> <span data-ttu-id="2643a-107">Definido como `false` para ignorar a função.</span><span class="sxs-lookup"><span data-stu-id="2643a-107">Set to `false` to step over the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2643a-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="2643a-108">Remarks</span></span>  
 <span data-ttu-id="2643a-109">A etapa é concluída quando o common language runtime executa a próxima instrução gerenciada no quadro deste seletor.</span><span class="sxs-lookup"><span data-stu-id="2643a-109">The step completes when the common language runtime performs the next managed instruction in this stepper's frame.</span></span> <span data-ttu-id="2643a-110">Se `Step` é chamado em um seletor, que não está no código gerenciado, a etapa será concluída quando a próxima instrução de código gerenciado é executada pelo thread.</span><span class="sxs-lookup"><span data-stu-id="2643a-110">If `Step` is called on a stepper, which is not in managed code, the step will complete when the next managed code instruction is executed by the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2643a-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2643a-111">Requirements</span></span>  
 <span data-ttu-id="2643a-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2643a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2643a-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2643a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2643a-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2643a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2643a-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2643a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
