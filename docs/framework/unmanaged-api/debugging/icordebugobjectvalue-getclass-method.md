---
title: Método ICorDebugObjectValue::GetClass
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue.GetClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue::GetClass
helpviewer_keywords:
- ICorDebugObjectValue::GetClass method [.NET Framework debugging]
- GetClass method, ICorDebugObjectValue interface [.NET Framework debugging]
ms.assetid: 5be25292-8357-445f-a09b-f997c0de761c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7a20ab7a7ecb5d01351d0c912e08955f44b26d5f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67756992"
---
# <a name="icordebugobjectvaluegetclass-method"></a><span data-ttu-id="2b09f-102">Método ICorDebugObjectValue::GetClass</span><span class="sxs-lookup"><span data-stu-id="2b09f-102">ICorDebugObjectValue::GetClass Method</span></span>
<span data-ttu-id="2b09f-103">Obtém a classe de valor desse objeto.</span><span class="sxs-lookup"><span data-stu-id="2b09f-103">Gets the class of this object value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b09f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2b09f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClass (  
    [out] ICorDebugClass     **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2b09f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2b09f-105">Parameters</span></span>  
 `ppClass`  
 <span data-ttu-id="2b09f-106">[out] Um ponteiro para o endereço de um objeto de "ICorDebugClass" que representa a classe do valor do objeto representado por esse objeto de "ICorDebugObjectValue".</span><span class="sxs-lookup"><span data-stu-id="2b09f-106">[out] A pointer to the address of an "ICorDebugClass" object that represents the class of the object value represented by this "ICorDebugObjectValue" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2b09f-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="2b09f-107">Remarks</span></span>  
 <span data-ttu-id="2b09f-108">O `GetClass` e [icordebugvalue:: GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md) informações sobre o tipo de um valor de retorno de métodos cada; elas são substituídas pelo reconhecimento de genéricos [ICorDebugValue2::GetExactType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md).</span><span class="sxs-lookup"><span data-stu-id="2b09f-108">The `GetClass` and [ICorDebugValue::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md) methods each return information about the type of a value; they are both superseded by the generics-aware [ICorDebugValue2::GetExactType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b09f-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2b09f-109">Requirements</span></span>  
 <span data-ttu-id="2b09f-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b09f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b09f-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2b09f-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2b09f-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2b09f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2b09f-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b09f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b09f-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2b09f-114">See also</span></span>
