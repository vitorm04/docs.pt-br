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
ms.openlocfilehash: d15938e94d647fd5fded23c72bdc200d198d21a7
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792699"
---
# <a name="icordebugobjectvaluegetclass-method"></a><span data-ttu-id="779df-102">Método ICorDebugObjectValue::GetClass</span><span class="sxs-lookup"><span data-stu-id="779df-102">ICorDebugObjectValue::GetClass Method</span></span>
<span data-ttu-id="779df-103">Obtém a classe desse valor de objeto.</span><span class="sxs-lookup"><span data-stu-id="779df-103">Gets the class of this object value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="779df-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="779df-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClass (  
    [out] ICorDebugClass     **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="779df-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="779df-105">Parameters</span></span>  
 `ppClass`  
 <span data-ttu-id="779df-106">fora Um ponteiro para o endereço de um objeto "ICorDebugClass" que representa a classe do valor do objeto representado por esse objeto "ICorDebugObjectValue".</span><span class="sxs-lookup"><span data-stu-id="779df-106">[out] A pointer to the address of an "ICorDebugClass" object that represents the class of the object value represented by this "ICorDebugObjectValue" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="779df-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="779df-107">Remarks</span></span>  
 <span data-ttu-id="779df-108">Os métodos `GetClass` e [ICorDebugValue:: GetType](icordebugvalue-gettype-method.md) retornam informações sobre o tipo de um valor; Eles são ambos substituídos pelo [ICorDebugValue2:: Getexatotype](icordebugvalue2-getexacttype-method.md)com reconhecimento de genéricos.</span><span class="sxs-lookup"><span data-stu-id="779df-108">The `GetClass` and [ICorDebugValue::GetType](icordebugvalue-gettype-method.md) methods each return information about the type of a value; they are both superseded by the generics-aware [ICorDebugValue2::GetExactType](icordebugvalue2-getexacttype-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="779df-109">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="779df-109">Requirements</span></span>  
 <span data-ttu-id="779df-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="779df-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="779df-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="779df-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="779df-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="779df-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="779df-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="779df-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="779df-114">Veja também</span><span class="sxs-lookup"><span data-stu-id="779df-114">See also</span></span>
