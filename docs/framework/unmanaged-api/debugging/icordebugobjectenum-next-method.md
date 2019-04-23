---
title: Método ICorDebugObjectEnum::Next
ms.date: 03/30/2017
api_name:
- ICorDebugObjectEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectEnum::Next
helpviewer_keywords:
- Next method, ICorDebugObjectEnum interface [.NET Framework debugging]
- ICorDebugObjectEnum::Next method [.NET Framework debugging]
ms.assetid: 10093e3d-26b6-4ad7-8ef3-bbf66243fc02
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6998be3daf0ab6a6290a3400b96c32227df3e022
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59175079"
---
# <a name="icordebugobjectenumnext-method"></a><span data-ttu-id="49a86-102">Método ICorDebugObjectEnum::Next</span><span class="sxs-lookup"><span data-stu-id="49a86-102">ICorDebugObjectEnum::Next Method</span></span>
<span data-ttu-id="49a86-103">Obtém os endereços virtuais (relacionados RVAs) do número especificado de objetos de enumeração, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="49a86-103">Gets the relative virtual addresses (RVAs) of the specified number of objects from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49a86-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="49a86-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]    
        CORDB_ADDRESS objects[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="49a86-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="49a86-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="49a86-106">[in] O número de objetos a serem recuperados.</span><span class="sxs-lookup"><span data-stu-id="49a86-106">[in] The number of objects to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="49a86-107">[out] Uma matriz de ponteiros, cada qual apontando para um objeto CORDB_ADDRESS.</span><span class="sxs-lookup"><span data-stu-id="49a86-107">[out] An array of pointers, each of which points to a CORDB_ADDRESS object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="49a86-108">[out] Ponteiro para o número de objetos, na verdade, é retornado.</span><span class="sxs-lookup"><span data-stu-id="49a86-108">[out] Pointer to the number of objects actually returned.</span></span> <span data-ttu-id="49a86-109">Esse valor pode ser nulo se `celt` é um.</span><span class="sxs-lookup"><span data-stu-id="49a86-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49a86-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="49a86-110">Requirements</span></span>  
 <span data-ttu-id="49a86-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49a86-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49a86-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="49a86-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="49a86-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="49a86-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="49a86-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49a86-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49a86-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="49a86-115">See also</span></span>
