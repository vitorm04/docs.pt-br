---
title: Método ICorDebugValue2::GetExactType
ms.date: 03/30/2017
api_name:
- ICorDebugValue2.GetExactType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue2::GetExactType
helpviewer_keywords:
- ICorDebugValue2::GetExactType method [.NET Framework debugging]
- GetExactType method [.NET Framework debugging]
ms.assetid: 8e9aae1b-d1b7-4b6e-b577-6faf36dcec85
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 002e53d380140a63297a90baa270b5a6f1e5e328
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59192258"
---
# <a name="icordebugvalue2getexacttype-method"></a><span data-ttu-id="1a0e0-102">Método ICorDebugValue2::GetExactType</span><span class="sxs-lookup"><span data-stu-id="1a0e0-102">ICorDebugValue2::GetExactType Method</span></span>
<span data-ttu-id="1a0e0-103">Obtém um ponteiro de interface para um objeto de "ICorDebugType" que representa o <xref:System.Type> desse valor.</span><span class="sxs-lookup"><span data-stu-id="1a0e0-103">Gets an interface pointer to an "ICorDebugType" object that represents the <xref:System.Type> of this value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a0e0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1a0e0-104">Syntax</span></span>  
  
```  
HRESULT GetExactType (  
    [out] ICorDebugType   **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1a0e0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1a0e0-105">Parameters</span></span>  
 `ppType`  
 <span data-ttu-id="1a0e0-106">[out] Um ponteiro para o endereço de um `ICorDebugType` objeto que representa o <xref:System.Type> do valor representado por esse objeto de "ICorDebugValue2".</span><span class="sxs-lookup"><span data-stu-id="1a0e0-106">[out] A pointer to the address of an `ICorDebugType` object that represents the <xref:System.Type> of the value represented by this "ICorDebugValue2" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1a0e0-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="1a0e0-107">Remarks</span></span>  
 <span data-ttu-id="1a0e0-108">O reconhecimento de genéricos `GetExactType` método substitui ambos o [icordebugobjectvalue:: Getclass](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md) e o [icordebugvalue:: GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md) métodos, cada um dos quais retornar informações sobre o tipo de um valor .</span><span class="sxs-lookup"><span data-stu-id="1a0e0-108">The generics-aware `GetExactType` method supersedes both the [ICorDebugObjectValue::GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md) and the [ICorDebugValue::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md) methods, each of which return information about the type of a value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a0e0-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1a0e0-109">Requirements</span></span>  
 <span data-ttu-id="1a0e0-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a0e0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a0e0-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1a0e0-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1a0e0-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1a0e0-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="1a0e0-113">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="1a0e0-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1a0e0-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1a0e0-114">See also</span></span>
