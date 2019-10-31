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
ms.openlocfilehash: 6ea2b24d37f56a5cb9e6b3dea0d666c8acc719dc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73091038"
---
# <a name="icordebugframecreatestepper-method"></a><span data-ttu-id="d08b3-102">Método ICorDebugFrame::CreateStepper</span><span class="sxs-lookup"><span data-stu-id="d08b3-102">ICorDebugFrame::CreateStepper Method</span></span>
<span data-ttu-id="d08b3-103">Obtém um stepper que permite que o depurador execute operações de depuração relativas a esse ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="d08b3-103">Gets a stepper that allows the debugger to perform stepping operations relative to this ICorDebugFrame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d08b3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d08b3-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateStepper (  
    [out] ICorDebugStepper   **ppStepper  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d08b3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d08b3-105">Parameters</span></span>  
 `ppStepper`  
 <span data-ttu-id="d08b3-106">fora Um ponteiro para o endereço de um objeto ICorDebugStepper que permite que o depurador execute operações de depuração relativas ao quadro atual.</span><span class="sxs-lookup"><span data-stu-id="d08b3-106">[out] A pointer to the address of an ICorDebugStepper object that allows the debugger to perform stepping operations relative to the current frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d08b3-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="d08b3-107">Remarks</span></span>  
 <span data-ttu-id="d08b3-108">Se o quadro não estiver ativo, o objeto stepper normalmente precisará retornar ao quadro antes da conclusão da etapa.</span><span class="sxs-lookup"><span data-stu-id="d08b3-108">If the frame is not active, the stepper object will typically have to return to the frame before the step is completed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d08b3-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d08b3-109">Requirements</span></span>  
 <span data-ttu-id="d08b3-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d08b3-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d08b3-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d08b3-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d08b3-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d08b3-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d08b3-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d08b3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
