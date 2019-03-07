---
title: Método ICorDebugFrameEnum::Next
ms.date: 03/30/2017
api_name:
- ICorDebugFrameEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrameEnum::Next
helpviewer_keywords:
- ICorDebugFrameEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugFrameEnum interface [.NET Framework debugging]
ms.assetid: 0bc96acb-6179-4328-a447-cda562ce9e98
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 68098895b2ad7f5c08d30f222777e52d4ee3f063
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57476653"
---
# <a name="icordebugframeenumnext-method"></a><span data-ttu-id="abada-102">Método ICorDebugFrameEnum::Next</span><span class="sxs-lookup"><span data-stu-id="abada-102">ICorDebugFrameEnum::Next Method</span></span>
<span data-ttu-id="abada-103">Obtém o número especificado de instâncias de ICorDebugFrame, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="abada-103">Gets the specified number of ICorDebugFrame instances, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abada-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="abada-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugFrame *frames[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="abada-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="abada-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="abada-106">[in] O número de `ICorDebugFrame` instâncias a serem recuperados.</span><span class="sxs-lookup"><span data-stu-id="abada-106">[in] The number of `ICorDebugFrame` instances to be retrieved.</span></span>  
  
 `frames`  
 <span data-ttu-id="abada-107">[out] Uma matriz de ponteiros, cada qual apontando para um `ICorDebugFrame` objeto.</span><span class="sxs-lookup"><span data-stu-id="abada-107">[out] An array of pointers, each of which points to an `ICorDebugFrame` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="abada-108">[out] Um ponteiro para o número de `ICorDebugFrame` instâncias, na verdade, retornadas.</span><span class="sxs-lookup"><span data-stu-id="abada-108">[out] A pointer to the number of `ICorDebugFrame` instances actually returned.</span></span> <span data-ttu-id="abada-109">Esse valor pode ser nulo se `celt` é um.</span><span class="sxs-lookup"><span data-stu-id="abada-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="abada-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="abada-110">Requirements</span></span>  
 <span data-ttu-id="abada-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="abada-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="abada-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="abada-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="abada-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="abada-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="abada-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="abada-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
