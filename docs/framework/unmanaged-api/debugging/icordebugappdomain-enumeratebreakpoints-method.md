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
ms.openlocfilehash: cfd7ee890a7f2c3ea8cd3de9fbe830575c0ca10c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402768"
---
# <a name="icordebugappdomainenumeratebreakpoints-method"></a><span data-ttu-id="5d4cb-102">Método ICorDebugAppDomain::EnumerateBreakpoints</span><span class="sxs-lookup"><span data-stu-id="5d4cb-102">ICorDebugAppDomain::EnumerateBreakpoints Method</span></span>
<span data-ttu-id="5d4cb-103">Obtém um enumerador para todos os pontos de interrupção ativos no domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5d4cb-103">Gets an enumerator for all active breakpoints in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d4cb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5d4cb-104">Syntax</span></span>  
  
```  
HRESULT EnumerateBreakpoints (  
    [out] ICorDebugBreakpointEnum   **ppBreakpoints  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5d4cb-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5d4cb-105">Parameters</span></span>  
 `ppBreakpoints`  
 <span data-ttu-id="5d4cb-106">[out] Um ponteiro para o endereço de um objeto de ICorDebugBreakpointEnum que é o enumerador para todos os pontos de interrupção ativos no domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5d4cb-106">[out] A pointer to the address of an ICorDebugBreakpointEnum object that is the enumerator for all active breakpoints in the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5d4cb-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="5d4cb-107">Remarks</span></span>  
 <span data-ttu-id="5d4cb-108">O enumerador inclui todos os tipos de pontos de interrupção, incluindo pontos de interrupção de função e os pontos de interrupção.</span><span class="sxs-lookup"><span data-stu-id="5d4cb-108">The enumerator includes all types of breakpoints, including function breakpoints and data breakpoints.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d4cb-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5d4cb-109">Requirements</span></span>  
 <span data-ttu-id="5d4cb-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d4cb-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d4cb-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5d4cb-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5d4cb-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5d4cb-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5d4cb-113">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d4cb-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
