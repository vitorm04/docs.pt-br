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
ms.openlocfilehash: 06e9c7af1c4a769bfb45a8e9f805d97b3bad94aa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61994533"
---
# <a name="icordebugobjectvaluegetclass-method"></a><span data-ttu-id="9b10b-102">Método ICorDebugObjectValue::GetClass</span><span class="sxs-lookup"><span data-stu-id="9b10b-102">ICorDebugObjectValue::GetClass Method</span></span>
<span data-ttu-id="9b10b-103">Obtém a classe de valor desse objeto.</span><span class="sxs-lookup"><span data-stu-id="9b10b-103">Gets the class of this object value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b10b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9b10b-104">Syntax</span></span>  
  
```  
HRESULT GetClass (  
    [out] ICorDebugClass     **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9b10b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9b10b-105">Parameters</span></span>  
 `ppClass`  
 <span data-ttu-id="9b10b-106">[out] Um ponteiro para o endereço de um objeto de "ICorDebugClass" que representa a classe do valor do objeto representado por esse objeto de "ICorDebugObjectValue".</span><span class="sxs-lookup"><span data-stu-id="9b10b-106">[out] A pointer to the address of an "ICorDebugClass" object that represents the class of the object value represented by this "ICorDebugObjectValue" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9b10b-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="9b10b-107">Remarks</span></span>  
 <span data-ttu-id="9b10b-108">O `GetClass` e [icordebugvalue:: GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md) informações sobre o tipo de um valor de retorno de métodos cada; elas são substituídas pelo reconhecimento de genéricos [ICorDebugValue2::GetExactType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md).</span><span class="sxs-lookup"><span data-stu-id="9b10b-108">The `GetClass` and [ICorDebugValue::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md) methods each return information about the type of a value; they are both superseded by the generics-aware [ICorDebugValue2::GetExactType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b10b-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9b10b-109">Requirements</span></span>  
 <span data-ttu-id="9b10b-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b10b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b10b-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9b10b-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9b10b-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9b10b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9b10b-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b10b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b10b-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9b10b-114">See also</span></span>
