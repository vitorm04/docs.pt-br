---
title: Método ICorDebugModuleEnum::Next
ms.date: 03/30/2017
api_name:
- ICorDebugModuleEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModuleEnum::Next
helpviewer_keywords:
- ICorDebugModuleEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugModuleEnum interface [.NET Framework debugging]
ms.assetid: 9ff3fcd6-38fe-41f8-bfd3-f0ab6c7d77ca
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7624a22e5d65ae94797779a0b8cfa70f226450ac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33418978"
---
# <a name="icordebugmoduleenumnext-method"></a><span data-ttu-id="4a2dd-102">Método ICorDebugModuleEnum::Next</span><span class="sxs-lookup"><span data-stu-id="4a2dd-102">ICorDebugModuleEnum::Next Method</span></span>
<span data-ttu-id="4a2dd-103">Obtém o número de instâncias de "ICorDebugModule" especificado pelo `celt` de enumeração, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="4a2dd-103">Gets the number of "ICorDebugModule" instances specified by `celt` from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a2dd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4a2dd-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in]  ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugModule *modules[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4a2dd-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4a2dd-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="4a2dd-106">[in] O número de `ICorDebugModule` instâncias a serem recuperados.</span><span class="sxs-lookup"><span data-stu-id="4a2dd-106">[in] The number of `ICorDebugModule` instances to be retrieved.</span></span>  
  
 `modules`  
 <span data-ttu-id="4a2dd-107">[out] Uma matriz de ponteiros, cada qual apontando para um `ICorDebugModule` objeto.</span><span class="sxs-lookup"><span data-stu-id="4a2dd-107">[out] An array of pointers, each of which points to an `ICorDebugModule` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="4a2dd-108">[out] Ponteiro para o número de `ICorDebugModule` , na verdade, retornadas de instâncias.</span><span class="sxs-lookup"><span data-stu-id="4a2dd-108">[out] Pointer to the number of `ICorDebugModule` instances actually returned.</span></span> <span data-ttu-id="4a2dd-109">Esse valor pode ser null se `celt` é um.</span><span class="sxs-lookup"><span data-stu-id="4a2dd-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a2dd-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4a2dd-110">Requirements</span></span>  
 <span data-ttu-id="4a2dd-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a2dd-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a2dd-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4a2dd-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4a2dd-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4a2dd-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4a2dd-114">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a2dd-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a2dd-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4a2dd-115">See Also</span></span>  
 
