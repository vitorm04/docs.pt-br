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
ms.openlocfilehash: 6c5e5d1c9f734e097fc9e871d7a0cffdc9bb9138
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791131"
---
# <a name="icordebugvalue2getexacttype-method"></a><span data-ttu-id="9fc5d-102">Método ICorDebugValue2::GetExactType</span><span class="sxs-lookup"><span data-stu-id="9fc5d-102">ICorDebugValue2::GetExactType Method</span></span>
<span data-ttu-id="9fc5d-103">Obtém um ponteiro de interface para um objeto "ICorDebugType" que representa a <xref:System.Type> desse valor.</span><span class="sxs-lookup"><span data-stu-id="9fc5d-103">Gets an interface pointer to an "ICorDebugType" object that represents the <xref:System.Type> of this value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fc5d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9fc5d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetExactType (  
    [out] ICorDebugType   **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9fc5d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9fc5d-105">Parameters</span></span>  
 `ppType`  
 <span data-ttu-id="9fc5d-106">fora Um ponteiro para o endereço de um objeto de `ICorDebugType` que representa a <xref:System.Type> do valor representado por esse objeto "ICorDebugValue2".</span><span class="sxs-lookup"><span data-stu-id="9fc5d-106">[out] A pointer to the address of an `ICorDebugType` object that represents the <xref:System.Type> of the value represented by this "ICorDebugValue2" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9fc5d-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="9fc5d-107">Remarks</span></span>  
 <span data-ttu-id="9fc5d-108">O método `GetExactType` com reconhecimento de genéricos substitui os métodos [ICorDebugObjectValue:: GetClass](icordebugobjectvalue-getclass-method.md) e [ICorDebugValue:: GetType](icordebugvalue-gettype-method.md) , cada um deles retorna informações sobre o tipo de um valor.</span><span class="sxs-lookup"><span data-stu-id="9fc5d-108">The generics-aware `GetExactType` method supersedes both the [ICorDebugObjectValue::GetClass](icordebugobjectvalue-getclass-method.md) and the [ICorDebugValue::GetType](icordebugvalue-gettype-method.md) methods, each of which return information about the type of a value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9fc5d-109">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="9fc5d-109">Requirements</span></span>  
 <span data-ttu-id="9fc5d-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9fc5d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9fc5d-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9fc5d-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9fc5d-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9fc5d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9fc5d-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9fc5d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fc5d-114">Veja também</span><span class="sxs-lookup"><span data-stu-id="9fc5d-114">See also</span></span>
