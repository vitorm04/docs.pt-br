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
ms.openlocfilehash: 43f86e704e4a52a702b8f563e3c613806eb061b5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137526"
---
# <a name="icordebugstepperstep-method"></a><span data-ttu-id="92126-102">Método ICorDebugStepper::Step</span><span class="sxs-lookup"><span data-stu-id="92126-102">ICorDebugStepper::Step Method</span></span>
<span data-ttu-id="92126-103">Faz com que esse ICorDebugStepper faça uma única etapa por meio de seu thread que o contém e, opcionalmente, continue a avançar por meio de funções que são chamadas dentro do thread.</span><span class="sxs-lookup"><span data-stu-id="92126-103">Causes this ICorDebugStepper to single-step through its containing thread, and optionally, to continue single-stepping through functions that are called within the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92126-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="92126-104">Syntax</span></span>  
  
```cpp  
HRESULT Step (  
    [in] BOOL   bStepIn  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92126-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="92126-105">Parameters</span></span>  
 `bStepIn`  
 <span data-ttu-id="92126-106">no Defina como `true` para entrar em uma função que é chamada dentro do thread.</span><span class="sxs-lookup"><span data-stu-id="92126-106">[in] Set to `true` to step into a function that is called within the thread.</span></span> <span data-ttu-id="92126-107">Defina como `false` para percorrer a função.</span><span class="sxs-lookup"><span data-stu-id="92126-107">Set to `false` to step over the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92126-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="92126-108">Remarks</span></span>  
 <span data-ttu-id="92126-109">A etapa é concluída quando o Common Language Runtime executa a próxima instrução gerenciada neste quadro de stepper.</span><span class="sxs-lookup"><span data-stu-id="92126-109">The step completes when the common language runtime performs the next managed instruction in this stepper's frame.</span></span> <span data-ttu-id="92126-110">Se `Step` for chamado em um stepper, que não está no código gerenciado, a etapa será concluída quando a próxima instrução de código gerenciado for executada pelo thread.</span><span class="sxs-lookup"><span data-stu-id="92126-110">If `Step` is called on a stepper, which is not in managed code, the step will complete when the next managed code instruction is executed by the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92126-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="92126-111">Requirements</span></span>  
 <span data-ttu-id="92126-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92126-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92126-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="92126-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="92126-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="92126-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="92126-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92126-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
