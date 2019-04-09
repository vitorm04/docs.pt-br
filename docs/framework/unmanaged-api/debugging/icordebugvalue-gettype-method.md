---
title: Método ICorDebugValue::GetType
ms.date: 03/30/2017
api_name:
- ICorDebugValue.GetType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue::GetType
helpviewer_keywords:
- ICorDebugValue::GetType method [.NET Framework debugging]
- GetType method, ICorDebugValue interface [.NET Framework debugging]
ms.assetid: 41e2d503-e1f1-407b-abe0-6a29adb3e0d1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 83265c4f6dffed76f1710378cf5293aac7020ef2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59119347"
---
# <a name="icordebugvaluegettype-method"></a><span data-ttu-id="ceca4-102">Método ICorDebugValue::GetType</span><span class="sxs-lookup"><span data-stu-id="ceca4-102">ICorDebugValue::GetType Method</span></span>
<span data-ttu-id="ceca4-103">Obtém o tipo primitivo deste objeto de "ICorDebugValue".</span><span class="sxs-lookup"><span data-stu-id="ceca4-103">Gets the primitive type of this "ICorDebugValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ceca4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ceca4-104">Syntax</span></span>  
  
```  
HRESULT GetType (  
    [out] CorElementType   *pType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ceca4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ceca4-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="ceca4-106">[out] Um ponteiro para um valor de enumeração "CorElementType" que indica o tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="ceca4-106">[out] A pointer to a value of the "CorElementType" enumeration that indicates the value's type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ceca4-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="ceca4-107">Remarks</span></span>  
 <span data-ttu-id="ceca4-108">Se o objeto for um tipo complexo de tempo de execução, esse tipo poderá ser examinado por meio de subclasses apropriadas do `ICorDebugValue` interface.</span><span class="sxs-lookup"><span data-stu-id="ceca4-108">If the object is a complex run-time type, that type may be examined through the appropriate subclasses of the `ICorDebugValue` interface.</span></span> <span data-ttu-id="ceca4-109">Por exemplo, "ICorDebugObjectValue", que herda de `ICorDebugValue`, representa um tipo complexo.</span><span class="sxs-lookup"><span data-stu-id="ceca4-109">For example, "ICorDebugObjectValue", which inherits from `ICorDebugValue`, represents a complex type.</span></span>  
  
 <span data-ttu-id="ceca4-110">O `GetType` e [icordebugobjectvalue:: Getclass](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md) métodos cada retornam informações sobre o tipo de um valor.</span><span class="sxs-lookup"><span data-stu-id="ceca4-110">The `GetType` and [ICorDebugObjectValue::GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md) methods each return information about the type of a value.</span></span> <span data-ttu-id="ceca4-111">Elas são substituídas pelo reconhecimento de genéricos [ICorDebugValue2::GetExactType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="ceca4-111">They are both superseded by the generics-aware [ICorDebugValue2::GetExactType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ceca4-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ceca4-112">Requirements</span></span>  
 <span data-ttu-id="ceca4-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ceca4-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ceca4-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ceca4-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ceca4-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ceca4-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="ceca4-116">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="ceca4-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ceca4-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ceca4-117">See also</span></span>
