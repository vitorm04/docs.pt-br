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
ms.openlocfilehash: 50794e96484432c8b7c203f6b8caa60130068a8c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122779"
---
# <a name="icordebugbreakpointactivate-method"></a><span data-ttu-id="5a63f-102">Método ICorDebugBreakpoint::Activate</span><span class="sxs-lookup"><span data-stu-id="5a63f-102">ICorDebugBreakpoint::Activate Method</span></span>
<span data-ttu-id="5a63f-103">Define o estado ativo deste `ICorDebugBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="5a63f-103">Sets the active state of this `ICorDebugBreakpoint`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a63f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5a63f-104">Syntax</span></span>  
  
```cpp  
HRESULT Activate (  
    [in] BOOL bActive  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5a63f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5a63f-105">Parameters</span></span>  
 `bActive`  
 <span data-ttu-id="5a63f-106">no Defina esse valor como `true` para especificar o estado como ativo; caso contrário, defina esse valor como `false`.</span><span class="sxs-lookup"><span data-stu-id="5a63f-106">[in] Set this value to `true` to specify the state as active; otherwise, set this value to `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a63f-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5a63f-107">Requirements</span></span>  
 <span data-ttu-id="5a63f-108">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a63f-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a63f-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5a63f-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5a63f-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5a63f-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5a63f-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a63f-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
