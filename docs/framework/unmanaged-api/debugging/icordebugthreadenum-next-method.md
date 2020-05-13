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
ms.openlocfilehash: c025afac1b53b23636a6160a475704011999d434
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379054"
---
# <a name="icordebugthreadenumnext-method"></a><span data-ttu-id="de4fb-102">Método ICorDebugThreadEnum::Next</span><span class="sxs-lookup"><span data-stu-id="de4fb-102">ICorDebugThreadEnum::Next Method</span></span>
<span data-ttu-id="de4fb-103">Obtém o número de instâncias ICorDebugThread especificadas da enumeração, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="de4fb-103">Gets the number of specified ICorDebugThread instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de4fb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="de4fb-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugThread *threads[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="de4fb-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="de4fb-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="de4fb-106">no O número de `ICorDebugThread` instâncias a serem recuperadas.</span><span class="sxs-lookup"><span data-stu-id="de4fb-106">[in] The number of `ICorDebugThread` instances to be retrieved.</span></span>  
  
 `threads`  
 <span data-ttu-id="de4fb-107">fora Uma matriz de ponteiros, cada um dos quais aponta para um `ICorDebugThread` objeto que representa um thread.</span><span class="sxs-lookup"><span data-stu-id="de4fb-107">[out] An array of pointers, each of which points to an `ICorDebugThread` object that represents a thread.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="de4fb-108">fora Aponta para o número de `ICorDebugThread` instâncias realmente retornadas.</span><span class="sxs-lookup"><span data-stu-id="de4fb-108">[out] Pointer to the number of `ICorDebugThread` instances actually returned.</span></span> <span data-ttu-id="de4fb-109">Esse valor pode ser nulo se `celt` for um.</span><span class="sxs-lookup"><span data-stu-id="de4fb-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de4fb-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="de4fb-110">Requirements</span></span>  
 <span data-ttu-id="de4fb-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="de4fb-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de4fb-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="de4fb-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="de4fb-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="de4fb-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="de4fb-114">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de4fb-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
