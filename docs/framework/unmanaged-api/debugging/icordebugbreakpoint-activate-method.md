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
ms.openlocfilehash: 0f056e4ae233e70223755c1961cd3ee5da68ec90
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745184"
---
# <a name="icordebugbreakpointactivate-method"></a><span data-ttu-id="b47aa-102">Método ICorDebugBreakpoint::Activate</span><span class="sxs-lookup"><span data-stu-id="b47aa-102">ICorDebugBreakpoint::Activate Method</span></span>
<span data-ttu-id="b47aa-103">Define o estado ativo disso `ICorDebugBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="b47aa-103">Sets the active state of this `ICorDebugBreakpoint`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b47aa-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b47aa-104">Syntax</span></span>  
  
```cpp  
HRESULT Activate (  
    [in] BOOL bActive  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b47aa-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b47aa-105">Parameters</span></span>  
 `bActive`  
 <span data-ttu-id="b47aa-106">[in] Defina esse valor como `true` para especificar o estado como ativa; caso contrário, defina esse valor como `false`.</span><span class="sxs-lookup"><span data-stu-id="b47aa-106">[in] Set this value to `true` to specify the state as active; otherwise, set this value to `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b47aa-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b47aa-107">Requirements</span></span>  
 <span data-ttu-id="b47aa-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b47aa-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b47aa-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b47aa-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b47aa-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b47aa-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b47aa-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b47aa-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
