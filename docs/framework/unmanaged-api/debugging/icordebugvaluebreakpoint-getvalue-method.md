---
title: Método ICorDebugValueBreakpoint::GetValue
ms.date: 03/30/2017
api_name:
- ICorDebugValueBreakpoint.GetValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValueBreakpoint::GetValue
helpviewer_keywords:
- GetValue method, ICorDebugValueBreakpoint interface [.NET Framework debugging]
- ICorDebugValueBreakpoint::GetValue method [.NET Framework debugging]
ms.assetid: 52a73654-bc47-48b6-b2b1-a4456b10140c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: da23c7da7869c9190b8ce4ad94553a1cb8fc958d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57495124"
---
# <a name="icordebugvaluebreakpointgetvalue-method"></a><span data-ttu-id="dfa21-102">Método ICorDebugValueBreakpoint::GetValue</span><span class="sxs-lookup"><span data-stu-id="dfa21-102">ICorDebugValueBreakpoint::GetValue Method</span></span>
<span data-ttu-id="dfa21-103">Obtém um ponteiro de interface para um objeto de "ICorDebugValue" que representa o valor do objeto em que o ponto de interrupção está definido.</span><span class="sxs-lookup"><span data-stu-id="dfa21-103">Gets an interface pointer to an "ICorDebugValue" object that represents the value of the object on which the breakpoint is set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfa21-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dfa21-104">Syntax</span></span>  
  
```  
HRESULT GetValue (  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dfa21-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dfa21-105">Parameters</span></span>  
 `ppValue`  
 <span data-ttu-id="dfa21-106">[out] Um ponteiro para o endereço de um `ICorDebugValue` objeto.</span><span class="sxs-lookup"><span data-stu-id="dfa21-106">[out] A pointer to the address of an `ICorDebugValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dfa21-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="dfa21-107">Requirements</span></span>  
 <span data-ttu-id="dfa21-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dfa21-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dfa21-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dfa21-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dfa21-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dfa21-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dfa21-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dfa21-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfa21-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dfa21-112">See also</span></span>

