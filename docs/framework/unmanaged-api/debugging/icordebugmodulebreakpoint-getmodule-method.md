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
ms.openlocfilehash: ce53137021fe9ccaf170bed28918b8f5fe87715b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54504985"
---
# <a name="icordebugmodulebreakpointgetmodule-method"></a><span data-ttu-id="b536e-102">Método ICorDebugModuleBreakpoint::GetModule</span><span class="sxs-lookup"><span data-stu-id="b536e-102">ICorDebugModuleBreakpoint::GetModule Method</span></span>
<span data-ttu-id="b536e-103">Obtém um ponteiro de interface para um "ICorDebugModule" que faz referência ao módulo no qual este ponto de interrupção está definido.</span><span class="sxs-lookup"><span data-stu-id="b536e-103">Gets an interface pointer to an "ICorDebugModule" that references the module in which this breakpoint is set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b536e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b536e-104">Syntax</span></span>  
  
```  
HRESULT GetModule (  
    [out] ICorDebugModule   **ppModule  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b536e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b536e-105">Parameters</span></span>  
 `ppModule`  
 <span data-ttu-id="b536e-106">[out] Um ponteiro para o endereço de um `ICorDebugModule` interface que faz referência ao módulo no qual o ponto de interrupção está definido.</span><span class="sxs-lookup"><span data-stu-id="b536e-106">[out] A pointer to the address of an `ICorDebugModule` interface that references the module in which the breakpoint is set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b536e-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b536e-107">Requirements</span></span>  
 <span data-ttu-id="b536e-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b536e-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b536e-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b536e-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b536e-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b536e-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b536e-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b536e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b536e-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b536e-112">See also</span></span>

