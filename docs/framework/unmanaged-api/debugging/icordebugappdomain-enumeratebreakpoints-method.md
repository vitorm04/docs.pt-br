---
title: Método ICorDebugAppDomain::EnumerateBreakpoints
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.EnumerateBreakpoints
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::EnumerateBreakpoints
helpviewer_keywords:
- ICorDebugAppDomain::EnumerateBreakpoints method [.NET Framework debugging]
- EnumerateBreakpoints method [.NET Framework debugging]
ms.assetid: 206069c5-25cb-4794-9d69-67c5aa7ed0af
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b00afc900a27aea94389ee81065ea22ae359440d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57498335"
---
# <a name="icordebugappdomainenumeratebreakpoints-method"></a><span data-ttu-id="ac6ee-102">Método ICorDebugAppDomain::EnumerateBreakpoints</span><span class="sxs-lookup"><span data-stu-id="ac6ee-102">ICorDebugAppDomain::EnumerateBreakpoints Method</span></span>
<span data-ttu-id="ac6ee-103">Obtém um enumerador para todos os pontos de interrupção ativos no domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ac6ee-103">Gets an enumerator for all active breakpoints in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac6ee-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ac6ee-104">Syntax</span></span>  
  
```  
HRESULT EnumerateBreakpoints (  
    [out] ICorDebugBreakpointEnum   **ppBreakpoints  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac6ee-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ac6ee-105">Parameters</span></span>  
 `ppBreakpoints`  
 <span data-ttu-id="ac6ee-106">[out] Um ponteiro para o endereço de um objeto ICorDebugBreakpointEnum que é o enumerador para todos os pontos de interrupção ativos no domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ac6ee-106">[out] A pointer to the address of an ICorDebugBreakpointEnum object that is the enumerator for all active breakpoints in the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ac6ee-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="ac6ee-107">Remarks</span></span>  
 <span data-ttu-id="ac6ee-108">O enumerador inclui todos os tipos de pontos de interrupção, incluindo pontos de interrupção de função e pontos de interrupção de dados.</span><span class="sxs-lookup"><span data-stu-id="ac6ee-108">The enumerator includes all types of breakpoints, including function breakpoints and data breakpoints.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac6ee-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ac6ee-109">Requirements</span></span>  
 <span data-ttu-id="ac6ee-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac6ee-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac6ee-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ac6ee-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ac6ee-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ac6ee-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ac6ee-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac6ee-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
