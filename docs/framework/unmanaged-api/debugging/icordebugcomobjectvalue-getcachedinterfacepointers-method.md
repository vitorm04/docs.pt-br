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
ms.openlocfilehash: c1e2b557a5e5794c50986b1af8ec39faba845cc9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125509"
---
# <a name="icordebugcomobjectvaluegetcachedinterfacepointers-method"></a><span data-ttu-id="cedda-102">Método ICorDebugComObjectValue::GetCachedInterfacePointers</span><span class="sxs-lookup"><span data-stu-id="cedda-102">ICorDebugComObjectValue::GetCachedInterfacePointers Method</span></span>
<span data-ttu-id="cedda-103">Obtém os ponteiros de interface bruto armazenados em cache no RCW (tempo de execução Callable Wrapper) atual.</span><span class="sxs-lookup"><span data-stu-id="cedda-103">Gets the raw interface pointers cached on the current runtime callable wrapper (RCW).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cedda-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cedda-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachedInterfacePointers(  
    [in] BOOL bIInspectableOnly,  
    [in] ULONG32 celt,  
    [out] ULONG32 *pceltFetched,  
    [out, size_is(celt), length_is(*pceltFetched) CORDB_ADDRESS *ptrs);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cedda-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cedda-105">Parameters</span></span>  
 `bIInspectableOnly`  
 <span data-ttu-id="cedda-106">no Um valor que indica se o método retornará apenas interfaces Windows Runtime (interfaces`IInspectable`) ou todas as interfaces COM armazenadas em cache pelo RCW (Runtime Callable Wrapper).</span><span class="sxs-lookup"><span data-stu-id="cedda-106">[in] A value that indicates whether the method will return only Windows Runtime interfaces (`IInspectable` interfaces) or all COM interfaces that are cached by the runtime callable wrapper (RCW).</span></span>  
  
 `celt`  
 <span data-ttu-id="cedda-107">no O número de objetos cujos endereços devem ser recuperados.</span><span class="sxs-lookup"><span data-stu-id="cedda-107">[in] The number of objects whose addresses are to be retrieved.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="cedda-108">fora Um ponteiro para o número de `CORDB_ADDRESS` valores realmente retornados em `ptrs`.</span><span class="sxs-lookup"><span data-stu-id="cedda-108">[out] A pointer to the number of `CORDB_ADDRESS` values actually returned in `ptrs`.</span></span>  
  
 `ptrs`  
 <span data-ttu-id="cedda-109">Um ponteiro para o endereço inicial de uma matriz de `CORDB_ADDRESS` valores que contêm os endereços dos objetos de interface em cache.</span><span class="sxs-lookup"><span data-stu-id="cedda-109">A pointer to the starting address of an array of `CORDB_ADDRESS` values that contain the addresses of cached interface objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cedda-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="cedda-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cedda-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cedda-111">Requirements</span></span>  
 <span data-ttu-id="cedda-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cedda-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cedda-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cedda-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cedda-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cedda-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cedda-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cedda-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cedda-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cedda-116">See also</span></span>

- [<span data-ttu-id="cedda-117">Interface ICorDebugComObjectValue</span><span class="sxs-lookup"><span data-stu-id="cedda-117">ICorDebugComObjectValue Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)
- [<span data-ttu-id="cedda-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="cedda-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
