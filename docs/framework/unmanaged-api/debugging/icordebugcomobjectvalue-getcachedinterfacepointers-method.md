---
title: "Método ICorDebugComObjectValue::GetCachedInterfacePointers"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugComObjectValue::GetCachedInterfacePointers
api_location:
- mscordbi.dll
f1_keywords:
- ICorDebugComObjectValue::GetCachedInterfacePointers
helpviewer_keywords:
- ICorDebugComObjectValue::GetCachedInterfacePointers method [.NET Framework debugging]
- GetCachedInterfacePointers method, ICorDebugComObjectValue interface [.NET Framework debugging]
ms.assetid: 08dbd558-bd39-4263-94c2-71e70687aaf0
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2b47395235ce21c7d40e4413702e6c655493a739
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcomobjectvaluegetcachedinterfacepointers-method"></a><span data-ttu-id="c8f49-102">Método ICorDebugComObjectValue::GetCachedInterfacePointers</span><span class="sxs-lookup"><span data-stu-id="c8f49-102">ICorDebugComObjectValue::GetCachedInterfacePointers Method</span></span>
<span data-ttu-id="c8f49-103">Obtém os ponteiros de interface bruto em cache no atual runtime callable wrapper (RCW).</span><span class="sxs-lookup"><span data-stu-id="c8f49-103">Gets the raw interface pointers cached on the current runtime callable wrapper (RCW).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8f49-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c8f49-104">Syntax</span></span>  
  
```  
HRESULT GetCachedInterfacePointers(  
    [in] BOOL bIInspectableOnly,  
    [in] ULONG32 celt,  
    [out] ULONG32 *pceltFetched,  
    [out, size_is(celt), length_is(*pceltFetched) CORDB_ADDRESS *ptrs);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c8f49-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c8f49-105">Parameters</span></span>  
 `bIInspectableOnly`  
 <span data-ttu-id="c8f49-106">[in] Um valor que indica se o método retornará somente [!INCLUDE[wrt](../../../../includes/wrt-md.md)] interfaces (`IInspectable` interfaces) ou interfaces COM todos os que são armazenados em cache pelo runtime callable wrapper (RCW).</span><span class="sxs-lookup"><span data-stu-id="c8f49-106">[in] A value that indicates whether the method will return only [!INCLUDE[wrt](../../../../includes/wrt-md.md)] interfaces (`IInspectable` interfaces) or all COM interfaces that are cached by the runtime callable wrapper (RCW).</span></span>  
  
 `celt`  
 <span data-ttu-id="c8f49-107">[in] O número de objetos cujos endereços devem ser recuperados.</span><span class="sxs-lookup"><span data-stu-id="c8f49-107">[in] The number of objects whose addresses are to be retrieved.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="c8f49-108">[out] Um ponteiro para o número de `CORDB_ADDRESS` valores retornados na verdade em `ptrs`.</span><span class="sxs-lookup"><span data-stu-id="c8f49-108">[out] A pointer to the number of `CORDB_ADDRESS` values actually returned in `ptrs`.</span></span>  
  
 `ptrs`  
 <span data-ttu-id="c8f49-109">Um ponteiro para o endereço inicial de uma matriz de `CORDB_ADDRESS` que contêm os endereços dos valores armazenados em cache objetos de interface.</span><span class="sxs-lookup"><span data-stu-id="c8f49-109">A pointer to the starting address of an array of `CORDB_ADDRESS` values that contain the addresses of cached interface objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c8f49-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="c8f49-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8f49-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c8f49-111">Requirements</span></span>  
 <span data-ttu-id="c8f49-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8f49-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8f49-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c8f49-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c8f49-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c8f49-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c8f49-115">**Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8f49-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8f49-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c8f49-116">See Also</span></span>  
 [<span data-ttu-id="c8f49-117">Interface ICorDebugComObjectValue</span><span class="sxs-lookup"><span data-stu-id="c8f49-117">ICorDebugComObjectValue Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)  
 [<span data-ttu-id="c8f49-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="c8f49-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
