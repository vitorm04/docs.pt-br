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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 51403c52d7f8a216e83b817f157979f4af1c433a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59162862"
---
# <a name="icordebugmodulebreakpointgetmodule-method"></a><span data-ttu-id="b171d-102">Método ICorDebugModuleBreakpoint::GetModule</span><span class="sxs-lookup"><span data-stu-id="b171d-102">ICorDebugModuleBreakpoint::GetModule Method</span></span>
<span data-ttu-id="b171d-103">Obtém um ponteiro de interface para um "ICorDebugModule" que faz referência ao módulo no qual este ponto de interrupção está definido.</span><span class="sxs-lookup"><span data-stu-id="b171d-103">Gets an interface pointer to an "ICorDebugModule" that references the module in which this breakpoint is set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b171d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b171d-104">Syntax</span></span>  
  
```  
HRESULT GetModule (  
    [out] ICorDebugModule   **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b171d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b171d-105">Parameters</span></span>  
 `ppModule`  
 <span data-ttu-id="b171d-106">[out] Um ponteiro para o endereço de um `ICorDebugModule` interface que faz referência ao módulo no qual o ponto de interrupção está definido.</span><span class="sxs-lookup"><span data-stu-id="b171d-106">[out] A pointer to the address of an `ICorDebugModule` interface that references the module in which the breakpoint is set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b171d-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b171d-107">Requirements</span></span>  
 <span data-ttu-id="b171d-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b171d-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b171d-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b171d-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b171d-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b171d-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b171d-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b171d-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b171d-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b171d-112">See also</span></span>
