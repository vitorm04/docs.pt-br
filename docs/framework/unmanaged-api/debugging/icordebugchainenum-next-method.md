---
title: Método ICorDebugChainEnum::Next
ms.date: 03/30/2017
api_name:
- ICorDebugChainEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChainEnum::Next
helpviewer_keywords:
- ICorDebugChainEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugChainEnum interface [.NET Framework debugging]
ms.assetid: 6b791351-bcc5-4ddd-9cab-eff2f7dd5142
topic_type:
- apiref
ms.openlocfilehash: 2d075820df534e08bdf4c2b75d36f6a60f979662
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894089"
---
# <a name="icordebugchainenumnext-method"></a><span data-ttu-id="bb015-102">Método ICorDebugChainEnum::Next</span><span class="sxs-lookup"><span data-stu-id="bb015-102">ICorDebugChainEnum::Next Method</span></span>
<span data-ttu-id="bb015-103">Obtém o número especificado de instâncias de ICorDebugChain da enumeração, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="bb015-103">Gets the specified number of ICorDebugChain instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb015-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bb015-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugChain *chains[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bb015-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bb015-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="bb015-106">no O número de `ICorDebugChain` instâncias a serem recuperadas.</span><span class="sxs-lookup"><span data-stu-id="bb015-106">[in] The number of `ICorDebugChain` instances to be retrieved.</span></span>  
  
 `chains`  
 <span data-ttu-id="bb015-107">fora Uma matriz de ponteiros, cada um dos quais aponta `ICorDebugChain` para um objeto que representa uma cadeia.</span><span class="sxs-lookup"><span data-stu-id="bb015-107">[out] An array of pointers, each of which points to an `ICorDebugChain` object that represents a chain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="bb015-108">fora Um ponteiro para o número de `ICorDebugChain` instâncias retornadas de fato.</span><span class="sxs-lookup"><span data-stu-id="bb015-108">[out] A pointer to the number of `ICorDebugChain` instances actually returned.</span></span> <span data-ttu-id="bb015-109">Esse valor pode ser nulo se `celt` for um.</span><span class="sxs-lookup"><span data-stu-id="bb015-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb015-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bb015-110">Requirements</span></span>  
 <span data-ttu-id="bb015-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb015-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb015-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bb015-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bb015-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bb015-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bb015-114">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb015-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
