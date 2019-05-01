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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 26df40297d080d1ccc9464f7b09e7731f135e270
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61989229"
---
# <a name="icordebugchainenumnext-method"></a><span data-ttu-id="386e7-102">Método ICorDebugChainEnum::Next</span><span class="sxs-lookup"><span data-stu-id="386e7-102">ICorDebugChainEnum::Next Method</span></span>
<span data-ttu-id="386e7-103">Obtém o número especificado de instâncias de ICorDebugChain de enumeração, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="386e7-103">Gets the specified number of ICorDebugChain instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="386e7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="386e7-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugChain *chains[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="386e7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="386e7-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="386e7-106">[in] O número de `ICorDebugChain` instâncias a serem recuperados.</span><span class="sxs-lookup"><span data-stu-id="386e7-106">[in] The number of `ICorDebugChain` instances to be retrieved.</span></span>  
  
 `chains`  
 <span data-ttu-id="386e7-107">[out] Uma matriz de ponteiros, cada qual apontando para um `ICorDebugChain` objeto que representa uma cadeia.</span><span class="sxs-lookup"><span data-stu-id="386e7-107">[out] An array of pointers, each of which points to an `ICorDebugChain` object that represents a chain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="386e7-108">[out] Um ponteiro para o número de `ICorDebugChain` instâncias, na verdade, retornadas.</span><span class="sxs-lookup"><span data-stu-id="386e7-108">[out] A pointer to the number of `ICorDebugChain` instances actually returned.</span></span> <span data-ttu-id="386e7-109">Esse valor pode ser nulo se `celt` é um.</span><span class="sxs-lookup"><span data-stu-id="386e7-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="386e7-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="386e7-110">Requirements</span></span>  
 <span data-ttu-id="386e7-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="386e7-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="386e7-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="386e7-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="386e7-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="386e7-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="386e7-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="386e7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
