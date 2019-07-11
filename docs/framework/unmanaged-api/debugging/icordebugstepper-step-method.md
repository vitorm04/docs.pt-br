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
ms.openlocfilehash: 9d0f601c4b454b55edc5fa25eb2ee33d491009b9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760572"
---
# <a name="icordebugstepperstep-method"></a><span data-ttu-id="a5616-102">Método ICorDebugStepper::Step</span><span class="sxs-lookup"><span data-stu-id="a5616-102">ICorDebugStepper::Step Method</span></span>
<span data-ttu-id="a5616-103">Faz com que esse ICorDebugStepper a etapa única por meio de seu recipiente thread e, opcionalmente, para continuar a depuração de único por meio de funções que são chamadas de dentro do thread.</span><span class="sxs-lookup"><span data-stu-id="a5616-103">Causes this ICorDebugStepper to single-step through its containing thread, and optionally, to continue single-stepping through functions that are called within the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5616-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a5616-104">Syntax</span></span>  
  
```cpp  
HRESULT Step (  
    [in] BOOL   bStepIn  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a5616-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a5616-105">Parameters</span></span>  
 `bStepIn`  
 <span data-ttu-id="a5616-106">[in] Definido como `true` para entrar em uma função que é chamada dentro do thread.</span><span class="sxs-lookup"><span data-stu-id="a5616-106">[in] Set to `true` to step into a function that is called within the thread.</span></span> <span data-ttu-id="a5616-107">Definido como `false` para ignorar a função.</span><span class="sxs-lookup"><span data-stu-id="a5616-107">Set to `false` to step over the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a5616-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="a5616-108">Remarks</span></span>  
 <span data-ttu-id="a5616-109">A etapa é concluída quando o common language runtime executa a próxima instrução gerenciada no quadro deste seletor.</span><span class="sxs-lookup"><span data-stu-id="a5616-109">The step completes when the common language runtime performs the next managed instruction in this stepper's frame.</span></span> <span data-ttu-id="a5616-110">Se `Step` é chamado em um seletor, que não está no código gerenciado, a etapa será concluída quando a próxima instrução de código gerenciado é executada pelo thread.</span><span class="sxs-lookup"><span data-stu-id="a5616-110">If `Step` is called on a stepper, which is not in managed code, the step will complete when the next managed code instruction is executed by the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5616-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a5616-111">Requirements</span></span>  
 <span data-ttu-id="a5616-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5616-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5616-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a5616-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a5616-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a5616-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a5616-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5616-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
