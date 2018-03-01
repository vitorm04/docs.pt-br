---
title: "Método ICorDebugBreakpoint::Activate"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ef0880c40cb09b836938f253447f5ffeaaec207b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugbreakpointactivate-method"></a><span data-ttu-id="acb5d-102">Método ICorDebugBreakpoint::Activate</span><span class="sxs-lookup"><span data-stu-id="acb5d-102">ICorDebugBreakpoint::Activate Method</span></span>
<span data-ttu-id="acb5d-103">Define o estado ativo deste `ICorDebugBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="acb5d-103">Sets the active state of this `ICorDebugBreakpoint`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="acb5d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="acb5d-104">Syntax</span></span>  
  
```  
HRESULT Activate (  
    [in] BOOL bActive  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="acb5d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="acb5d-105">Parameters</span></span>  
 `bActive`  
 <span data-ttu-id="acb5d-106">[in] Defina esse valor como `true` para especificar o estado como ativo; caso contrário, defina esse valor como `false`.</span><span class="sxs-lookup"><span data-stu-id="acb5d-106">[in] Set this value to `true` to specify the state as active; otherwise, set this value to `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="acb5d-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="acb5d-107">Requirements</span></span>  
 <span data-ttu-id="acb5d-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="acb5d-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="acb5d-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="acb5d-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="acb5d-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="acb5d-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="acb5d-111">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="acb5d-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
