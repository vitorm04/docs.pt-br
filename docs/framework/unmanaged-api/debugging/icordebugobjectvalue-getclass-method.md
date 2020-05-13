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
ms.openlocfilehash: b0e8fd162ccc1cfc944fb870f493febfe2e5ef42
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207678"
---
# <a name="icordebugobjectvaluegetclass-method"></a><span data-ttu-id="ab530-102">Método ICorDebugObjectValue::GetClass</span><span class="sxs-lookup"><span data-stu-id="ab530-102">ICorDebugObjectValue::GetClass Method</span></span>
<span data-ttu-id="ab530-103">Obtém a classe desse valor de objeto.</span><span class="sxs-lookup"><span data-stu-id="ab530-103">Gets the class of this object value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab530-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ab530-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClass (  
    [out] ICorDebugClass     **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ab530-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ab530-105">Parameters</span></span>  
 `ppClass`  
 <span data-ttu-id="ab530-106">fora Um ponteiro para o endereço de um objeto "ICorDebugClass" que representa a classe do valor do objeto representado por esse objeto "ICorDebugObjectValue".</span><span class="sxs-lookup"><span data-stu-id="ab530-106">[out] A pointer to the address of an "ICorDebugClass" object that represents the class of the object value represented by this "ICorDebugObjectValue" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ab530-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="ab530-107">Remarks</span></span>  
 <span data-ttu-id="ab530-108">Os `GetClass` métodos e [ICorDebugValue:: GetType](icordebugvalue-gettype-method.md) retornam informações sobre o tipo de um valor; eles são ambos substituídos pelo [ICorDebugValue2:: getexatotype](icordebugvalue2-getexacttype-method.md)com reconhecimento de genéricos.</span><span class="sxs-lookup"><span data-stu-id="ab530-108">The `GetClass` and [ICorDebugValue::GetType](icordebugvalue-gettype-method.md) methods each return information about the type of a value; they are both superseded by the generics-aware [ICorDebugValue2::GetExactType](icordebugvalue2-getexacttype-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab530-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ab530-109">Requirements</span></span>  
 <span data-ttu-id="ab530-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab530-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab530-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ab530-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ab530-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ab530-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ab530-113">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab530-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab530-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="ab530-114">See also</span></span>
