---
title: "Método ICorDebugValue::GetType"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugValue.GetType
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugValue::GetType
helpviewer_keywords:
- ICorDebugValue::GetType method [.NET Framework debugging]
- GetType method, ICorDebugValue interface [.NET Framework debugging]
ms.assetid: 41e2d503-e1f1-407b-abe0-6a29adb3e0d1
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2a79ef332361fdaa3a23cc4e13daa8b4a8303d2c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvaluegettype-method"></a><span data-ttu-id="73915-102">Método ICorDebugValue::GetType</span><span class="sxs-lookup"><span data-stu-id="73915-102">ICorDebugValue::GetType Method</span></span>
<span data-ttu-id="73915-103">Obtém o tipo primitivo do objeto "ICorDebugValue".</span><span class="sxs-lookup"><span data-stu-id="73915-103">Gets the primitive type of this "ICorDebugValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73915-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="73915-104">Syntax</span></span>  
  
```  
HRESULT GetType (  
    [out] CorElementType   *pType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="73915-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="73915-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="73915-106">[out] Um ponteiro para um valor da enumeração "CorElementType" que indica o tipo do valor.</span><span class="sxs-lookup"><span data-stu-id="73915-106">[out] A pointer to a value of the "CorElementType" enumeration that indicates the value's type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73915-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="73915-107">Remarks</span></span>  
 <span data-ttu-id="73915-108">Se o objeto for um tipo complexo de tempo de execução, esse tipo pode ser examinado por meio das subclasses apropriadas a `ICorDebugValue` interface.</span><span class="sxs-lookup"><span data-stu-id="73915-108">If the object is a complex run-time type, that type may be examined through the appropriate subclasses of the `ICorDebugValue` interface.</span></span> <span data-ttu-id="73915-109">Por exemplo, "ICorDebugObjectValue", que herda de `ICorDebugValue`, representa um tipo complexo.</span><span class="sxs-lookup"><span data-stu-id="73915-109">For example, "ICorDebugObjectValue", which inherits from `ICorDebugValue`, represents a complex type.</span></span>  
  
 <span data-ttu-id="73915-110">O `GetType` e [Icordebugobjectvalue](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md) métodos retornam informações sobre o tipo de um valor.</span><span class="sxs-lookup"><span data-stu-id="73915-110">The `GetType` and [ICorDebugObjectValue::GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md) methods each return information about the type of a value.</span></span> <span data-ttu-id="73915-111">Elas são substituídas pelas com reconhecimento de genéricos [Icordebugvalue2](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="73915-111">They are both superseded by the generics-aware [ICorDebugValue2::GetExactType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73915-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="73915-112">Requirements</span></span>  
 <span data-ttu-id="73915-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73915-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73915-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="73915-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="73915-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="73915-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73915-116">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73915-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73915-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="73915-117">See Also</span></span>  
 
