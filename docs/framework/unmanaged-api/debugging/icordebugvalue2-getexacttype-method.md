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
ms.openlocfilehash: dcec97bac2aefc8db1f9351f1dacb0f36fc0d2a0
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396808"
---
# <a name="icordebugvalue2getexacttype-method"></a><span data-ttu-id="065f0-102">Método ICorDebugValue2::GetExactType</span><span class="sxs-lookup"><span data-stu-id="065f0-102">ICorDebugValue2::GetExactType Method</span></span>
<span data-ttu-id="065f0-103">Obtém um ponteiro de interface para um objeto "ICorDebugType" que representa o <xref:System.Type> desse valor.</span><span class="sxs-lookup"><span data-stu-id="065f0-103">Gets an interface pointer to an "ICorDebugType" object that represents the <xref:System.Type> of this value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="065f0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="065f0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetExactType (  
    [out] ICorDebugType   **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="065f0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="065f0-105">Parameters</span></span>  
 `ppType`  
 <span data-ttu-id="065f0-106">fora Um ponteiro para o endereço de um `ICorDebugType` objeto que representa o <xref:System.Type> do valor representado por esse objeto "ICorDebugValue2".</span><span class="sxs-lookup"><span data-stu-id="065f0-106">[out] A pointer to the address of an `ICorDebugType` object that represents the <xref:System.Type> of the value represented by this "ICorDebugValue2" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="065f0-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="065f0-107">Remarks</span></span>  
 <span data-ttu-id="065f0-108">O método com reconhecimento de genéricos `GetExactType` substitui os métodos [ICorDebugObjectValue:: GetClass](icordebugobjectvalue-getclass-method.md) e [ICorDebugValue:: GetType](icordebugvalue-gettype-method.md) , sendo que cada um retorna informações sobre o tipo de um valor.</span><span class="sxs-lookup"><span data-stu-id="065f0-108">The generics-aware `GetExactType` method supersedes both the [ICorDebugObjectValue::GetClass](icordebugobjectvalue-getclass-method.md) and the [ICorDebugValue::GetType](icordebugvalue-gettype-method.md) methods, each of which return information about the type of a value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="065f0-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="065f0-109">Requirements</span></span>  
 <span data-ttu-id="065f0-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="065f0-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="065f0-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="065f0-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="065f0-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="065f0-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="065f0-113">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="065f0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="065f0-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="065f0-114">See also</span></span>
