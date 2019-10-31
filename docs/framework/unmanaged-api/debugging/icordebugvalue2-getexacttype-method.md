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
ms.openlocfilehash: 441d225dadbbca09ab27c8ccd70debe32f4c12da
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140259"
---
# <a name="icordebugvalue2getexacttype-method"></a><span data-ttu-id="d3bd9-102">Método ICorDebugValue2::GetExactType</span><span class="sxs-lookup"><span data-stu-id="d3bd9-102">ICorDebugValue2::GetExactType Method</span></span>
<span data-ttu-id="d3bd9-103">Obtém um ponteiro de interface para um objeto "ICorDebugType" que representa a <xref:System.Type> desse valor.</span><span class="sxs-lookup"><span data-stu-id="d3bd9-103">Gets an interface pointer to an "ICorDebugType" object that represents the <xref:System.Type> of this value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3bd9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d3bd9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetExactType (  
    [out] ICorDebugType   **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d3bd9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d3bd9-105">Parameters</span></span>  
 `ppType`  
 <span data-ttu-id="d3bd9-106">fora Um ponteiro para o endereço de um objeto de `ICorDebugType` que representa a <xref:System.Type> do valor representado por esse objeto "ICorDebugValue2".</span><span class="sxs-lookup"><span data-stu-id="d3bd9-106">[out] A pointer to the address of an `ICorDebugType` object that represents the <xref:System.Type> of the value represented by this "ICorDebugValue2" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d3bd9-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="d3bd9-107">Remarks</span></span>  
 <span data-ttu-id="d3bd9-108">O método `GetExactType` com reconhecimento de genéricos substitui os métodos [ICorDebugObjectValue:: GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md) e [ICorDebugValue:: GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md) , cada um deles retorna informações sobre o tipo de um valor.</span><span class="sxs-lookup"><span data-stu-id="d3bd9-108">The generics-aware `GetExactType` method supersedes both the [ICorDebugObjectValue::GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md) and the [ICorDebugValue::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md) methods, each of which return information about the type of a value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3bd9-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d3bd9-109">Requirements</span></span>  
 <span data-ttu-id="d3bd9-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3bd9-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3bd9-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d3bd9-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d3bd9-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d3bd9-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d3bd9-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3bd9-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3bd9-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d3bd9-114">See also</span></span>
