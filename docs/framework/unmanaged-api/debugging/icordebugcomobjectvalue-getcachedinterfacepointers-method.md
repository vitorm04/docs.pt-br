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
ms.openlocfilehash: fa22c17ed7d5bcd689f21d2d855d9be7a6a8e164
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82892804"
---
# <a name="icordebugcomobjectvaluegetcachedinterfacepointers-method"></a><span data-ttu-id="58eb2-102">Método ICorDebugComObjectValue::GetCachedInterfacePointers</span><span class="sxs-lookup"><span data-stu-id="58eb2-102">ICorDebugComObjectValue::GetCachedInterfacePointers Method</span></span>
<span data-ttu-id="58eb2-103">Obtém os ponteiros de interface bruto armazenados em cache no RCW (tempo de execução Callable Wrapper) atual.</span><span class="sxs-lookup"><span data-stu-id="58eb2-103">Gets the raw interface pointers cached on the current runtime callable wrapper (RCW).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58eb2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="58eb2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachedInterfacePointers(  
    [in] BOOL bIInspectableOnly,  
    [in] ULONG32 celt,  
    [out] ULONG32 *pceltFetched,  
    [out, size_is(celt), length_is(*pceltFetched) CORDB_ADDRESS *ptrs);  
```  
  
## <a name="parameters"></a><span data-ttu-id="58eb2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="58eb2-105">Parameters</span></span>  
 `bIInspectableOnly`  
 <span data-ttu-id="58eb2-106">no Um valor que indica se o método retornará apenas interfaces Windows Runtime (`IInspectable` interfaces) ou todas as interfaces com armazenadas em cache pelo RCW (Runtime Callable Wrapper).</span><span class="sxs-lookup"><span data-stu-id="58eb2-106">[in] A value that indicates whether the method will return only Windows Runtime interfaces (`IInspectable` interfaces) or all COM interfaces that are cached by the runtime callable wrapper (RCW).</span></span>  
  
 `celt`  
 <span data-ttu-id="58eb2-107">no O número de objetos cujos endereços devem ser recuperados.</span><span class="sxs-lookup"><span data-stu-id="58eb2-107">[in] The number of objects whose addresses are to be retrieved.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="58eb2-108">fora Um ponteiro para o número de `CORDB_ADDRESS` valores realmente retornados em `ptrs`.</span><span class="sxs-lookup"><span data-stu-id="58eb2-108">[out] A pointer to the number of `CORDB_ADDRESS` values actually returned in `ptrs`.</span></span>  
  
 `ptrs`  
 <span data-ttu-id="58eb2-109">Um ponteiro para o endereço inicial de uma matriz de `CORDB_ADDRESS` valores que contêm os endereços dos objetos de interface em cache.</span><span class="sxs-lookup"><span data-stu-id="58eb2-109">A pointer to the starting address of an array of `CORDB_ADDRESS` values that contain the addresses of cached interface objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="58eb2-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="58eb2-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58eb2-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="58eb2-111">Requirements</span></span>  
 <span data-ttu-id="58eb2-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58eb2-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58eb2-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="58eb2-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="58eb2-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="58eb2-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="58eb2-115">**.NET Framework versões:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58eb2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58eb2-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="58eb2-116">See also</span></span>

- [<span data-ttu-id="58eb2-117">Interface ICorDebugComObjectValue</span><span class="sxs-lookup"><span data-stu-id="58eb2-117">ICorDebugComObjectValue Interface</span></span>](icordebugcomobjectvalue-interface.md)
- [<span data-ttu-id="58eb2-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="58eb2-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
