---
title: Método ICorDebugFrame::CreateStepper
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.CreateStepper
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::CreateStepper
helpviewer_keywords:
- ICorDebugFrame::CreateStepper method [.NET Framework debugging]
- CreateStepper method, ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 689e7f28-20c1-4d5c-9baa-17441cd63a88
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fd105a5cbdb857aaa902e60968ff1d94473259b6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754246"
---
# <a name="icordebugframecreatestepper-method"></a><span data-ttu-id="c3b5a-102">Método ICorDebugFrame::CreateStepper</span><span class="sxs-lookup"><span data-stu-id="c3b5a-102">ICorDebugFrame::CreateStepper Method</span></span>
<span data-ttu-id="c3b5a-103">Obtém um seletor que permite que o depurador executar operações de passo a passo em relação a esse ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="c3b5a-103">Gets a stepper that allows the debugger to perform stepping operations relative to this ICorDebugFrame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3b5a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c3b5a-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateStepper (  
    [out] ICorDebugStepper   **ppStepper  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3b5a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c3b5a-105">Parameters</span></span>  
 `ppStepper`  
 <span data-ttu-id="c3b5a-106">[out] Um ponteiro para o endereço de um objeto de ICorDebugStepper que permite que o depurador executar operações de passo a passo em relação ao quadro atual.</span><span class="sxs-lookup"><span data-stu-id="c3b5a-106">[out] A pointer to the address of an ICorDebugStepper object that allows the debugger to perform stepping operations relative to the current frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c3b5a-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="c3b5a-107">Remarks</span></span>  
 <span data-ttu-id="c3b5a-108">Se o quadro não estiver ativo, o objeto escalonador normalmente terá que retornar para o quadro antes que a etapa for concluída.</span><span class="sxs-lookup"><span data-stu-id="c3b5a-108">If the frame is not active, the stepper object will typically have to return to the frame before the step is completed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3b5a-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c3b5a-109">Requirements</span></span>  
 <span data-ttu-id="c3b5a-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3b5a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3b5a-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c3b5a-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c3b5a-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c3b5a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c3b5a-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3b5a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
