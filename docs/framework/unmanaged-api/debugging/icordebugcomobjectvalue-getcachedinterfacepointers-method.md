---
title: Método ICorDebugComObjectValue::GetCachedInterfacePointers
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4a77e7f20aba1908a63d77b4ccada7fabacf55f7
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025855"
---
# <a name="icordebugcomobjectvaluegetcachedinterfacepointers-method"></a><span data-ttu-id="55ab5-102">Método ICorDebugComObjectValue::GetCachedInterfacePointers</span><span class="sxs-lookup"><span data-stu-id="55ab5-102">ICorDebugComObjectValue::GetCachedInterfacePointers Method</span></span>
<span data-ttu-id="55ab5-103">Obtém os ponteiros de interface bruto armazenado em cache no runtime callable wrapper atual (RCW).</span><span class="sxs-lookup"><span data-stu-id="55ab5-103">Gets the raw interface pointers cached on the current runtime callable wrapper (RCW).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55ab5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="55ab5-104">Syntax</span></span>  
  
```  
HRESULT GetCachedInterfacePointers(  
    [in] BOOL bIInspectableOnly,  
    [in] ULONG32 celt,  
    [out] ULONG32 *pceltFetched,  
    [out, size_is(celt), length_is(*pceltFetched) CORDB_ADDRESS *ptrs);  
```  
  
## <a name="parameters"></a><span data-ttu-id="55ab5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="55ab5-105">Parameters</span></span>  
 `bIInspectableOnly`  
 <span data-ttu-id="55ab5-106">[in] Um valor que indica se o método retornará somente interfaces de tempo de execução do Windows (`IInspectable` interfaces) ou todas as interfaces COM que são armazenados em cache, o runtime callable wrapper (RCW).</span><span class="sxs-lookup"><span data-stu-id="55ab5-106">[in] A value that indicates whether the method will return only Windows Runtime interfaces (`IInspectable` interfaces) or all COM interfaces that are cached by the runtime callable wrapper (RCW).</span></span>  
  
 `celt`  
 <span data-ttu-id="55ab5-107">[in] O número de objetos cujos endereços devem ser recuperadas.</span><span class="sxs-lookup"><span data-stu-id="55ab5-107">[in] The number of objects whose addresses are to be retrieved.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="55ab5-108">[out] Um ponteiro para o número de `CORDB_ADDRESS` valores realmente retornados na `ptrs`.</span><span class="sxs-lookup"><span data-stu-id="55ab5-108">[out] A pointer to the number of `CORDB_ADDRESS` values actually returned in `ptrs`.</span></span>  
  
 `ptrs`  
 <span data-ttu-id="55ab5-109">Um ponteiro para o endereço inicial de uma matriz de `CORDB_ADDRESS` que contêm os endereços dos valores armazenados em cache objetos de interface.</span><span class="sxs-lookup"><span data-stu-id="55ab5-109">A pointer to the starting address of an array of `CORDB_ADDRESS` values that contain the addresses of cached interface objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="55ab5-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="55ab5-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55ab5-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="55ab5-111">Requirements</span></span>  
 <span data-ttu-id="55ab5-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="55ab5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55ab5-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="55ab5-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="55ab5-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="55ab5-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="55ab5-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55ab5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55ab5-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="55ab5-116">See also</span></span>

- [<span data-ttu-id="55ab5-117">Interface ICorDebugComObjectValue</span><span class="sxs-lookup"><span data-stu-id="55ab5-117">ICorDebugComObjectValue Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)
- [<span data-ttu-id="55ab5-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="55ab5-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
