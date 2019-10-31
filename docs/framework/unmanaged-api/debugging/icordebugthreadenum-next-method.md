---
title: Método ICorDebugThreadEnum::Next
ms.date: 03/30/2017
api_name:
- ICorDebugThreadEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThreadEnum::Next
helpviewer_keywords:
- ICorDebugThreadEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugThreadEnum interface [.NET Framework debugging]
ms.assetid: f967c93d-9a7f-4aaf-99a1-a1317899ff3f
topic_type:
- apiref
ms.openlocfilehash: 0c455706b0d644d2444e9fbdf49c5a5d4f5295a9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122397"
---
# <a name="icordebugthreadenumnext-method"></a><span data-ttu-id="5f3f9-102">Método ICorDebugThreadEnum::Next</span><span class="sxs-lookup"><span data-stu-id="5f3f9-102">ICorDebugThreadEnum::Next Method</span></span>
<span data-ttu-id="5f3f9-103">Obtém o número de instâncias ICorDebugThread especificadas da enumeração, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="5f3f9-103">Gets the number of specified ICorDebugThread instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f3f9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5f3f9-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugThread *threads[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5f3f9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5f3f9-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="5f3f9-106">no O número de instâncias de `ICorDebugThread` a serem recuperadas.</span><span class="sxs-lookup"><span data-stu-id="5f3f9-106">[in] The number of `ICorDebugThread` instances to be retrieved.</span></span>  
  
 `threads`  
 <span data-ttu-id="5f3f9-107">fora Uma matriz de ponteiros, cada um dos quais aponta para um objeto `ICorDebugThread` que representa um thread.</span><span class="sxs-lookup"><span data-stu-id="5f3f9-107">[out] An array of pointers, each of which points to an `ICorDebugThread` object that represents a thread.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="5f3f9-108">fora Aponta para o número de instâncias de `ICorDebugThread` retornadas na verdade.</span><span class="sxs-lookup"><span data-stu-id="5f3f9-108">[out] Pointer to the number of `ICorDebugThread` instances actually returned.</span></span> <span data-ttu-id="5f3f9-109">Esse valor pode ser nulo se `celt` for um.</span><span class="sxs-lookup"><span data-stu-id="5f3f9-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f3f9-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5f3f9-110">Requirements</span></span>  
 <span data-ttu-id="5f3f9-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5f3f9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f3f9-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5f3f9-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5f3f9-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5f3f9-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5f3f9-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f3f9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
