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
ms.openlocfilehash: 3662ed8a3fda5881b0e0929a830d19b0d805299f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugframecreatestepper-method"></a><span data-ttu-id="c0459-102">Método ICorDebugFrame::CreateStepper</span><span class="sxs-lookup"><span data-stu-id="c0459-102">ICorDebugFrame::CreateStepper Method</span></span>
<span data-ttu-id="c0459-103">Obtém um seletor que permite que o depurador executar operações de revisão em relação a essa ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="c0459-103">Gets a stepper that allows the debugger to perform stepping operations relative to this ICorDebugFrame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0459-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c0459-104">Syntax</span></span>  
  
```  
HRESULT CreateStepper (  
    [out] ICorDebugStepper   **ppStepper  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c0459-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c0459-105">Parameters</span></span>  
 `ppStepper`  
 <span data-ttu-id="c0459-106">[out] Um ponteiro para o endereço de um objeto de ICorDebugStepper que permite que o depurador executar operações de revisão em relação ao quadro atual.</span><span class="sxs-lookup"><span data-stu-id="c0459-106">[out] A pointer to the address of an ICorDebugStepper object that allows the debugger to perform stepping operations relative to the current frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c0459-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="c0459-107">Remarks</span></span>  
 <span data-ttu-id="c0459-108">Se o quadro não está ativo, o objeto de seletor normalmente terá que retornar ao quadro antes que a etapa seja concluída.</span><span class="sxs-lookup"><span data-stu-id="c0459-108">If the frame is not active, the stepper object will typically have to return to the frame before the step is completed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0459-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c0459-109">Requirements</span></span>  
 <span data-ttu-id="c0459-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0459-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0459-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c0459-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c0459-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c0459-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c0459-113">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0459-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
