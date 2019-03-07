---
title: Método ICorDebugChain::GetCaller
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetCaller
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetCaller
helpviewer_keywords:
- ICorDebugChain::GetCaller method [.NET Framework debugging]
- GetCaller method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: d0b8ab4b-d7d2-4fa0-945f-3d2b87e7e991
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fd65de77209f5a981c0a4c291f8573a61cf6335b
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57489547"
---
# <a name="icordebugchaingetcaller-method"></a><span data-ttu-id="1fdea-102">Método ICorDebugChain::GetCaller</span><span class="sxs-lookup"><span data-stu-id="1fdea-102">ICorDebugChain::GetCaller Method</span></span>
<span data-ttu-id="1fdea-103">Obtém a cadeia que chamou esta cadeia.</span><span class="sxs-lookup"><span data-stu-id="1fdea-103">Gets the chain that called this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fdea-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1fdea-104">Syntax</span></span>  
  
```  
HRESULT GetCaller (  
    [out] ICorDebugChain      **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1fdea-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1fdea-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="1fdea-106">[out] Um ponteiro para o endereço de um objeto de ICorDebugChain que representa a cadeia de chamada.</span><span class="sxs-lookup"><span data-stu-id="1fdea-106">[out] A pointer to the address of an ICorDebugChain object that represents the calling chain.</span></span>  
  
 <span data-ttu-id="1fdea-107">Se esta cadeia espontaneamente foi chamada (como seria o caso se esta cadeia ou o depurador inicializado a pilha de chamadas), `ppChain` será nulo.</span><span class="sxs-lookup"><span data-stu-id="1fdea-107">If this chain was spontaneously called (as would be the case if this chain or the debugger initialized the call stack), `ppChain` will be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1fdea-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="1fdea-108">Remarks</span></span>  
 <span data-ttu-id="1fdea-109">A cadeia de chamada pode estar em um thread diferente, se a chamada passou por marshalling entre threads.</span><span class="sxs-lookup"><span data-stu-id="1fdea-109">The calling chain may be on a different thread, if the call was marshaled across threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1fdea-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1fdea-110">Requirements</span></span>  
 <span data-ttu-id="1fdea-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1fdea-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1fdea-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1fdea-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1fdea-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1fdea-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1fdea-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1fdea-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
