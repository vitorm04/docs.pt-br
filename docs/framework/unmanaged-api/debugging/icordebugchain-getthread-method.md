---
title: Método ICorDebugChain::GetThread
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetThread
helpviewer_keywords:
- GetThread method, ICorDebugChain interface [.NET Framework debugging]
- ICorDebugChain::GetThread method [.NET Framework debugging]
ms.assetid: b3390319-6366-418c-ba80-b552ac4dfc1e
topic_type:
- apiref
ms.openlocfilehash: 28b54026c8743f31a420e164944f60709e2e271b
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894363"
---
# <a name="icordebugchaingetthread-method"></a><span data-ttu-id="8f0e8-102">Método ICorDebugChain::GetThread</span><span class="sxs-lookup"><span data-stu-id="8f0e8-102">ICorDebugChain::GetThread Method</span></span>
<span data-ttu-id="8f0e8-103">Obtém o thread físico para o qual esta cadeia de chamadas faz parte.</span><span class="sxs-lookup"><span data-stu-id="8f0e8-103">Gets the physical thread this call chain is part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f0e8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8f0e8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThread (  
    [out] ICorDebugThread    **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8f0e8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8f0e8-105">Parameters</span></span>  
 `ppThread`  
 <span data-ttu-id="8f0e8-106">fora Um ponteiro para um objeto ICorDebugThread que representa o thread físico para o qual esta cadeia de chamada faz parte.</span><span class="sxs-lookup"><span data-stu-id="8f0e8-106">[out] A pointer to an ICorDebugThread object that represents the physical thread this call chain is part of.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f0e8-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8f0e8-107">Requirements</span></span>  
 <span data-ttu-id="8f0e8-108">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f0e8-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f0e8-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8f0e8-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8f0e8-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8f0e8-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8f0e8-111">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f0e8-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
