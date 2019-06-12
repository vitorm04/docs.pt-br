---
title: Método ICorDebugGuidToTypeEnum::Next
ms.date: 03/30/2017
api_name:
- ICorDebugGuidToTypeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGuidToTypeEnum::Next
helpviewer_keywords:
- ICorDebugGuidToTypeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugGuidToTypeEnum interface [.NET Framework debugging]
ms.assetid: c9937666-8e18-484d-9fe0-b9ac95199530
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 160ddbf9be8eb9f3b99d159aa8b36a22b58a9f55
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025814"
---
# <a name="icordebugguidtotypeenumnext-method"></a><span data-ttu-id="6beb1-102">Método ICorDebugGuidToTypeEnum::Next</span><span class="sxs-lookup"><span data-stu-id="6beb1-102">ICorDebugGuidToTypeEnum::Next Method</span></span>
<span data-ttu-id="6beb1-103">Obtém o número especificado de [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) instâncias que mapeiam as GUIDs para informações de tipo.</span><span class="sxs-lookup"><span data-stu-id="6beb1-103">Gets the specified number of [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) instances that map GUIDs to type information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6beb1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6beb1-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched] CorDebugGuidToTypeMapping values[  ],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6beb1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6beb1-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="6beb1-106">[in] O número de objetos de mapeamento de tipo de GUID a ser recuperado.</span><span class="sxs-lookup"><span data-stu-id="6beb1-106">[in] The number of GUID-to-type mapping objects to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="6beb1-107">[out] Uma matriz de ponteiros, cada qual apontando para um [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) objeto que mapeia um GUID de tempo de execução do Windows para seu objeto correspondente do ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="6beb1-107">[out] An array of pointers, each of which points to a [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) object that maps a Windows Runtime GUID to its corresponding ICorDebugType object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="6beb1-108">[out] Um ponteiro para o número de [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) objetos, na verdade, são retornados em `values`.</span><span class="sxs-lookup"><span data-stu-id="6beb1-108">[out] A pointer to the number of [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) objects actually returned in `values`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6beb1-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="6beb1-109">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6beb1-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6beb1-110">Requirements</span></span>  
 <span data-ttu-id="6beb1-111">**Plataformas:** Tempo de Execução do Windows</span><span class="sxs-lookup"><span data-stu-id="6beb1-111">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="6beb1-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6beb1-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6beb1-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6beb1-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6beb1-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6beb1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6beb1-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6beb1-115">See also</span></span>

- [<span data-ttu-id="6beb1-116">Interface ICorDebugGuidToTypeEnum</span><span class="sxs-lookup"><span data-stu-id="6beb1-116">ICorDebugGuidToTypeEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)
- [<span data-ttu-id="6beb1-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="6beb1-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
