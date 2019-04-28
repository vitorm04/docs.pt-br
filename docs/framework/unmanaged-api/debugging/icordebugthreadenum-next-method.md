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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61903312"
---
# <a name="icordebugthreadenumnext-method"></a><span data-ttu-id="3a85a-102">Método ICorDebugThreadEnum::Next</span><span class="sxs-lookup"><span data-stu-id="3a85a-102">ICorDebugThreadEnum::Next Method</span></span>
<span data-ttu-id="3a85a-103">Obtém o número de instâncias especificadas de ICorDebugThread de enumeração, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="3a85a-103">Gets the number of specified ICorDebugThread instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a85a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3a85a-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugThread *threads[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3a85a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3a85a-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="3a85a-106">[in] O número de `ICorDebugThread` instâncias a serem recuperados.</span><span class="sxs-lookup"><span data-stu-id="3a85a-106">[in] The number of `ICorDebugThread` instances to be retrieved.</span></span>  
  
 `threads`  
 <span data-ttu-id="3a85a-107">[out] Uma matriz de ponteiros, cada qual apontando para um `ICorDebugThread` objeto que representa um thread.</span><span class="sxs-lookup"><span data-stu-id="3a85a-107">[out] An array of pointers, each of which points to an `ICorDebugThread` object that represents a thread.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="3a85a-108">[out] Ponteiro para o número de `ICorDebugThread` instâncias, na verdade, retornadas.</span><span class="sxs-lookup"><span data-stu-id="3a85a-108">[out] Pointer to the number of `ICorDebugThread` instances actually returned.</span></span> <span data-ttu-id="3a85a-109">Esse valor pode ser nulo se `celt` é um.</span><span class="sxs-lookup"><span data-stu-id="3a85a-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a85a-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3a85a-110">Requirements</span></span>  
 <span data-ttu-id="3a85a-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a85a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a85a-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3a85a-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3a85a-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3a85a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3a85a-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a85a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
