---
title: Método ICorDebugReferenceValue::Dereference
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue.Dereference
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue::Dereference
helpviewer_keywords:
- ICorDebugReferenceValue::Dereference method [.NET Framework debugging]
- Dereference method [.NET Framework debugging]
ms.assetid: 5ec8cf76-3deb-4ce6-9a49-77a4c35d80b9
topic_type:
- apiref
ms.openlocfilehash: 6bb2a6b68a3c6e981a2d6c833d3f44d4c836bd23
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124004"
---
# <a name="icordebugreferencevaluedereference-method"></a><span data-ttu-id="1e461-102">Método ICorDebugReferenceValue::Dereference</span><span class="sxs-lookup"><span data-stu-id="1e461-102">ICorDebugReferenceValue::Dereference Method</span></span>
<span data-ttu-id="1e461-103">Obtém o objeto que é referenciado.</span><span class="sxs-lookup"><span data-stu-id="1e461-103">Gets the object that is referenced.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e461-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1e461-104">Syntax</span></span>  
  
```cpp  
HRESULT Dereference (  
    [out] ICorDebugValue  **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1e461-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1e461-105">Parameters</span></span>  
 `ppValue`  
 <span data-ttu-id="1e461-106">fora Um ponteiro para o endereço de um ICorDebugValue que representa o objeto ao qual esse objeto ICorDebugReferenceValue aponta.</span><span class="sxs-lookup"><span data-stu-id="1e461-106">[out] A pointer to the address of an ICorDebugValue that represents the object to which this ICorDebugReferenceValue object points.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1e461-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="1e461-107">Remarks</span></span>  
 <span data-ttu-id="1e461-108">O objeto `ICorDebugValue` é válido somente enquanto sua referência ainda não foi desabilitada.</span><span class="sxs-lookup"><span data-stu-id="1e461-108">The `ICorDebugValue` object is valid only while its reference has not yet been disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e461-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1e461-109">Requirements</span></span>  
 <span data-ttu-id="1e461-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1e461-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e461-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1e461-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1e461-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1e461-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1e461-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e461-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
