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
ms.openlocfilehash: 2f049a7cadf1857495e49b9bdc2fecd1b49103af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugframeenumnext-method"></a><span data-ttu-id="508ee-102">Método ICorDebugFrameEnum::Next</span><span class="sxs-lookup"><span data-stu-id="508ee-102">ICorDebugFrameEnum::Next Method</span></span>
<span data-ttu-id="508ee-103">Obtém o número especificado de instâncias ICorDebugFrame, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="508ee-103">Gets the specified number of ICorDebugFrame instances, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="508ee-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="508ee-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugFrame *frames[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="508ee-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="508ee-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="508ee-106">[in] O número de `ICorDebugFrame` instâncias a serem recuperados.</span><span class="sxs-lookup"><span data-stu-id="508ee-106">[in] The number of `ICorDebugFrame` instances to be retrieved.</span></span>  
  
 `frames`  
 <span data-ttu-id="508ee-107">[out] Uma matriz de ponteiros, cada qual apontando para um `ICorDebugFrame` objeto.</span><span class="sxs-lookup"><span data-stu-id="508ee-107">[out] An array of pointers, each of which points to an `ICorDebugFrame` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="508ee-108">[out] Um ponteiro para o número de `ICorDebugFrame` , na verdade, retornadas de instâncias.</span><span class="sxs-lookup"><span data-stu-id="508ee-108">[out] A pointer to the number of `ICorDebugFrame` instances actually returned.</span></span> <span data-ttu-id="508ee-109">Esse valor pode ser null se `celt` é um.</span><span class="sxs-lookup"><span data-stu-id="508ee-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="508ee-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="508ee-110">Requirements</span></span>  
 <span data-ttu-id="508ee-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="508ee-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="508ee-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="508ee-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="508ee-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="508ee-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="508ee-114">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="508ee-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
