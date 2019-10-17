---
title: Método ICorDebugCodeEnum::Next
ms.date: 03/30/2017
api_name:
- ICorDebugCodeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCodeEnum::Next
helpviewer_keywords:
- ICorDebugCodeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: 644ece86-384d-4c63-9fba-52c789616ff7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ac3fc157543f2990c7c9f9917140b35f8948108e
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395471"
---
# <a name="icordebugcodeenumnext-method"></a><span data-ttu-id="7482d-102">Método ICorDebugCodeEnum::Next</span><span class="sxs-lookup"><span data-stu-id="7482d-102">ICorDebugCodeEnum::Next Method</span></span>

<span data-ttu-id="7482d-103">Obtém o número especificado de instâncias "ICorDebugCode" da enumeração, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="7482d-103">Gets the specified number of "ICorDebugCode" instances from the enumeration, starting at the current position.</span></span>

## <a name="syntax"></a><span data-ttu-id="7482d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7482d-104">Syntax</span></span>

```cpp
HRESULT Next (
    [in] ULONG  celt,
    [out, size_is(celt), length_is(*pceltFetched)]
        ICorDebugCode *values[],
    [out] ULONG *pceltFetched
);
```

## <a name="parameters"></a><span data-ttu-id="7482d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7482d-105">Parameters</span></span>

`celt`  
<span data-ttu-id="7482d-106">no O número de instâncias `ICorDebugCode` a serem recuperadas.</span><span class="sxs-lookup"><span data-stu-id="7482d-106">[in] The number of `ICorDebugCode` instances to be retrieved.</span></span>

`values`  
<span data-ttu-id="7482d-107">fora Uma matriz de ponteiros, cada um dos quais aponta para um objeto `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="7482d-107">[out] An array of pointers, each of which points to an `ICorDebugCode` object.</span></span>

`pceltFetched`  
<span data-ttu-id="7482d-108">fora Um ponteiro para o número de instâncias `ICorDebugCode` realmente retornadas.</span><span class="sxs-lookup"><span data-stu-id="7482d-108">[out] A pointer to the number of `ICorDebugCode` instances actually returned.</span></span> <span data-ttu-id="7482d-109">Esse valor pode ser nulo se `celt` for um.</span><span class="sxs-lookup"><span data-stu-id="7482d-109">This value may be null if `celt` is one.</span></span>

## <a name="requirements"></a><span data-ttu-id="7482d-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7482d-110">Requirements</span></span>

<span data-ttu-id="7482d-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7482d-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="7482d-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7482d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="7482d-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7482d-113">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="7482d-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7482d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
