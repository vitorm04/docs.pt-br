---
title: Método ICorDebugBreakpoint::Activate
ms.date: 03/30/2017
api_name:
- ICorDebugBreakpoint.Activate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpoint::Activate
helpviewer_keywords:
- ICorDebugBreakpoint::Activate method [.NET Framework debugging]
- Activate method [.NET Framework debugging]
ms.assetid: e30c29f7-3f19-4081-b572-a731aa14cd44
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2ac37df58762dac4e3a6161361cafd8ea87e2657
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57491353"
---
# <a name="icordebugbreakpointactivate-method"></a><span data-ttu-id="5dc9f-102">Método ICorDebugBreakpoint::Activate</span><span class="sxs-lookup"><span data-stu-id="5dc9f-102">ICorDebugBreakpoint::Activate Method</span></span>
<span data-ttu-id="5dc9f-103">Define o estado ativo disso `ICorDebugBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="5dc9f-103">Sets the active state of this `ICorDebugBreakpoint`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5dc9f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5dc9f-104">Syntax</span></span>  
  
```  
HRESULT Activate (  
    [in] BOOL bActive  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5dc9f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5dc9f-105">Parameters</span></span>  
 `bActive`  
 <span data-ttu-id="5dc9f-106">[in] Defina esse valor como `true` para especificar o estado como ativa; caso contrário, defina esse valor como `false`.</span><span class="sxs-lookup"><span data-stu-id="5dc9f-106">[in] Set this value to `true` to specify the state as active; otherwise, set this value to `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5dc9f-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5dc9f-107">Requirements</span></span>  
 <span data-ttu-id="5dc9f-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5dc9f-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5dc9f-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5dc9f-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5dc9f-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5dc9f-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5dc9f-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5dc9f-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
