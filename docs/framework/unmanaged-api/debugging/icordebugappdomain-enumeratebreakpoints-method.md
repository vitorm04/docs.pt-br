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
ms.openlocfilehash: bb994ae32c9e0e61c06c60521361a5c6c78d12fa
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895272"
---
# <a name="icordebugappdomainenumeratebreakpoints-method"></a><span data-ttu-id="9d63b-102">Método ICorDebugAppDomain::EnumerateBreakpoints</span><span class="sxs-lookup"><span data-stu-id="9d63b-102">ICorDebugAppDomain::EnumerateBreakpoints Method</span></span>
<span data-ttu-id="9d63b-103">Obtém um enumerador para todos os pontos de interrupção ativos no domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9d63b-103">Gets an enumerator for all active breakpoints in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d63b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9d63b-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateBreakpoints (  
    [out] ICorDebugBreakpointEnum   **ppBreakpoints  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d63b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9d63b-105">Parameters</span></span>  
 `ppBreakpoints`  
 <span data-ttu-id="9d63b-106">fora Um ponteiro para o endereço de um objeto ICorDebugBreakpointEnum que é o enumerador para todos os pontos de interrupção ativos no domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9d63b-106">[out] A pointer to the address of an ICorDebugBreakpointEnum object that is the enumerator for all active breakpoints in the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9d63b-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="9d63b-107">Remarks</span></span>  
 <span data-ttu-id="9d63b-108">O enumerador inclui todos os tipos de pontos de interrupção, incluindo pontos de interrupção de função e pontos de interrupção de dados.</span><span class="sxs-lookup"><span data-stu-id="9d63b-108">The enumerator includes all types of breakpoints, including function breakpoints and data breakpoints.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d63b-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9d63b-109">Requirements</span></span>  
 <span data-ttu-id="9d63b-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d63b-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d63b-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9d63b-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9d63b-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9d63b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9d63b-113">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d63b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
