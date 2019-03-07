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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b80e0cc026ce80950c14436abb2e84548f9adb64
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57499570"
---
# <a name="icordebugthreadenumnext-method"></a><span data-ttu-id="f5507-102">Método ICorDebugThreadEnum::Next</span><span class="sxs-lookup"><span data-stu-id="f5507-102">ICorDebugThreadEnum::Next Method</span></span>
<span data-ttu-id="f5507-103">Obtém o número de instâncias especificadas de ICorDebugThread de enumeração, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="f5507-103">Gets the number of specified ICorDebugThread instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5507-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f5507-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugThread *threads[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f5507-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f5507-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="f5507-106">[in] O número de `ICorDebugThread` instâncias a serem recuperados.</span><span class="sxs-lookup"><span data-stu-id="f5507-106">[in] The number of `ICorDebugThread` instances to be retrieved.</span></span>  
  
 `threads`  
 <span data-ttu-id="f5507-107">[out] Uma matriz de ponteiros, cada qual apontando para um `ICorDebugThread` objeto que representa um thread.</span><span class="sxs-lookup"><span data-stu-id="f5507-107">[out] An array of pointers, each of which points to an `ICorDebugThread` object that represents a thread.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="f5507-108">[out] Ponteiro para o número de `ICorDebugThread` instâncias, na verdade, retornadas.</span><span class="sxs-lookup"><span data-stu-id="f5507-108">[out] Pointer to the number of `ICorDebugThread` instances actually returned.</span></span> <span data-ttu-id="f5507-109">Esse valor pode ser nulo se `celt` é um.</span><span class="sxs-lookup"><span data-stu-id="f5507-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5507-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f5507-110">Requirements</span></span>  
 <span data-ttu-id="f5507-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5507-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5507-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f5507-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f5507-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f5507-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f5507-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5507-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
