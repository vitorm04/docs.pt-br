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
ms.openlocfilehash: b964d58bddb174da38fc8988ec807fd3129b5fcf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123822"
---
# <a name="icordebugchaingetthread-method"></a><span data-ttu-id="d9a02-102">Método ICorDebugChain::GetThread</span><span class="sxs-lookup"><span data-stu-id="d9a02-102">ICorDebugChain::GetThread Method</span></span>
<span data-ttu-id="d9a02-103">Obtém o thread físico para o qual esta cadeia de chamadas faz parte.</span><span class="sxs-lookup"><span data-stu-id="d9a02-103">Gets the physical thread this call chain is part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9a02-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d9a02-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThread (  
    [out] ICorDebugThread    **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d9a02-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d9a02-105">Parameters</span></span>  
 `ppThread`  
 <span data-ttu-id="d9a02-106">fora Um ponteiro para um objeto ICorDebugThread que representa o thread físico para o qual esta cadeia de chamada faz parte.</span><span class="sxs-lookup"><span data-stu-id="d9a02-106">[out] A pointer to an ICorDebugThread object that represents the physical thread this call chain is part of.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9a02-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d9a02-107">Requirements</span></span>  
 <span data-ttu-id="d9a02-108">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9a02-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9a02-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d9a02-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d9a02-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d9a02-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d9a02-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9a02-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
