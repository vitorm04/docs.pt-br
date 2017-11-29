---
title: "Método ICorDebugGuidToTypeEnum::Next"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugGuidToTypeEnum.Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugGuidToTypeEnum::Next
helpviewer_keywords:
- ICorDebugGuidToTypeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugGuidToTypeEnum interface [.NET Framework debugging]
ms.assetid: c9937666-8e18-484d-9fe0-b9ac95199530
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 277661c8c5490b5c1f68cb8fdaf1eff5a020250f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugguidtotypeenumnext-method"></a><span data-ttu-id="07cf7-102">Método ICorDebugGuidToTypeEnum::Next</span><span class="sxs-lookup"><span data-stu-id="07cf7-102">ICorDebugGuidToTypeEnum::Next Method</span></span>
<span data-ttu-id="07cf7-103">Obtém o número especificado de [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) instâncias que mapeiam os GUIDs para informações de tipo.</span><span class="sxs-lookup"><span data-stu-id="07cf7-103">Gets the specified number of [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) instances that map GUIDs to type information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07cf7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="07cf7-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched] CorDebugGuidToTypeMapping values[  ],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="07cf7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="07cf7-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="07cf7-106">[in] O número de objetos de mapeamento de tipo de GUID a ser recuperado.</span><span class="sxs-lookup"><span data-stu-id="07cf7-106">[in] The number of GUID-to-type mapping objects to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="07cf7-107">[out] Uma matriz de ponteiros, cada qual apontando para um [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) objeto que mapeia um [!INCLUDE[wrt](../../../../includes/wrt-md.md)] GUID correspondente ao objeto ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="07cf7-107">[out] An array of pointers, each of which points to a [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) object that maps a [!INCLUDE[wrt](../../../../includes/wrt-md.md)] GUID to its corresponding ICorDebugType object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="07cf7-108">[out] Um ponteiro para o número de [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) objetos retornados na verdade em `values`.</span><span class="sxs-lookup"><span data-stu-id="07cf7-108">[out] A pointer to the number of [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) objects actually returned in `values`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="07cf7-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="07cf7-109">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07cf7-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="07cf7-110">Requirements</span></span>  
 <span data-ttu-id="07cf7-111">**Plataformas:**[!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07cf7-111">**Platforms:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span></span>  
  
 <span data-ttu-id="07cf7-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="07cf7-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="07cf7-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="07cf7-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="07cf7-114">**Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07cf7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07cf7-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="07cf7-115">See Also</span></span>  
 [<span data-ttu-id="07cf7-116">Interface ICorDebugGuidToTypeEnum</span><span class="sxs-lookup"><span data-stu-id="07cf7-116">ICorDebugGuidToTypeEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)  
 [<span data-ttu-id="07cf7-117">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="07cf7-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
