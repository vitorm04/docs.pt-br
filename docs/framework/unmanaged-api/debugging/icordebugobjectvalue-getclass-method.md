---
title: "Método ICorDebugObjectValue::GetClass"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugObjectValue.GetClass
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugObjectValue::GetClass
helpviewer_keywords:
- ICorDebugObjectValue::GetClass method [.NET Framework debugging]
- GetClass method, ICorDebugObjectValue interface [.NET Framework debugging]
ms.assetid: 5be25292-8357-445f-a09b-f997c0de761c
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6135dd3806d72b59ce858fab9d0a0b6c3b1f11b6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugobjectvaluegetclass-method"></a><span data-ttu-id="467b6-102">Método ICorDebugObjectValue::GetClass</span><span class="sxs-lookup"><span data-stu-id="467b6-102">ICorDebugObjectValue::GetClass Method</span></span>
<span data-ttu-id="467b6-103">Obtém a classe de valor desse objeto.</span><span class="sxs-lookup"><span data-stu-id="467b6-103">Gets the class of this object value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="467b6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="467b6-104">Syntax</span></span>  
  
```  
HRESULT GetClass (  
    [out] ICorDebugClass     **ppClass  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="467b6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="467b6-105">Parameters</span></span>  
 `ppClass`  
 <span data-ttu-id="467b6-106">[out] Um ponteiro para o endereço de um objeto de "ICorDebugClass" que representa a classe do valor do objeto representado pelo objeto "ICorDebugObjectValue".</span><span class="sxs-lookup"><span data-stu-id="467b6-106">[out] A pointer to the address of an "ICorDebugClass" object that represents the class of the object value represented by this "ICorDebugObjectValue" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="467b6-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="467b6-107">Remarks</span></span>  
 <span data-ttu-id="467b6-108">O `GetClass` e [Icordebugvalue](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md) métodos retornam informações sobre o tipo de um valor; elas são substituídas pelas com reconhecimento de genéricos [Icordebugvalue2](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md).</span><span class="sxs-lookup"><span data-stu-id="467b6-108">The `GetClass` and [ICorDebugValue::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md) methods each return information about the type of a value; they are both superseded by the generics-aware [ICorDebugValue2::GetExactType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="467b6-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="467b6-109">Requirements</span></span>  
 <span data-ttu-id="467b6-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="467b6-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="467b6-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="467b6-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="467b6-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="467b6-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="467b6-113">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="467b6-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="467b6-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="467b6-114">See Also</span></span>  
    
 
