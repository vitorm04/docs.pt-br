---
title: Método ICorDebugModuleBreakpoint::GetModule
ms.date: 03/30/2017
api_name:
- ICorDebugModuleBreakpoint.GetModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModuleBreakpoint::GetModule
helpviewer_keywords:
- ICorDebugModuleBreakpoint::GetModule method [.NET Framework debugging]
- GetModule method, ICorDebugModuleBreakpoint interface [.NET Framework debugging]
ms.assetid: ffd5d9ec-4564-4200-b625-b306eec0ebd7
topic_type:
- apiref
ms.openlocfilehash: 6f9d8cd79ac4107817d19fc0632aeaee287d253a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73097008"
---
# <a name="icordebugmodulebreakpointgetmodule-method"></a><span data-ttu-id="066dd-102">Método ICorDebugModuleBreakpoint::GetModule</span><span class="sxs-lookup"><span data-stu-id="066dd-102">ICorDebugModuleBreakpoint::GetModule Method</span></span>
<span data-ttu-id="066dd-103">Obtém um ponteiro de interface para um "ICorDebugModule" que faz referência ao módulo no qual esse ponto de interrupção está definido.</span><span class="sxs-lookup"><span data-stu-id="066dd-103">Gets an interface pointer to an "ICorDebugModule" that references the module in which this breakpoint is set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="066dd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="066dd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModule (  
    [out] ICorDebugModule   **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="066dd-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="066dd-105">Parameters</span></span>  
 `ppModule`  
 <span data-ttu-id="066dd-106">fora Um ponteiro para o endereço de uma interface de `ICorDebugModule` que faz referência ao módulo no qual o ponto de interrupção está definido.</span><span class="sxs-lookup"><span data-stu-id="066dd-106">[out] A pointer to the address of an `ICorDebugModule` interface that references the module in which the breakpoint is set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="066dd-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="066dd-107">Requirements</span></span>  
 <span data-ttu-id="066dd-108">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="066dd-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="066dd-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="066dd-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="066dd-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="066dd-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="066dd-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="066dd-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="066dd-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="066dd-112">See also</span></span>
