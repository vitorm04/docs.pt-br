---
title: Método ICorDebugProcessEnum::Next
ms.date: 03/30/2017
api_name:
- ICorDebugProcessEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcessEnum::Next
helpviewer_keywords:
- Next method, ICorDebugProcessEnum interface [.NET Framework debugging]
- ICorDebugProcessEnum::Next method [.NET Framework debugging]
ms.assetid: 4ac7077c-8d88-49c4-b360-b3af0c541c63
topic_type:
- apiref
ms.openlocfilehash: 0666becb5a34688d3f4cf5bddd1e2fa71785b38a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139795"
---
# <a name="icordebugprocessenumnext-method"></a><span data-ttu-id="70be6-102">Método ICorDebugProcessEnum::Next</span><span class="sxs-lookup"><span data-stu-id="70be6-102">ICorDebugProcessEnum::Next Method</span></span>
<span data-ttu-id="70be6-103">Obtém o número especificado de instâncias de ICorDebugProcess da enumeração, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="70be6-103">Gets the specified number of ICorDebugProcess instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70be6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="70be6-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in]  ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugProcess *processes[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="70be6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="70be6-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="70be6-106">no O número de instâncias de `ICorDebugProcess` a serem recuperadas.</span><span class="sxs-lookup"><span data-stu-id="70be6-106">[in] The number of `ICorDebugProcess` instances to be retrieved.</span></span>  
  
 `processes`  
 <span data-ttu-id="70be6-107">fora Uma matriz de ponteiros, cada um dos quais aponta para um objeto `ICorDebugProcess` que representa um processo.</span><span class="sxs-lookup"><span data-stu-id="70be6-107">[out] An array of pointers, each of which points to an `ICorDebugProcess` object that represents a process.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="70be6-108">fora Aponta para o número de instâncias de `ICorDebugProcess` retornadas na verdade.</span><span class="sxs-lookup"><span data-stu-id="70be6-108">[out] Pointer to the number of `ICorDebugProcess` instances actually returned.</span></span> <span data-ttu-id="70be6-109">Esse valor pode ser nulo se `celt` for um.</span><span class="sxs-lookup"><span data-stu-id="70be6-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70be6-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="70be6-110">Requirements</span></span>  
 <span data-ttu-id="70be6-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70be6-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70be6-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="70be6-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="70be6-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="70be6-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="70be6-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70be6-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
