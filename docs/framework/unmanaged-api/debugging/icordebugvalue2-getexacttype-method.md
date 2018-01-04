---
title: "Método ICorDebugValue2::GetExactType"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugValue2.GetExactType
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugValue2::GetExactType
helpviewer_keywords:
- ICorDebugValue2::GetExactType method [.NET Framework debugging]
- GetExactType method [.NET Framework debugging]
ms.assetid: 8e9aae1b-d1b7-4b6e-b577-6faf36dcec85
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ad7d0e2ddcd8b66fd87cffa23204ae3b859f368c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvalue2getexacttype-method"></a><span data-ttu-id="51146-102">Método ICorDebugValue2::GetExactType</span><span class="sxs-lookup"><span data-stu-id="51146-102">ICorDebugValue2::GetExactType Method</span></span>
<span data-ttu-id="51146-103">Obtém um ponteiro de interface para um objeto de "ICorDebugType" que representa o <xref:System.Type> desse valor.</span><span class="sxs-lookup"><span data-stu-id="51146-103">Gets an interface pointer to an "ICorDebugType" object that represents the <xref:System.Type> of this value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51146-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="51146-104">Syntax</span></span>  
  
```  
HRESULT GetExactType (  
    [out] ICorDebugType   **ppType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="51146-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="51146-105">Parameters</span></span>  
 `ppType`  
 <span data-ttu-id="51146-106">[out] Um ponteiro para o endereço de um `ICorDebugType` objeto que representa o <xref:System.Type> do valor representado pelo objeto "ICorDebugValue2".</span><span class="sxs-lookup"><span data-stu-id="51146-106">[out] A pointer to the address of an `ICorDebugType` object that represents the <xref:System.Type> of the value represented by this "ICorDebugValue2" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="51146-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="51146-107">Remarks</span></span>  
 <span data-ttu-id="51146-108">O com reconhecimento de genéricos `GetExactType` método substitui ambos o [Icordebugobjectvalue](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md) e [Icordebugvalue](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md) métodos, cada um dos quais retornar informações sobre o tipo de um valor .</span><span class="sxs-lookup"><span data-stu-id="51146-108">The generics-aware `GetExactType` method supersedes both the [ICorDebugObjectValue::GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md) and the [ICorDebugValue::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md) methods, each of which return information about the type of a value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51146-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="51146-109">Requirements</span></span>  
 <span data-ttu-id="51146-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51146-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51146-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="51146-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="51146-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="51146-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="51146-113">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51146-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51146-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="51146-114">See Also</span></span>  
 
